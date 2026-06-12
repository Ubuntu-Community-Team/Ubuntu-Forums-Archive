---
title: "mdadm raid5 array - 0 space available but usage is less than capacity"
date: 2010-09-22
forum: General Help
---

### Post by RDoh on 2010-09-22
I have a RAID5 array of 5 1TB disks that has worked fine for 2 years but now says that it has 0 space available (even though it does have space available). It will allow me to read from it but not write. I can delete things, and the usage goes down but the space stays at 0.

I can touch but not mkdir:

```
rob@cholera ~ $ mkdir /share/test
mkdir: cannot create directory `/share/test': No space left on device
rob@cholera ~ $ touch /share/test 
rob@cholera ~ $ rm /share/test
rob@cholera ~ $
```

Output from df -h (/dev/md2 is the problem array):

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1               23G   15G  6.1G  72% /
varrun               1008M  328K 1007M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  140K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
/dev/md0              183M   43M  131M  25% /boot
/dev/md2              3.6T  3.5T     0 100% /share
```

and without the -h:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md1              23261796  15696564   6392900  72% /
varrun                 1031412       328   1031084   1% /var/run
varlock                1031412         0   1031412   0% /var/lock
udev                   1031412       140   1031272   1% /dev
devshm                 1031412         0   1031412   0% /dev/shm
/dev/md0                186555     43532    133391  25% /boot
/dev/md2             3843709832 3705379188         0 100% /share
```

Everything looks fine with the mdadm array as far as I can tell from the following:

```
rob@cholera /share $ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sda4[0] sde4[4] sdd4[3] sdc4[2] sdb4[1]
      3874235136 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
md1 : active raid5 sda3[0] sde3[4] sdd3[3] sdc3[2] sdb3[1]
      31262208 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
md0 : active raid1 sda1[0] sde1[4](S) sdd1[3] sdc1[2] sdb1[1]
      192640 blocks [4/4] [UUUU]
      
unused devices: <none>


rob@cholera /share $ sudo mdadm -D /dev/md2
/dev/md2:
        Version : 00.90.03
  Creation Time : Sat May  3 13:45:54 2008
     Raid Level : raid5
     Array Size : 3874235136 (3694.76 GiB 3967.22 GB)
  Used Dev Size : 968558784 (923.69 GiB 991.80 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Wed Sep 22 23:16:06 2010
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 4387b8c0:21551766:ed750333:824b67f8
         Events : 0.651050

    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       20        1      active sync   /dev/sdb4
       2       8       36        2      active sync   /dev/sdc4
       3       8       52        3      active sync   /dev/sdd4
       4       8       68        4      active sync   /dev/sde4


rob@cholera /share $ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=a761c788:81771ba6:c983b0fe:7dba32e6
ARRAY /dev/md1 level=raid5 num-devices=5 UUID=291649db:9f874a3c:def17491:656cf263
ARRAY /dev/md2 level=raid5 num-devices=5 UUID=4387b8c0:21551766:ed750333:824b67f8

# This file was auto-generated on Sun, 04 May 2008 14:57:35 +0000
# by mkconf $Id$
```

So maybe this is a file system problem rather than an mdadm problem? Either way I've already bashed my head against a brick wall for a few weeks and I don't know where to go from here so any advice would be appreciated.

Thanks
Rob

---

