# SOC Lab with Real-Time Threat Monitoring

![Wazuh Dashboard](./images/wazuh-dashboard.png)


## Abstract

This project presents the design, implementation, and evaluation of a SOC homelab capable of real-time cyber threat detection and incident response. The lab utilizes open-source tools including:

- Wazuh for SIEM
- Suricata for network intrusion detection
- pfSense for firewall management
- Atomic Red Team tests 
- Integration of VirusTotal and Abuse IP DB
- Slack configuration in wazuh for notification of alerts

Key features:
- Simulates attack scenarios (brute-force attacks, malware infections, file integrity violations)
- Implements MITRE ATT&CK techniques
- Integrates real-time Slack alerting
- Managed using Jira for project tracking

## Table of Contents

- [Hardware Requirements](#hardware-requirements)
- [Environment Setup](#environment-setup)
- [Simulated Attack Scenarios](#simulated-attack-scenarios)
- [MITRE ATT&CK Framework](#attack-emulation-using-mitre-attck-framework)
- [Real-Time Alerting](#setting-up-slack-to-receive-alerts-in-real-time)
- [Conclusion](#conclusion)
- [Future Work](#future-work)

## Hardware Requirements

| Component           | Memory (RAM) | Storage |
|---------------------|--------------|---------|
| Wazuh SIEM VM       | 12 GB        | 50+ GB  |
| PfSense Firewall VM | 4 GB         | 20 GB   |
| Windows Server VM   | 8 GB         | 10 GB   |
| Windows Client VM   | 4 GB         | 10 GB   |
| Kali Linux VM       | 4 GB         | 10 GB   |


## SOC Homelab Architecture

### Core Components
- **Host System**: Windows machine running VMware Workstation Pro 17 (Free License)
- **pfSense Firewall**: Central gateway for all network traffic
- **Segmented Networks**:
  - `VMnet2`: Kali Linux attack machine (192.168.1.2)
  - `VMnet3`: Domain Controller + Victim machines
  - `VMnet4`: Wazuh SIEM server (192.168.4.1)


### Core Components

#### SIEM (Wazuh)
![Wazuh Dashboard](images/wazuh-dashboard.png)

#### IDS (Suricata)
![Suricata IDS](images/suricata-dashboard.png)

#### Firewall (pfSense)
![pfSense Dashboard](images/pfsense-dashboard.png)

#### Network Architecture
![Homelab Network Diagram](images/image6.png)

### Configuration Steps

1. **pfSense Setup**:
   - Interface configuration
   - NAT and IP forwarding
   - Syslog integration with Wazuh

2. **Wazuh Installation**:
   - Server setup
   - Agent deployment

## Simulated Attack Scenarios

### File Integrity Monitoring
![FIM Working](images/image16.png)

### Brute-force RDP Attacks
![Hydra Attack](images/image19.png)
![Auth Failure Logs](images/image20.png)

### Malware Detection with VirusTotal
![Active Response](images/image21.png)

### Malicious IP Blocking
![Blocking IP](images/image22.png)

### Suspicious Command Detection
![Malicious Commands](images/image24.png)

## Attack Emulation Using MITRE ATT&CK Framework

| Technique | Description 
|-----------|-------------
| T1053 | Scheduled Task/Job 
| T1218.010 | Regsvr32 Execution 
| T1518.001 | Security Software Discovery 
| T1548.003 | Windows Service Modification
| T1123 | Audio Capture

## Real-Time Alerting with Slack
![Slack Notification](images/slack-alerts.png)

## Conclusion

This project successfully implemented a functional SOC homelab with:
- Real-time threat detection
- Comprehensive monitoring
- Automated response capabilities
- MITRE ATT&CK emulation
- Effective alerting mechanisms

## Future Work

Planned enhancements:
- Suricata NIDS fine-tuning
- Automated incident response playbooks
- Expanded MITRE ATT&CK coverage
- Threat intelligence integration

## Acknowledgements

Special thanks to:
- [Dayspring Johnson](https://www.linkedin.com/in/dayspringjohnson/)
- [Steven Rocks](https://www.linkedin.com/company/mydfir/about/)

## References

1. [CyberWox SOC Homelab](https://www.youtube.com/playlist?list=PLDqMNdDvMsRkmtiKcZwbhOz7MeLQE0r3G)
2. [MyDFIR Projects](https://www.youtube.com/playlist?list=PLG6KGSNK4PuBWmX9NykU0wnWamjxdKhDJ)
3. [pfSense-Wazuh Integration](https://benheater.com/integrating-pfsense-with-wazuh/)