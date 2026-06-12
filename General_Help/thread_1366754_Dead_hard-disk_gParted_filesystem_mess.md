---
title: "Dead hard-disk: gParted filesystem mess"
date: 2009-12-28
forum: General Help
---

### Post by balta on 2009-12-28
Hi everybody!
I have an external hard disk that used to be partitioned in 2: one (smaller) part was FAT32 (labeled XT), the other NTFS.

I moved the contents of the FAT32 part into the NTFS one.

Using gparted under Ubuntu 9.04:
First I deleted the FAT32 partition (which was on the left).

Everything was fine: on the left some unallocated space on the right the big NTFS partition.

Then I started the moving\resizing of the NFTS one: I wanted it to take the entire hard disk so it had to be first moved to the left then grown.

Unfortunately during the "read-only" test (which is made after the selection of the optimal block size) my (idiot) little sister pushed "cancel"... :shock::shock:



The situation is now this:

gparted sees the hard disk is partitioned in 2:
The right part is unallocated and has the size that the unallocated (on the left) had before the beginning of the process.
The left size is the big one but it's FAT32, labeled XT and seems to be full of stuff (as full as it was before moving it) but when I try to browse it using nautilus I can only see one folder: the very same folder (which is way smaller than the size marked as used by gparted) that was in the initial FAT32 partition.



I run the command from terminal:
```
sudo fdisk -l && blkid
```
and the output was:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c4b3c4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19221   154390288+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           19222       19246      200812+  82  Linux swap / Solaris
/dev/sda3           19247       24321    40764937+  83  Linux



Disk /dev/sdf: 750.1 GB, 750156373504 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042c0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf2               1       65706   527775412+   7  HPFS/NTFS
/dev/sda1: UUID="8CACB0C9ACB0AED8" TYPE="ntfs" 
/dev/sda2: UUID="81acf489-7714-471b-a704-aca71df1d933" TYPE="swap" 
/dev/sda3: UUID="ecae136f-26cf-4f26-b46b-af4d50796a2a" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"
```

(personally I believe only the second half matters but for completeness's sake I posted both)



Moreover I read the article [*_Data Recovery: Community Ubuntu Documentation_*]("https://help.ubuntu.com/community/DataRecovery") but I'm not sure if I must follow advices from the **Lost Partition** section or from the ***Data Recovery from damaged filesystem or drive*** one...  
...and if the right one is *Lost Partition*, which of the 3 presented tools you advice me to use?

Are they equivalent?


Please, any help or hint on how to proceed is greatly appreciated!
At least tell me which of the two situations I am in...
thanks!

---

### Post by balta on 2010-03-11
[http://ubuntuforums.org/showthread.php?t=1358317](http://ubuntuforums.org/showthread.php?t=1358317)

---

