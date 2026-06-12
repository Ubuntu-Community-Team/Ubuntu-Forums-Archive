---
title: "Windows + Ubuntu + Acronis = fail"
date: 2009-08-06
forum: General Help
---

### Post by walll on 2009-08-06
I have dualboot Windows 7 + Ubuntu 9.04 (windows is on "/sda/dev1" and ubuntu on "/sda/dev2" - no pagefile). All worked fine, but when i  enabled Acronis Startup Recovery Manager, Ubuntu loader was replaced with Acronis and i booted directly to windows. So i reinstalled grub loader and i maked this c[COLOR=Black]hanges[/COLOR] : [COLOR=Blue][http://kb.acronis.com/content/1504](http://kb.acronis.com/content/1504)[/COLOR]. 
It's working, after Acronis i can see dualboot Ubuntu and Windows. But when a boot windows, my Active partition is always automatically changed from "/sda/dev2" back to "sda/dev1". And after restart i'm booting directly to windows again. How can i disable that windows malware from changing my Active partition, or what can i do? Thanks for help.

---

### Post by starcraft.man on 2009-08-06
The problem here is simple, you enabled Acronis Startup Recovery Manager. I've been an Acronis user a while (mostly because I started on Windows, there are good alternatives), and I can assure it's crap (the startup manager, the program itself is very good). Do yourself a favour and disable it. Then make a recovery CD from Acronis to boot when you need to image and restore, the odd time that is. Once disabled, restore GRUB to proper functioning as your master bootloader (installed to the drives MBR, not a partition). From what your saying, seems you installed it to the partition instead of MBR. Problem solved.

---

### Post by walll on 2009-08-06
I maked it! I installed grub to MBR and i copied files from Acronis BootCD to /boot/acronis directory and i added appropriate entries to grub menu.lst. Now is working fine.

---

### Post by aerogamer on 2009-08-19
> **walll said:**
> I maked it! I installed grub to MBR and i copied files from Acronis BootCD to /boot/acronis directory and i added appropriate entries to grub menu.lst. Now is working fine.


I've been trying to do this as well with Acronis True Image Home 2009 PC Backup & Recovery.  I have seen the old post ([http://ubuntuforums.org/showthread.php?t=449167](http://ubuntuforums.org/showthread.php?t=449167)) that details how to do this with Acronis TI 10, but I cannot extract the ramdisk.dat from the 2009 boot disc.  All I get in the terminal instance is about 10 minutes of scrolling random characters followed by an error.  I dual boot with 2 seperate sata drives.  Any ideas?

---

