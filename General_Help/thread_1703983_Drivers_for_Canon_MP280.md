---
title: "Drivers for Canon MP280"
date: 2011-03-10
forum: General Help
---

### Post by Tabourie on 2011-03-10
:confused: I have a CanonMP280 printer and Ubuntu 10.10.
Mp280 is not recognized by Ubuntu 10.10.

Through 'cybertechhelp' I was very lucky to get the printing drivers to install.
So the printer works.

No-one seems to be able to find the 'scanner' drivers and Canon_help is useless.
So I must dual-boot with Windows to be able to scan.

Although win7 is a vast improvement on vista. I would much prefer to single-boot with Ubuntu.

I tried other Ubuntu and Ubuntu-Based distros, but, the printer-drivers I have, only work in Ubuntu 08.04 - 10.10 

Can anybody tell me where to find the drivers I need please?

---

### Post by nickleboyblue on 2011-03-10
Cannon doesn't support Linux with their recent printer/scanners, and any drivers that are available are most likely hacks.  Cannon doesn't seem to have any plans in place to extend Linux support in the near future either.  If you want to have a fully functional all in one printer, get one from HP instead.  HP has excellent support for Linux, and their printers are usually very nice.

BTW, Welcome to Ubuntu!  Most likely, you won't find anything better once you get past the driver issues.

---

### Post by Tabourie on 2011-03-10
**@Tabourie**
There are some support sites of Canon where Linux drivers can be found. Even for your printer: [http://software.canon-europe.com/products/0010883.asp](http://software.canon-europe.com/products/0010883.asp). Download the driver from the site i give you and try that out. In 99.9% of all cases those drivers do work. The problem with Canon is not that they don't care about Linux, the problem is the poor support for Canon hardware in Linux.[/QUOTE]


Thankyou...

I went in there and downloaded the MP280 drivers.
I extracted and installed the scanner drivers.
Now. Xsane keeps telling me :-  no devices are available.

I have tried restarting the printer and Ubuntu.
I have tried re-installing the drivers.

XSane keeps giving me the same answer.

Do you have any ideas please?

---

### Post by nomko on 2011-03-10
Connect your printer to the computer (obviously you did this already ;) ) and turn the power on.
Now open a terminal and type: **lsusb**.
Place the output of this command here.

---

### Post by nomko on 2011-03-10
> **nickleboyblue said:**
> Cannon doesn't support Linux with their recent printer/scanners, and any drivers that are available are most likely hacks.

**WRONG!**
 
There are drivers available for Canon hardware. Just do some research first before making such conclusions. 
 
Canon doesn't work out-of-the-box like HP or Epson. Canon has a poorly support under Linux. But thtre are drivers available at official Canon support sites.
 
> 
 Cannon doesn't seem to have any plans in place to extend Linux support in the near future either. If you want to have a fully functional all in one printer, get one from HP instead. HP has excellent support for Linux, and their printers are usually very nice.
 

---

### Post by Tabourie on 2011-03-10
> **nomko said:**
> Connect your printer to the computer (obviously you did this already ;) ) and turn the power on.
Now open a terminal and type: **lsusb**.
Place the output of this command here.


dave@dave-desktop:~$ lsusb
Bus 013 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 012 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 004 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 Webcam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 04e8:3409 Samsung Electronics Co., Ltd SCX-4216F Scanner
Bus 003 Device 006: ID 0b05:1723 ASUSTek Computer, Inc. WL-167G v2 802.11g Adapter [ralink]
Bus 003 Device 005: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 002: ID 04a9:1746 Canon, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dave@dave-desktop:~$

---

### Post by nickleboyblue on 2011-03-10
Um, sorry about that mistake.  I got a bit confused with the brands.  My recent camera company printer gave me all sorts of problems, and I obviously mixed up the brands.  Steer clear of Kodak at all costs.  THEY are the ones that don't plan on supporting Linux in their latest line, as was expressed to me through their "customer service" emails.

---

### Post by nomko on 2011-03-11
> **nickleboyblue said:**
> Um, sorry about that mistake. I got a bit confused with the brands. My recent camera company printer gave me all sorts of problems, and I obviously mixed up the brands. Steer clear of Kodak at all costs. THEY are the ones that don't plan on supporting Linux in their latest line, as was expressed to me through their "customer service" emails.
 
Kodak, Brother, Lexmark... most of those brands are just aiming for the Windows users and Windows market. Besides that, those brands simply don't have the knowledge "in the house" to make a driver for Linux. Producing a driver for Windows is much easier then producing a driver for Linux. For Windows all they have to do is developing 1 single driver, despite the numerous differences in Windows systems. For Linux they have to produce the driver on a different way which requires knowledge on another level. 
 
Canon for instance, does support Linux, but not out-of-the-box. They do have several support sites which provides the users of drivers which normally do work. But then again, succes is not garanteed. 
 
I've recently bought a new HP printer, HP B110a ePhotosmart which was too new for Ubuntu 10.04.1. Just updating the HPLIP driver and it works perfectly! That;s the biggest benefit of HP and Epson, better support for Linux, out-of-the-box and through driver updates.

---

### Post by wildmanne39 on 2011-05-18
> **Tabourie said:**
> :confused: I have a CanonMP280 printer and Ubuntu 10.10.
Mp280 is not recognized by Ubuntu 10.10.

Through 'cybertechhelp' I was very lucky to get the printing drivers to install.
So the printer works.

No-one seems to be able to find the 'scanner' drivers and Canon_help is useless.
So I must dual-boot with Windows to be able to scan.

Although win7 is a vast improvement on vista. I would much prefer to single-boot with Ubuntu.

I tried other Ubuntu and Ubuntu-Based distros, but, the printer-drivers I have, only work in Ubuntu 08.04 - 10.10 

Can anybody tell me where to find the drivers I need please?

Hi, also here is ehat you need I think if the other way does not work. [http://ubuntuforums.org/showthread.php?t=1582497](http://ubuntuforums.org/showthread.php?t=1582497)

---

