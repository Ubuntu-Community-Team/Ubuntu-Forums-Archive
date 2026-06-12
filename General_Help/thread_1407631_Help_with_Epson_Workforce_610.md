---
title: "Help with Epson Workforce 610"
date: 2010-02-15
forum: General Help
---

### Post by sarajevl on 2010-02-15
I know you all hear this on most of the posts but I am new to ubuntu, and to complicate I am not a terrific techy or a programmer for anything above html. I can follow directions well.

My problem:

Bought an Epson Workforce 610 because the store and a website I found showed it would function in Linux. ( [http://www.openprinting.org/show_printer.cgi?recnum=Epson-WorkForce_610](http://www.openprinting.org/show_printer.cgi?recnum=Epson-WorkForce_610) ). This site wants me to download a driver package (I guessed I needed the [FONT=ms sans serif, helvetica][x86 32 bit (DEB for LSB 3.1)]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.1/gutenprint/binary-i386/gutenprint_5.0.1-1lsb3.1_i386.deb") )[/FONT] and I installed it.

I installed the printer in ubuntu as a workforce 600.

I can print.

However, This is a multifunction device and I cannot scan. When I open xsane it says: "no devices available"

Info I can provide:

sara@ubuntulap:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 04b8:0855 Seiko Epson Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I am running on a Toshiba Satellite L305-S5955

I am running Ubuntu 9.10

If you need anymore info let me know. 

I really need to get this scanner working.

---

### Post by ellgor on 2010-02-16
Hi,

Go to the "Avasys" site, its for Epson's, and get their Imagescan package, get the Deb package as gdebi loads it in auto, takes a reboot to make it work.

Regards, Ellgor.

---

### Post by rocker2344 on 2010-05-09
well this took me a wile to figure out.
i know 100% it will work on ubuntu 10.04 with some old deb packages.
1)[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)  <needed for iscan

2)[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
select the workforce 610 (you can use ctrl f to find it)

Search for this:
**Download for Epson Stylus Office BX610FW/TX610FW,Epson Stylus  SX610FW,WorkForce 610/615 Latest Version**

and choose your bit version

install xsane from the package manager

restart your computer

Happy scanning!

---

### Post by SoFl W on 2010-06-01
Just wanted to thank you and let you know this information helped out and worked.  This went quickly and smoothly, I think the time from taking it out of the box to my first print, to my first scan was about a half hour.

**IMPORTANT NOTE**:  I did set up the unit with a static IP.  (Epson calls it manual set up)  I think it is important to set up the printer/scanner with a static IP when it comes to scanning because of the configuration file "/etc/sane.d/epkowa.conf"  This way you are sure the address doesn't change.

If found [this other page ]("http://ubuntuforums.org/showthread.php?t=1393162")of use also:
[http://ubuntuforums.org/showthread.php?t=1393162](http://ubuntuforums.org/showthread.php?t=1393162)

I want to thank the users on this page and the other page listed above for their help.

---

