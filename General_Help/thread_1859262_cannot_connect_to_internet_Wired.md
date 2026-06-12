---
title: "cannot connect to internet Wired"
date: 2011-10-13
forum: General Help
---

### Post by thebigd123 on 2011-10-13
I am trying Linux and Ubuntu for the first time. I took an old Dell Dimension 3100 P4 PC erased XP and have installed Ubuntu 11.04 on it from the Live CD.

When I plugged my Comcast WIRED modem cable into the computer it is unable to establish connection to the internet. (It also was unable to connect during install of Ubuntu)

I found lots of post on the web of people having the same problem with no answer to how to fix the problem.

Any ideas?

---

### Post by thebigd123 on 2011-10-15
[SIZE=3]**Here are the results when I run lspci -nn**[/SIZE]

 
dennis@dennis-Dell-DV051:~$ lspci -nn  
 00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)  
 00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)  
 00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 04)  
 00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)  
 00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04)  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)  
 00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)  
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d4)  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 04)  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)  
 00:1f.2 IDE interface [0101]: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller [8086:2652] (rev 04)  
 00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)  
 03:02.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]  
 03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 04)  
 


[SIZE=3]**When I run sudo lshw**[/SIZE]


 dennis@dennis-Dell-DV051:~$ sudo lshw -c network;lsb_release -a; uname -a
   *-network                
        description: Ethernet interface
        product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
        vendor: Intel Corporation
        physical id: 8
        bus info: pci@0000:03:08.0
        logical name: eth0
        version: 04
        serial: 00:16:76:68:20:9d
        size: 10Mbit/s
        capacity: 100Mbit/s
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
        resources: irq:20 memory:dfcef000-dfceffff ioport:dcc0(size=64)
 No LSB modules are available.

---

