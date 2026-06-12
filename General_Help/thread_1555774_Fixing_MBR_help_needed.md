---
title: "Fixing MBR help needed"
date: 2010-08-18
forum: General Help
---

### Post by KarmicKlot on 2010-08-18
I have an old laptop with a small hard drive on which I had Ubuntu 9.04 and Windows XP. I tried to recover the hard drive space used by Ubuntu and run it as a pure XP machine.  I deleted the Ubuntu partition by running Gparted from the Ubuntu live DVD.  The result is that the computer will not boot.  All that happens is that this appears.
 
GRUB Loading.
error : no such partition
grub rescue> _
 
The underscore is flashing but I have no idea what command to use.
Can anybody help?  I do not have a full Windows disk to run recovery console and the fixmbr command.

---

### Post by howefield on 2010-08-18
Plenty of threads for you to search through answering this question, eg..

[http://ubuntuforums.org/showthread.php?t=712435](http://ubuntuforums.org/showthread.php?t=712435)

---

### Post by wilee-nilee on 2010-08-18
> **KarmicKlot said:**
> I have an old laptop with a small hard drive on which I had Ubuntu 9.04 and Windows XP. I tried to recover the hard drive space used by Ubuntu and run it as a pure XP machine.  I deleted the Ubuntu partition by running Gparted from the Ubuntu live DVD.  The result is that the computer will not boot.  All that happens is that this appears.
 
GRUB Loading.
error : no such partition
grub rescue> _
 
The underscore is flashing but I have no idea what command to use.
Can anybody help?  I do not have a full Windows disk to run recovery console and the fixmbr command.

Here are the instructions and a XP ISO link if you don't have a XP disc.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

You should only have to boot the disc get to the repair console and run fixmbr. Yo can use a live Ubuntu cd to expand XP with gparted after you have it booting again.

---

### Post by oldfred on 2010-08-18
From the Ubuntu liveCd you can run this:

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

The lilo boot loader works just like the windows boot loader in that it just looks for the active partition (boot flag) and jumps to that partition to continue booting.

---

### Post by KarmicKlot on 2010-08-18
Thank you all. I could not install LILO because I had deleted the Ubuntu partition, but I downloaded the Windows XP ISO image from one of the links, and burned it to a CD on my desktop machine, booted from it and ran fixmbr.  The laptop is now back from the dead!

---

