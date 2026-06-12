---
title: "headless server without monitor?"
date: 2010-06-13
forum: General Help
---

### Post by Enthrall on 2010-06-13
Well xubuntu wont boot without a monitor. I booted freenas without the monitor and plugged it back in and got a signal. So it isnt the bios. Thank god because there is no vga halt option.

So anyone out there, that can help me out?

---

### Post by spiky001 on 2010-06-13
I found this about editing xorg file #8
[http://ohioloco.ubuntuforums.org/showthread.php?t=1223504](http://ohioloco.ubuntuforums.org/showthread.php?t=1223504)

---

### Post by Enthrall on 2010-06-13
Well there is no xorg.conf in x11 so i created one and tryed two different configs each time it boots blank. Then I have to boot ubuntu and go into my hard drive and find the xorg file to delete so i can boot to desktop again.

Any advice anyone?

---

### Post by Enthrall on 2010-06-13
lspci shows this if it'll help, where is the config file for intel?

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)

---

