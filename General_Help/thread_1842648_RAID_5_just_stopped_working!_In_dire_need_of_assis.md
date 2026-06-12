---
title: "RAID 5 just stopped working! In dire need of assistance!"
date: 2011-09-11
forum: General Help
---

### Post by mxyzptlk1 on 2011-09-11
So, I'm a fairly new linux user and I have a machine with ubuntu server 11.04 that I use as media center.
I run 5 drives with raid 5 and a few hours ago it just stopped working without any apparent reason.

Outputs:

cat /etc/mdadm/mdadm.conf
```
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
ARRAY /dev/md/0 metadata=1.2 name=MediaServer:0 UUID=abed07c8:642dcdf4:1dab4941:46f4a7e1
```mount -t ext4 /dev/md0 /home/Media/                              
 ```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```fdisk -l                                                          
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ec505

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30142   242109440   83  Linux
/dev/sda2           30142       30402     2086913    5  Extended
/dev/sda5           30142       30402     2086912   82  Linux swap / Solaris

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1eca617b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf40865d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xcb79cc05

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x898dceae

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x566e97a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243201  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

```cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb1[0](S) sdf1[5](S) sde1[3](S) sdd1[2](S) sdc1[1](S)
      9767554885 blocks super 1.2

unused devices: <none>
```mdadm --examine --scan
```
ARRAY /dev/md/0 metadata=1.2 UUID=abed07c8:642dcdf4:1dab4941:46f4a7e1 name=MediaServer:0
```mdadm --detail /dev/md0
```
mdadm: md device /dev/md0 does not appear to be active.
```mdadm --stop /dev/md0
```
mdadm: stopped /dev/md0
```mdadm --assemble --verbose --scan
```
mdadm: looking for devices for /dev/md/0
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sde1 is identified as a member of /dev/md/0, slot 3.
mdadm: /dev/sdf1 is identified as a member of /dev/md/0, slot 4.
mdadm: added /dev/sdc1 to /dev/md/0 as 1
mdadm: added /dev/sdd1 to /dev/md/0 as 2
mdadm: added /dev/sde1 to /dev/md/0 as 3
mdadm: added /dev/sdf1 to /dev/md/0 as 4
mdadm: added /dev/sdb1 to /dev/md/0 as 0
mdadm: /dev/md/0 assembled from 3 drives - not enough to start the array.
```cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bcb92102-2e87-4058-8905-8c50567bb283 none            swap    sw              0       0

/dev/LVM1/Media         /home/Media     ext4    defaults        1       2

```

---

### Post by mxyzptlk1 on 2011-09-12
I'v now gotten the RAID working with 4 discs out of 5... I ran **mdadm /dev/md0 --stop** and then I waited some time before running mdadm **--assemble --verbose --force /dev/md0 /dev/sd[bcdef]1**
```
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: forcing event count in /dev/sdf1(4) from 191319 upto 191333
mdadm: clearing FAULTY flag for device 4 in /dev/md0 for /dev/sdf1
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sde1 to /dev/md0 as 3
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sdb1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 4 drives (out of 5).
```**cat /proc/mdstat**
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sdf1[5] sdd1[2] sdc1[1]
      7814041600 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/4] [UUU_U]

unused devices: <none>
```

Used **mdadm --add /dev/md0 /dev/sde1** to add the missing disc. 

**cat /proc/mdstat**
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[3] sdb1[0] sdf1[5] sdd1[2] sdc1[1]
      7814041600 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/4] [UUU_U]
      [>....................]  recovery =  0.3% (7317888/1953510400) finish=626.8min speed=51748K/sec

unused devices: <none>
```

---

