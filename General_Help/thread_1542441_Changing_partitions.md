---
title: "Changing partitions"
date: 2010-07-30
forum: General Help
---

### Post by LeifAndersen on 2010-07-30
So, when I first got my laptop, I up and installed ubuntu on it (after making sure it worked properly anyway).  At the time I didn't think I would need windows much, So I gave it ~10 GB of hardrive space (on top of what windows 'needed') thinking that that was plenty.  Well...now my latest CS course is using C#, and I *need* (according to them anyway, I suppose I could try monodevelop) to install visual studio.  The problem is that I don't have the needed space on my partition Oo.  And even worse, I can't seem to resize my partitions (because there was more than 4, ubuntu's installer automatically split it up into several extended partitions (or logical partitions?).  Anyway, while I can resize partitions on each of the 4 main partitions, I can't actually change the sizeof one of the main partitions (I'm using gparted on the ubuntu live cd).

So, is there any way I can resize my main partitions, so that I can increase the size of the windows partition on my machine to make room for required bloatware for my next CS course?

Thank you.

---

### Post by Rubi1200 on 2010-07-30
Hi,
to give us a better view of what your setup looks like please post a screenshot of your partitions as seen by GParted (Applications > Accessories for the screenshot tool). Also, post the output of ```
sudo fdisk -l
``` please.

---

### Post by LeifAndersen on 2010-07-30
Here you go:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24a40e43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1145     9191424   27  Unknown
/dev/sda2   *        1145        1158      102400    7  HPFS/NTFS
/dev/sda3            1158        6165    40222085+   7  HPFS/NTFS
/dev/sda4            6165       38914   263052289    5  Extended
/dev/sda5            6165       16155    80246445+  83  Linux
/dev/sda6           37582       38914    10698752   82  Linux swap / Solaris
/dev/sda7           16156       37581   172104313+  83  Linux

Partition table entries are not in disk order

```

Thank you.

---

### Post by LeifAndersen on 2010-08-01
No suggestions whatsoever?  :(  Rats...I suppose I 'could' just wipe the hardrive and start over again...

---

