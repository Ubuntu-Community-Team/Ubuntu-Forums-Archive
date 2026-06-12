---
title: "Mapping /proc/scsi/scsi entries with respective device names in /dev/ directory"
date: 2011-04-12
forum: General Help
---

### Post by neo3matrix on 2011-04-12
Hello friends,

In my understanding, the way /proc/scsi/scsi gets populated, /proc/paritions also gets populated in the same fashion. i.e. the description for first entry of /proc/scsi/scsi can be seen in the first entry of /proc/partitions and same for rest.

So, With this assumption, in my project, I used to relate first entry of /proc/scsi/scsi with first entry of /proc/partitions to get its total size and same for all entries.

But, I observed some differences in following scenario, where

1) The first 4 entries in /proc/scsi/scsi are SAN luns attached to my system and for which the actual device names in /dev/ are sda,sdb,sdc and sdd.

2) The last 4 entries are the internal HDDs on same system. In /dev/, their respective device names are sde,sdf,sdg & sdh.

(Output attached at end of the thread)

But in /proc/partitions, the device order is different.

You can see their respective sizes in /proc/partition output as well.

So, my question is, in this particular scenario, I can't relate the first entry of /proc/scsi/scsi with first entry of /proc/partition.
i.e. scsi0:00:00:00 is not /dev/sde, because it is actually /dev/sda.

It seems that my assumption is wrong in this scenario.

**Is there any way or mechanism to figure out actual device name for an entry in /proc/scsi/scsi in /dev/ directory?**

How can my application should relate /proc/scsi/scsi entries with their respective device names and sizes?



Thanks in advance.



[root@rh12 ~]# cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
Vendor: DGC Model: RAID 5 Rev: 0220
Type: Direct-Access ANSI SCSI revision: 04
Host: scsi0 Channel: 00 Id: 00 Lun: 01
Vendor: DGC Model: RAID 5 Rev: 0220
Type: Direct-Access ANSI SCSI revision: 04
Host: scsi0 Channel: 00 Id: 00 Lun: 02
Vendor: DGC Model: RAID 5 Rev: 0220
Type: Direct-Access ANSI SCSI revision: 04
Host: scsi0 Channel: 00 Id: 00 Lun: 03
Vendor: DGC Model: RAID 5 Rev: 0220
Type: Direct-Access ANSI SCSI revision: 04
Host: scsi4 Channel: 00 Id: 00 Lun: 00
Vendor: ATA Model: GB0160CAABV Rev: n/a
Type: Direct-Access ANSI SCSI revision: 05
Host: scsi4 Channel: 00 Id: 01 Lun: 00
Vendor: ATA Model: GB0160CAABV Rev: n/a
Type: Direct-Access ANSI SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
Vendor: ATA Model: GB0160CAABV Rev: n/a
Type: Direct-Access ANSI SCSI revision: 05
Host: scsi5 Channel: 00 Id: 01 Lun: 00
Vendor: ATA Model: GB0160CAABV Rev: n/a
Type: Direct-Access ANSI SCSI revision: 05




[root@rh12 ~]# cat /proc/partitions
major minor #blocks name

8 64 156290904 sde
8 65 30720000 sde1
8 66 2048000 sde2
8 67 7168000 sde3
8 80 156290904 sdf
8 81 30720000 sdf1
8 82 6144000 sdf2
8 48 2097152 sdd
8 49 1466331 sdd1
8 0 2097152 sda
8 1 1466331 sda1
8 112 156290904 sdh
8 113 7168000 sdh1
8 96 156290904 sdg
8 97 6144000 sdg1
8 98 7168000 sdg2
8 32 2097152 sdc
8 33 1466331 sdc1
8 16 2097152 sdb
8 17 1466331 sdb1

---

