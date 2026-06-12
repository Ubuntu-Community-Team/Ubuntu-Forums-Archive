---
title: "RAID5 dying.  No superblock.  Is it salvageable?"
date: 2009-10-02
forum: General Help
---

### Post by valadil on 2009-10-02
Hi.  Last week one of the disks (/dev/sdc1) in my raid degraded.  It appeared to fix itself almost immediately.  Today it outright failed.  About two hours later /dev/sdd1 failed too.

I know that this usually means my data is lost.  I just want to make sure the drives are actually done before I give up hope entirely.  I have a sneaking suspicion it's the sata card and not the disks.  That said, I'm not sure how to get them back into the array.  I saw this happen once before and killed the raid trying to reassemble it.

Here's some relevant data:

I can still see all the disks at boot up.  I can cfdisk into all of them.  In previous drive failures, I haven't been able to get into one of the disks.  This gives me hope that I can recover from this one.

$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[4](S) sdd1[3](S) sdb1[1](S) sda1[0](S)
      1562834944 blocks
unused devices: <none>

$ sudo mdadm --query /dev/md0
/dev/md0: is an md device which is not active

$ sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.


$ sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0eefbcf4:8e9db20c:2601fd00:14612f60 (local to host robotjesus)
  Creation Time : Thu Sep  4 18:17:22 2008
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct  1 22:27:13 2009
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 2bf600f7 - correct
         Events : 313842

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       33        4      spare   /dev/sdc1


$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0eefbcf4:8e9db20c:2601fd00:14612f60 (local to host robotjesus)
  Creation Time : Thu Sep  4 18:17:22 2008
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct  1 22:27:13 2009
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 2bf60109 - correct
         Events : 313842

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       33        4      spare   /dev/sdc1


$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0eefbcf4:8e9db20c:2601fd00:14612f60 (local to host robotjesus)
  Creation Time : Thu Sep  4 18:17:22 2008
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct  1 22:27:13 2009
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 2bf60119 - correct
         Events : 313842

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       33        4      spare   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       33        4      spare   /dev/sdc1


$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0eefbcf4:8e9db20c:2601fd00:14612f60 (local to host robotjesus)
  Creation Time : Thu Sep  4 18:17:22 2008
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct  1 22:21:34 2009
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 2bf5ffbd - correct
         Events : 313834

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      spare   /dev/sdc1


What confuses me is sda{a,b,c} claiming 3 working and 2 failed devices.  I only have 4 drives.

I haven't done any mdadm commands aside from examine and query.  I'm tempted to assemble and see what happens, but the no superblock error scares me.  I saw that the last time I lost a raid and wasn't able to get by that error.

---

### Post by sedawk on 2009-10-02
If the data is still on the disks you might be
able to recover it, even if you cannot repair
the RAID (it might be a good idea to create
full disk images with "dd" to another big disk).

You have to find out the disk layout
(0=sda 1=sdb 2/3=sdd 4=sdc)
and the block layout (where is block(1), block(2), block(3),
where is the parity P for block(1),block(2), and block(3).

But even without knowing this, you might be able to
verify that parity is still okay:
For every block N (blocksize 512 bytes) read it
from all disks and then check if
sda(N) XOR sdb(N) XOR sdc(N) == sdd(N)
is okay. It his works for all blocks (>0 ?), then 
the data is still okay.

---

### Post by valadil on 2009-10-02
Thanks sedawk.  In theory all that makes sense but I haven't a clue how to verify each block.  Even if they are alright, how would I go about convincing the drives they hadn't failed out of the raid?  And what if one of the two failures is legit?  With only three disks I could rebuilt the fourth, but I couldn't verify anything.

---

### Post by valadil on 2009-10-06
I reassembled the drive, minus the disk I trust least.  Data was still readable.  I ordered a new drive (though it's twice the size of my other disks, so I can use the spare space from this one as backup).  Haven't touched the raid since.  If I can sync to this disk I'll only have one drive I don't trust and I think I can live with that.  I think the command I used was

mdadm --create --assume-clean /dev/md0 /dev/sda1 /dev/sdb1 missing /dev/sdd1

---

### Post by fjgaude on 2009-10-06
From what you have shown I don't think a drive is bad, though I could be wrong. What does this command show:

```
sudo mdadm -D /dev/md0
```

You don't use the -E command on arrays, just drives.

---

### Post by valadil on 2009-10-06
I don't think sdd is bad either.  I think mdadm marked it as failed for having missed a timeout.  sdc has been kicked out several times and I no longer trust it

I can't do mdadm -D at the moment because I've pulled out the drive I don't trust and that changed sdd to sdc, so the raid is disassembled until I plug in the new drive.

---

