---
title: "After a clean re-install I suddenly can not mount my other volumes"
date: 2011-04-24
forum: General Help
---

### Post by amaruq_atka on 2011-04-24
I have absolutely positively no clue why not. They don't show up under "Places". Judging by the stuff I have found searching you probably want my fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
```

Also, the error I get when trying to mount in the disk utility:

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, none is already mounted on none
mount failed
```

I have not a clue what any of this means. I am trying to figure it out but finding dead ends. Any and all help is much appreciated!


EDIT: I got it working. I just reinstalled it again. Same liveCD, same everything. Have no idea why but it works now. :)

---

### Post by WorMzy on 2011-04-24
What does

```
sudo fdisk -l
```
(that's a lowercase L btw)
and
```
sudo blkid -c /dev/null
```

say?

---

### Post by amaruq_atka on 2011-04-24
the first one gives me

```
Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23424   188153248+   7  HPFS/NTFS
/dev/sda2           23425       36480   104872320    f  W95 Ext'd (LBA)
/dev/sda5           23425       36480   104872288+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f58a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        9605        9730     1000448   82  Linux swap / Solaris
/dev/sdb2               1        9605    77149185    5  Extended
/dev/sdb5               1        9605    77149184   83  Linux

Partition table entries are not in disk order

Disk /dev/sdg: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

```


and the second one

```
/dev/sda1: UUID="F838D9E038D99E46" TYPE="ntfs" 
/dev/sda5: UUID="4AC41F25C41F1335" TYPE="ntfs" 
/dev/sdb1: UUID="1737c012-d2d8-4440-834e-88b292401187" TYPE="swap" 
/dev/sdb5: UUID="b87d93d5-0478-46a2-a1ed-8e576f14c6a7" TYPE="ext4" 
/dev/sdg: LABEL="New Volume" UUID="0058-C375" TYPE="vfat" 
```

---

### Post by WorMzy on 2011-04-24
Well, it looks like all you partitions are fine, but there may be a problem with your 4GB removable media (unless you missed a bit of the output of fdisk -l)

Can you mount partitions manually via command line?

```
sudo mount -t ntfs-3g /dev/sda1 /mnt
```

---

### Post by amaruq_atka on 2011-04-24
no no, the flash drive works seamlessly, in and out and no difference. I tried the command, it returned nothing. Going into disk utility it says its mounted at /mnt, which when clicked brings me to the drive. But the second partition. I need that one too, I always used to have it say 193gb file system, and 107gb file system. Now I can get to the 107 but only though clicking /mnt in the disk utility. I must be doing something wrong.

---

