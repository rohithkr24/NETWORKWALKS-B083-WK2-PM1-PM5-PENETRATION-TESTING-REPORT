# NETWORKWALKS-B083-WK2-PM1-PM5-PENETRATION-TESTING-REPORT
Footprinting and reconnaissance attacks with multiple Kali tools &amp; Network Scanning with Zenmap
# 🔐 Penetration Testing Report — Footprinting & Network Scanning

**W2-PM-FINAL | Cybersecurity | Networkwalks**

## 👤 Author

**Rohith K R**

**Cybersecurity Intern — B083 Networkwalks**

**Date:** 15 September 2026

---

## 📌 Project Information

| Field                  | Details                                   |
| ---------------------- | ----------------------------------------- |
| **Program**            | Cybersecurity Program at Networkwalks     |
| **Week**               | 02                                        |
| **Modules Completed**  | W2-PM1 — Multiple Kali Tools              |
|                        | W2-PM5 — Zenmap Scanning                  |
| **Phases Covered**     | Phase 1: Reconnaissance & Footprinting    |
|                        | Phase 2: Scanning & Network Discovery     |
| **Client/Target**      | Networkwalks — secured written permission |
| **Additional Target**  | My own local LAN Network                  |
| **Permission Secured** | Yes                                       |
| **Repository**         | GitHub                                    |

---

## ⚠️ Liability Disclaimer

I have performed these activities only on systems and devices where I had secured written permission or on devices/systems that I own myself.

All materials in this repository are intended for **educational and research purposes only**. Do not use anything from this project to break the law.

The instructor, authors, and Networkwalks are not responsible for any misuse of this knowledge. Every action you take is your own responsibility.

Unauthorized access may result in criminal charges, fines, loss of employment, or a permanent record. In most countries, unauthorized access is a crime even when no damage is caused.

---

## 📖 Introduction

This report covers the **footprinting of the `networkwalks.com` domain** using various Kali Linux tools (**W2-PM1**) and the **scanning of my own local network using Zenmap (W2-PM5)**.

One module focuses on the footprinting stage, while the other focuses on the scanning stage. Together, they demonstrate how an attacker can move from collecting publicly available information to identifying and mapping active hosts within a network.

This work was completed as part of **Week 2 of my Cybersecurity & Ethical Hacking internship at Networkwalks**.

All commands were performed in **Kali Linux** for the footprinting activities and on a **Windows PC with Zenmap installed** for the scanning activities.

Each step includes the command executed, result obtained, screenshot evidence, and a brief explanation of the importance of the finding from an attacker's perspective.

---

# 🛠️ Tools Used

| Tool                     | Purpose                                                                       |
| ------------------------ | ----------------------------------------------------------------------------- |
| **Kali Linux & Windows** | Operating systems used for reconnaissance and scanning activities             |
| **WHOIS**                | Find domain registration details such as owner, dates, and name servers       |
| **WhatWeb**              | Fingerprint web technologies such as server, CMS, plugins, and IP information |
| **Nslookup**             | Resolve the domain name to its IP address using DNS                           |
| **Curl**                 | Read HTTP response headers of the website                                     |
| **Wafw00f**              | Detect whether a Web Application Firewall protects the site                   |
| **DNSRecon**             | Enumerate DNS records including NS, MX, SPF, TXT, and SRV records             |
| **Zenmap (Nmap GUI)**    | Scan the local subnet to find live hosts, IP addresses, and MAC addresses     |
| **Windows CMD**          | Identify local IP and MAC address information                                 |

---

# 🔎 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

I performed reconnaissance against the `networkwalks.com` domain using six Kali Linux tools:

* WHOIS
* WhatWeb
* Nslookup
* Curl
* Wafw00f
* DNSRecon

Each tool was used to collect a different type of information about the target.

### 1. WHOIS

WHOIS was used to obtain publicly available domain registration information and identify the domain's name servers.

The results provided information about the domain registration and hosting infrastructure.

**Purpose:**

* Identify domain registration details
* Identify name servers
* Gather publicly available domain information

---

### 2. WhatWeb

WhatWeb was used to identify technologies used by the website.

The results identified:

* **WordPress 7.0.4**
* **WP Download Manager 3.3.58**
* Additional information exposed by the website

**Purpose:**

* Fingerprint web technologies
* Identify CMS and plugins
* Gather information that may require further security review

---

### 3. Nslookup

Nslookup was used to resolve the domain name to its IP address.

**Identified IP Address:**

```text
192.232.216.135
```

**Purpose:**

* Resolve domain names
* Identify the IP address associated with the domain
* Gather basic DNS information

---

### 4. Curl

Curl was used with the `-I` option to inspect HTTP response headers.

```bash
curl -I https://networkwalks.com
```

The results provided additional information about the web application and exposed the WordPress REST API endpoint:

```text
/wp-json/
```

**Purpose:**

* Inspect HTTP response headers
* Identify technical information exposed by the web server
* Observe application-related endpoints

---

### 5. Wafw00f

Wafw00f was used to determine whether a Web Application Firewall (WAF) was protecting the website.

The result identified:

```text
ModSecurity (SpiderLabs)
```

**Purpose:**

* Detect Web Application Firewall technology
* Understand the security architecture exposed by the target

---

### 6. DNSRecon

DNSRecon was used to enumerate DNS records.

The results provided information related to:

* Name servers
* Mail servers
* SPF/TXT records
* Service records
* DNS software information

**Purpose:**

* Enumerate DNS infrastructure
* Identify DNS records
* Build a broader infrastructure profile

---

# 🌐 4.2 Network Scanning with Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my local network.

The practical required me to:

* Identify my local IP address
* Identify the LAN subnet
* Discover live hosts
* Identify IP addresses
* Identify MAC addresses
* Generate a network topology

### Step 1 — Identify Local Network

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet.

```cmd
ipconfig
```

The identified subnet was then entered into Zenmap.

### Step 2 — Perform Ping Scan

I entered the subnet into **Zenmap** and selected **Ping Scan** to identify active hosts.

The example results provided in the practical identified four live hosts:

```text
10.0.0.1
10.0.0.4
10.0.0.19
10.0.0.5
```

The example results also included four MAC addresses.

### Step 3 — Generate Network Topology

After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend, and saved the network topology in PDF format as required by the practical task.

> **Note:** The actual subnet, number of hosts, IP addresses, and MAC addresses should be replaced with the results from the actual local network when submitting the final report.

---

# ⚠️ 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, the following potential risks were identified.

| # | Risk / Finding                               | Evidence / Observation                                      | Potential Impact                                                                                                | Risk Level |
| - | -------------------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ---------- |
| 1 | Web technology information exposed           | WhatWeb identified WordPress and WP Download Manager        | Attackers may use exposed technology/version information to identify software requiring further security review | **Medium** |
| 2 | Server IP address identifiable               | Nslookup resolved the domain to `192.232.216.135`           | Provides information about the network location of the web service                                              | **Low**    |
| 3 | HTTP technical information exposed           | Curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration                                                    | **Low**    |
| 4 | WAF technology identifiable                  | Wafw00f identified ModSecurity (SpiderLabs)                 | Reveals information about the web application's security architecture                                           | **Low**    |
| 5 | DNS infrastructure information exposed       | DNSRecon identified DNS, mail, and service-related records  | DNS information can help build a broader infrastructure profile                                                 | **Medium** |
| 6 | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network    | Unknown or unauthorized devices may potentially be present on a network                                         | **Medium** |

### Risk Level Key

* 🔴 **Critical**
* 🟠 **Medium**
* 🟢 **Low**

> **Important:** The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical exercises primarily involved **information gathering and host discovery**. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address, or DNS record does **not by itself mean that the system is vulnerable**. Further authorized security testing would be required to confirm any actual vulnerability.

---

# 🛡️ 6. Recommendations

Based on the observations from these activities, the following security improvements are recommended.

### 1. Review Publicly Exposed Technology Information

Organizations should regularly review what information about their web technologies, CMS, and plugins is publicly visible.

### 2. Keep Software Updated

CMS platforms, plugins, and other web technologies should be regularly updated and reviewed against current security advisories.

### 3. Review HTTP Headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

### 4. Review DNS Records Regularly

DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

### 5. Properly Configure and Monitor the WAF

Keep the WAF (**ModSecurity**) enabled and properly tuned, since it already blocks naive attacks.

### 6. Perform Regular Internal Network Discovery

Organizations should periodically scan their own networks to identify active devices.

### 7. Investigate Unknown Devices

Any unexpected device discovered during network scanning should be investigated and verified.

### 8. Maintain Network Documentation

Network topology and device information should be documented and updated regularly.

### 9. Perform Security Testing with Authorization

Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

---

# 📝 7. Conclusion

During **Week 2 of my Cybersecurity & Ethical Hacking internship**, I completed practical exercises focused on **footprinting, reconnaissance, and network scanning**.

As part of the footprinting activity, I worked with six Kali Linux tools to gather information about the target domain. I gained an understanding of how:

* **WHOIS** can provide domain registration details
* **WhatWeb** can identify web technologies
* **Nslookup** can resolve domain names
* **Curl** can examine HTTP headers
* **Wafw00f** can detect a Web Application Firewall
* **DNSRecon** can gather additional DNS-related information

For the network scanning activity, I used **Zenmap** to examine my local network configuration and identify active hosts. I also gathered IP and MAC address details and created a network topology to better understand the network structure.

These activities helped me understand the importance of **information gathering in cybersecurity**. Before attempting to exploit a system, a security professional can obtain valuable insights by analyzing publicly available information and responses from network services.

I also learned the importance of properly documenting technical findings. An effective cybersecurity report should clearly describe the activities performed, findings identified, their significance, potential risks, and possible measures to reduce those risks.

Finally, I understood that reconnaissance and network scanning should always be conducted within an **authorized scope**. All activities in this module were performed as part of the assigned educational cybersecurity lab.

---

# 📸 8. Evidence Collected

Evidence and screenshots collected during the practical activities include:

* WHOIS results
* WhatWeb results
* Nslookup results
* Curl HTTP header results
* Wafw00f results
* DNSRecon results
* Windows `ipconfig` output
* Zenmap Ping Scan results
* IP and MAC address information
* Zenmap network topology

> Add the corresponding screenshots/evidence files to this section of the GitHub repository.

---

# 👨‍💻 Author

**Rohith K R**
Cybersecurity Intern — B083

**LinkedIn:** [linkedin.com/in/rohith-k-r-55236a30b](https://linkedin.com/in/rohith-k-r-55236a30b)

---

# 📚 Project Information

**Program Name:** Cybersecurity Program at Networkwalks
**Week:** 02
**Modules:** W2-PM1 — Multiple Kali Tools | W2-PM5 — Zenmap Scanning
**Project:** Penetration Testing — Footprinting & Network Scanning
**Repository:** GitHub

---

## 🔐 Ethical Use

This project was created for **educational and cybersecurity research purposes**. All reconnaissance and network scanning activities should be performed only on systems that you own or where you have explicit authorization.

**Never use these techniques against unauthorized systems or networks.**
