---
title: "Dell Inspiron 1501-no wireless connection"
date: 2010-05-03
forum: General Help
---

### Post by mr_biglz0rth1985 on 2010-05-03
well I had an HP a year ago that got destroyed from a worm and my friend gave me this laptop. Its a Dell Inspiron 1501 . I'm not sure what kind of wireless card it is using nor do I know how to find out. The computer was built in 2004 to my knowledge. How do I troubleshoot this and what do I do as far as trying to get it to work? I'm very much a newb but have a heart for open source products. I have something called synaptics on here....will that help me?
I have Lucid Lynx.

I want to be able to detach from the wires and roam freely with my newly established Ubuntu pc. Please help!

---

### Post by mr_biglz0rth1985 on 2010-05-03
Do I need to move this thread somewhere else?

---

### Post by clhsharky on 2010-05-03
HI mr_biglz0rth1985

First

Run code in terminsl
```
lspci
```

Or if its USB
```
lsusb
```

To find out what card you have.

Sharky

---

### Post by mr_biglz0rth1985 on 2010-05-03
> **clhsharky said:**
> HI mr_biglz0rth1985

First

Run code in terminsl
```
lspci
```

Or if its USB
```
lsusb
```

To find out what card you have.

Sharky



this is what I got
-----------------------------------------------------------------------


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

----------------------------------------------------------------------


**[COLOR="DarkGreen"]what do I do next to enable my wireless? [/COLOR]** :o :confused:

---

### Post by mr_biglz0rth1985 on 2010-05-03
or at least what can I try to start out with to troubleshoot?

---

### Post by clhsharky on 2010-05-03
mr_biglz0rth1985


Yep its a

Broadcom Corporation BCM4311

I don't have that card. 

Search this forum 'BCM4311'

Or goggle 'Ubuntu BCM4311'

Sorry I wasn't more help

Sharky

---

### Post by mr_biglz0rth1985 on 2010-05-03
BCM4311 it seems that this card has had a TON of issues....I just don't know where I need to look first!....I'm soooo lost!

---

### Post by john newbuntu on 2010-05-03
Here's something for a start:
[http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/](http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/)

---

### Post by mr_biglz0rth1985 on 2010-05-03
> **john newbuntu said:**
> Here's something for a start:
[http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/](http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/)


sadly that didn't work either.....what next?

---

### Post by mr_biglz0rth1985 on 2010-05-03
Wow I'm such a NEWB,.......
I just realized it was something as simple as pressing a couple of keys....Thank you for your help shark

[I] Re: Ubuntu 9.10; wireless network connectivity
Thank you Epoh,

I got my Wireless working, thank to your drivers and instructions.
I wouldn't have done without it.

My exp: When every thing is configured, the hardware GUI says, cannot find the hardware even after i used [SIZE="6"][FONT="Times New Roman"]Fn F2[/FONT][/SIZE] [/I]

I gave it a thought that it was something as simple as pressing the fn function on my laptop and that was it.....wow I feel like such a dummy,...I hope that during this process I didn't hurt my laptop in any way haha

---

### Post by DirtyPC on 2011-06-09
Resurection or what :P
But, curious, the tag says it was 10.04, did you just turn wifi and it worked? nothing else? Thanks.

---

