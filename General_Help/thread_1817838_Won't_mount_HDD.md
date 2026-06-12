---
title: "Won't mount HDD"
date: 2011-08-03
forum: General Help
---

### Post by delmembrane on 2011-08-03
Hello!

I was wondering if you guys help me, for some odd reason Ubuntu 10.10 won't mount my ntfs disk, I did all the sudo mount -a thing, I went deeper and uhmm I'm wondering that there is something wrong with the fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3b887b56-8200-48c9-bd83-385f443590a3 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a2ab3651-24cb-47da-81a0-ea3a9ec9d92a none            swap    sw              0       0
# /dev/sda2
UUID=80C8A6FEC8A6F218 /media/Membrane ntfs user,auto,rw 0 0
```That last part I modified a lot of times haha

# dev/sda2
UUID=80C8A6FEC8A6F218 /media/Membrane **ntfs-3g** user,auto,rw 0 0

# dev/sda2
UUID=80C8A6FEC8A6F218 /media/Membrane ntfs user,auto,rw 0 **1**

# dev/sda2
UUID=80C8A6FEC8A6F218 /media/Membrane **auto** user,auto,rw 0 0

And stuff like that. I get the error type 1, then after tweaking it I get the "only root can mount /dev/sda2" error.

Any idea?

Useful info:
```
root@delmembrane:/media# mount.ntfs-3g /dev/sda2 /media/Membrane
bash: /sbin/mount.ntfs-3g: No such file or directory

``````
root@delmembrane:/media# mount.ntfs /dev/sda2 /media/Membrane
bash: /sbin/mount.ntfs: No such file or directory

``````
root@delmembrane:/media# blkid
/dev/sda1: LABEL="Reservado para el sistema" UUID="2E94A12C94A0F78B" TYPE="ntfs" 
/dev/sda2: UUID="80C8A6FEC8A6F218" TYPE="ntfs" 
/dev/sda5: UUID="3b887b56-8200-48c9-bd83-385f443590a3" TYPE="ext3" 
/dev/sda6: UUID="a2ab3651-24cb-47da-81a0-ea3a9ec9d92a" TYPE="swap"
``````
delmembrane@delmembrane:/media$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31ac024b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13       59527   478041088    7  HPFS/NTFS
/dev/sda3           59527       60802    10240001    5  Extended
/dev/sda5           59527       60621     8787968   83  Linux
/dev/sda6           60621       60802     1451008   82  Linux swap / Solaris
``````
delmembrane@delmembrane:/media$ dmesg |grep sd
[ 5443.953197] sd 6:0:0:0: Device offlined - not ready after error recovery
``````
/dev/sda5 / ext3 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/delmembrane/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=delmembrane 0 0
/dev/sr0 /media/Ubuntu\04011.04\040i386 iso9660 ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 0 0
```

Oh yeah Im using 10.10

---

### Post by delmembrane on 2011-08-04
bump

---

