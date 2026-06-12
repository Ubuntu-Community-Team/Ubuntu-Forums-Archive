---
title: "Help! Broadcom Driver-Dell WLAN 1395."
date: 2009-12-09
forum: General Help
---

### Post by heeb2008 on 2009-12-09
Hello ubuntu community,


I am brand new to the ubuntu world. I installed Ubuntu Karmic 9.10 and I am excited to begin using it, however, I cannot figure out how to enable my wireless card (Dell Wireless WLAN 1395) with the correct driver. At first, when I opened my hardware drivers, Jockey said that there were no drivers on the system. Since then, I have tried using a couple things such as the bcmwl-kernel-source package, and another package that put b43 and b43legacy folders in my firmware folder. Now, I can see a Broadcom B43 Driver and STA Driver in my hardware drivers but they are both gray. I can't disable (does not give me the option to remove or disable) and when I try to activate it it just freezes up.

As a beginner to Ubuntu, I could have easily did something wrong while trying to do these things, but I have been trying for days to get this wireless card working and I haven't found any luck.

The only internet access I have is this wireless internet (no wired connection).




Thank you!

---

### Post by heeb2008 on 2009-12-09
I thought that this was a common issue, doesn't anyone know how to fix?

---

### Post by paradigm2 on 2009-12-09
What does 'lspci' show in a terminal window?

---

### Post by PRC09 on 2009-12-09
Try this page....



[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by deathbyswiftwind on 2009-12-10
In synaptic install the broadcom firmware cutter package. Just search broadcom and it will show up. After it installs it wil ask you if youd like to automatically fetch and extract the firmware. You do want to do that so make sure you select it. After everythng gets done restart and  see if your wireless now works. If not try one of the broadcom help posts but with all 5 of my broadcom cards Ive had it always worked 100%

---

### Post by heeb2008 on 2009-12-10
Deathbyswiftwind: It will not let me do that unless I have an internet connection, which, btw, I tried to connect to a wired connection and it didn't work. I already went to my user permissions to allow the internet.

My lspci is:

```
mjhebron@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
mjhebron@ubuntu:~$ 


```

---

### Post by Sin@Sin-Sacrifice on 2009-12-10
[http://ubuntuforums.org/showthread.php?t=765448](http://ubuntuforums.org/showthread.php?t=765448)

---

