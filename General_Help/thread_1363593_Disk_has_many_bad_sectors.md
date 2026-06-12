---
title: "Disk has many bad sectors"
date: 2009-12-24
forum: General Help
---

### Post by xpwnerlol on 2009-12-24
Hello everyone, I recently have installed Ubuntu 9.10. with Windows XP. When I log into Ubuntu I get something that says 250 GB Hard Disk_ata st3250310as DISK HAS MANY BAD SECTORS. Then after that it completely freezes everything, I can't use my mouse or anything. I am a newbie at Ubuntu. Can anyone help me out with this?

---

### Post by fragos on 2009-12-24
If you can't boot to XP either then your disk is likely bad. You could also boot from the Ubuntu LiveCD, open a terminal session and try running "fsck".

---

### Post by mocoloco on 2009-12-24
You *might* have bad sectors, but there's a [potential bug in Palimpsest]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/413673"), which is called "disk utility" in the menus.  I would first try a scandisk under Windows and see if it detects any bad sectors.  It will only scan it's own partition, but that will give you an idea of if there are bad sectors on the whole disk.  To do that right-click drive C, and I think it's under tools.  Select the boxes to have it check for and fix bad sectors too.  Then it will tell you to reboot.

If you do think there are problems you can do some further testing as outlined in the link above.  I saw this issue on a recent install on a new Dell, and after reading through the bug decided I don't think there's an issue with the disc.  I've turned off warnings from the Disk Utility and am watching the bug to see if the app gets improved before I'll trust it.

---

### Post by emarkay on 2010-01-24
It's a bug!  
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all)

Same issue posted here:
[http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2)

---

### Post by wrose51106 on 2010-01-24
Stupid bug, I just replaced the hard disk with a spare, literally like 5 minutes ago. At least I got enough spare drives laying around!

-Bill

---

