---
title: "fdisk and second hard drive?"
date: 2009-10-07
forum: General Help
---

### Post by MonsterDuc on 2009-10-07
Hey, I have gotten my hands on an older PC that I installed ubuntu on.  I haven't opened it yet so not sure what is inside it.

I ran fdisk and it looks to me like there are two hard disks available:

```
$ sudo fdisk -l
]
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a412729

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19744   158593648+  83  Linux
/dev/sda2           19745       19929     1486012+   5  Extended
/dev/sda5           19745       19929     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d10349b

Disk /dev/sdb doesn't contain a valid partition table
```

It also looks like the second hard disk would be available for me to format without messing up the current installation.  If so, would fdisk be the best tool for that, and how would it be done (I know there are man pages but would prefer some advise here as I am worried about messing up the current installation).

Help appreciated.

---

### Post by StuartN on 2009-10-07
> **MonsterDuc said:**
> would fdisk be the best tool for that

Install Gparted if it is not already installed, then System->Administration->Partition editor.

Install, for instance, ntfstools as well to add NTFS formatting / checking / labelling to Gparted's functions. FAT is part of Gparted's base functionality.

---

### Post by MonsterDuc on 2009-10-10
Thanks for the suggestion!  Gparted did what I needed!

---

