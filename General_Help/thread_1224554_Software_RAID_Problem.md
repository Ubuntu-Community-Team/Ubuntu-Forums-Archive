---
title: "Software RAID Problem"
date: 2009-07-27
forum: General Help
---

### Post by gus_zernial on 2009-07-27
I have a Kubuntu Jaunty system with a custom 2.6.28 kernel. I recently
added a Sil3132/4726 based eSATA RAID box to use for backup. The box has
two drives set up as JBOD (pass-through) in the hardware. I broke each disk into two partitions, and and I used Linux software RAID to mirror the partitions on the two disks, to create two RAID devices. This worked fine for about a week.

At that point I tried to upgrade the kernel to 2.6.31_rc3. The upgrade didn't work, due to problems with my graphics card, and I noticed that when I booted into recovery mode to try to fix the problems, the log showed lots of errors with the disks in the RAID box. I then went back to the 2.6.28 kernel, and now the mirrored partitions on the disks in the RAID box show they're in degraded mode, and I can't recover the mirrors. See below for example, the symptoms for the second of the two RAID devices are essentially the same.

If I hot-remove and hot-re-add the faulty spare the commands look like they work, see below, but the array almost immediately goes back to the degraded state with faulty spare. The re-add results in a ton of output in /var/log/message, also see below, but I can't discern if this output reflects a problem. I note that the faulty spare on the first of the two RAID devices is on one of the disks (sdc), and the faulty spare on the second of the two RAID devices is on the other of the disks (sdd).  

How can I fix this?

# mdadm --detail /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Fri Jul 24 13:27:32 2009
     Raid Level : raid1
     Array Size : 366281856 (349.31 GiB 375.07 GB)
  Used Dev Size : 366281856 (349.31 GiB 375.07 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Mon Jul 27 11:43:56 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           UUID : 75653f14:a5d9312e:8ccdfa7d:0ed26058 (local to host jboat17)
         Events : 0.532

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1

       2       8       33        -      faulty spare   /dev/sdc1
------------------------------------------------
# mdadm --remove /dev/md2 /dev/sdc1
mdadm: hot removed /dev/sdc1
# mdadm --add /dev/md2 /dev/sdc1
mdadm: re-added /dev/sdc1
------------------------------------------------
#tail -f /var/log/messages

Jul 27 12:04:18 jboat17 kernel: [ 2981.219363] sd 6:0:0:0: [sdc] Add. Sense: No additional sense information
Jul 27 12:04:18 jboat17 kernel: [ 2981.219407] sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 27 12:04:18 jboat17 kernel: [ 2981.219413] sd 6:0:0:0: [sdc] Sense Key : Hardware Error [current] [descriptor]
Jul 27 12:04:18 jboat17 kernel: [ 2981.219421] Descriptor sense data with sense descriptors (in hex):
Jul 27 12:04:18 jboat17 kernel: [ 2981.219425]         72 04 00 00 00 00 00 0c 00 0a 80 00 00 00 36 e0
Jul 27 12:04:18 jboat17 kernel: [ 2981.219440]         00 00 00 00
Jul 27 12:04:18 jboat17 kernel: [ 2981.219446] sd 6:0:0:0: [sdc] Add. Sense: No additional sense information
Jul 27 12:04:18 jboat17 kernel: [ 2981.219490] ata7: EH complete
Jul 27 12:04:18 jboat17 kernel: [ 2981.221837] sd 6:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
Jul 27 12:04:18 jboat17 kernel: [ 2981.221872] sd 6:0:0:0: [sdc] Write Protect is off
Jul 27 12:04:18 jboat17 kernel: [ 2981.221921] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 27 12:04:18 jboat17 kernel: [ 2981.221971] sd 6:2:0:0: [sdd] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
Jul 27 12:04:18 jboat17 kernel: [ 2981.221995] sd 6:2:0:0: [sdd] Write Protect is off
Jul 27 12:04:18 jboat17 kernel: [ 2981.222044] sd 6:2:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 27 12:04:18 jboat17 kernel: [ 2981.262163] md: md2: recovery done.
Jul 27 12:04:18 jboat17 kernel: [ 2981.279523] RAID1 conf printout:
Jul 27 12:04:18 jboat17 kernel: [ 2981.279531]  --- wd:1 rd:2
Jul 27 12:04:18 jboat17 kernel: [ 2981.279536]  disk 0, wo:1, o:0, dev:sdc1
Jul 27 12:04:18 jboat17 kernel: [ 2981.279541]  disk 1, wo:0, o:1, dev:sdd1
Jul 27 12:04:18 jboat17 kernel: [ 2981.285536] RAID1 conf printout:
Jul 27 12:04:18 jboat17 kernel: [ 2981.285542]  --- wd:1 rd:2
Jul 27 12:04:18 jboat17 kernel: [ 2981.285550]  disk 1, wo:0, o:1, dev:sdd1

---

