---
title: "mounting from previous distro"
date: 2010-09-27
forum: General Help
---

### Post by buffchick on 2010-09-27
I just moved from rpath to ubuntu server and I'm totally digging it so far. However, even though the install found my software raid 1 drives it didn't mount them. I'm not sure what I should do. here's the previous fstab.

```
LABEL=/1 / ext3 defaults 1 1
LABEL=/boot /boot ext3 defaults 1 2
devpts /dev/pts devpts gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs defaults 0 0
/proc /proc proc defaults 0 0
/sys /sys sysfs defaults 0 0
LABEL=SWAP-hda2 swap swap defaults 0 0
/dev/media/media /mnt/media/media xfs defaults,usrquota,grpquota 0 0
/dev/backup/backup /mnt/backup/backup xfs defaults,usrquota,grpquota 0 0
```new fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nas-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=396cdac2-cf82-4030-ae71-e6533a721e05 /boot           ext2    defaults        0       2
/dev/mapper/nas-swap_1 none            swap    sw              0       0

```fdisk -l
```
Disk /dev/sda: 8119 MB, 8119738368 bytes
255 heads, 63 sectors/track, 987 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065dcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32         988     7677953    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5              32         988     7677952   8e  Linux LVM

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b3fb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020d2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a184f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/md2: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050689

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 320.1 GB, 320070221824 bytes
2 heads, 4 sectors/track, 78142144 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```old mdadm.conf
```
DEVICE partitions
ARRAY /dev/md2 UUID=6230047a:d8c5281f:e9172a5d:f35a5034
ARRAY /dev/md0 UUID=7ff0af91:929bfc9e:535c52dc:9684c473

```new mdadm.conf
```
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=7ff0af91:929bfc9e:535c52dc:9684c473
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=6230047a:d8c5281f:e9172a5d:f35a5034

```

```
temp@nas:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sde1[1] sdd1[0]
      976759936 blocks [2/2] [UU]

md0 : active raid1 sdc1[1] sdb1[0]
      312568576 blocks [2/2] [UU]

unused devices: <none>
temp@nas:~$ sudo mount /dev/md0 /mnt/media
[sudo] password for temp:
mount: unknown filesystem type 'LVM2_member'

```
Suggestions? Thanks in advance!

---

### Post by buffchick on 2010-09-27
I figured it out. it was a LVM2 issue since I came from a fedora based distro. I'm all good.

---

### Post by buffchick on 2010-09-27
I lied, I got the lvm mounted with this

[http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

but, I don't know how to make it stay that way. isn't that something to with fstab?

---

### Post by buffchick on 2010-09-27
is ok to be marked as solved. I just had to keep at it.

---

