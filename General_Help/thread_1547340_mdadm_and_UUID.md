---
title: "mdadm and UUID"
date: 2010-08-06
forum: General Help
---

### Post by fenix_ on 2010-08-06
I'm trying to get mdadm to assemble all my drives with help of uuid.

When I use

$ sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd
mdadm: /dev/md0 has been started with 3 drives.

So the setup works. But I want to do it the proper way with UUID.

$ sudo blkid
/dev/sda1: UUID="273cf478-7b19-4233-91be-5c8b49898542" TYPE="ext4"
/dev/sda5: UUID="b63ae843-24d3-4f5e-b4e0-5074af0c0d4a" TYPE="swap"
/dev/sdb: UUID="38b2a00d-687c-b168-30f0-d821417134d7" TYPE="linux_raid_member"
/dev/sdc: UUID="38b2a00d-687c-b168-30f0-d821417134d7" TYPE="linux_raid_member"
/dev/sdd: UUID="38b2a00d-687c-b168-30f0-d821417134d7" TYPE="linux_raid_member"
/dev/sde1: LABEL="DistStorage1TB" UUID="ec9f8b33-8df3-4136-9761-57b60076b4be" TYPE="ext4"

shows that /dev/sdb /dev/sdc and /dev/sdd have the same UUID.

so I should be able to use the UUID for the array
$ sudo mdadm --assemble /dev/md0 -u 38b2a00d:687c:b168:30f0:d821417134d7
mdadm: /dev/md0 has been started with 2 drives (out of 3)

Why does /dev/md0 only start 2 drives, did I miss something?

---
Debug info
---

$ sudo mdadm -E /dev/sdb
/dev/sdb:
Magic : a92b4efc
Version : 00.90.00
UUID : 38b2a00d:687cb168:30f0d821:417134d7 (local to host fenixbrood-desktop)
Creation Time : Fri Jul 16 07:50:57 2010
Raid Level : raid5
Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
Array Size : 2930276992 (2794.53 GiB 3000.60 GB)
Raid Devices : 3
Total Devices : 3
Preferred Minor : 0

Update Time : Fri Aug 6 20:35:58 2010
State : clean
Active Devices : 3
Working Devices : 3
Failed Devices : 0
Spare Devices : 0
Checksum : acae3586 - correct
Events : 56

Layout : left-symmetric
Chunk Size : 64K

Number Major Minor RaidDevice State
this 0 8 16 0 active sync /dev/sdb

0 0 8 16 0 active sync /dev/sdb
1 1 8 32 1 active sync /dev/sdc
2 2 8 48 2 active sync /dev/sdd
$ sudo mdadm -E /dev/sdb
/dev/sdb:
Magic : a92b4efc
Version : 00.90.00
UUID : 38b2a00d:687cb168:30f0d821:417134d7 (local to host fenixbrood-desktop)
Creation Time : Fri Jul 16 07:50:57 2010
Raid Level : raid5
Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
Array Size : 2930276992 (2794.53 GiB 3000.60 GB)
Raid Devices : 3
Total Devices : 3
Preferred Minor : 0

Update Time : Fri Aug 6 20:35:58 2010
State : clean
Active Devices : 3
Working Devices : 3
Failed Devices : 0
Spare Devices : 0
Checksum : acae3586 - correct
Events : 56

Layout : left-symmetric
Chunk Size : 64K

Number Major Minor RaidDevice State
this 0 8 16 0 active sync /dev/sdb

0 0 8 16 0 active sync /dev/sdb
1 1 8 32 1 active sync /dev/sdc
2 2 8 48 2 active sync /dev/sdd
$ sudo mdadm -E /dev/sdc
/dev/sdc:
Magic : a92b4efc
Version : 00.90.00
UUID : 38b2a00d:687cb168:30f0d821:417134d7 (local to host fenixbrood-desktop)
Creation Time : Fri Jul 16 07:50:57 2010
Raid Level : raid5
Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
Array Size : 2930276992 (2794.53 GiB 3000.60 GB)
Raid Devices : 3
Total Devices : 3
Preferred Minor : 0

Update Time : Fri Aug 6 20:35:58 2010
State : clean
Active Devices : 3
Working Devices : 3
Failed Devices : 0
Spare Devices : 0
Checksum : acae3598 - correct
Events : 56

Layout : left-symmetric
Chunk Size : 64K

Number Major Minor RaidDevice State
this 1 8 32 1 active sync /dev/sdc

0 0 8 16 0 active sync /dev/sdb
1 1 8 32 1 active sync /dev/sdc
2 2 8 48 2 active sync /dev/sdd
$ sudo mdadm -E /dev/sdd
/dev/sdd:
Magic : a92b4efc
Version : 00.90.00
UUID : 38b2a00d:687cb168:30f0d821:417134d7 (local to host fenixbrood-desktop)
Creation Time : Fri Jul 16 07:50:57 2010
Raid Level : raid5
Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
Array Size : 2930276992 (2794.53 GiB 3000.60 GB)
Raid Devices : 3
Total Devices : 3
Preferred Minor : 0

Update Time : Fri Aug 6 20:35:58 2010
State : clean
Active Devices : 3
Working Devices : 3
Failed Devices : 0
Spare Devices : 0
Checksum : acae35aa - correct
Events : 56

Layout : left-symmetric
Chunk Size : 64K

Number Major Minor RaidDevice State
this 2 8 48 2 active sync /dev/sdd

0 0 8 16 0 active sync /dev/sdb
1 1 8 32 1 active sync /dev/sdc
2 2 8 48 2 active sync /dev/sdd

---

### Post by jacekk015 on 2010-08-06
Check
mdadm -D /dev/md0
cat /proc/mdstat

If you don't have any failed drives there's nothing to worry about.
When you created array RAID5 he has also created a 2 drive array, and third was added as spare, and then synced together.
That's the way mdadm works.

By the way. You should edit /etc/mdadm/mdadm.conf and add the array there, that will make assemble automatic with every boot.
You can use that
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```It will add line to the end of the file, and you have to cut/paste that to needed position in the conf file.

---

