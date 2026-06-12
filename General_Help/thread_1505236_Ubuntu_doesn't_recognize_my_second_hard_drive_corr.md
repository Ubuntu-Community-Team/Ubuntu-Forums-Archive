---
title: "Ubuntu doesn't recognize my second hard drive correctly"
date: 2010-06-08
forum: General Help
---

### Post by zglynn on 2010-06-08
I had windows 7 installed on my machine and decided to go with a ubuntu win7 dual boot.  The install went fine, but Ubuntu doesn't see my second HDD as anything but empty.  My second HDD I set up in win7. It is actually two 320GB HDD striped together. It is holding alot of data that I would like to be able to access from both win7 and ubuntu. 

When i run fdisk -l in the terminal i get:

[COLOR=DarkGreen][COLOR=DarkRed]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1c572ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7901    63458787    7  HPFS/NTFS
/dev/sda2            7901        9730    14691329    5  Extended
/dev/sda5            7901        9647    14026752   83  Linux
/dev/sda6            9647        9730      663552   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e78d528

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312570168+  42  SFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d2b7d34

[COLOR=Black]So Ubuntu sees the two HDD, just not as one with all my data on it like I see it in windows.
Is there a way to set it up so I can use that second HDD (the two stripped) in both win7 and Ubuntu?

Thanks 

Zach
[/COLOR][/COLOR][/COLOR]

---

### Post by quixote on 2010-06-10
Since your two 320gb drives were set up using win7, they're probably hpfs/ntfs filesystem, just like the sda1 win7 partition.  Linux should have no trouble seeing those, but fdisk is reporting them as unformatted, which is bizarre.

Have you tried looking at them with gparted, just to see what it reports?

I take it that win7 has no trouble seeing those drives, right?  Have you shared the drive in windows?  Maybe that's necessary in win7.  (I have no idea.  Just guessing.)

---

### Post by bab1 on 2010-06-10
>  My second HDD I set up in win7. It is actually two 320GB HDD striped together.

This was done using Win7.  It is essentially a software only (and proprietary to Microsoft) RAID setup.  Ubuntu has no way of reconstituting the volume that you have made.  So it only sees the physical devices with unknown formating.

> Is there a way to set it up so I can use that second HDD (the two stripped) in both win7 and Ubuntu?


Not that I know of.  Certainly not with the native Linux tools.

---

