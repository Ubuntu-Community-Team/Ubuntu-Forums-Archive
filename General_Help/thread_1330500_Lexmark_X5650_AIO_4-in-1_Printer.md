---
title: "Lexmark X5650 AIO 4-in-1 Printer"
date: 2009-11-18
forum: General Help
---

### Post by UKBB on 2009-11-18
Is anyone using this printer successfully with Ubuntu?

---

### Post by fluffman86 on 2009-11-18
I can't get lexmark printer to work in Windows, much less Ubuntu. :P

But seriously...Lexmark printers are notorious for having poor drivers to begin with, and they don't release any drivers at all for Linux.  A few may have been reverse engineered.  Check [http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)

---

### Post by UKBB on 2009-11-18
Thanks, I didn't see it listed at all.

---

### Post by el_camello on 2010-02-27
Hello,

I have found that lexmark has drivers for for X7600, X6600, X5600, Z2400, X4900, X4600 and X3600. The file is " lexmark-08z-series-driver-1.0-1.i386.rpm.sh.tar.gz " I tested it with suse gnome 32 bits and it can print from open office; also I use fedora 12 but has to be in 32 bits; It does not work with suse 64 bits or Kubuntu 64 bits (my current system).

It will be nice if any person can find the solution to make it work in my kubuntu 64.

Thanks.

---

### Post by awakecoding on 2010-03-01
Hi,

I found your thread yesterday as I was trying the new Linux driver for my Lexmark printer. I have actually gone through the process of making it work on my 64-bit Debian system and I almost got it to work on 64-bit Ubuntu 9.10. I'm hoping that someone here can figure out the part I'm missing to make it work in Ubuntu. Something about the USB device detection or with the CUPS backends appears to be broken. Here is the article I've written just for you guys:
[U]
[Installing Lexmark Linux Drivers in 64-bit Debian-Based Distributions]("http://www.awakecoding.com/index.php?option=com_content&view=article&id=20:installing-lexmark-linux-drivers-in-64-bit-debian-based-distributions&catid=1:home")
[/U]
I hope this will help some of you get their printer to work. If anybody figures out the problem with Ubuntu compared to Debian, please tell me so that I update my article :)

---

### Post by Bob_G7 on 2010-03-22
I have both the Lexmark x5650 USB and x6650 wireless. I went to Lexmark, looked up the printers and downloaded the package from them (lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz).

After unpacking the file with Archive Mounter I ran the lexmark-08z-series-driver-1.0-1.i386.deb.sh file produced and followed the onscreen instructions.

At first I couldn't get the printers to work till I unplugged both the power and USB cables and plugged them back in.

I still can't get the x6650 Wireless to work without having the USB cable plugged in but they both do print and scan, still not tried the FAX yet.

---

### Post by wbar2 on 2010-03-28
Anybody have any luck with installing on a 64-bit Ubuntu 9.10? I downloaded the drivers from Lexmark and it installed without errors, but I still can't get it to print.

---

### Post by wbar2 on 2010-03-30
Got it working on 64-bit: [http://ubuntuforums.org/showthread.php?t=1441862](http://ubuntuforums.org/showthread.php?t=1441862)

---

