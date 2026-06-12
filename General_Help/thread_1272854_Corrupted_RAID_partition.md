---
title: "Corrupted RAID partition"
date: 2009-09-22
forum: General Help
---

### Post by devguy on 2009-09-22
Hey guys.  So my machine has a RAID setup with 2 500GB hdds.  It is categorized into two arrays, a RAID 0 array of size ~150GB, and a RAID 1 array of size ~425GB.  I have on the RAID 0 array, 3 partitions: a boot partition of ~100MB that has my grub files, a partition of ~100GB housing my Windows 7 install, and a partition of ~50GB housing my Ubuntu install.

Today, booting into my Windows 7 install, I got a "memory management" BSOD (never mind the causes for it) and now, whenever I boot up my machine, it does everything normally through to the RAID initializer.  In fact, it says that both of my raid arrays are fine.  However after that, my machine just hangs, with a little blinking dash in the upper left corner (you've all seen that), where it used to load grub.

I tried using the Windows 7 install dvd to go to the recovery console.  I loaded my raid drivers, but it found no windows 7 installation.  Then, I booted up this ubuntu 9.04 live cd and installed dmraid.  Here are my results from "sudo dmraid -ay":

```
RAID set "pdc_chgeaeibgf" already active
RAID set "pdc_echafijeii" already active
ERROR: dos: partition address past end of RAID device
RAID set "pdc_chgeaeibgf1" already active
RAID set "pdc_chgeaeibgf2" already active
RAID set "pdc_echafijeii1" already active

```

The pdc_ech... array is the raid 1 one, and I successfully mounted it with the live cd to a directory.  But, the other array won't.  In fact, it only lists two partitions (1,2), but there should be 3.  The same thing shows with GParted and I see two partitions (one 100mb and one 100GB), but there is no 50GB partition in there.  My guess is that the error is what is killing it.  Anyone know how to repair this?  I have all my important stuff backed on the RAID 1 array, but I'd prefer not to have to deal with reinstalling OS's.

---

### Post by devguy on 2009-09-22
Bump

---

### Post by Lepy on 2009-09-24
I can't really offer any help, as I am having a similar issue, except dmraid won't even mount my RAID 1 at all. 
Windows XP and 7 have no problem mounting the RAID, but I would really like to use it in Ubuntu.

I get the same "ERROR: dos: partition address past end of RAID device" which seems to be caused by improper cylinder calculation.

[http://ubuntuforums.org/showthread.php?t=1269291](http://ubuntuforums.org/showthread.php?t=1269291)

---

