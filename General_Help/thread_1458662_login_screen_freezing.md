---
title: "login screen freezing"
date: 2010-04-20
forum: General Help
---

### Post by jsvidyad on 2010-04-20
Hi!!

  I am running 64 bit karmic koala. I use the Gnome desktop. My issue is that the login screen sometimes freezes. This happens sometimes when I don't login immediately and try to log in after some time. The computer is completely unresponsive and all I can do is press the power key till the computer shuts off. Does anyone know why this happens?

---

### Post by Ravernomina on 2010-04-20
This is not enough Information... please give the results of the following Commands

```
uname -a
```
and
```
lspci
```
and
```
lsusb
```

---

### Post by dannyboy79 on 2010-04-20
is this an issue with gdm crashing and then restarting? are you're saying that the computer completely freezes and you can't do anything if you dont login immediately. if you haev other computers in the house it may be a good idea to install ssh server on this box, let it freeze up but see if you can still ssh into it. after it locks up, can you reboot it and post these 2 log files using pastebin.  
/var/log/xorg.0.log
and a session log file located in /var/log/gdm
im wondering if it's related to bug [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200)
good luck

---

### Post by jsvidyad on 2010-04-20
The computer freezes completely if I wait for some time before logging in. It doesn't happen always. It has happened a couple of times. The computer becomes completely unresponsive and I have to press the power switch till it shuts off. The next time that happens, I will paste those files.

---

### Post by jsvidyad on 2010-04-20
uname -a gives

Linux garuda 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

lspci gives

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

lsusb gives

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

