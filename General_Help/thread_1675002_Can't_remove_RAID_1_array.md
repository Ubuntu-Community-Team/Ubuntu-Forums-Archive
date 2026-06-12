---
title: "Can't remove RAID 1 array"
date: 2011-01-24
forum: General Help
---

### Post by buffchick on 2011-01-24
I'm going a little bit crazy. I can't seem to remove my RAID 1 arrays. Any suggestions? I don't need to save data. The drives are empty. I'm upgrading to 4 2TB drives.

Running Lucid Lynx server

```
jessica@nas:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sdb1[1]
      976759936 blocks [2/1] [_U]

md0 : active raid1 sdd1[0]
      312568576 blocks [2/1] [U_]

unused devices: <none>
jessica@nas:~$

jessica@nas:~$ sudo umount /dev/md0
umount: /dev/md0: not mounted
jessica@nas:~$ sudo mdadm --stop /dev/md0
mdadm: fail to stop array /dev/md0: Device or resource busy
jessica@nas:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Aug 15 21:41:22 2009
     Raid Level : raid1
     Array Size : 312568576 (298.09 GiB 320.07 GB)
  Used Dev Size : 312568576 (298.09 GiB 320.07 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jan 24 19:32:16 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 7ff0af91:929bfc9e:535c52dc:9684c473
         Events : 0.154872

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       0        0        1      removed
```################
```
# mdadm.conf
#
# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions /dev/sdd1 /dev/sdd1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=7ff0af91:929bfc9e:535c52dc:9684c473
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=6230047a:d8c5281f:e9172a5d:f35a5034

```

Should also note that I can't remove logical volumes from the volume group.

---

### Post by Ocxic on 2011-01-24
the state of your RAID array is "DEGRADED" therefor your cannot disassemble/stop it

---

### Post by buffchick on 2011-01-24
so I have to recover the array and then get rid of it?

---

### Post by buffchick on 2011-01-24
:| Are we sure there's no other way to do this? I just want to remove the empty drives.

Every 10.0s: cat /proc/mdstat                                                                   Mon Jan 24 21:14:55 2011

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdd1[2] sde1[0]
      312568576 blocks [2/1] [U_]
      [======>..............]  recovery = 31.5% (98728064/312568576) finish=155.3min speed=22947K/sec

md2 : active raid1 sdc1[2] sdb1[1]
      976759936 blocks [2/1] [_U]
      [=>...................]  recovery =  8.8% (86487488/976759936) finish=475.5min speed=31197K/sec

unused devices: <none>

---

### Post by buffchick on 2011-01-25
OK. It's done. I still can't remove it. "This RAID device cannot be mounted, de-activated, deleted or re-formatted as it is currently active" Now what?

jessica@nas:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdd1[1] sde1[0]
      312568576 blocks [2/2] [UU]

md2 : active raid1 sdc1[2] sdb1[1]
      976759936 blocks [2/1] [_U]
      [=======>.............]  recovery = 36.5% (356828288/976759936) finish=202.5min speed=51018K/sec

unused devices: <none>

---

### Post by Quackers on 2011-01-25
So the drives are empty? And the array is definitely raid1?
Are they recognised in gparted from the live cd desktop?

---

