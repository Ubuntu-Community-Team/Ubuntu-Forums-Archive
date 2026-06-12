---
title: "strange mdadm raid5 issue, drive ok depending on what is examined.."
date: 2011-03-07
forum: General Help
---

### Post by railan on 2011-03-07
Hey guys,

I'm having a strange issue with mdadm, my raid 5 has gone down, but all the drives appear present, I can't get the thing to assemble, here are the details;

I have many drives in this machine

/dev/md0 = raid0 of sdb & sdc (2x750 = 1.5tb)
/dev/md1 = raid0 of sdd & sde (2x750 = 1.5tb)
/dev/sdf 1.5tb
/dev/sdh 1.5tb
/dev/sdg 1.5tb

sdh & sdg are on a PCI-E expansion slot.

The thing that scares me here is all drives in md2 are flagged as spare..
```

$ sudo cat /proc/mdstat
Personalities : [raid0] [linear] [multipath] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : inactive md0[0](S) sdg[4](S) sdh[3](S) sdf[2](S) md1[1](S)
      7325713216 blocks

md0 : active raid0 sdb[0] sdc[1]
      1465148928 blocks 64k chunks

md1 : active raid0 sdd[0] sde[1]
      1465148928 blocks 64k chunks

```

Attempting to assemble this, it finds all slots, and then says failure? I don't get it.
```

$ sudo mdadm -Av /dev/md2 --uuid=4402efa0:856b496c:55fd68b1:9d3aeb74 /dev/md0 /dev/md1 /dev/sdf /dev/sdh /dev/sdg
mdadm: looking for devices for /dev/md2
mdadm: /dev/md0 is identified as a member of /dev/md2, slot 0.
mdadm: /dev/md1 is identified as a member of /dev/md2, slot 1.
mdadm: /dev/sdf is identified as a member of /dev/md2, slot 2.
mdadm: /dev/sdh is identified as a member of /dev/md2, slot 3.
mdadm: /dev/sdg is identified as a member of /dev/md2, slot 4.
mdadm: added /dev/md1 to /dev/md2 as 1
mdadm: added /dev/sdf to /dev/md2 as 2
mdadm: added /dev/sdh to /dev/md2 as 3
mdadm: added /dev/sdg to /dev/md2 as 4
mdadm: added /dev/md0 to /dev/md2 as 0
mdadm: /dev/md2 assembled from 3 drives - not enough to start the array.

```

mdadm.conf for good measure...
```
ARRAY /dev/md2 level=raid5 num-devices=5 UUID=4402efa0:856b496c:55fd68b1:9d3aeb74
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=349c3012:20c47bc7:55fd68b1:9d3aeb74
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=b5dde747:e0effdaf:55fd68b1:9d3aeb74
```

Now, this is where it gets me, depending on which drive I examine, it shows some drives as faulty (at worse case), or it shows they are all attached and okay (at best case..). (/dev/sdg reports the best case)
```

$sudo mdadm --examine /dev/md0
/dev/md0:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 4402efa0:856b496c:55fd68b1:9d3aeb74 (local to host railbox)
  Creation Time : Mon Apr 26 18:16:41 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 5860553984 (5589.06 GiB 6001.21 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 2

    Update Time : Mon Mar  7 09:03:08 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 56a622d1 - correct
         Events : 1760094

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       9        0        0      active sync   /dev/block/9:0

   0     0       9        0        0      active sync   /dev/block/9:0
   1     1       9        1        1      active sync   /dev/block/9:1
   2     2       8       80        2      active sync   /dev/sdf
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
$ sudo mdadm --examine /dev/md1
/dev/md1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 4402efa0:856b496c:55fd68b1:9d3aeb74 (local to host railbox)
  Creation Time : Mon Apr 26 18:16:41 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 5860553984 (5589.06 GiB 6001.21 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 2

    Update Time : Mon Mar  7 09:03:08 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 56a622d4 - correct
         Events : 1760094

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       9        1        1      active sync   /dev/block/9:1

   0     0       9        0        0      active sync   /dev/block/9:0
   1     1       9        1        1      active sync   /dev/block/9:1
   2     2       8       80        2      active sync   /dev/sdf
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
$ sudo mdadm --examine /dev/sdf
/dev/sdf:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 4402efa0:856b496c:55fd68b1:9d3aeb74 (local to host railbox)
  Creation Time : Mon Apr 26 18:16:41 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 5860553984 (5589.06 GiB 6001.21 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 2

    Update Time : Mon Mar  7 09:03:08 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 56a62324 - correct
         Events : 1760094

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       80        2      active sync   /dev/sdf

   0     0       9        0        0      active sync   /dev/block/9:0
   1     1       9        1        1      active sync   /dev/block/9:1
   2     2       8       80        2      active sync   /dev/sdf
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
$ sudo mdadm --examine /dev/sdg
/dev/sdg:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 4402efa0:856b496c:55fd68b1:9d3aeb74 (local to host railbox)
  Creation Time : Mon Apr 26 18:16:41 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 5860553984 (5589.06 GiB 6001.21 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 2

    Update Time : Sat Feb 26 23:22:46 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5697e38e - correct
         Events : 1656218

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       96        4      active sync   /dev/sdg

   0     0       9        0        0      active sync   /dev/block/9:0
   1     1       9        1        1      active sync   /dev/block/9:1
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8      112        3      active sync   /dev/sdh
   4     4       8       96        4      active sync   /dev/sdg
rail@railbox:/$ sudo mdadm --examine /dev/sdh
/dev/sdh:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 4402efa0:856b496c:55fd68b1:9d3aeb74 (local to host railbox)
  Creation Time : Mon Apr 26 18:16:41 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 5860553984 (5589.06 GiB 6001.21 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 2

    Update Time : Mon Mar  7 09:01:49 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 56a622de - correct
         Events : 1760089

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      112        3      active sync   /dev/sdh

   0     0       9        0        0      active sync   /dev/block/9:0
   1     1       9        1        1      active sync   /dev/block/9:1
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8      112        3      active sync   /dev/sdh
   4     4       0        0        4      faulty removed

```

At this stage I don't know what to do, at some times the drives are all present, yet I can't assemble it.. I have tried removing two of the 750's (/dev/md0) and attaching two of the 1.5s (sdg & sdh) directly into the motherboard, but that didn't help. It just reported /dev/md0 as missing (as it was unplugged) and said only 2 devices were available. It's like the two 1.5's currently in my PCI-E expansion slot are borked :(

Anyone got any other ideas? Is there are possible logical explanation as to why the raid5 will be reported differently depending on which drive i examine?

I could go and buy a different PCI-E controller, but I'm rather sure that its working, the drive is being detected fine, I just can't push the raid together..

would very much appreciate any help with this one,

thanks in advance.

---

### Post by YesWeCan on 2011-03-07
Yes it is nice that mdadm gives such useful error messages. :???:
This was all working ok before? What changed just before it wouldn't work?

According to the man page --examine shows what was last written to the superblocks on each device. This is not the same as the current state of each device according to mdadm. The --examine of sdg shows all drives ok and sdh shows sdg faulty and all the others show sdg and sdh faulty. From this you can deduce that sdg was failed first (and its superblock was not updated because it had failed) and sdh failed next (having had its superblock updated to show sdg failed).

As sdg and sdh were on the PCIE expansion slot, this suggests something changed with this card. Do you have any idea what it might have been?

---

### Post by railan on 2011-03-07
Thanks for your reply!

And wow 5th page over night, this board moves quickly :D

According to my wife who was home, she couldn't access the machine (via smb), hit reboot and from then it was in this stage. I haven't opned the machine up or even ssh'd in for months, its just a smb file server.

Once I finally got to it, I could see the PCI-E sata card had trouble finding the devices during boot (it took minutes or longer to find them). What's strange is now on boot it's almost instant. I have unplugged & replugged the card, maybe its faulty or on the way out, or maybe there was dust, who knows.

Thanks for your explanation of mdadm --examine, that actually makes some sense :) The next obvious question is going to be, am I able to restore the raid to a state where all the devies were in sync? :) It can't be as simple as unflagging /dev/sdh & sdg as removed ? heh

The machine is failing to boot (since my md2 is mounted to /home). I am hoping all devices should still be in sync since I see no way why they could not be. If 2 devices in a raid5 disappear, the raid should stop operating, until at least 1 of those devices is returned (at which case you could force a degraded mount -- which I have not done anyway).

---

### Post by YesWeCan on 2011-03-07
I believe you can force an assembly of the array...I think this resets the superblocks and removes the failed flags. I'm not an expert.

I run a RAID1+0 with 4 drives with my OS installed on it. All sata on the mobo connectors. I decided to test its resilience by powering off my PC while writing to the array. When it rebooted one of the drives had been spared out and failed. It then did a resync. I think this was due to the OS detecting a journalling error, fixing it, and then telling mdadm that the drive had a read fault...or something along those lines. So it wouldn't surprise me too much if a reboot had caused your PCIE drives to be failed by mdadm, although I cannot guess the exact mechanism.

---

### Post by railan on 2011-03-08
you're right on the money

successfully mounted it with a --force, it removed the faulty flag from one of my drives and mounted with 4/5 degraded.

then re-added the 5th drive, and the raid is now rebuilding (250mins to go heh)

thanks very much! :D

---

