---
title: "MDADM : /dev/md0 fs &amp; partition gone"
date: 2010-11-21
forum: General Help
---

### Post by koenbuys on 2010-11-21
I made a MDADM Raid1 array (two actually /dev/md0 and /dev/md1) with two disks and installed a ext3 partition on it. I was able to copy files onto it. However when I rebooted the partition is nowhere to be found. The superblocks seem to be empty.
I would like to recover the files I have on this disk.

What do I need to do? It seems that lots of people had similar problems (fora) but I didn't found any guide that helped my problem.
My /dev/md0p1 doesn't list anymore in /dev

```

koen@torvalds:/dev$ mdadm --version
mdadm - v2.6.7.1 - 15th October 2008
koen@torvalds:/dev$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```Some more output:

```

koen@torvalds:/dev$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdc1[0] sdd1[1]
      976759936 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[1] sda1[0]
      976759936 blocks [2/2] [UU]
      
unused devices: <none

koen@torvalds:/dev$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Nov 11 17:14:24 2010
     Raid Level : raid1
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Nov 21 11:56:42 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9d3d123a:4dfdcf65:8640cfad:c339c03e
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

koen@torvalds:/dev$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Thu Nov 11 17:14:39 2010
     Raid Level : raid1
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Nov 21 13:30:50 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : b22de8fc:86a0136c:34991773:01ad2fdd
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1

koen@torvalds:/dev$ sudo mount /dev/md0 /mnt/raidA/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

koen@torvalds:/dev$ dmesg | tail
[   27.410292] type=1400 audit(1290342111.015:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1063 comm="apparmor_parser"
[   27.410593] type=1400 audit(1290342111.015:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1063 comm="apparmor_parser"
[   27.924611] r8169 0000:06:00.0: eth0: link up
[   27.924616] r8169 0000:06:00.0: eth0: link up
[   27.926102] eth1: link down
[   27.926588] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.372569] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   32.199206] ppdev: user-space parallel port driver
[   38.010977] eth0: no IPv6 routers present
[  678.691068] EXT4-fs (md0): Couldn't mount because of unsupported optional features (1c98000)

koen@torvalds:/dev$ sudo fsck /dev/md0
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Filesystem revision too high while trying to open /dev/md0
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

koen@torvalds:/dev$ sudo e2fsck -b 8193 /dev/md0
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

koen@torvalds:/dev$ sudo dumpe2fs /dev/md0 | grep -i superblock
dumpe2fs 1.41.12 (17-May-2010)
dumpe2fs: Filesystem revision too high while trying to open /dev/md0
Couldn't find valid filesystem superblock.

koen@torvalds:/dev$ sudo fsck /dev/sda
fsck from util-linux-ng 2.17.2
fsck: fsck.linux_raid_member: not found
fsck: Error 2 while executing fsck.linux_raid_member for /dev/sda


```

---

### Post by ian dobson on 2010-11-21
Hi,

Edit you /etc/mdadm/mdadm.conf and change the metadata to version 0.90 (not 00.90). Then recreate your inital ram disk with update-initramfs -u (you need root rights for both).

That should solve it.

Regards
Ian Dobson

---

### Post by koenbuys on 2010-11-21
I've tried it without any success. I still get the same errors.

```

root@torvalds:/dev# cat /etc/mdadm/mdadm.conf
DEVICE /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=0.90 UUID=9d3d123a:4dfdcf65:8640cfad:c339c03e devices=/dev/sda1,/dev/sdb1
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=0.90 UUID=b22de8fc:86a0136c:34991773:01ad2fdd devices=/dev/sdc1,/dev/sdd1

```

---

