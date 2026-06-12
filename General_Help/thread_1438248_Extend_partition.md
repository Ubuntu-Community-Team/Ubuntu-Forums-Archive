---
title: "Extend partition"
date: 2010-03-24
forum: General Help
---

### Post by jochem on 2010-03-24
[http://z1.zod.fr/z/screenshot-TW0.png](http://z1.zod.fr/z/screenshot-TW0.png)

I've got 13gb of unused space (unallocated), still I can't extend my linux or windows partition. How do I achieve my goal? I tried gparted too...

Thanks in advance

---

### Post by Serpher on 2010-03-24
I would also like to know how to do this. I'm also out of primary partitions and have no room in my extended cause I kinda messed things up.

---

### Post by mechro on 2010-03-24
> **jochem said:**
> [http://z1.zod.fr/z/screenshot-TW0.png](http://z1.zod.fr/z/screenshot-TW0.png)

I've got 13gb of unused space (unallocated), still I can't extend my linux or windows partition. How do I achieve my goal? I tried gparted too...

Thanks in advance

Not enough information. Either post a Gparted screenshot or do **sudo fdisk -l** in aTerminal and post the results here.

---

### Post by jochem on 2010-03-24
```
jochem@jochem-laptop:~$ sudo fdisk -l
[sudo] password for jochem: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdcc33cae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1580       17175   125269840    7  HPFS/NTFS
/dev/sda2           17176       19457    18330165   83  Linux

```

[http://z1.zod.fr/z/screenshot-1-UW0.png](http://z1.zod.fr/z/screenshot-1-UW0.png)

---

### Post by garvinrick4 on 2010-03-24
> **jochem said:**
> [http://z1.zod.fr/z/screenshot-TW0.png](http://z1.zod.fr/z/screenshot-TW0.png)

I've got 13gb of unused space (unallocated), still I can't extend my linux or windows partition. How do I achieve my goal? I tried gparted too...

Thanks in advance
  gparted does it. Unallocated space should be formatted to use. If coming from Windows defrag at least 2 times that is your windows install. Then resize. Stay with gparted it is good solid software. If confused a bit just Google, Google and Google till you understand. 
Lots of good articles on resizing partitions.

---

### Post by mechro on 2010-03-24
That looks OK.

Are you using Gparted from a LiveCD?

If you're running Gparted from a Ubuntu installation in sda2 you won't be able to manipulate sda2. You could manipulate sda1 but you need to unmount it before running Gparted.

---

### Post by jochem on 2010-03-24
> **mechro said:**
> That looks OK.

Are you using Gparted from a LiveCD?

No, should I? Because I can't resize my linux partition while mounted?

> **garvinrick4 said:**
> gparted does it. Unallocated space should be formatted to use. If coming from Windows defrag at least 2 times that is your windows install. Then resize. Stay with gparted it is good solid software. If confused a bit just Google, Google and Google till you understand. 
Lots of good articles on resizing partitions.

Formatted to use? Like formatted to ext4? I'll read a few articles tomorrow, thanks

Thanks everyone

---

### Post by drs305 on 2010-03-24
Here is a guide on expanding an Ubuntu system partition. Start with the "basic rules" section about half way down.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

The important things to do are backup important data, defrag Windows, and for gparted operations do it from the LiveCD, with the partitions (including swap) unmounted. The guide will provide more information and techniques.

---

### Post by mechro on 2010-03-24
> **jochem said:**
> No, should I? Because I can't resize my linux partition while mounted?



Formatted to use? Like formatted to ext4? I'll read a few articles tomorrow, thanks

Thanks averyone

If you're running Gparted from a Ubuntu installation in sda2 you won't be able to manipulate sda2. You could manipulate sda1 but you need to unmount it before running Gparted.

edit... + what drs305 says.

---

### Post by Mark Phelps on 2010-03-25
If you're running Vista or Win7, do NOT use GParted (LiveCD or otherwise) to resize that.  Doing that runs the risk of corrupting the Vista/Win7 OS and rendering it unbootable.  Use the Vista/Win7 Disk Management utility instead.

---

