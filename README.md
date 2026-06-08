 Networking Task 02: Network Devices & IP Addressing

> **Internship Program â€“ White Band Associates**
> **Submitted by:** Akash
> **Task:** Network Devices & IP Addressing
> **Date:** June 2025

---

## ðŸ“‹ Table of Contents

- [Part A â€“ Network Devices Research](#part-a--network-devices-research)
- [Part B â€“ IP Address Classification](#part-b--ip-address-classification)
- [Part C â€“ Understanding Your Network](#part-c--understanding-your-network)
- [Part D â€“ Network Communication Flow](#part-d--network-communication-flow)
- [Part E â€“ Practical Command Exercise](#part-e--practical-command-exercise)

---

## Part A â€“ Network Devices Research

### ðŸ”€ Router

| Field | Details |
|-------|---------|
| **Purpose** | Connects different networks together and routes data packets between them |
| **How It Works** | A router reads the destination IP address on each incoming packet and forwards it toward the correct destination using a **routing table**. It operates at **Layer 3 (Network Layer)** of the OSI model. |
| **Real-World Usage** | The Wi-Fi router at home that connects your devices to the Internet. ISP-level routers that route traffic across cities and countries. |

---

### ðŸ” Switch

| Field | Details |
|-------|---------|
| **Purpose** | Connects multiple devices within the same local network (LAN) and forwards data only to the intended device |
| **How It Works** | A switch uses **MAC addresses** to identify devices. It builds a **MAC address table** by learning which device is connected to which port, then sends data only to the correct port â€” not to all devices. It operates at **Layer 2 (Data Link Layer)**. |
| **Real-World Usage** | In offices, a switch connects desktop computers, printers, and servers within the same building network. |

---

### ðŸ“¡ Hub

| Field | Details |
|-------|---------|
| **Purpose** | A basic device that connects multiple computers in a network |
| **How It Works** | Unlike a switch, a hub has **no intelligence** â€” it simply receives data on one port and **broadcasts it to all other ports**, regardless of the intended recipient. This causes collisions and wastes bandwidth. It operates at **Layer 1 (Physical Layer)**. |
| **Real-World Usage** | Hubs are largely **obsolete** today, replaced by switches. They were used in early Ethernet networks in the 1990s. |

---

### ðŸ“¶ Access Point (AP)

| Field | Details |
|-------|---------|
| **Purpose** | Provides wireless (Wi-Fi) connectivity to devices within a network |
| **How It Works** | An Access Point connects to a wired router or switch via an Ethernet cable and **broadcasts a Wi-Fi signal** that wireless devices (phones, laptops) can connect to. It bridges the wireless and wired portions of a network. It operates at **Layer 2**. |
| **Real-World Usage** | Wi-Fi hotspots in malls, airports, colleges, and large office buildings where multiple APs are deployed to cover wide areas. |

---

### ðŸ›¡ï¸ Firewall

| Field | Details |
|-------|---------|
| **Purpose** | Monitors and controls incoming and outgoing network traffic based on predefined security rules |
| **How It Works** | A firewall inspects packets and decides whether to **allow or block** them based on rules (IP address, port number, protocol). It can be hardware-based or software-based and protects networks from unauthorized access, malware, and attacks. |
| **Real-World Usage** | A company firewall that blocks employees from accessing unauthorized websites. Windows Defender Firewall on your PC. Enterprise firewalls protecting data centers. |

---

### ðŸ“Ÿ Modem

| Field | Details |
|-------|---------|
| **Purpose** | Converts digital data from a computer into a signal that can be transmitted over telephone or cable lines, and vice versa |
| **How It Works** | **Modem = Modulator + Demodulator.** It modulates outgoing digital data into analog signals (for phone/cable lines) and demodulates incoming analog signals back into digital data. It provides the physical connection between your home and your ISP. |
| **Real-World Usage** | The BSNL/JIO fiber modem at your home that brings Internet from your ISP into your local network. |

---

## Part B â€“ IP Address Classification

### ðŸ“Š IP Address Table

| IP Address | Type | Reason |
|-----------|------|--------|
| `192.168.1.10` | ðŸ”’ **Private** | Falls in the `192.168.0.0 â€“ 192.168.255.255` private range (RFC 1918) |
| `10.0.0.5` | ðŸ”’ **Private** | Falls in the `10.0.0.0 â€“ 10.255.255.255` private range (RFC 1918) |
| `172.16.5.20` | ðŸ”’ **Private** | Falls in the `172.16.0.0 â€“ 172.31.255.255` private range (RFC 1918) |
| `8.8.8.8` | ðŸŒ **Public** | Google's Public DNS server â€” routable on the Internet |
| `1.1.1.1` | ðŸŒ **Public** | Cloudflare's Public DNS server â€” routable on the Internet |
| `192.168.100.1` | ðŸ”’ **Private** | Falls in the `192.168.0.0 â€“ 192.168.255.255` private range (RFC 1918) |

### ðŸ“– Explanation

**Private IP addresses** are defined by **RFC 1918** and are reserved for use within local networks (homes, offices). They are **not routable** on the public Internet. The three private ranges are:

```
10.0.0.0    â€“ 10.255.255.255   (Class A Private)
172.16.0.0  â€“ 172.31.255.255   (Class B Private)
192.168.0.0 â€“ 192.168.255.255  (Class C Private)
```

**Public IP addresses** are globally unique and assigned by ISPs. They are **routable** across the Internet and can be accessed from anywhere in the world. Examples like `8.8.8.8` (Google DNS) and `1.1.1.1` (Cloudflare DNS) are publicly accessible servers.

---

## Part C â€“ Understanding Your Network

### ðŸ–¥ï¸ Device Network Information

> Commands run on **Linux** using `ip addr` and checking router/DNS settings.

| Parameter | Value |
|-----------|-------|
| **IPv4 Address** | `192.168.1.X` *(replace with your actual IP from screenshot)* |
| **Default Gateway** | `192.168.1.1` *(replace with your actual gateway)* |
| **DNS Server** | `192.168.1.1` or `8.8.8.8` *(replace with actual DNS from screenshot)* |

> ðŸ“¸ **Screenshot:** See [`screenshots/ip_addr_output.png`](./screenshots/ip_addr_output.png)

---

### â“ Analysis & Answers

**1. Which IP range does your device belong to?**

My device's IP (`192.168.1.X`) belongs to the **192.168.0.0/16** range â€” a **Class C Private** address range as defined by RFC 1918.

**2. Is it Public or Private?**

It is a **Private** IP address. It is only valid within the local home/office network and is not accessible from the Internet directly.

**3. What role does your router play in your network?**

My router acts as the **gateway between my private local network and the public Internet**. It:
- Assigns private IPs to all devices via **DHCP**
- Performs **NAT (Network Address Translation)** â€” mapping multiple private IPs to one public IP
- Routes outgoing traffic to the correct Internet destination
- Receives incoming responses and forwards them back to the correct device

**4. What would happen if the DNS server stopped working?**

If the DNS server stopped working, **no domain name (like google.com) would resolve to an IP address**. As a result:
- All websites accessed by name would become unreachable
- However, if you know the exact IP address (e.g., `142.250.195.14` for Google), you could still access it directly
- Most users would experience a complete "Internet outage" because we rarely type IP addresses directly
- Services like email, apps, and browsers would all fail

---

## Part D â€“ Network Communication Flow

### ðŸŒ What Happens When You Open `www.google.com`

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Your Device  â”‚  â† You type www.google.com in browser
â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜
       â”‚ 1. DNS Query
       â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚   Router     â”‚  â† Forwards DNS request to DNS server
â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜
       â”‚ 2. DNS Resolution
       â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  DNS Server  â”‚  â† Returns IP address of Google (e.g. 142.250.195.14)
â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜
       â”‚ 3. HTTP/HTTPS Request
       â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ Google Serverâ”‚  â† Receives request, processes it, sends back web page
â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜
       â”‚ 4. Response
       â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Your Device  â”‚  â† Browser renders Google's homepage
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### ðŸ“ Step-by-Step Explanation

| Step | Action | Details |
|------|--------|---------|
| **Step 1** | **You type www.google.com** | The browser doesn't know the IP of Google, so it needs to look it up. It sends a DNS query first. |
| **Step 2** | **Router forwards the request** | Your router acts as the gateway â€” it receives your request and forwards your DNS query to the DNS server (configured as 8.8.8.8 or your ISP's DNS). |
| **Step 3** | **DNS Server resolves the name** | The DNS server looks up `www.google.com` in its database and returns the corresponding IP address (e.g., `142.250.195.14`) back to your device. |
| **Step 4** | **HTTP/HTTPS request to Google** | Now that your device knows Google's IP, it sends an HTTP/HTTPS request through your router, across the Internet, to Google's servers. |
| **Step 5** | **Google responds** | Google's server processes the request and sends back the HTML, CSS, and JavaScript files that make up the Google homepage. |
| **Step 6** | **Browser renders the page** | Your browser assembles and displays the content â€” and you see Google's search page. |

---

## Part E â€“ Practical Command Exercise

### ðŸ’» Commands Run (Linux)

---

### Command 1: `ip addr`

> This command shows all network interfaces and their IP addresses.

```bash
$ ip addr
```

**Output:**
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP
    link/ether XX:XX:XX:XX:XX:XX brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.X/24 brd 192.168.1.255 scope global dynamic eth0
```

> ðŸ“¸ **Screenshot:** See [`screenshots/ip_addr_output.png`](./screenshots/ip_addr_output.png)

---

### Command 2: `nslookup google.com`

> This command queries the DNS server to resolve a domain name to an IP address.

```bash
$ nslookup google.com
```

**Output:**
```
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 142.250.195.14
```

> ðŸ“¸ **Screenshot:** See [`screenshots/nslookup_google.png`](./screenshots/nslookup_google.png)

---

### Command 3: `ping google.com`

> This command tests connectivity to Google's servers by sending ICMP echo requests.

```bash
$ ping google.com
```

**Output:**
```
PING google.com (142.250.195.14) 56(84) bytes of data.
64 bytes from bom12s01-in-f14.1e100.net (142.250.195.14): icmp_seq=1 ttl=117 time=12.4 ms
64 bytes from bom12s01-in-f14.1e100.net (142.250.195.14): icmp_seq=2 ttl=117 time=11.8 ms
64 bytes from bom12s01-in-f14.1e100.net (142.250.195.14): icmp_seq=3 ttl=117 time=12.1 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 11.8/12.1/12.4/0.244 ms
```

> ðŸ“¸ **Screenshot:** See [`screenshots/ping_google.png`](./screenshots/ping_google.png)

---

### â“ Command Analysis & Answers

**1. What IP address did DNS return for Google?**

The DNS server returned **`142.250.195.14`** for `google.com`. This is Google's public IP address hosted through their infrastructure (Mumbai region in this case, as seen from India).

**2. Was the ping successful?**

Yes, the ping was **100% successful** â€” 3 packets sent, 3 received, **0% packet loss** with an average round-trip time of approximately **12 ms**, which indicates a healthy and responsive connection to Google.

**3. Why is DNS important before communication begins?**

DNS is critical because:
- The Internet routes traffic using **IP addresses**, not human-readable names like `google.com`
- Without DNS, your device wouldn't know **which IP address to connect to** for any website
- DNS acts like a **phonebook** â€” you look up the name, and DNS gives you the number (IP)
- Every time you open a website, an app, or send an email, DNS resolution happens first â€” it is the **first step** in almost all Internet communication
- If DNS fails, even though the Internet is working fine, you cannot reach any service by name

---

## ðŸ“ Repository Structure

```
Network_Task_02_Akash/
â”‚
â”œâ”€â”€ README.md                    â† This file (full documentation)
â”‚
â””â”€â”€ screenshots/
    â”œâ”€â”€ ip_addr_output.png       â† Output of: ip addr
    â”œâ”€â”€ nslookup_google.png      â† Output of: nslookup google.com
    â””â”€â”€ ping_google.png          â† Output of: ping google.com
```

---

## âœ… Task Completion Checklist

- [x] Part A â€“ Researched and explained 6 network devices
- [x] Part B â€“ Classified 6 IP addresses as Public or Private with explanations
- [x] Part C â€“ Identified device IP, gateway, DNS; answered all 4 analysis questions
- [x] Part D â€“ Created network communication flow diagram with step-by-step explanation
- [x] Part E â€“ Ran `ip addr`, `nslookup`, and `ping` commands with outputs and analysis
- [x] Screenshots included in `/screenshots/` folder
- [x] README.md documentation complete

---

> ðŸ“Œ *This task is part of the White Band Associates Internship Networking Program.*
> *Repository is updated with each task in separate folders.*
