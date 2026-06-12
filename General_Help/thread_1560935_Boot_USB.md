---
title: "Boot USB"
date: 2010-08-25
forum: General Help
---

### Post by Vexiphne on 2010-08-25
Hi.

A client want me to install windows on his laptop :(
I have windows xp pro sp3 on an iso, but is there an application like startup disk creator that I can use to make a boot usb from that windows iso?

**Note:** I'm installing windows on that laptop under strong protest :D

---

### Post by oldfred on 2010-08-25
We are not a windows forum. :p

But I did save, but have not used any of these:
Windows In Your Pocket USB using BartPE
[http://www.tomshardware.com/reviews/windows-pocket,1113.html](http://www.tomshardware.com/reviews/windows-pocket,1113.html)
Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)

---

### Post by Vexiphne on 2010-08-25
I know this isn't a windows forum. So when I wrote that I needed an application I thought it was self explanatory that I was looking for a linux/ubuntu application and NOT windows application. I guess I have to explain from now on that I'm talking about Ubuntu/Linux. ;)

Sooo.... I'm looking for a **UBUNTU/LINUX APPLICATION** that can make bootable USB. **I USE UBUNTU** and need to make a bootable windows install USB. Is there an application or a way to do this?

Again for those that does not understand what I'm talking about. I need a **linux** application that does what I wrote above. :rolleyes:

---

### Post by oldfred on 2010-08-25
I think not as you have to get the windows boot loader into the partition boot sector.

As a test I tried with the win7 recovery CD from Neosmart. I was not able to get it to copy and boot. What I ended up doing was creating a CD and using the CD to copy to the USB. Somewhere in the copy functions windows copied the MBR & PBR boot to the USB. After booting once with windows I installed grub2 to the USB and chainloaded to the windows partition PBR and it still booted.

---

### Post by Vexiphne on 2010-08-25
Thanx oldfred :)

---

