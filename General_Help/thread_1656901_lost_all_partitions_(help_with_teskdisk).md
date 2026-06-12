---
title: "lost all partitions (help with teskdisk)"
date: 2010-12-31
forum: General Help
---

### Post by dejaaan on 2010-12-31
when i try to boot the system i get something like grub resque.

now i'm running TeskDisk under the ubuntu live cd, and with quick search it finds my partitions:

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 12015 254 55  193036969
P Linux                12016   0  1 12907 254 59   14329976
P Linux Swap           12908   0  1 13409 254 41    8064608
L HPFS - NTFS          13411  62 28 38913  37 36  409688064

```but when i choose P to list files it quits with this:

```
Aborted (core dumped)
ubuntu@ubuntu:~/Desktop/testdisk-6.11.3$ 
```

when i type sudo -fdisk -l i get:

```

ubuntu@ubuntu:~/Desktop/testdisk-6.11.3$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c96be80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       13412       38914   204844032    7  HPFS/NTFS

```

previously there were more items in the list..

how can i get my partitions back? i've got very important files here...

---

### Post by nitro_n2o on 2010-12-31
try the grub rescue [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) it will not delete your files

---

