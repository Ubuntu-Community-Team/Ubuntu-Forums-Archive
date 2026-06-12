---
title: "mdadm recreation of array"
date: 2011-03-04
forum: General Help
---

### Post by Tynx on 2011-03-04
hey guys

so I wanted to game some NFS on my computer, and how i did that: installing windows 7... 
thanks to this "lovely" OS, it created a "system-partition" on my mdadm-raid WITHOUT noticing the user. Destroyed partitiontable and everything (i think)...

so now im back on my ubuntu and trying to recreate the raid and recalculate the hd which is overwritten... I reseted the partition table with gparted to make sure that the hd is empty and this stupid "system-partition" is gone...

how can i do that? im really scared i could lose all my data, literally ALL my data. so i tried just a few things to be sure im not doing it even worser than it is. i really could use some experienced users help..:) 

this is my config:```

# cat /etc/mdadm/mdadm.conf 
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
DEVICE /dev/sdc /dev/sdd /dev/sde
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=21141dfb:7ccc5ded:f343cfc1:f6dfb684

```

and what i did is:
```
# mdadm -A -vv -f /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sde is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdd to /dev/md0 as 1
mdadm: added /dev/sde to /dev/md0 as 2
mdadm: added /dev/sdc to /dev/md0 as 0
mdadm: /dev/md0 has been started with 3 drives.

# sudo mount /dev/md0 /media/raid/
mount: you must specify the filesystem type
```

Then i tought, maybe i have to force it to sync:
```
# echo check > /sys/block/md0/md/sync_action
```

syslog didn't say anything interesting (at least for me):
```
Mar  4 23:16:09 desktop mdadm[7850]: RebuildStarted event detected on md device /dev/md0
Mar  4 23:16:09 desktop kernel: [ 8620.611440] md: data-check of RAID array md0
Mar  4 23:16:09 desktop kernel: [ 8620.611442] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Mar  4 23:16:09 desktop kernel: [ 8620.611444] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for data-check.
Mar  4 23:16:09 desktop kernel: [ 8620.611447] md: using 128k window, over a total of 1465138496 blocks.

```

i would really appreciate it to get help. I'm pretty worried about it...

thanks for the time,
tynx

---

