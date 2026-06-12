---
title: "software raid1 array fails to activate on boot"
date: 2012-01-19
forum: General Help
---

### Post by buffchick on 2012-01-19
So, I have a raid 1 array that's not starting at boot. I have to manually restart the array, mount it, then add the second drive to as it shows 1 drive failed. it recovers and works fine... until I reboot. Then I have to start all over again. The error message I get is this.

```
init: ureadahead-other main process (404) terminated with status 4
The disk drive for /mnt/storage is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
```I press s, let it boot, and do this to reactivate it
```
sudo mdadm -R /dev/md0
sudo mount /dev/md0 /mnt/storage
```here's some drive info
```
sudo blkid
/dev/sda1: UUID="a1a91b1f-6d2b-462d-84e6-46e949211979" TYPE="ext2"
/dev/sda5: UUID="rTyUA4-GtXV-EPbg-25AR-ydjT-5Me0-UP2k6E" TYPE="LVM2_member"
/dev/mapper/NAS-root: UUID="92cb1a8c-3068-453b-ac92-1850fe98811c" TYPE="ext4"
/dev/sdb1: UUID="306e2114-444e-0ff2-cced-5de7ca715931" TYPE="linux_raid_member"
/dev/mapper/NAS-swap_1: UUID="c8938871-ee53-4356-afad-62ae666c5de6" TYPE="swap"
/dev/md0: UUID="894c0448-f517-4c86-821d-ebcfab67278a" TYPE="ext3"
/dev/sdc1: UUID="306e2114-444e-0ff2-cced-5de7ca715931" TYPE="linux_raid_member"
/dev/sdd1: UUID="c4989226-40ca-5381-cced-5de7ca715931" TYPE="linux_raid_member"
/dev/sde1: UUID="c4989226-40ca-5381-cced-5de7ca715931" TYPE="linux_raid_member"
/dev/md1: UUID="c3320348-3937-4bb9-920a-8d0a693ddb7d" TYPE="ext4"

```fdisk -l
```

Disk /dev/sda: 8119 MB, 8119738368 bytes
255 heads, 63 sectors/track, 987 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32         988     7677953    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5              32         988     7677952   8e  Linux LVM

Disk /dev/dm-0: 7470 MB, 7470055424 bytes
255 heads, 63 sectors/track, 908 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa99677fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/dm-1: 390 MB, 390070272 bytes
255 heads, 63 sectors/track, 47 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/md0: 2000.4 GB, 2000396222464 bytes
2 heads, 4 sectors/track, 488377984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa76e8de3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x934a5078

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2236a1e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md1: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

```/etc/mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdc1 /dev/sdb1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR no@spam.com
MAILFROM nas-server - mdadm

# definitions of existing MD arrays
# This file was auto-generated on Tue, 25 Jan 2011 04:21:13 -0600
# by mkconf $Id$
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=306e2114:444e0ff2:cced5de7:ca715931
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=c4989226:40ca5381:cced5de7:ca715931

```/etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/NAS-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a1a91b1f-6d2b-462d-84e6-46e949211979 /boot           ext2    defaults        0       2
/dev/mapper/NAS-swap_1 none            swap    sw              0       0
#
/dev/scd0               /media/cdrom    udf,iso9660 user,noauto,exec,utf8       0       0
/dev/md0                /mnt/storage    ext3    defaults        0       0
/dev/md1                /mnt/backup     ext4    defaults        0       0

```cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sde1[1] sdd1[0]
      976759936 blocks [2/2] [UU]

md0 : active raid1 sdb1[2] sdc1[0]
      1953511936 blocks [2/1] [U_]
      [>....................]  recovery =  4.3% (84445056/1953511936) finish=682.0min speed=45669K/sec

```sudo mdadm --detail --scan
```
ARRAY /dev/md0 metadata=0.90 spares=1 UUID=306e2114:444e0ff2:cced5de7:ca715931
ARRAY /dev/md1 metadata=0.90 UUID=c4989226:40ca5381:cced5de7:ca715931

```

Suggestions?

---

### Post by buffchick on 2012-01-20
Anyone?

---

### Post by dcstar on 2012-01-21
> **buffchick said:**
> Anyone?

Maybe:

[http://ubuntuforums.org/showthread.php?t=1764861](http://ubuntuforums.org/showthread.php?t=1764861)

---

### Post by buffchick on 2012-01-22
alas no. This wasn't due to an update it was due to me accidentally unplugging both drives in the array while the machine was running.

---

### Post by buffchick on 2012-01-24
Still nothing. In desperate  search of an answer. Anyone know a software RAID expert?

---

