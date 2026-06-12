---
title: "RAID 5 - unable to remove failed disk, now array won't assemble even degraded"
date: 2011-11-24
forum: General Help
---

### Post by jtholb on 2011-11-24
I'm running RAID 5 with three disks and one of the disks failed.  I marked the disk as failed with

```
sudo mdadm /dev/md127 -f /dev/sdd1
```

(I'm not sure at what point it changed to /dev/md127, and I just haven't had the chance to implement the fix on [this thread]("http://ubuntuforums.org/showthread.php?t=1764861") to change it back to /dev/md0)

and then

```
sudo mdadm /dev/md127 -r /dev/sdd1
mdadm: hot remove failed for /dev/sdd1: Device or resource busy
```

I was going to shutdown, replace the drive, and rebuild the array, but I wasn't sure if it was wise to do it without hot removing it.  The output from mdadm --examine was odd as the first two non-failed drives managed to see the third as failed, but you can see that the third drive didn't manage to register the change (thus possible the error above)

```
sudo mdadm --examine /dev/sd[b,c,d]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d6bfa8db:624bcebf:cd0fe2e0:41039747
  Creation Time : Sat Dec  4 00:09:58 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 127

    Update Time : Tue Nov 22 21:19:25 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8205ef - correct
         Events : 2580

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed

/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d6bfa8db:624bcebf:cd0fe2e0:41039747
  Creation Time : Sat Dec  4 00:09:58 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 127

    Update Time : Tue Nov 22 21:19:25 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 820601 - correct
         Events : 2580

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed

/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d6bfa8db:624bcebf:cd0fe2e0:41039747
  Creation Time : Sat Dec  4 00:09:58 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 127

    Update Time : Tue Nov 22 21:17:46 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 82052a - correct
         Events : 2455

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
```

So I rebooted the machine and now I can't even get the array to assemble...and I'm not sure if it's wise to remove the failed drive and replace it and try and rebuild or if I might manage to lose data since at this point is isn't even running a degraded array (which it was prior to reboot).  

At the moment /proc/mdstat reads 
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdb1[0](S) sdd1[2](S) sdc1[1](S)
      5860540224 blocks
       
unused devices: <none>
```

which I find odd.  Prior to my reboot it listed sdd1 as failed (F).

/etc/mdadm/mdadm.conf contains
```
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
MAILADDR jtholb

# definitions of existing MD arrays
ARRAY /dev/md127 UUID=d6bfa8db:624bcebf:cd0fe2e0:41039747

# This file was auto-generated on Mon, 19 Sep 2011 06:53:09 -0700
# by mkconf $Id$

#added for alert sent to your gmail
MAILFROM mdadm - mdadm
```

and

```
sudo mdadm -Av /dev/md127]mdadm: looking for devices for /dev/md127
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: /dev/sdd1 has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.

```

and lastly running ```
sudo mdadm --assemble /dev/md127 /dev/sd[b,c,d]1
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted
```

which makes me think that possibly I may need to zero the superblock.  But really my question is whether I can replace the failed drive and try and rebuild the array, or whether I need to address my other current issues first so as not to lose data.  Any help would really be appreciated since left to my own devices I might manage to screw up the arrary.

---

### Post by jtholb on 2011-11-25
So my impetuousness got the better of me and I decided (foolishly I now think) to recreate the array with a missing disk 

```
mdadm --create /dev/md127 --chunk=64 --level=raid5 --raid-devices=3 /dev/sdb1 /dev/sdc1 missing
```

Life initially seemed good until I realized that I think I nuked my lvm partition table (which wasn't backed up because my primary boot disk had previously failed and in the restoration I didn't back this up--dumb).  At least the array is technically working, although it's still in a degraded state (I didn't want to add the new disk until I was sure I had totally screwed myself over).

So my final hope is that it's not totally nuked, but I think basically I don't have any chance of that.  If anyone knows of any way to recover something (ideally I'd actually just like to recover one partition on the disk...which I think was the first partition) I'd really appreciate it.  It's not the end of the world if I can't, just a bit of a headache for me.

In the end I'm afraid this has been a steep learning curve for me, but a good one all in all just because I've learned so much.

---

### Post by jtholb on 2011-12-01
For anyone in the future that is interested, I managed to get all my data back (although I'm yet to add the replacement for the failed drive), but I just wanted to put down what saved me in the end.  In the end it was much more straightforward than I thought it would be, and thankfully as long as you're not writing anything to the array or reformatting the partitions then the data just stays there waiting for you to get it right.  The commands were

```
mdadm --create --metadata=0.9 --raid-devices=3 --chunk=64 --level=5 --assume-clean /dev/md127 /dev/sdb1 /dev/sdc1 missing --uuid=d6bfa8db:624bcebf:cd0fe2e0:41039747
``````
pvcreate -u sftW7n-JaLc-l85n-IcJg-3fqW-Dd9k-NxyKjK /dev/md127
``````
vgcfgrestore -f /etc/lvm/archive/group0_00001.vg group0
```  After that they just mounted normally--no need to run e2fsck or anything else.  I hope that helps someone in the future.  Now to add the new disk and stop worrying--this has been killing me!

---

