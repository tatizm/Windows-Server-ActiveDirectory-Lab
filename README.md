# Windows Server 2016 Enterprise Lab & Active Directory Setup

## 📌 Overview
This repository documents the step-by-step deployment and troubleshooting of a virtual network infrastructure using Windows Server 2016 and Windows 10 Enterprise in an isolated lab environment.

## 🛠️ Network Architecture & Topology
- **Domain Name:** `aria.local`
- **Domain Controller (DC):** Windows Server 2016 (`192.168.10.2 /24`)
- **Roles Installed:** Active Directory Domain Services (AD DS), DNS Server, DHCP Server
- **Client Machine:** Windows 10 Enterprise (`192.168.10.50 /24`)
- **Virtualization:** VMware Workstation (Isolated Host-Only `VMnet1`)

## 🚀 Key Implementations
- Configured AD DS and promoted the server to Primary Domain Controller for `aria.local`.
- Created custom DHCP Scope (`192.168.10.100 - 192.168.10.200`) and authorized the DHCP server within Active Directory.
- Successfully joined the Windows 10 client machine to the domain.

## 🔍 Troubleshooting Log & Lessons Learned
During the implementation, a DHCP assignment issue occurred where the client machine received an APIPA address (`169.254.x.x`). 

### Root Cause Analysis & Resolution Steps:
1. **Network Connectivity Verification:** Verified layer-2/3 connectivity between host and client using static IPv4 configurations and successful ICMP Echo Requests (`ping`).
2. **DHCP Binding & Authorization Check:** Verified DHCP server status in the Active Directory management console and validated interface bindings on `192.168.10.2`.
3. **Virtual Network Editor Adjustment:** Reconfigured VMware Workstation `VMnet1` subnet configuration to align with the server's scope (`192.168.10.0/24`) and resolved virtual switch broadcast isolation.
