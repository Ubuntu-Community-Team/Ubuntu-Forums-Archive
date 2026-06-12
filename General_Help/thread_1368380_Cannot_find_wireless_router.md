---
title: "Cannot find wireless router"
date: 2009-12-30
forum: General Help
---

### Post by Anaximander2889 on 2009-12-30
Hi,  this is my first time working with Linux, and I installed Ubuntu 9.10 on my Dell laptop, but I cannot get it to connect to the internet.  I also have windows vista installed on the computer and it connects to the internet just fine, but Ubuntu will not even display the wireless networks available.  When I click to view the wirelss networks, all it says is disconnected, and it will not ping to the ip address of the network.  I've read different walkthroughs but I had some trouble understanding some parts.  I was wondering if anyone could help me out?   Thanks

---

### Post by bkratz on 2009-12-30
> **Anaximander2889 said:**
> Hi,  this is my first time working with Linux, and I installed Ubuntu 9.10 on my Dell laptop, but I cannot get it to connect to the internet.  I also have windows vista installed on the computer and it connects to the internet just fine, but Ubuntu will not even display the wireless networks available.  When I click to view the wirelss networks, all it says is disconnected, and it will not ping to the ip address of the network.  I've read different walkthroughs but I had some trouble understanding some parts.  I was wondering if anyone could help me out?   Thanks

Well first we would need to determine the wireless card used. Go to Applications>>accessories>>terminal and type in

lspci -nn

(that is LSPCI in lowercase) and either post the results here or decode them and let us know what the wireless card is.

---

### Post by Anaximander2889 on 2009-12-30
Here's the code for the wireless card, thanks for the quick response.
 
 
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)

---

### Post by bkratz on 2009-12-30
> **Anaximander2889 said:**
> Here's the code for the wireless card, thanks for the quick response.
 
 
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
**[COLOR="Red"]05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)[/COLOR]**
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)



You have the BCM4311
See post #8 of this thread


(Have a wired connection attached)

[http://ubuntuforums.org/showthread.php?t=1345519](http://ubuntuforums.org/showthread.php?t=1345519)

Well you can read the whole thread!

---

### Post by Anaximander2889 on 2009-12-30
Well, this fixed the problem temporarily.  Now I can only access my router if I activate the Broadcom STA driver each time I restart the computer.  The problem is though, once I connect to my router and go to Mozilla Firefox, one of two things happen:

1.  The screen flashes black and grey until I power it down manually.

2.  The mouse and keyboard no longer work and the caps and number lock flash until I power it down manually.

---

### Post by Anaximander2889 on 2010-01-01
I was working on trying to connect to the internet in this thread and now I have a new problem as shown in my last post.

[http://ubuntuforums.org/showthread.php?t=1368380](http://ubuntuforums.org/showthread.php?t=1368380)

---

### Post by cariboo on 2010-01-01
Please don't create multiple threads on the same problem. I have merged you two threads. If your threads falls way off the front page its acceptable to bump a thread after 24 hours has elapsed.

---

### Post by Anaximander2889 on 2010-01-03
Ok, thanks.  I'm still having the problem and not sure where to proceed with this.

---

