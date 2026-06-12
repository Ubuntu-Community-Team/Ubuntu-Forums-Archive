---
title: "Wireless with EeePC"
date: 2010-06-22
forum: General Help
---

### Post by MadCookie on 2010-06-22
There are some issues with wireless on my sisters EeePC 900. The wireless worked before, and then suddenly networking was disabled, and randomly wired networking got enabled. Still wireless does not seem to work.

```
lsnina@Nina:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
**03:00.0 Ethernet controller: Atheros Communications L2 100 Mbit Ethernet Adapter (rev a0)** 

```
(Only ethernet detected? [in bold])
Help me please :P

---

### Post by AgentWD-40 on 2010-06-22
Hmmmmm, can you plug it in via an Ethernet cable and try updating the system?

---

### Post by MadCookie on 2010-06-22
> **AgentWD-40 said:**
> Hmmmmm, can you plug it in via an Ethernet cable and try updating the system?

Already done :P

---

### Post by AgentWD-40 on 2010-06-22
I don't see your wireless device listed in the output you posted from lspci. Could you try running lsusb and post the results?

---

### Post by MadCookie on 2010-06-23
here:
```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 002: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by MadCookie on 2010-06-24
Bump!

---

### Post by gaussian on 2010-06-24
Try rebooting and check it is not disabled in the BIOS.

---

