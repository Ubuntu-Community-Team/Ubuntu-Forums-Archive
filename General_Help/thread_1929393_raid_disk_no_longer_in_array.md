---
title: "raid disk no longer in array"
date: 2012-02-21
forum: General Help
---

### Post by crash8080 on 2012-02-21
Hopefully I'm posting this to the right place. I am new to software raid and have a problem I am stuck with and am not really sure what my next step should be.

I set up a raid 5 array with three disks using mdadm some time ago. Now when I start up my computer, bios detects all 3 drives and even shows all the drives in gparted but the raid is degraded and missing a disk. I don't know why the disk is no longer in the raid array. I am not booting to the raid array (I have another disk for that to make it less complicated). Here is the output of some commands that seem relevent. If there's other information I should be including, let me know because part of my problem is not knowing where to look.

Also, I don't see the files on this drive anymore. Why doesn't it automatically mount like before when it was not degraded?

cat /proc/mdstat

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid5 sdb1[0] sdd1[3]
      2930271232 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      
unused devices: <none>vi /etc/mdadm/mdadm.conf

> # mdadm.conf
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


# This file was auto-generated on Sat, 19 Nov 2011 16:19:03 -0600
# by mkconf $Id$
"mdadm.conf" [readonly] 23 lines, 627 characters


---

