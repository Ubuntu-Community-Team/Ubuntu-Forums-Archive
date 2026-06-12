---
title: "dual boot from old XP disk"
date: 2010-10-15
forum: General Help
---

### Post by azou on 2010-10-15
Hi,
I have Ubuntu on my PC. I have found a hard disk with XP on it and put it in the PC because I wanted to make a dual boot configuration. I've already modified menu.lst. The problem is that when I choose from grub menu to start XP, it shows 'Starting up ...' and nothing happens. If I choose to boot ubuntu (sda), it boots ok. Well this happens if in BIOS boot priority is given to ubuntu' hard disk. If it's given to hard disk with XP on it (sdb), it loads normally (from its own mbr) but obviously there's no dual boot option. 

I added this at the end of menu.lst:
title		Microsoft Windows XP
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

How can I make an operating dual boot configuration?

Best regards!

---

### Post by blueridgedog on 2010-10-15
Try editing the boot.ini file on the windows disk to instruct it that windows is no longer on hard drive 0.  Make a backup before you make any edits!!

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

The file should be in the root of the windows partition and can be edited with gedit.

---

