---
title: "system daznt recognize allocated space"
date: 2011-05-28
forum: General Help
---

### Post by aninona on 2011-05-28
I've just allocated some 50 GIB to HD[live cd gparted], rebooted and the system does not recognize it [the livecd does recognize]


what should I do??

---

### Post by sikander3786 on 2011-05-28
From the Live environment, please go to Applications > Accessories > Terminal (or if using Unity, press <Super> (Windows logo key) and type 'Terminal') and post the output of this command:

```
sudo fdisk -lu
```

Or also, a screenshot of GParted.

---

### Post by aninona on 2011-05-28
Thanks!\

here it is
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d8562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   606999959   303499948+  83  Linux
/dev/sda2       606999960   625137344     9068692+   5  Extended
/dev/sda5       607000023   625137344     9068661   82  Linux swap / Solaris
```

---

### Post by sikander3786 on 2011-05-28
The 50 GB partition isn't there I think. Can you post a screenshot of GParted?

---

### Post by aninona on 2011-05-28
> **sikander3786 said:**
> The 50 GB partition isn't there I think. Can you post a screenshot of GParted?

Hey thanks and sorry about the delay
Ive ALREADY allocated the 50 gbs it was 240 before
[IMG]http://img717.imageshack.us/img717/2312/screenshotdevsdagparted.png[/IMG]

:P:KS

---

### Post by aninona on 2011-05-28
bumpin:KS:KS:KS

---

### Post by sikander3786 on 2011-05-28
It might sound dumb but how was the new partition created? Did you click the 'Apply' button afterwards?

According to the calculations, you are not missing 50 GB of space at all. All the usable space is there in the present partitions.

Can you post the output of GParted from the Live CD as well where you say that it can recognize that partition?

---

