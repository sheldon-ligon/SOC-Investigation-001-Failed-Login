# SOC Investigation 001: Failed Login Analysis

## Objective

Investigate failed Windows authentication attempts using Splunk and Windows Security Event Logs to identify authentication failures, analyze relevant security events, and document findings.

## Environment

### Systems

- Ubuntu Server (Splunk Enterprise)
- Windows 11 Lab Workstation (WIN11-LAB)

### Data Sources

- Windows Security Event Logs
- Splunk Universal Forwarder

### Tools Used

- Splunk Enterprise
- Windows Event Viewer
- Sysmon
- Splunk Universal Forwarder

## Investigation Process

1. Generated multiple failed login attempts on WIN11-LAB using an incorrect password.
2. Collected authentication events in Splunk.
3. Investigated Windows Security Event ID 4625 (Failed Logon).
4. Verified a successful authentication using Event ID 4624 after the failed attempts.
5. Documented findings and evidence.

## Evidence

### Failed Logon Event

- Event ID: 4625
- Host: WIN11-LAB
- Account: CN_Win11_lab
- Failure Reason: Unknown user name or bad password
- Logon Type: 2 (Interactive)

### Successful Logon Event

- Event ID: 4624
- Successful authentication observed following failed login attempts.

## Findings

Analysis of Windows Security Event Logs identified eight failed authentication attempts against the account CN_Win11_lab on host WIN11-LAB.

The failures were recorded as Event ID 4625 and were associated with Logon Type 2 (Interactive Logon), indicating a user physically interacting with the workstation. The failure reason was identified as "Unknown user name or bad password."

A successful authentication event (Event ID 4624) was observed shortly after the failed attempts, confirming successful access following the correction of the credentials.

No evidence of remote access activity, lateral movement, or additional affected accounts was identified during the investigation period.
## MITRE ATT&CK Mapping

### T1110 - Brute Force

Repeated authentication failures are consistent with password guessing or brute force activity. In this lab, the events were intentionally generated to simulate failed authentication attempts for investigation purposes.

## Recommendations

- Monitor repeated Event ID 4625 activity.
- Configure alerts for excessive failed login attempts.
- Correlate failed logons with successful authentication events.
- Investigate repeated failures against privileged accounts.
