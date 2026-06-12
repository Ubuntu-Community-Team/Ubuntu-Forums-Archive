---
title: "GParted error: ext3 filesystem indicated as swap"
date: 2010-07-02
forum: General Help
---

### Post by krispisvis on 2010-07-02
Hi there,

I just got a new hard disk so that my "/" and "/home" partitions would be located at their own separate drives. All was well until i tried to expand my "/home" partition to fill up the entire drive that used to also have the "/" and swap partitions on there. Let me sketch the before-and-after scenario in GParted,



*before*:
[FONT=Courier New]| -- swap -- | --- "/" --- | -------------- "/home" -------------- |[/FONT]


desired *after*:
[FONT=Courier New]| --------------------------- "/home" ---------------------------- |
[/FONT]

what actually happened *after*:
 [FONT=Courier New]| --------------- swap --------------- | ------ unallocated ------ |[/FONT]



Gparted gave an error prompt after which i found out that the entire  ext3 partition (/home) had been moved to the left but not yet expanded  to the right, which is of course not a problem. However, for some reason  it has labelled the entire ext3 partition as a swap partition! 

I'm still running ubuntu from the usb flash drive, because i dont want to risk that the (120GB) swap area will actually be used and cause my data to be lost.

I guess my question is, can i relabel the swap partition as ext3 like it was before without formatting (ie without losing data)?


Thanks a lot!
kris


P.S. here's the output of "fdisk -l", which doesn't show the swap area (the drive in question is "/dev/sdb"):
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f366

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         498     3998720   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         498        3893    27266048   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf308f308

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         732     5879758+   0  Empty
/dev/sdb4               1       16572   133106557+  83  Linux

Disk /dev/sdc: 3963 MB, 3963617280 bytes
122 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7564 * 512 = 3872768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f3d03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1023     3868955    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1023, 121, 62) logical=(1022, 121, 62)

```

---

### Post by krispisvis on 2010-07-02
I'm sorry for posting such an elaborate post before finding out about testdisk data recovery tool,
```
sudo testdisk
```
which is in ubuntu's universe repository. Worked like a charm, what a relieve!

---

### Post by dino99 on 2010-07-02
i use partedmagic (boot with) to resize or create partition(s)
Better to apply modification(s) one by one

Renaming swap cant be done without reformating (swap is not ext*)

---

