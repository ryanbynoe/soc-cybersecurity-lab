# 🧪 SOC Cybersecurity Lab  
## Active Directory Infrastructure (Phase 1)

> This lab simulates a small-to-mid enterprise Active Directory environment designed to support security testing, detection engineering, and blue team workflows.  
>  
> The focus of this phase is identity infrastructure, organizational structure, and realistic host enrollment to support future attack-and-defend scenarios.

---

## 🧱 Lab Environment Overview

### Hypervisor
- VMware Workstation Pro

### Domain Controller
- **OS:** Windows Server 2025  
- **VM Name:** `thinkfusion`  
- **Domain Name:** `corp.thinkfusion`  
- **IP Address:** `10.0.0.8`  
- **Subnet:** `10.0.0.0/24`  
- **Role:** Primary Domain Controller (DC)

### Joined Clients
| Hostname       | OS Type | Purpose |
|----------------|--------|--------|
| WIN-CLI        | Windows | Standard domain workstation |
| LINUX-CLIENT   | Linux   | Standard domain workstation |
| SEC-BOX        | Windows/Linux | Security tooling & attack simulation |

---

## 🧠 Design Rationale

This Active Directory environment was intentionally designed to resemble a realistic enterprise setup rather than a flat lab domain.

Key goals:
- Enterprise-style naming conventions
- Identity-based attack surface (Kerberos, LDAP, NTLM)
- Log generation for later SIEM integration
- Organizational segmentation using OUs

This phase establishes the foundation for future security testing rather than attempting to harden everything immediately.

---

## 🗂️ Organizational Unit (OU) Structure

The domain is segmented by geographic location to simulate a distributed organization.

corp.thinkfusion
│
├── ATLANTA
├── LOS ANGELES
└── HOUSTON


Each OU is intended to later support:
- Scoped Group Policy Objects
- Delegated administration
- OU-specific attack simulations

### 📸 Screenshot Placeholder
**Active Directory Users and Computers (ADUC)**  
- Full OU tree visible  
- Domain root and child OUs clearly shown  

---

## 👤 User Accounts

### Created Users
| Full Name     | Username | Description |
|--------------|----------|------------|
| Sec User     | suser    | Security-focused test account |
| Steve Austin | saustin | Standard user |
| Brett Hart   | bhart   | Standard user |

**Naming Convention:**  
First initial + last name (enterprise-standard)

### 📸 Screenshot Placeholder
- Users displayed inside an OU (not default Users container)
- Optional: User account properties → Account tab

---

## 🖥️ Domain Join Validation

All client systems were successfully joined to the `corp.thinkfusion` domain.

### 📸 Screenshot Placeholder
Recommended captures:
- Windows client showing domain membership  
- Linux client showing `realm list`, `id`, or equivalent domain verification output  

This confirms proper DNS configuration and domain trust functionality.

---

## 🌐 Network Configuration

- Domain Controller configured with a static IP
- Clients configured to use the DC (`10.0.0.8`) as their primary DNS server

### 📸 Screenshot Placeholder
- DC network adapter IPv4 settings  
- Client DNS configuration pointing to the DC  

---

## 🔐 Security Foundations (Current State)

The environment currently supports:
- Centralized authentication
- Kerberos-based logons
- Event generation for:
  - User logons
  - Account management
  - Directory service activity

No aggressive hardening has been applied yet by design. This allows controlled misconfigurations and attack simulations in later phases.

---

## 📌 Recommendations & Next Improvements

### Short-Term
- Enable Advanced Audit Policy on the Domain Controller
- Separate Users and Computers into dedicated OU subtrees
- Introduce at least one service account

### Mid-Term
- Create location-based Group Policy Objects
- Apply different password policies by OU
- Forward DC security logs to a central log collector

### Long-Term
- Deploy a SIEM (Splunk, ELK, Sentinel)
- Simulate:
  - Kerberoasting
  - Password spraying
  - Lateral movement from compromised clients

---

## 🧭 Lab Roadmap

- [x] Active Directory deployment  
- [x] Client domain enrollment  
- [ ] Group Policy configuration  
- [ ] Centralized logging  
- [ ] Attack simulation & detection engineering  

---

## 📎 Notes for Reviewers

This lab is actively expanded and documented to demonstrate:
- Identity infrastructure knowledge
- Security-first lab design
- Realistic enterprise workflows

Each phase builds on the last, focusing on process, validation, and visibility rather than screenshots alone.
