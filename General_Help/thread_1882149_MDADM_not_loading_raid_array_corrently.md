---
title: "MDADM not loading raid array corrently"
date: 2011-11-16
forum: General Help
---

### Post by Onthax on 2011-11-16
I'm having some issues connecting a mdadm array to a system after reinstalling ubuntu on it

Instead of it assembling the array using the partitions i've created. eg. /dev/sda1 it's creating them using the drives /dev/sda

this doesnt assemble properly and lvm cant find the volume groups, but on reboot despite what i say in /etc/mdadm/mdadm.conf it still keeps trying to use the drives

Here is 'sudo mdadm --detail /dev/md0 after a reboot
```


sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Sep 10 22:35:28 2010
     Raid Level : raid6
     Array Size : 7814049792 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953512448 (1863.01 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Nov 17 10:47:22 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : e60b2d7e:a5b6dc0e:462a36bb:f8f383a4 (local to host media)
         Events : 0.8641516

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf

```

and my /etc/mdadm/mdadm.conf file

```


# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=md

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR myemail@mydomain.com

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid6 num-devices=6 devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdf1 metadata=0.90 UUID=e60b2d7e:a5b6dc0e:462a36bb:f8f383a4

```

and if i use 'sudo mdadm --stop /dev/md0' then 'sudo mdadm --assemble --scan' i get this on 'sudo --detail /dev/md0'

```

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Sep 10 22:35:28 2010
     Raid Level : raid6
     Array Size : 7814049792 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953512448 (1863.01 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Nov 17 10:47:22 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : e60b2d7e:a5b6dc0e:462a36bb:f8f383a4 (local to host media)
         Events : 0.8641516

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda1
       1       8       16        1      active sync   /dev/sdb1
       2       8       32        2      active sync   /dev/sdc1
       3       8       48        3      active sync   /dev/sdd1
       4       8       64        4      active sync   /dev/sde1
       5       8       80        5      active sync   /dev/sdf1

```

Any Ideas on how to make it use partitions instead of disks on boot?

---

### Post by Onthax on 2011-11-16
Solved, just had to put 

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid6 num-devices=6 devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdf1 metadata=0.90 UUID=e60b2d7e:a5b6dc0e:462a36bb:f8f383a4

before Create

---

