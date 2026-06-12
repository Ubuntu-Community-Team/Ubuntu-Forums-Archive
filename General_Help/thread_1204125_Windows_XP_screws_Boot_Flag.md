---
title: "Windows XP screws Boot Flag"
date: 2009-07-04
forum: General Help
---

### Post by salvachn on 2009-07-04
I've installed Windows Xp and Jaunty on a disk and fedora on another. I installed jaunty last, and it booted fine into all systems. But if I log into XP and then restart, the boot flag in jaunty's partition is gone. Any remedies for this?

---

### Post by ajgreeny on 2009-07-04
Linux does not need a boot flag, unlike windows which must have its partition with a boot flag.

What exactly is the problem?  If you can't boot jaunty after using windows there is something else wrong, not just a boot flag problem

---

### Post by salvachn on 2009-07-05
My partition layout is:

On 250GB HDD:
60GB Data
30GB XP
30GB Jaunty
110GB Backup

On 40GB: 
30GB Leonidas
10GB Data

When I switch on my PC I get into XP instead of grub.

---

### Post by lisati on 2009-07-05
Have a look here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by salvachn on 2009-07-05
> **lisati said:**
> Have a look here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks, that worked but not before from some more tweaking. I installed grub to the 250 gig disk's mbr, and it wouldn't boot into xp and fedora. But I installed it to the 40 gig's mbr and everything works fine now!

---

