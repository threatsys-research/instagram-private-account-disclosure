<div align="center">

<img src="https://img.shields.io/badge/Platform-Instagram-E1306C?style=for-the-badge&logo=instagram&logoColor=white"/>
<img src="https://img.shields.io/badge/Risk%20Level-CRITICAL-FF0000?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Impact-Critical-FF0000?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Likelihood-High-FF6600?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Type-IDOR%20%2F%20Broken%20Access%20Control-9B00FF?style=for-the-badge"/>
<img src="https://img.shields.io/badge/License-CC%20BY--ND%204.0-lightgrey?style=for-the-badge"/>

<br/><br/>

# 🔓 Instagram Private Account Bypass
## Public Disclosure Report

> **A Critical-severity vulnerability in Instagram where private account media is fully accessible via backend API-extracted CDN URLs — bypassing the "Private Account" restriction entirely at the resource level. No login, account, or follow approval required.**

<br/>

🔗 **Repository:** [https://github.com/threatsys-research/instagram-private-account-disclosure](https://github.com/threatsys-research/instagram-private-account-disclosure)

*Researched & Responsibly Disclosed by* **[Threatsys Technologies Private Limited](http://www.threatsys.co.in)**

</div>

---

## 📋 Table of Contents

- [Report Details](#-report-details)
- [Vulnerability Summary](#-vulnerability-summary)
- [Description](#-description)
- [Technical Details](#-technical-details)
- [Steps to Reproduce](#-steps-to-reproduce)
- [Impact](#-impact)
- [Recommended Remediation](#-recommended-remediation)
- [Repository Structure](#-repository-structure)
- [License](#-license)
- [Disclaimer](#-disclaimer)
- [Contact](#-contact)

---

## 📄 Report Details

| Field | Details |
|:---|:---|
| **Prepared By** | Threatsys R&D Team |
| **Reviewed By** | Threatsys R&D Team |
| **Approved By** | Deepak Kumar Nath |
| **Email** | threatsysrd@gmail.com |
| **Website** | [www.threatsys.co.in](http://www.threatsys.co.in) |

---

## ⚠️ Vulnerability Summary

| Attribute | Details |
|:---|:---|
| **Vulnerability Name** | Instagram Private Account Bypass — Public Disclosure |
| **Risk Level** | 🔴 **Critical** |
| **Impact** | Critical |
| **Likelihood** | High |
| **Vulnerability Class** | IDOR / Broken Object Level Authorization (BOLA) |
| **Attack Vector** | Network — Instagram Backend API |
| **Authentication Required** | ❌ None |
| **Privileges Required** | ❌ None |
| **Account Required** | ❌ None |
| **Follow Approval Required** | ❌ None |

---

## 📝 Description

Instagram **fails to enforce resource-level authorization** on media content belonging to private accounts.

By using a script  to query Instagram's backend API with only a target **User ID**, an attacker can extract **direct CDN media URLs** of any private account's posts. These extracted URLs are **completely publicly accessible** - they load in any standard browser without:

- ❌ Being an approved follower of the target account
- ❌ Sending or having an accepted follow request
- ❌ Even having an Instagram account at all

> 💡 The `"Private Account"` setting is enforced **only at the frontend/UI layer**.
> At the **API and resource (CDN) level**, there is zero access control — making the privacy feature entirely ineffective.

---

## 🔬 Technical Details

```
Vulnerability Class  :  IDOR / Broken Object Level Authorization (BOLA)
Attack Vector        :  Network (Instagram Backend API)
Root Cause           :  Missing server-side access control on media CDN URLs
Input Required       :  Target Instagram User ID
Authentication       :  None required
Privileges           :  None required
User Interaction     :  None required
```

### Attack Flow

```
  Attacker
     │
     │  1. Provides Target Instagram User ID
     ▼
  poc.py
     │
     │  2. Programmatically queries Instagram Backend API
     ▼
  Instagram Backend API
     │
     │  3. Returns direct CDN media URLs (no auth check)
     ▼
  extracted_urls.txt  ◄──── Direct media links saved here
     │
     │  4. Attacker copies any URL
     ▼
  Any Browser (Not logged in / No account)
     │
     ▼
  ✅ Private media loads successfully
     └── "Private Account" restriction is NOT enforced at resource level
```

---

## 🧪 Steps to Reproduce

> ⚠️ **For Knowledge & Security Research Purposes Only.**
> The reproduction steps are intentionally withheld from this public disclosure to prevent misuse.
> Full technical details are available to verified security researchers and platform vendors upon request.
> Contact: [threatsysrd@gmail.com](mailto:threatsysrd@gmail.com)

---

## 💥 Impact

| # | Impact |
|:---|:---|
| 1 | **Complete privacy bypass** of Instagram's Private Account feature |
| 2 | Private photos of **any** Instagram user can be accessed by anyone worldwide |
| 3 | Attack requires **no authentication**, account, login, or follow approval |
| 4 | Affects **all Instagram users** with their account set to `"Private"` |
| 5 | Direct CDN URLs remain accessible **without session cookies or tokens** |
| 6 | Attack is **completely passive** — no notification or trace left on the target's account |

---



## 📁 Repository Structure

```
instagram-private-account-disclosure/
│
├── 📄 README.md                              ← This file
├── 🐍 poc.py                                 ← Proof-of-concept exploit script
├── 📋 extracted_urls.txt                     ← Sample output: extracted CDN media URLs
├── 📝 Public_Disclosure_Report.docx          ← Full assessment report by Threatsys
└── 📜 LICENSE                                ← CC BY-ND 4.0
```

---

## 📜 License

**Creative Commons Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)**

© 2026 Threatsys Technologies Private Limited. All rights reserved.

| Permission | Status |
|:---|:---|
| ✅ View | Allowed |
| ✅ Download | Allowed |
| ❌ Modify / Edit | **Not Permitted** |
| ❌ Redistribute altered versions | **Not Permitted** |
| ❌ Commercial use | **Not Permitted** |

Full license text: [https://creativecommons.org/licenses/by-nd/4.0/](https://creativecommons.org/licenses/by-nd/4.0/)

---

## ⚖️ Disclaimer

This vulnerability disclosure is published strictly for **educational and security awareness purposes only**. The proof-of-concept is provided solely to help security professionals and platform vendors understand the severity and real-world impact of this issue.

**⚠️ Do not use this against any account you do not own or have explicit written permission to test.**

Unauthorized access to private user data may violate applicable laws including but not limited to:
- **IT Act 2000** (India)
- **Computer Fraud and Abuse Act (CFAA)** (USA)
- **General Data Protection Regulation (GDPR)** (EU)

Threatsys Technologies Private Limited and the authors bear **no responsibility** for any misuse of the information or tools contained in this repository.



<br/>

---

*Responsibly researched and publicly disclosed by*
**Threatsys Technologies Private Limited · 2026**

</div>
