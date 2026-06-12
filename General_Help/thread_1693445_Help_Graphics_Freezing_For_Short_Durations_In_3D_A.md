---
title: "Help: Graphics Freezing For Short Durations In 3D Accelerated Programs."
date: 2011-02-22
forum: General Help
---

### Post by Mao Brutus on 2011-02-22
Any time I use a program that has 3D graphics everything has a 'laggy' appearance and freezes for short seconds. These programs included any of the games from Ubuntu Software Center, along with other applications such as games ran through Wine(seperate problem). This is a brand new installation of Ubuntu 10.10, and any suggestions would help.

Things to keep in mind:
-I've downloaded the automatic updates through Ubuntu Software Center.
-I'm fairly new to Ubuntu(still learning).
-Provide as many details in, if, you post a possible solution.
-I'm only using Ubuntu 10.10 as my OS, no dual-boots with Windows or any other OS.

[FONT=Verdana]If anyone could shed some light on this I would be massively in debt to you, and you would have my millions of thanks.[/FONT] 

LSPCI (Hardware Info):

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
**01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)**
03:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
03:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
03:03.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)

---

### Post by Mao Brutus on 2011-02-23
Simple Newbie Mistake:
Forgot to update drivers...

System > Administration > Additional Drivers > Nvidia (Recommended).

Hooray! If any other in-experienced Ubuntu 10.10 users have this problem, hope this helps.

---

