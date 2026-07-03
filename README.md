# Flag Capture - Official Write-up

## Overview

**Difficulty:** Medium

This room simulates a real-world Linux system compromise. The objective is to enumerate the target, discover leaked credentials, gain initial access, perform privilege escalation, and capture both the user and root flags.

---

## Learning Objectives

By completing this room, you will learn how to:

- Perform network reconnaissance.
- Enumerate Linux services.
- Discover sensitive files and exposed credentials.
- Gain initial access to a Linux machine.
- Perform privilege escalation.
- Capture user and root flags.

---

# Task 1 - Introduction

In this challenge, an Ubuntu server belonging to ABC Technologies has been compromised.

Your goal is to investigate the target system, gain access, escalate your privileges, and capture both flags.

---

# Task 2 - Connect to the Machine

Deploy the virtual machine and note the assigned IP address.

Verify connectivity:

```bash
ping <Machine-IP>
```

Perform an Nmap scan:

```bash
nmap -sC -sV -A <Machine-IP>
```

Identify the running services before continuing.

---

# Task 3 - Enumeration

Carefully enumerate every exposed service.

Useful commands include:

```bash
nmap -sC -sV <Machine-IP>

gobuster dir -u http://<Machine-IP> -w /usr/share/wordlists/dirb/common.txt

enum4linux <Machine-IP>
```

Look for:

- Hidden directories
- Configuration files
- Backup files
- Credentials
- Usernames

---

# Task 4 - Initial Access

Using the information gathered during enumeration, obtain valid credentials.

Connect using SSH:

```bash
ssh username@<Machine-IP>
```

After successful login, verify your access:

```bash
whoami

hostname

id
```

---

# Task 5 - Capture the User Flag

Navigate to the user's home directory.

Locate the first flag.

Example:

```bash
cd /home/<user>

cat user.txt
```

Submit the contents of the flag.

---

# Task 6 - Privilege Escalation

Enumerate the system thoroughly.

Useful commands:

```bash
sudo -l

find / -perm -4000 2>/dev/null

getcap -r / 2>/dev/null

linpeas.sh
```

Identify the intended privilege escalation path.

Gain root privileges.

Verify:

```bash
whoami
```

Expected output:

```
root
```

---

# Task 7 - Capture the Root Flag

Navigate to the root directory.

Retrieve the final flag.

```bash
cd /root

cat root.txt
```

Submit the root flag to complete the room.

---

# Summary

Congratulations!

You have successfully completed the **Flag Capture** room by:

- Enumerating the target
- Identifying vulnerable services
- Obtaining initial access
- Escalating privileges
- Capturing both user and root flags

---

# Skills Covered

- Linux Enumeration
- Nmap
- Service Enumeration
- Credential Discovery
- SSH
- Linux Privilege Escalation
- Capture the Flag (CTF)

---

## Credits

**Room Author:** Pragadesh Sundhar

Created as a TryHackMe Flag Capture challenge focusing on Linux system hacking and privilege escalation.
