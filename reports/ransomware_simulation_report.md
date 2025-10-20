# Incident Report – Ransomware Simulation  

## 🧠 Summary  
A simulated ransomware event was executed in a controlled lab to evaluate detection and response capabilities using Splunk and Microsoft Sentinel.

---

## 📅 Incident Timeline  
| Time (UTC) | Event | Description |
|-------------|--------|-------------|
| 13:00 | Suspicious process alert | Sentinel rule triggered for PowerShell encryption command |
| 13:10 | SOC triage | Splunk confirmed anomalous file writes |
| 13:20 | Containment | Host isolated in lab environment |
| 13:30 | Analysis | Identified encryption tool mimicking ransomware behavior |
| 14:00 | Recovery | System restored from snapshot |

---

## 🔍 Indicators of Compromise (IOCs)  
| Type | Value | Description |
|------|--------|-------------|
| Process | `powershell.exe -enc ...` | Encoded PowerShell command |
| File | `C:\Users\Public\encryptor.exe` | Simulated ransomware binary |
| Registry | `HKCU\Software\Microsoft\Windows\CurrentVersion\Run\encryptor` | Persistence mechanism |

---

## 🧩 Analysis & Evidence  
- **Splunk:** Correlated high volume of file write events followed by process creation logs.  
- **Sentinel:** Detected encoded PowerShell command.  
- **Sysmon:** Logged process execution and registry modification.  
- **Wireshark:** Outbound C2 communication attempt to `198.51.100.45`.  

*(Add screenshots later in `/images`.)*

---

## 🧰 Tools Used  
- Splunk Enterprise  
- Microsoft Sentinel  
- Sysmon  
- Wireshark  
- CyberChef  

---

## 🛠 MITRE ATT&CK Mapping  
- T1059 – Command and Scripting Interpreter  
- T1486 – Data Encrypted for Impact  
- T1547 – Persistence via Registry Run Keys  

---

## 🚑 Containment, Eradication & Recovery  
- Host isolated immediately via EDR simulation.  
- Removed persistence registry key.  
- Restored files from backup snapshot.  
- Re-tested detection rules post-cleanup.  

---

## 📘 Lessons Learned  
- Improve PowerShell logging and alert thresholds.  
- Integrate Sentinel playbook for automated host isolation.  
- Enhance Splunk correlation rules for mass file modification events.
