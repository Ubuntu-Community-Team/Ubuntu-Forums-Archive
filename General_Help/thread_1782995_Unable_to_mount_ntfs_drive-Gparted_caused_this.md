---
title: "Unable to mount ntfs drive-Gparted caused this"
date: 2011-06-15
forum: General Help
---

### Post by vanlong441 on 2011-06-15
Hi,
I had trouble using Gparted on a Ntfs drive. There was some kind of error after resizing my drive (it took only a sec to show the error). After that, I was unable to mount that drive again. All other drives are still fine and can be mounted.
Here is the ss:

[IMG]http://i286.photobucket.com/albums/ll84/vanlong441/Selection_002.png[/IMG]

I searched the forum and found this (but not sure whether it would apply to my system): [http://ubuntuforums.org/showthread.php?t=882473](http://ubuntuforums.org/showthread.php?t=882473)
Here is my result, please help:

Sudo fdisk -L

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb898b898

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       60801   437176814+   f  W95 Ext'd (LBA)
/dev/sda5            6376       24223   143356877    7  HPFS/NTFS
/dev/sda6           31872       60801   232380193+   7  HPFS/NTFS
/dev/sda7           28047       28078      251904   83  Linux
/dev/sda8           28078       28321     1951744   82  Linux swap / Solaris
/dev/sda9           28322       29537     9764864   83  Linux
/dev/sda10          29537       31871    18748416   83  Linuxcat /etc/fstab

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=8d769c81-0c1f-4f8a-af45-bd213461e531 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=f6181907-2f72-4d6d-bb53-499d7ca09cad /boot           ext2    defaults        0       2
# /home was on /dev/sda10 during installation
UUID=c2a87eda-2ca3-4e58-a4e1-6724a711cea7 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=510936dc-9281-4292-9689-136d5c8ea177 none            swap    sw              0       0sudo blkid

> /dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="12E8A955E8A9383D" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="3EF0D395F0D3522F" TYPE="ntfs" 
/dev/sda6: LABEL="DATA2" UUID="D65CE0E65CE0C27B" TYPE="ntfs" 
/dev/sda7: UUID="f6181907-2f72-4d6d-bb53-499d7ca09cad" TYPE="ext2" 
/dev/sda8: UUID="510936dc-9281-4292-9689-136d5c8ea177" TYPE="swap" 
/dev/sda9: UUID="8d769c81-0c1f-4f8a-af45-bd213461e531" TYPE="ext4" 
/dev/sda10: UUID="c2a87eda-2ca3-4e58-a4e1-6724a711cea7" TYPE="ext4" 
mount

> /dev/sda9 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda7 on /boot type ext2 (rw)
/dev/sda10 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
cgroup on /dev/cgroup/cpu type cgroup (rw,cpu)

---

### Post by vanlong441 on 2012-10-30
please help delete this thread. Thank you :)

---

