---
title: "Swap partition showing as unknown"
date: 2011-08-30
forum: General Help
---

### Post by jasef on 2011-08-30
Hey,

I just reinstalled Ubuntu 11.04 on my netbook, and I've  noticed that my swap partition is now showing as "unknown" in GParted (I  recreated the partitions completely when I reinstalled, so it's not an  old swap partition), I don't remember it showing as unknown before  reinstalling, but I'm not completely sure.

When I execute 'free'  on the terminal, it shows the swap space as available (output pasted  below if it matters), and swapon -a and swapoff -a execute fine with no  errors, so I assume that there's no actual problem with the swap, but  rather the problem is with GParted, so it's not a big issue, but I'd  like to understand why this is happening and possibly fix it.

```

jason@dionysus:~$ free
             total       used       free     shared    buffers     cached
Mem:       2050904     910048    1140856          0      84032     545424
-/+ buffers/cache:     280592    1770312
Swap:      2096124          0    2096124

```

---

### Post by searchfgold6789 on 2011-08-30
[LIST]
[*]See if GParted will make you a swap partition.
[*]If it will, try recreating the one you have.
[*]Try right-clicking on the partition and select "properties", see if it says anything useful.
[*]Make sure you are fully updated.
[/LIST]

---

### Post by scott_g on 2011-08-30
> **searchfgold6789 said:**
> [LIST]
[*]See if GParted will make you a swap partition.
[*]If it will, try recreating the one you have.
[*]Try right-clicking on the partition and select "properties", see if it says anything useful.
[*]Make sure you are fully updated.
[/LIST]

Could also try a ```
sudo fdisk -l
``` to make sure there's nothing actually wrong with the swap partition, and that it's just gparted?

Just a thought.

---

### Post by jasef on 2011-08-30
I'm fully updated (first thing I did when I installed was updated all packages). Can't test if it can make a swap partition on sda because all my space is allocated. I tried deleting and recreating the one I've got but I can't delete it because it's sda6 and it wants me to unmount sda7 (/) and sda8 (/home) first.

I'll recreate my startup disk on my SD card when I get home and test from that.

Running sudo fdisk -l produces the following output (I cut off a bunch of output at the end which is for other drives) which looks fine to me, but posting just in case: 
```

jason@dionysus:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfebe0e78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sda2           13055       15013    15728640   1b  Hidden W95 FAT32
/dev/sda3           15013       30400   123591681    5  Extended
/dev/sda4           30400       30402       16384   ef  EFI (FAT-12/16/32)
/dev/sda5           17752       30400   101593088    7  HPFS/NTFS
/dev/sda6           17491       17752     2096128   82  Linux swap / Solaris
/dev/sda7           15013       16319    10485760   83  Linux
/dev/sda8           16319       17491     9413632   83  Linux

Partition table entries are not in disk order

```

---

