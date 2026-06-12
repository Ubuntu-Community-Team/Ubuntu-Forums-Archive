---
title: "Ubuntu 11.04 Automount problems (fstab)"
date: 2011-07-01
forum: General Help
---

### Post by HNIH on 2011-07-01
Hey all.

I've a clean installation of Ubuntu 11.04 (AMD64) and i'm having problems with automount ntfs partitions/disks.

fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad59f04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38bb0b6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000990bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14341   115189760   83  Linux
/dev/sdc2           14341       14594     2028545    5  Extended
/dev/sdc5           14341       14594     2028544   82  Linux swap / Solaris

blkid:

/dev/sda1: LABEL="ShareII" UUID="921A19ED1A19CF5B" TYPE="ntfs"
/dev/sdb1: LABEL="ShareI" UUID="4801B06568C157EE" TYPE="ntfs"
/dev/sdc1: UUID="97d52bff-5050-4de1-af88-1adc3631e03c" TYPE="ext4"
/dev/sdc5: UUID="0b7fd151-6280-4d27-89e0-8fe0e9ee7710" TYPE="swap"


fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc  nodev,noexec,nosuid  0  0
/dev/sda1                                  /              ext4  errors=remount-ro    0  1
# swap was on /dev/sda5 during installation
UUID=0b7fd151-6280-4d27-89e0-8fe0e9ee7710  none           swap  sw                   0  0
/dev/sdb1                                  /media/sharei  ntfs  defaults             0  0
/dev/sda1                                  /media/shareii  ntfs  defaults             0  0

What am i doing wrong?! :) On start up, it only mounts /dev/sda1 and mounts it on /media/sharei... 

Thank you in advance for any help :)

---

### Post by ajgreeny on 2011-07-01
Make sure you have already made the folders in /media with command  ```
sudo mkdir /media/sharei /media/shareii
```or the whole thing  will fail.  I assume you must have done this or you would not get the  one successful mount that you do seem to manage.

Your lines in fstab ought to be in the format of ```
UUID=921A19ED1A19CF5B /media/sharei/    ntfs-3g        auto,user,rw 0 0
```so change the /dev/sda1 and /dev/sdb1 to the correct UUIDs for each partition and then edit the rest of the lines to show as mine.

---

