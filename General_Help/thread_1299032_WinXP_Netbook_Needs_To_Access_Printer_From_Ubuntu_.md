---
title: "WinXP Netbook Needs To Access Printer From Ubuntu 9.04 Desktop"
date: 2009-10-23
forum: General Help
---

### Post by s1mp13m4n on 2009-10-23
Hello everyone.  The computer in the kitchen was a WinXP machine, now it is an Ubuntu 9.04 machine.  It has a HP Officejet J4550 all in one printer hooked to the usb port of the Ubuntu machine.  My bedroom computer which is Ubuntu 9.04 can see and use the printer.  My wife's WinXP netbook does not see the printer.  How can I make WinXP see a printer on an Ubuntu machine?  The netbook is wireless using 802.11g and a Linksys router.

---

### Post by s1mp13m4n on 2009-10-23
I finally got it figured out.  It was not a Linux issue at all, so i have to make it work in Windows and it was easy once I got passed the DUH factor.  

I downloaded the driver only for my printer from HP
I used WinRAR to extract the files to an HP folder on my desktop
I went into the add printer qizzard and typed in the address of the printer which is on the Linux machine http://192.168.x.x:631/printers/"my printer name as listed in Linux"
Winxp found the networked printer and asked for a driver
selected Have Disk and point it to the folder you just made with the driver in it
you are all done

---

