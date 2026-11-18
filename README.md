# NETWORKWALKS-B084-WK3-JTR-PASSWORD-CRACKING

# Week 3 – Project Module 1: Password Cracking with John the Ripper

![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)
![Tool](https://img.shields.io/badge/Tool-John%20the%20Ripper-black)
![GUI](https://img.shields.io/badge/GUI-Johnny-6E56CF)
![Status](https://img.shields.io/badge/Status-Educational%20Lab-success)

A hands-on password-auditing lab from the **NetworkWalks Cybersecurity & Ethical Hacking Program (Batch B084J)**: using **John the Ripper (JTR)** and its graphical front end **Johnny** to recover the password of a protected PDF on a Windows PC.

> 🔗 Project post: [LinkedIn](https://www.linkedin.com/feed/update/urn:li:ugcPost:7528635127849971712/)

---

<details>
<summary><strong>📌 Documentation notes (click to expand)</strong></summary>

- Screenshots below are grouped into workflow stages and ordered by filename timestamp. Each caption describes the *expected* action at that point in the lab manual's sequence — the exact visual content of each image hasn't been individually confirmed, so adjust any caption that doesn't match what's actually shown.
- The lab manual names the test file `My Locked PDF1.pdf`; adjust if your repo's `PDF/` folder uses a different filename.
- The manual's own steps don't name a specific wordlist for Johnny's "Start new attack" — rockyou is referenced here on the project description provided; confirm against your screenshots which attack mode/wordlist Johnny was actually set to.

</details>

---

## Table of Contents

1. [Overview](#overview)
2. [Lab Objectives](#lab-objectives)
3. [Lab Environment](#lab-environment)
4. [Tools & Technologies](#tools--technologies)
5. [Repository Structure](#repository-structure)
6. [Practical Workflow](#practical-workflow)
7. [Screenshot Evidence](#screenshot-evidence)
8. [Result](#result)
9. [Learning Outcomes](#learning-outcomes)
10. [Security Insights](#security-insights)
11. [Ethical Considerations](#ethical-considerations)
12. [References](#references)
13. [Author](#author)
14. [Disclaimer](#disclaimer)

---

## Overview

John the Ripper (JTR) is a widely used password-auditing tool for testing password strength, capable of checking many hash types and unlocking password-protected files such as PDF, ZIP, and Office documents. **Johnny** is its graphical companion, giving JTR a point-and-click interface so attacks can be configured without hand-typing commands.

This lab uses both tools together, in a controlled training environment, to recover the password of a protected PDF — and in doing so, demonstrates concretely why weak passwords are a security liability.

## Lab Objectives

- Understand the fundamentals of password auditing.
- Explore John the Ripper's core functionality.
- Learn the Johnny graphical interface as a front end for JTR.
- Understand the difference between a password-protected file and the password hash representation JTR actually attacks.
- Walk through a dictionary-based password-auditing workflow end to end.
- Document the process with real screenshots, in chronological order.

## Lab Environment

| Component | Detail |
|---|---|
| Host OS | Windows PC |
| Password-Auditing Tool | John the Ripper (JTR) |
| GUI Front End | Johnny |
| Target File | Password-protected PDF (`My Locked PDF1.pdf`) |

> The lab manual specifies a Windows environment for installing JTR and Johnny directly (as opposed to using JTR's Kali-preinstalled build), and the screenshots in this repository follow that Windows workflow.

## Tools & Technologies

| Tool | Purpose |
|---|---|
| [John the Ripper](https://www.openwall.com/john/) | Core password-auditing engine |
| [Johnny](https://openwall.info/wiki/john/johnny) | Graphical interface for John the Ripper |
| Windows | Lab operating system |
| [Online PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) | Extracts the password-hash representation of a protected PDF |
| Dictionary wordlist | Candidate-password list used for the audit attack |

## Repository Structure

```text
NETWORKWALKS-B084J-WK3-JTR-PASSWORD-AUDIT/
│
├── README.md
│
├── John/
│   ├── Screenshot 2026-11-16 014535.png
│   ├── Screenshot 2026-11-16 015330.png
│   ├── ... (25 screenshots total — see Screenshot Evidence below)
│   └── Screenshot 2026-11-16 023610.png
│
├── PDF/
│   └── My Locked PDF1.pdf   (confirm exact filename against the repo)
│
└── W3-PM1 - Week3 - Project Module1 - Password Cracking with JTR v1   (lab manual)
```

## Practical Workflow

**Step 1 — Download John the Ripper**
Downloaded from the [official Openwall site](https://www.openwall.com/john/) (Windows build).

**Step 2 — Download and install Johnny**
Downloaded [Johnny](https://openwall.info/wiki/john/johnny), ran the installer, then opened Johnny and used its Settings to browse to and select `john.exe` (located in JTR's `run` folder), linking the GUI to the JTR engine.

**Step 3 — Prepare the target PDF and extract its hash**
Downloaded the encrypted lab PDF to the Windows PC, then used the [online PDF hash extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) to upload the file and generate its password-hash representation (format `$pdf$...`).

**Step 4 — Save the hash for Johnny**
Copied the extracted hash into Notepad and saved it as `hash1.txt`, trimming any stray characters (e.g. a leading `b'`) so the file starts cleanly with `$pdf$`.

**Step 5 — Load the hash and run the audit**
In Johnny, used **Open password file** to load `hash1.txt`, then clicked **Start new attack** to begin the dictionary-based password audit.

**Step 6 — Verify the result**
Once JTR/Johnny recovered the password, reopened the original encrypted PDF and entered the recovered password to confirm it worked.

## Screenshot Evidence

*(Grouped by workflow stage, ordered by capture timestamp. Captions describe the expected action at each stage — confirm against the actual images.)*

### 1. Installation & Initial Setup

<a href="John/Screenshot%202026-11-16%20014535.png"><img src="John/Screenshot%202026-11-16%20014535.png" alt="JTR download page" width="700"></a>

*Downloading John the Ripper / Johnny from the official site.*

<details>
<summary>Additional installation screenshots (5)</summary>

[![Step](John/Screenshot%202026-11-16%20015330.png)](John/Screenshot%202026-11-16%20015330.png)
[![Step](John/Screenshot%202026-11-16%20020842.png)](John/Screenshot%202026-11-16%20020842.png)
[![Step](John/Screenshot%202026-11-16%20021923.png)](John/Screenshot%202026-11-16%20021923.png)
[![Step](John/Screenshot%202026-11-16%20022003.png)](John/Screenshot%202026-11-16%20022003.png)
[![Step](John/Screenshot%202026-11-16%20022040.png)](John/Screenshot%202026-11-16%20022040.png)

</details>

### 2. Johnny Configuration

<a href="John/Screenshot%202026-11-16%20022211.png"><img src="John/Screenshot%202026-11-16%20022211.png" alt="Johnny settings" width="700"></a>

*Opening Johnny and configuring it to point at `john.exe`.*

<details>
<summary>Additional configuration screenshots (3)</summary>

[![Step](John/Screenshot%202026-11-16%20022325.png)](John/Screenshot%202026-11-16%20022325.png)
[![Step](John/Screenshot%202026-11-16%20022408.png)](John/Screenshot%202026-11-16%20022408.png)
[![Step](John/Screenshot%202026-11-16%20022428.png)](John/Screenshot%202026-11-16%20022428.png)

</details>

### 3. PDF Hash Preparation

<a href="John/Screenshot%202026-11-16%20022501.png"><img src="John/Screenshot%202026-11-16%20022501.png" alt="PDF hash extraction" width="700"></a>

*Uploading the protected PDF to the online hash extractor and retrieving its hash.*

<details>
<summary>Additional hash-preparation screenshots (5)</summary>

[![Step](John/Screenshot%202026-11-16%20022535.png)](John/Screenshot%202026-11-16%20022535.png)
[![Step](John/Screenshot%202026-11-16%20022601.png)](John/Screenshot%202026-11-16%20022601.png)
[![Step](John/Screenshot%202026-11-16%20022650.png)](John/Screenshot%202026-11-16%20022650.png)
[![Step](John/Screenshot%202026-11-16%20022707.png)](John/Screenshot%202026-11-16%20022707.png)
[![Step](John/Screenshot%202026-11-16%20022733.png)](John/Screenshot%202026-11-16%20022733.png)

</details>

### 4. Password Audit Setup

<a href="John/Screenshot%202026-11-16%20022751.png"><img src="John/Screenshot%202026-11-16%20022751.png" alt="Loading hash1.txt into Johnny" width="700"></a>

*Loading `hash1.txt` into Johnny via "Open password file".*

<details>
<summary>Additional setup screenshots (2)</summary>

[![Step](John/Screenshot%202026-11-16%20022948.png)](John/Screenshot%202026-11-16%20022948.png)
[![Step](John/Screenshot%202026-11-16%20023009.png)](John/Screenshot%202026-11-16%20023009.png)

</details>

### 5. Audit Execution

<a href="John/Screenshot%202026-11-16%20023138.png"><img src="John/Screenshot%202026-11-16%20023138.png" alt="Attack running" width="700"></a>

*Running "Start new attack" — the dictionary-based audit in progress.*

<details>
<summary>Additional execution screenshots (2)</summary>

[![Step](John/Screenshot%202026-11-16%20023154.png)](John/Screenshot%202026-11-16%20023154.png)
[![Step](John/Screenshot%202026-11-16%20023438.png)](John/Screenshot%202026-11-16%20023438.png)

</details>

### 6. Result Verification

<a href="John/Screenshot%202026-11-16%20023506.png"><img src="John/Screenshot%202026-11-16%20023506.png" alt="Password recovered" width="700"></a>

*Password recovered by Johnny.*

<details>
<summary>Additional verification screenshots (2)</summary>

[![Step](John/Screenshot%202026-11-16%20023545.png)](John/Screenshot%202026-11-16%20023545.png)
[![Step](John/Screenshot%202026-11-16%20023610.png)](John/Screenshot%202026-11-16%20023610.png)

</details>

*Final step: the recovered password was used to reopen the originally protected PDF, confirming the audit succeeded.*

## Result

The password for `My Locked PDF1.pdf` was successfully recovered via John the Ripper, driven through Johnny's GUI, and verified by reopening the file. The following flags were captured from the recovered PDF content:

```text
nw{networkwalks_flag1_jtr_270521_1}
nw{networkwalks_persistence_jtr_270521}
```

## Learning Outcomes

- Practical exposure to password auditing using an industry-standard tool.
- Working understanding of John the Ripper's core engine and the Johnny GUI.
- Clear grasp of the role password hashes play in security testing — and that a hash is not simply "scrambled" data you decrypt back to the original.
- Hands-on experience with dictionary-based auditing against a real protected file.
- Reinforced awareness of why weak passwords are a serious security liability.
- Improved technical documentation and evidence-based writeup skills.

## Security Insights

- **Weak passwords fall fast:** dictionary attacks like this one succeed quickly against common, short, or predictable passwords.
- **Length and complexity matter:** longer passwords with mixed character types dramatically increase the search space an attacker has to cover.
- **Reuse compounds risk:** a password cracked once can unlock every other account that reuses it.
- **Hashing vs. encryption:** encryption is reversible with the right key; hashing is a one-way function. Tools like JTR don't "decrypt" a password hash — they hash candidate passwords from a wordlist and check for a match, which is why a strong, unpredictable password resists this kind of audit even when the hash itself is exposed.
- **Defense in depth:** strong password policies plus multi-factor authentication (MFA) meaningfully reduce the real-world impact of a cracked or leaked password.
- **Responsible use:** password auditing is a legitimate security practice only when performed on systems and files you're authorized to test.

## Ethical Considerations

This project was carried out strictly for educational purposes, as part of an authorized NetworkWalks Cybersecurity training exercise in a controlled lab environment.

- Intended for learning password-security concepts and authorized security testing only.
- Not intended to encourage or assist cracking passwords on files, accounts, or systems you do not own or have explicit permission to test.
- Password auditing should always be performed responsibly, with proper authorization.

## References

- John the Ripper (official): [https://www.openwall.com/john/](https://www.openwall.com/john/)
- Johnny (official): [https://openwall.info/wiki/john/johnny](https://openwall.info/wiki/john/johnny)
- NetworkWalks Academy: [https://www.networkwalks.com/](https://www.networkwalks.com/)

## Author

**Rajatava Ghosh**
Cybersecurity Student — NetworkWalks Cybersecurity & Ethical Hacking Program (Batch B084J)

- GitHub: [RaxingR](https://github.com/RaxingR) (this lab repository is hosted under [Hypo46](https://github.com/Hypo46))
- LinkedIn: [rajatava-ghosh](https://www.linkedin.com/in/rajatava-ghosh-265aa6316/)
- Project post: [LinkedIn](https://www.linkedin.com/feed/update/urn:li:ugcPost:7528635127849971712/)

## Disclaimer

This repository documents a training lab exercise completed as part of NetworkWalks Academy's cybersecurity coursework. It is shared for educational and portfolio purposes only and does not constitute professional penetration-testing services or endorse unauthorized password recovery of any kind.
