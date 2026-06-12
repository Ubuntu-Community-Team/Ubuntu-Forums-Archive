---
title: "Corrupt partition table?"
date: 2010-10-05
forum: General Help
---

### Post by Kahuin on 2010-10-05
*I did have another problem I believed to be related, but I no longer believe this to be the case. I have solved this problem on my own, but still have the following problem:*

What I believe has happened is that I've **corrupted the partition table.**
This is based on the thread @[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
output from
```
sudo fdisk -l
```is:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x068e068e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21006   168730656+   7  HPFS/NTFS
/dev/sda2           21007       24831    30723072    7  HPFS/NTFS
/dev/sda3           24832       29124    34483488   83  Linux
/dev/sda4           29125       30402    10265535    f  W95 Ext'd (LBA)
/dev/sda5           29125       29314     1526132   82  Linux swap / Solaris
/dev/sda6           29315       30401     8731327+   c  W95 FAT32 (LBA)

```where /dev/sda4 is 30402 cylinders and yet my disk only has 30401
sda1 is XP
sda2 is Win7
sda3 is Ubuntu
sda6 is HP WinXP recovery I think

When I try to look at SDA in **GParted** everything shows up as unallocated (though it's obviously not) and it says
```
Cannot have a partition outside the disk!
```under **Information**

There seemed to be a simple fix in the above thread but its doesn't appear to be something someone knowledgeable like me can just do. I am aware there may be more than one error here, but I figured I'd try let you know as much as I can surmise by myself. Any help would be appreciated :)


More information:
**sudo fdisk -lu**
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x068e068e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   337461375   168730656+   7  HPFS/NTFS
/dev/sda2       337463296   398909439    30723072    7  HPFS/NTFS
/dev/sda3       398910078   467877053    34483488   83  Linux
/dev/sda4       467877060   488408129    10265535    f  W95 Ext'd (LBA)
/dev/sda5       467877123   470929386     1526132   82  Linux swap / Solaris
/dev/sda6       470929410   488392064     8731327+   c  W95 FAT32 (LBA)
```**sudo sfdisk -d**
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=337461313, Id= 7, bootable
/dev/sda2 : start=337463296, size= 61446144, Id= 7
/dev/sda3 : start=398910078, size= 68966976, Id=83
/dev/sda4 : start=467877060, size= 20531070, Id= f
/dev/sda5 : start=467877123, size=  3052264, Id=82
/dev/sda6 : start=470929410, size= 17462655, Id= c
```[B]sudo parted /dev/sda print
[/B]```
Error: Cannot have a partition outside the disk! 
```

---

### Post by Kahuin on 2010-10-05
.

---

### Post by jerome1232 on 2010-10-05
testdisk is an excellent utility for repairing partition table issues.

---

### Post by Kahuin on 2010-10-05
> **jerome1232 said:**
> testdisk is an excellent utility for repairing partition table issues.

Tried that, had absolutely no effect, thanks for replying though :)
I have managed to fix Windows XP and GRUB but GPated still shows the disk as unallocated. Can anyone show me how to fix the sectors?

---

### Post by srs5694 on 2010-10-05
This thread seems to be a duplicate with [this one.](http://ubuntuforums.org/showthread.php?t=1588809) I've already replied there.

---

