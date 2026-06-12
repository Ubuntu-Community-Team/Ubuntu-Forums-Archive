---
title: "corrupt hard drive partition table"
date: 2011-08-20
forum: General Help
---

### Post by maxxum on 2011-08-20
I have a system with a 32gb SSD as boot and three 3TB HDDs (call them 3T-1, 3T2 and 3T-3). I swapped 3T-2 with a 500gb HDD temporarily. When I reconnect it, it does not mount. It tries to mount itself as 3T-1. In my computer I see 
3.0TB Hard Disk:3T-1
3.0TB Hard Disk:3T-1
3.0TB Hard Disk:3T-3

The file system on 3T-2 was ext4 (only one partition). When I do fdisk-l, I see that it cannot see partition table on either of the three drives. How can I mount 3T-2 or recover its data and copy it to 3T-3?
```
Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000caf59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2850    22886400   83  Linux
/dev/sdc2            2850        3893     8377345    5  Extended
/dev/sdc5            2850        3893     8377344   82  Linux swap / Solaris

Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
```

I determined by using mount command that sda and sdb are the 3T-1 and 3T-3 (which are mounted and working just fine, even though fdisk cannot find any partition table on them). So I manually tried to remount 3T-2:
```
:~$ sudo mount /dev/sdd /media/3T-2ext4
mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
So I check dmesg
```
[ 1213.266165] EXT4-fs (sdd): ext4_check_descriptors: Checksum for group 0 failed (11707!=18835)
[ 1213.266168] EXT4-fs (sdd): group descriptors corrupted!

```
Any way to fix this?

---

### Post by maxxum on 2011-08-20
Found a solution.
[http://ubuntuforums.org/showpost.php?p=9106100&postcount=4](http://ubuntuforums.org/showpost.php?p=9106100&postcount=4)
Consider this solved. Mods can delete this thread if they want.

---

