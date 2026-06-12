---
title: "partitioned drive (or not??)"
date: 2012-08-26
forum: General Help
---

### Post by londoncall on 2012-08-26
Just installed Lubuntu (fab - love it) over my Windows XP instalation  - I had a C and a D drive - Windows was on the C.  Now I can't see the D drive and neither can NTFS config tool. Has it been erased.  This is what terminal says but  (gotta be honest here) I'm one small step away from being a newbie - so a bit lost.

Here's the read out from terminal


Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       148G  4.9G  136G   4% /
udev            490M   12K  490M   1% /dev
tmpfs           199M  792K  198M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            497M  136K  497M   1% /run/shm


Disk /dev/sda: 160.0 GB, 160041885696 bytes
heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009bfb1

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   310503423   155250688   83  Linux
/dev/sda2       310505470   312580095     1037313    5  Extended
/dev/sda5       310505472   312580095     1037312   82  Linux swap / Solaris

Would love to know if sda2 is it and how I access it.. (but what does it all mean - do I still have the partition -  can anyone help???

---

### Post by ajgreeny on 2012-08-26
The big problem is that Ubuntu does not use the letters C and D as drive demarcation. It uses the sda1, sda2, etc etc that you see in the fdisk output that you are showing here.

I assume the D drive was formatted to ntfs in the past, and if that is so, unfortunately it is no longer available, but was formatted over when you installed Lubuntu.  If you had important files on that partition you may be able to get something back with testdisk, but I have never had to use it so can do nothing except point you in its direction.

It seems that you probably let Lubuntu install to the whole disk and that gave you a root partition, ie the whole OS, which looks to be around 155GB in size, and an extended partition which contains the logical swap partition of about 1GB.  All your old files will be gone, I'm afraid.

---

### Post by londoncall on 2012-08-26
> **ajgreeny said:**
> 

It seems that you probably let Lubuntu install to the whole disk and that gave you a root partition, ie the whole OS, which looks to be around 155GB in size, and an extended partition which contains the logical swap partition of about 1GB.  All your old files will be gone, I'm afraid.

Hi, thanks for the reply... appreciated.  However I'm sure my drive is 300gig and it seems sda 3 & 4 (if they exist) aren't mentioned in the terminal report.  I remember under windows C and D were around  equal sizes of 160 gig's each.

---

### Post by londoncall on 2012-08-26
...and that's where Windoze caught me out.  It did show 160 on C and 160 on D... but it shouldn't have!  It was 160 for BOTH.  So whilst I thought I was being short changed in Linux I actually only have 160 :) No harm done. Apart from a little embarrassment

---

