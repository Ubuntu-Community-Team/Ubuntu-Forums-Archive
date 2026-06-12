---
title: "Would this work on Ubuntu 12.04.1"
date: 2012-09-10
forum: General Help
---

### Post by ubuntu27 on 2012-09-10
HP Pavilion dv6700 Notebook PC
Proccesor: AMD Ahlon(tm) 64 X2 Dual-Core Processor TK-57 1.90 GHz
Network Adapters: Atheros AR5007 802.11b/g/ WiFi Adapter
Display: **Nvidia GeForce 7150M / nForce 630 M**
RAM: 2 GB


This laptop currently has Ubuntu 11.04 (Natty Narwhal) and it is running fine. However I will like to upgrade to Ubuntu 12.04 and I was wondering if the Nvidia card will be a problem.

I tested in on a Live USB session with Ubuntu 12.04.1 image. And it seems that it cannot find any proprietary Nvidia drivers and the screen looks ugly. Is there a fix that could be applied after installing Ubuntu?

Thank you guys!


Further info:

```
lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by Epodx64 on 2012-09-10
For some reason the Nvidia drivers really regressed in 12.04.1 what you'd need to do is install 12.04.1 then when you get to the log in screen right click the logo and select 2D Unity and log into that then add x-swat/x-updaters ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) then do sudo apt-get update then load jockey and install the 304.x driver don't even bother installing the recommended driver it will break X the 29x.x series are utterly worthless and don't work.

---

### Post by ubuntu27 on 2012-09-10
Hi Epodx64. Thank you for the reply.

What about about the "nvidia-current-updates" in the repo that has Nvidia 295.49-0ubuntu0.2 driver? That dosn't work either?


Thanks for the suggestion of x-updaters ppa :popcorn:

---

### Post by jerome1232 on 2012-09-10
> **Epodx64 said:**
> For some reason the Nvidia drivers really regressed in 12.04.1 what you'd need to do is install 12.04.1 then when you get to the log in screen right click the logo and select 2D Unity and log into that then add x-swat/x-updaters ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) then do sudo apt-get update then load jockey and install the 304.x driver don't even bother installing the recommended driver it will break X the 29x.x series are utterly worthless and don't work.


I'm using 295.4 flawlessly here /shrug It got installed automatically during the installation.

---

### Post by Epodx64 on 2012-09-10
When I had my Nvidia chipset (MCP 61 Geforce 6150se Nforce430) the 295.4 couldn't even draw a window trust me in KDE it's pretty frustrating had the same problem when I was giving Linux Mint 13 Cinnamon a try but once I got the 304.x driver it worked flawless  kde & cinnamon & on unity but getting the drivers was alot easier on unity because of the 2d mode

---

### Post by jerome1232 on 2012-09-10
I am on a desktop , with an Nvidia  GTS450 so that may make a big difference .

---

### Post by ubuntu27 on 2012-09-11
Hi everyone!

I jumped in and installed Ubuntu 12.04.1 and nvidia 295.49 from the repo. It is workign wonderfully.

I have not tested the gaming performance, so if I see a negative impact, then I might try the  x-swat/x-updaters ppa.


For now it is solved. Thank you all!

---

