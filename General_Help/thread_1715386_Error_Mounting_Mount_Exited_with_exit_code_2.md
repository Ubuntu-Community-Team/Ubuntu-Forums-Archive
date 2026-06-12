---
title: "Error Mounting: Mount Exited with exit code 2"
date: 2011-03-26
forum: General Help
---

### Post by ic3coldh20 on 2011-03-26
My computer has been acting quite strange lately. It's been taking longer to boot, and my sound doesn't play anymore (Only a high pitched sound is heard, and no hardware for sound is detected). Just recently, my Windows 7 Partition returned the error of Disk Error Occured. Press CTRL+ALT+DEL to restart. 

Any way I can fix my whole issue, I think my desktop is starting to die on me :O (And its only about 7 months old T_T)

Please help!

---

### Post by NuMPTy_87 on 2011-03-26
Well, for starters make sure you have backups of everything :)

Check the disk with fsck:
```
fsck -fy /dev/sdx
```

(where sdx = your appropriate drive)

!Make sure you unmount it first!

Cheers,

---

### Post by ic3coldh20 on 2011-03-26
> **NuMPTy_87 said:**
> Well, for starters make sure you have backups of everything :)

Check the disk with fsck:
```
fsck -fy /dev/sdx
```(where sdx = your appropriate drive)

!Make sure you unmount it first!

Cheers,

Edit: This might be what you needed?

```
$ sudo fsck -fy /dev/sda2
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

```

Returns with ```
$ fsck -fy /dev/sd2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: No such file or directory while trying to open /dev/sd2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```Though I've seen posts requesting people post the result of sudo fdisk -l  so here is the result of that input 

```
$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8393931    b  W95 FAT32
/dev/sda2            1046       97183   772223755    7  HPFS/NTFS
/dev/sda3           97183      121602   196144129    5  Extended
/dev/sda5           97183      120606   188148736   83  Linux
/dev/sda6          120606      121602     7994368   82  Linux swap / Solaris


```

---

### Post by ic3coldh20 on 2011-03-27
After clearing some dust from the inside of my pc, I'm not unable to boot past bios! :(

The screen goes and blank after the Bios screen, and just reboots. It's and infinite loop :O

I need desperate help! Please! I'm afraid if I take it to my local best buy my data will be missing when my computer gets back to me...and I don't want that! 

Thanks!

---

### Post by ic3coldh20 on 2011-03-28
Well, my hard drive is dead. Can anyone recommend any bootable data recovery software i can use?

---

