---
title: "lucid upgrade change drive order and broke mdadm"
date: 2010-05-19
forum: General Help
---

### Post by vtec on 2010-05-19
I have 4 drives in my system. Two are SATA and configured in a RAID 1. This is my main drive for the system. The other two drives are IDE drives used to bulk temp storage. Before the upgrade my RAID drives were:

/dev/sda
/dev/sdb

I'm not sure what the IDE drives were. Now after the upgrade the IDE drives are:

/dev/sda
/dev/sdb

and the RAID SATA drives are:

/dev/sdc
/dev/sdd

Needless to say on reboot the raid blow up and the system would not boot. I was able to get it working for now by removing the IDE drives. My current mdadm.conf file is as follows:

DEVICE partitions
ARRAY /dev/md1 level=raid1 num-devices=3 UUID=20fd5b92:860d9ca3:57d3b65c:14fcf2fb
   devices=/dev/sda2,/dev/sdb2
ARRAY /dev/md0 level=raid1 num-devices=3 UUID=16401201:52cf4cc0:27286d7a:ac5234f7
   devices=/dev/sda1,/dev/sdb1
MAILADDR root

Now I assume that I could change the devices to the new devices names. However I was hoping for a better way to do this. The IDE drives are only semi permanent. Is there a way to configure mdadm with partition labels like you can in fstab? Or maybe some other better way to do this?

---

### Post by vtec on 2010-05-19
OK turns out this is much easier to do then i thought. In mdadm.conf:

DEVICE partitions
ARRAY /dev/md1 level=raid1 num-devices=3 UUID=20fd5b92:860d9ca3:57d3b65c:14fcf2fb
devices=/dev/sda2,/dev/sdb2
ARRAY /dev/md0 level=raid1 num-devices=3 UUID=16401201:52cf4cc0:27286d7a:ac5234f7
devices=/dev/sda1,/dev/sdb1
MAILADDR root

The 'DEVICE partitions' tells it to search all partitions. If the 'devices=/dev/sda2,/dev/sdb2' and 'devices=/dev/sda1,/dev/sdb1' lines are removed it will search for the array in all partitions on the system.

---

