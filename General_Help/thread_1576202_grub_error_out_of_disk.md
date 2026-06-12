---
title: "grub error: out of disk"
date: 2010-09-16
forum: General Help
---

### Post by utnubuuser on 2010-09-16
Hello

I've installed Ubuntu on a 4gig usb-flash drive, a kingston, and I'm only getting Grub Error: out of disk

I've searched the posts and I've found several posts regarding the error message, mostly they pertain to external usb-hdd.

I've gone through the Documentation and tried the solutions there, to no avail - Grub returns the same error: out of disk and no such file.

I've tried reinstalling grub2, again, same result.

I'm hoping someone has had the same/similar experience and found a solution/reason to the error message.

The flash drive shows that the root partition is 2/3 full, so it's not out of space,  
I noticed that the installer leaves a small unused area at the start of the disk - regardless of whether it's ext4 or ext3(which it is).

---

### Post by Rubi1200 on 2010-09-18
Not sure if this will help you, but take a look here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk)

---

### Post by briancfletcher on 2010-09-19
I spent a lot of time with this one.  My hard drive was bad.  Went to  System>Administration>Disk Utility, clicked on my hard drive icon  and SMART data showed that I had thousands of bad sectors on the disk.  I  plugged a new hard drive, installed Ubuntu 10.04.1 LTS and all is now  fine.  Then used the old disk as a slave drive and retrieved my old  files.  Hope this helps.  

I also posted this to [http://ubuntuforums.org/showthread.php?t=1511448](http://ubuntuforums.org/showthread.php?t=1511448).

---

### Post by utnubuuser on 2010-09-20
Thanks,

No solution yet...

---

