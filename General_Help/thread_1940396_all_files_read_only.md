---
title: "all files read only"
date: 2012-03-13
forum: General Help
---

### Post by tbhatia4 on 2012-03-13
hello
i am using dual boot ubuntu 10.10 & xp pro
i have just found out that all my files in d: drive in xp have been converted to read only and i am unable to change it from windows

has ubuntu settings changed it if so kindly help me out rectify this

---

### Post by ajgreeny on 2012-03-13
How are you accessing those files on the windows partition?  Do you have to manually mount the partition to see the files, or is it mounted at boot time?

Let's see the output of ```
cat /etc/fstab
``` from your ubuntu terminal, please, then the output of ```
sudo fdisk -l
``` and then ```
sudo blkid
```

---

### Post by tbhatia4 on 2012-03-14
> **ajgreeny said:**
> How are you accessing those files on the windows partition?  Do you have to manually mount the partition to see the files, or is it mounted at boot time?

Let's see the output of ```
cat /etc/fstab
``` from your ubuntu terminal, please, then the output of ```
sudo fdisk -l
``` and then ```
sudo blkid
```
that system is in my office
 will give this a try and let you know
thanks 4 help

---

### Post by tbhatia4 on 2012-03-19
> **ajgreeny said:**
> How are you accessing those files on the windows partition?  Do you have to manually mount the partition to see the files, or is it mounted at boot time?

Let's see the output of ```
cat /etc/fstab
``` from your ubuntu terminal, please, then the output of ```
sudo fdisk -l
``` and then ```
sudo blkid
```

tarun@respawn-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1fe495bf-e973-4fc2-a708-41276bc6d000 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8018187a-df6a-4ac4-affb-0021b2aff595 none            swap    sw              0       0
tarun@respawn-ubuntu:~$ sudo fdisk -l
[sudo] password for tarun: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33863386

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       30402   192999214+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            6375       24309   144058222    7  HPFS/NTFS
/dev/sda6           24309       30147    46892032   83  Linux
/dev/sda7           30147       30402     2046976   82  Linux swap / Solaris
tarun@respawn-ubuntu:~$ sudo blkid
/dev/sda1: UUID="E2A0EFD3A0EFABEB" TYPE="ntfs" 
/dev/sda5: LABEL="Local Disk" UUID="CE9CADCE9CADB0FF" TYPE="ntfs" 
/dev/sda6: UUID="1fe495bf-e973-4fc2-a708-41276bc6d000" TYPE="ext4" 
/dev/sda7: UUID="8018187a-df6a-4ac4-affb-0021b2aff595" TYPE="swap" 
tarun@respawn-ubuntu:~$ cat /etc/fstabcat /etc/fstab
cat: /etc/fstabcat: No such file or directory
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1fe495bf-e973-4fc2-a708-41276bc6d000 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8018187a-df6a-4ac4-affb-0021b2aff595 none            swap    sw              0       0

---

