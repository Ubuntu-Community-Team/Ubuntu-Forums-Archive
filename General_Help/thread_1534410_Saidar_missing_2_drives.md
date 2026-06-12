---
title: "Saidar missing 2 drives"
date: 2010-07-19
forum: General Help
---

### Post by dbrine on 2010-07-19
I'm using Ubuntu and when in run saidar it only shows 3 mounted drives and 2 are missing. I am access them locally and through network. I also check the fstab and everything looks ok

any ideas?


thanks.

---

### Post by rubylaser on 2010-07-19
If you open a terminal what is the output of
```
fdisk -l
```

---

### Post by dbrine on 2010-07-19
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeda3bc4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6665c95f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028bd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
64 heads, 32 sectors/track, 953869 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46321f00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      953869   976761840   83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
64 heads, 32 sectors/track, 953869 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ba2995e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      953869   976761840   83  Linux


I'm not seeing the 2 2TB HDD in SAIDAR

---

### Post by rubylaser on 2010-07-19
I'm not sure what you mean.  Are they just not mounted?  The two disks are showing up in your fdisk -l

```
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6665c95f

Device Boot Start End Blocks Id System
/dev/sdb1 1 243201 1953512001 83 Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028bd6

Device Boot Start End Blocks Id System
/dev/sdc1 1 243201 1953512001 83 Linux
```

What does your /etc/fstab look like?

---

### Post by dbrine on 2010-07-19
Everything is mounted fine but when I run saidar it doesn't show the 2, 2TB drives. I will post the fstab in a bit

---

### Post by Sebastian Danielache on 2010-07-19
What do I do when I know that there is a disk operating in my system (I can see it from BIOS) and does not show up with the fdisk -l command? 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92446a79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29273   235135341   83  Linux
/dev/sda2           29274       30515     9976365    5  Extended
/dev/sda5           29274       30515     9976333+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe375ef6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    c  W95 FAT32 (LBA)

 Thanks for any advice

---

### Post by rubylaser on 2010-07-19
What you would normally do is start a new thread, because this is not the same problem as the original poster.  But to answer your question, I'd need to know a lot more info.  What type of drive is it (IDE, SATA2, SATA3), how is it connected to the motherboard (onboard head, PCI / X / Express Card, etc).  I would guess it's unsupported hardware, but without more info, I'm not sure.

---

### Post by dbrine on 2010-07-20
any ideas to fix the saidar reporting?

---

