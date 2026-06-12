---
title: "how to stop automounting both ntfs partitions"
date: 2009-08-01
forum: General Help
---

### Post by mitodonesov on 2009-08-01
i have two ntfs partitions and i want to  prevent ubuntu from automounting the second one when one of them is mounted. both partitions are on the same disk. fstab file looks like this (nothing about ntfs drives). ubuntu version is 9.04 - clean install.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
# UUID=3c9a7399-37d6-4041-8f1e-16cd5ade3888 /               ext4    relatime,errors=remount-ro 0       1

/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by michy99 on 2009-08-01
The partitions are not 'automounting.' They don't actually mount until you click on them in Places or Nautilus.

---

### Post by mitodonesov on 2009-08-01
they are not automounting. when i mount one partition, the other ntfs partition is automounted.

---

### Post by michy99 on 2009-08-01
What is the output of these commands with the partitions mounted?```
sudo fdisk -l
mount
```

---

### Post by mitodonesov on 2009-08-01
fdisk -l:

mito@Tiger:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4c8d4c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7833    62918540+   7  HPFS/NTFS
/dev/sda2   *        7834        9807    15856155   83  Linux
/dev/sda3            9808       30401   165421305    5  Extended
/dev/sda5            9808       29820   160754391    7  HPFS/NTFS
/dev/sda6           29821       30401     4666851   82  Linux swap / Solaris


mount:

mito@Tiger:~$ mount
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda5 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


probably this 'allow_other' setting should be deleted, but where to find it, it's not in fstab.

---

