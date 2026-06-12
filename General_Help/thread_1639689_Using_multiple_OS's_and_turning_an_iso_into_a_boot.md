---
title: "Using multiple OS's and turning an iso into a bootable usb"
date: 2010-12-07
forum: General Help
---

### Post by mrmoocky on 2010-12-07
I am currently running Ubuntu 10.10 64 bit. I have the ISO for windows 7 and would like to be able to boot it from a USB pendrive. I was hoping it would be as easy as extracting the ISO copying the files onto the pendrive. Upon rebooting I changed the boot order so my pendrive was first but once I left the BIOS my computer complained it couldn't find Ubuntu. Now obviously I want to install windows 7 not run Ubuntu. So what I want is this:

1) Create a windows 7 bootable pendrive from an ISO, while running Ubuntu
2) Clear my hard drive and install windows 7 from said pendrive

With windows installed I'll re-install Ubuntu so I may chose from either OS's upon boot up. 
Help would be much appreciated.

---

### Post by Megaptera on 2010-12-07
Is this guide any help?

Create A Bootable Windows 7 USB Drive From Linux (Tested On Ubuntu)

[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by C.S.Cameron on 2010-12-07
Using gparted, format the USB drive NTFS and set the boot flag.
Copy the files to it from the DVD or extract the iso to it.

---

