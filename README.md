# Local Network Port Scanning with Nmap

This project demonstrates how to scan a local network device for open ports using **Nmap**, analyze the services, and assess potential vulnerabilities.

---

## Installation

**Nmap self-installer for Windows** from the official website:

[https://nmap.org/download#windows](https://nmap.org/download#windows)

**"Microsoft Windows Self-installer" (`.exe` file)** to install Nmap and Zenmap GUI.

---

## Commands Used

### Step 1: Identify Local IP Address

```
ipconfig
```

**SOutput:**

```
Windows IP Configuration


Wireless LAN adapter Local Area Connection* 1:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Local Area Connection* 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::c562:d4b7:1c0:4d99%5
   IPv4 Address. . . . . . . . . . . : 192.168.0.104
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1
```

---

### Step 2: Scanning the Host Using Nmap

```
nmap -sS 192.168.0.104
```

**Output:**

```
Starting Nmap 7.97 ( https://nmap.org ) at 2025-06-23 20:57 +0530
Nmap scan report for 192.168.0.104
Host is up (0.00022s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.97 seconds
```

---

## Zenmap (GUI Version)

*Below is a screenshot of the Nmap Zenmap GUI scan interface.*

![Zenmap GUI Screenshot](path/to/your/screenshot.png)

---

## Port Analysis

| Port | Service      | Description                                                                        |
| ---- | ------------ | ---------------------------------------------------------------------------------- |
| 135  | MSRPC        | Microsoft RPC (Remote Procedure Call). Used for Windows services like DCOM.        |
| 139  | NetBIOS-SSN  | NetBIOS Session Service. Used for Windows file/printer sharing (legacy).           |
| 445  | Microsoft-DS | SMB over TCP (Server Message Block). Used for file sharing, Active Directory, etc. |

### Potential Risks

| Port | Risks                                                                                                       |
| ---- | ----------------------------------------------------------------------------------------------------------- |
| 135  | May allow service enumeration — attacker can list services remotely.                                        |
| 139  | Vulnerable to NetBIOS name spoofing, session hijacking, etc.                                                |
| 445  | High risk — Targeted by many worms/ransomware if unpatched. Possible remote code execution vulnerabilities. |

---

## Full Scan Report

Access the saved HTML scan report here:
🔗 [scan.html](./scan.html)

---
