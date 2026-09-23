<div align="center">

# 🔓 Password Cracking with JTR & Networkwalks Tools

### Week 3 — Project Modules 1 & 2 · Networkwalks Cybersecurity & Ethical Hacking Training

![Status](https://img.shields.io/badge/status-completed-brightgreen)
![Tool](https://img.shields.io/badge/tool-John%20the%20Ripper-red)
![Tool](https://img.shields.io/badge/tool-Johnny%20GUI-orange)
![Tool](https://img.shields.io/badge/tool-Networkwalks%20Tools-blue)
![Category](https://img.shields.io/badge/category-Password%20Security-yellow)
![Platform](https://img.shields.io/badge/platform-Windows%2011-lightgrey)

*Cracking the same locked PDFs two ways — offline with JTR, and online with zero installation.*

</div>

---

## 📖 Table of Contents

- [Overview](#-project-overview)
- [Tools Used](#-tools-used)
- [Methodology](#️-methodology)
- [Results](#-results)
- [Key Learnings](#-key-learnings)
- [Repository Structure](#-repository-structure)
- [References](#-references)

---

## ⚠️ Ethical Use Disclaimer

> This project was carried out in a **controlled training lab** on files provided specifically for educational purposes. Password cracking techniques shown here must only be used on systems or files you **own** or have **explicit authorization** to test. Unauthorized access to protected data is illegal.

---

## 📌 Project Overview

This repository documents two hands-on labs focused on **password recovery from encrypted PDF files**:

| 🧪 | Module | Approach |
|:---:|---|---|
| 1️⃣ | **PM1 — JTR + Johnny** | Offline dictionary attack using John the Ripper with a GUI front-end |
| 2️⃣ | **PM2 — Networkwalks Tools** | Online dictionary attack, entirely in-browser, zero install |

Both modules were run against the **same three locked PDFs**, giving a direct side-by-side comparison of an offline pentesting tool vs. a modern browser-based one.

<div align="center">

| | |
|---|---|
| 🏫 **Training** | Networkwalks Cybersecurity & Ethical Hacking |
| 📅 **Week** | Week 3 |
| 🎯 **Target Files** | 3 password-protected PDFs (`My Locked PDF1/2/3.pdf`) |
| 🙋 **Submitted By** | Sagar Shah |
| 🗓️ **Date** | 22–23 September 2026 |

</div>

---

## 🧰 Tools Used

<table>
<tr>
<td valign="top" width="50%">

### 🖥️ PM1 — Offline (JTR)
- 🔑 [John the Ripper](https://www.openwall.com/john/) `1.9.0-jumbo-1` (OMP, cygwin 64-bit, AVX2)
- 🖱️ [Johnny](https://www.openwall.info/wiki/john/johnny) — GUI front-end for JTR
- 🧬 [OnlineHashCrack PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php)

</td>
<td valign="top" width="50%">

### 🌐 PM2 — Online (Networkwalks)
- #️⃣ [Hash Calculator](https://networkwalks.com/hash-calculator/) — local, in-browser hash extraction
- 🧩 [Password Cracker](https://networkwalks.com/password-cracker/) — browser-based dictionary attack

</td>
</tr>
</table>

---

## ⚙️ Methodology

### 🖥️ PM1 — Offline Cracking with JTR + Johnny

```
1. Download & extract John the Ripper (jumbo build) for Windows
2. Download & install Johnny (GUI for JTR)
3. Link Johnny → JTR by browsing to john.exe under Settings
4. For each locked PDF:
     a. Extract its hash via Online Hash Crack
     b. Save the hash as a .txt file
     c. Load it in Johnny → Open password file → PASSWD format
     d. Click "Start new attack"
5. Unlock the PDF with the cracked password → capture the flag 🚩
```

### 🌐 PM2 — Online Cracking with Networkwalks Tools

```
1. Download the same locked PDFs from the Networkwalks lab page
2. Upload each PDF to the Hash Calculator (PDF tab) — parsed
   client-side, nothing sent to a server
3. Paste the extracted $pdf$... hash into the Password Cracker
4. Run a dictionary attack (built-in 100-password wordlist)
5. Unlock the PDF with the cracked password → capture the flag 🚩
```

> 💡 PM2 needed **zero installation** — both tools run entirely in-browser, making it a faster (if less "authentic") alternative to the offline JTR workflow.

---

## 🏁 Results

<div align="center">

| 📄 PDF File | 🔑 Cracked Password | 🚩 Flag Captured |
|---|---|---|
| `My Locked PDF1.pdf` | `good-luck` (JTR) / `password1` (NW Tools) | `nw{cybersecurity_flag_captured_2608}` / `nw{networkwalks_flag1_jtr_270521_1}` |
| `My Locked PDF2.pdf` | `password1` | `nw{networkwalks_persistence_jtr_270521}` |
| `My Locked PDF3.pdf` | `1qaz2wsx` | `nw{networkwalks_flag_260821_1}` |

**✅ 3 / 3 PDFs cracked in both modules — 100% success rate**

</div>

The same weak passwords were recoverable whether the attack was run **offline via JTR** or **online via Networkwalks tools** — proving the underlying weakness was the password itself, not the tool used to find it.

---

## 🎓 Key Learnings

| Insight | Takeaway |
|---|---|
| 🔍 **Hash extraction** | Protected PDFs store a hash (`$pdf$...`, `pdf2john`/`hashcat`-compatible, R4/V4 128-bit), not the raw password — cracking means matching a candidate word against that hash |
| ⚡ **Weak passwords fall fast** | `password1`, `good-luck`, `1qaz2wsx` were all cracked within seconds via dictionary attack |
| 🖥️ vs 🌐 **Offline vs. online tooling** | JTR + Johnny = more control (dictionary, brute-force, rules) but needs setup; Networkwalks tools = zero setup, great for quick tests/CTFs |
| 🔐 **Strong passwords matter** | 12+ characters, mixed case, numbers, symbols — avoid dictionary words and keyboard-walk patterns like `1qaz2wsx` |
| 🧭 **Responsible testing** | Password cracking should only ever be performed with proper authorization |

---

## 📁 Repository Structure

```
.
├── README.md                                       # This file
├── WK3-PM1_Password_Cracking_Report.docx           # Detailed report — JTR + Johnny (offline)
├── WK3-PM2_Password_Cracking_NW_Tools_Report.docx  # Detailed report — Networkwalks tools (online)
├── Final_Report_Week3_Sagar_Shah.docx              # Combined summary report (PM1 + PM2)
└── screenshots/                                     # Supporting screenshots referenced in the reports
```

---

## 📚 References

- 🔑 John the Ripper — [openwall.com/john](https://www.openwall.com/john/)
- 🖱️ Johnny (JTR GUI) — [openwall.info/wiki/john/johnny](https://www.openwall.info/wiki/john/johnny)
- 🧬 Online Hash Crack — [onlinehashcrack.com](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php)
- #️⃣ Networkwalks Hash Calculator — [networkwalks.com/hash-calculator](https://networkwalks.com/hash-calculator/)
- 🧩 Networkwalks Password Cracker — [networkwalks.com/password-cracker](https://networkwalks.com/password-cracker/)
- 🌐 Networkwalks Academy — [networkwalks.com](https://www.networkwalks.com)

---

<div align="center">

*Submitted by **Sagar Shah** — Networkwalks Cybersecurity & Ethical Hacking Training, Week 3*

⭐ *If this helped you understand password cracking basics, feel free to star the repo!*

</div>
