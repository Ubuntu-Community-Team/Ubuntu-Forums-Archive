---
title: "repartitioning woes!"
date: 2010-01-01
forum: General Help
---

### Post by ngourley on 2010-01-01
Hello all! this is my first post and I'm hoping i can get some useful advice.

I have a dual boot Ubuntu/XP machine with XP on a 750 gig hd and Ubuntu on a 500 gig drive.  I was re-partitioning and reformatting my external usb drive, but it Gparted defaulted to the XP drive and so I've deleted its partition, and reformatted it to FAT32.

Is there any way to recover the XP drive??  I've seen a few windows based programs but was hoping i could do it from within Ubuntu.  I now have no XP :(

Any help is greatly appreciated.

Neil.

---

### Post by Bradj47 on 2010-01-01
No, if you reformatted it it should be gone unless you didn't click the **Apply** button yet. If you didn't click the **Apply** button it's just giving you a preview of what would happen if you *did* click the **Apply** button. But if you really did reformat it, it's gone forever.

---

### Post by ajgreeny on 2010-01-01
Not necessarily.  If you have a look at [testdisk]("http://www.softpedia.com/get/System/Hard-Disk-Utils/TestDisk.shtml") you may be lucky.

---

### Post by Leppie on 2010-01-01
> **ajgreeny said:**
> Not necessarily.  If you have a look at [testdisk]("http://www.softpedia.com/get/System/Hard-Disk-Utils/TestDisk.shtml") you may be lucky.

so can it actually recover a partition after formatting it to another filesystem type? i know it can recover files, accessing the disk at low level.

---

