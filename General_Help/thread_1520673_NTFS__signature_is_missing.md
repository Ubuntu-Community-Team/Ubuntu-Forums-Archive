---
title: "NTFS  signature is missing"
date: 2010-06-29
forum: General Help
---

### Post by jfluckey on 2010-06-29
I have searched many forums with no luck in find how to mount my external hard drive.  The output of ```
fdisk -l
``` was pretty lengthy but I am including all output anyway. The device I am trying to mount is the 1 TB drive /dev/sde.  After running fdisk, I ran ```
sudo mount -t ntfs-3g /dev/sde /media/myHD
``` and the output can be seen after the fdisk output (and yes I tried sde1 in lieu of sde).  Thanks for any help.


> jfluckey@jfluckey-desktop:~$ sudo fdisk -l
[sudo] password for jfluckey: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x767f767f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15383   123562923+   7  HPFS/NTFS
/dev/sda2           15384       30402   120634369    5  Extended
/dev/sda5           15384       29851   116210688   83  Linux
/dev/sda6           29851       30402     4422656   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
256 heads, 63 sectors/track, 30282 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19ff1bd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc93e1af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdd: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         123      987104    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x601d5817

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001    7  HPFS/NTFS> jfluckey@jfluckey-desktop:~$ sudo mount -t ntfs-3g /dev/sde /media/myHD
NTFS signature is missing.
Failed to mount '/dev/sde': Invalid argument
The device '/dev/sde' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by mikewhatever on 2010-06-30
That error message was wonderfully informative. sde is a device, sde1 is the partition you want to mount. The command should look as follows:
```
sudo mount -t ntfs-3g /dev/sde1 /media/myHD
```

---

### Post by jfluckey on 2010-07-01
> **mikewhatever said:**
> That error message was wonderfully informative. sde is a device, sde1 is the partition you want to mount. The command should look as follows:
```
sudo mount -t ntfs-3g /dev/sde1 /media/myHD
```
I tried that too, but didn't post the output the first post, so here it  is:

> jfluckey@jfluckey-desktop:~$ sudo mount -t ntfs-3g /dev/sde1  /media/myHD
[sudo] password for jfluckey: 
NTFS signature is missing.
Failed to mount '/dev/sde1': Invalid argument
The device '/dev/sde1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way  around?

---

