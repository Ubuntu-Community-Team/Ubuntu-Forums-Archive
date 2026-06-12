---
title: "Add Windows to Boot Menu"
date: 2009-08-30
forum: General Help
---

### Post by mibbster on 2009-08-30
Okay, so I've installed Ubuntu Server 8.04.3, and now I'd like to install Windows in the empty space I've left on my hard drive.

I realize that I need to backup my MBR before I do so.  Is there anything else I should do before I install Windows?

After I install Windows, I know that I will need to restore my MBR using dd from a livedisc.  Now -- here's my main question: I'm assuming that GRUB will be entirely unaware of the fact that Windows is installed on the machine.  How do I add Windows to the boot menu?  I know that there is a way to do it by adding an entry to grub.cfg or something like that, but I would like to know if there is a more straightforward, automatic way to do it.  I think there must be, because had Windows been installed prior to my Ubuntu installation, the ububntu-server installer would have scanned my HDD and auto-detected Windows there and then automatically added it to the boot menu.  How can I prompt it to go through this procedure again and update the boot menu?  Thanks in advance :)!

---

### Post by dandnsmith on 2009-08-30
I don't know of an automatic method (no guarantee one does not exist) - you add to the grub.conf (or menu.lst) a new section, something like:

title Windows
rootnoverify (hd0,3)      *or wherever your partition is*
chainloader +1


and that should do it. Note that description of partition is grub fashion, with disk and partition numbering from zero.

---

### Post by mibbster on 2009-08-31
So basically do [this]("http://ubuntuforums.org/showthread.php?t=610557#post3755614"), and replace hd0,1 with hd<0 for sda, 1 for sdb, 2 for sdc, etc>,<partition number, i.e. 1 for sda1, 2 for sda2, etc.

Is that correct?

---

### Post by hyperdude111 on 2009-08-31
I made a guide for this, its written for Windows7 but will work with any other windows.

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by mibbster on 2009-08-31
Link index for posterity googlers (and just a nice centralized place for myself to review my research).

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)
[http://ubuntuforums.org/showthread.php?t=610557](http://ubuntuforums.org/showthread.php?t=610557)
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)
[http://ubuntuforums.org/showthread.php?t=610557](http://ubuntuforums.org/showthread.php?t=610557)

---

