---
title: "225GB drive seems to be 200GB..."
date: 2011-08-04
forum: General Help
---

### Post by fr0d0 on 2011-08-04
I have met an interesting case in ubuntu 11.04.
I have created a partition of 225GB, but gparted says it's only 210 and nautilus cuts extra 10GB of free space. What does it mean? Why does it happen? Thanks!

OUTPUT ONE
ted@ted-HP-625:~$ **sudo parted -l**
Model: ATA WDC WD3200BEVT-6 (scsi)
Drive /dev/sda: 320GB
Sector size (&#1083;&#1086;&#1075;&#1080;&#1095;./&#1092;&#1080;&#1079;&#1080;&#1095;.): 512B/512B
Partition table: msdos

 #     Begin     End        Size        Type       Filesystem  Flags
 1     1049kB  106MB   105MB   primary   ntfs              &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1086;&#1095;&#1085;&#1099;&#1081;
 2     106MB   52,4GB  52,3GB  primary   ntfs
** 3     52,4GB  89,6GB  37,2GB  primary   ext3**
 4     89,6GB  320GB   230GB   extended
 5     89,6GB  95,0GB  5399MB  logical   linux-swap(v1)
** 6     95,0GB  320GB   225GB   logical   ext3**

OUTPUT TWO
ted@ted-HP-625:~$ **df -a -h**
Filesystem            Size  Used  Available  Used% Mounted as
**/dev/sda3              35G  3,4G   30G  11% /**
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
fusectl                  0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  1,4G  704K  1,4G   1% /dev
none                     0     0     0   -  /dev/pts
none                  1,4G  1,3M  1,4G   1% /dev/shm
none                  1,4G   92K  1,4G   1% /var/run
none                  1,4G     0  1,4G   0% /var/lock
**/dev/sda6             207G   12G  185G   6% /home**
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0     0     0   -  /home/ted/.gvfs

Ted Biryukov

---

### Post by Kira_Belka on 2011-08-04
use fdisk and mkfs

---

### Post by fr0d0 on 2011-08-04
> **Kira_Belka said:**
> use fdisk and mkfs
Should I create all the partitions once more? I suppose you have seen that / partition is also 2.3GB smaller than it should be.

---

