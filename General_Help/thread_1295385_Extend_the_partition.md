---
title: "Extend the partition"
date: 2009-10-19
forum: General Help
---

### Post by vvfrn on 2009-10-19
Can anyone explain in begginner talk how to extendmy partition from 5gbs to like probaly 16 gbs
here are the stats
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            3931        4865     7510387+   5  Extended
/dev/sda5            4729        4729        8032+  82  Linux swap / Solaris
/dev/sda6            3931        4687     6080539+  83  Linux
/dev/sda7            4688        4728      329301   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by louieb on 2009-10-19
I would say Gparted using it is pretty unintuitive.  seems you have free space at the start and end of the disk. The only thing that might confuse you trying to use space at the front - you will have to grow sda2 1st then you can grow sda6 to use that space.
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 
[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018") 
 
and last you will have to run Gparted from a live CD. Even though its on the Ubuntu Live CD - I recommend you  get a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") 

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, [COLOR=DarkOrchid]4865[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

/dev/sda2            3931        4865     7510387+   5  Extended
/dev/sda6            3931        4687     6080539+  83  Linux
/dev/sda7            4688        4728      329301   82  Linux swap / Solaris
/dev/sda5            4729        [COLOR=DarkOrchid]4729 [/COLOR]       8032+  82  Linux swap / Solaris
 

```

---

