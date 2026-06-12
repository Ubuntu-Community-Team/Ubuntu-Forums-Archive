---
title: "RAID not working properly"
date: 2011-01-31
forum: General Help
---

### Post by rob1101 on 2011-01-31
Hello, I downloaded and installed ubuntu server 10.10 to use as a personal desktop. I chose the server version for the RAID and LVM support during install, and because it is less bloated. However it does not seem to be working properly.

I have two 1.5TB drives that I wish to use in RAID1. I currently have 4 partitions (swap, /boot, /, /home) and a generous amount of unallocated free space for growth or some other use.


```
$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive dm-2[0](S)
      9764800 blocks
       
md2 : active raid1 dm-4[0]
      195312576 blocks [2/1] [U_]
      
md1 : active raid1 dm-3[0]
      976832 blocks [2/1] [U_]
      
md3 : active raid1 dm-5[0]
      976562112 blocks [2/1] [U_]
      
unused devices: <none>

```

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
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=28d99b7c:491ebb5f:52690630:928a3253
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=a3c2123e:6e66200c:fd7d2328:5a964bad
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=6b44b45d:f97d18cb:db3a50f1:e0d3560d
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=7975ffae:862d7753:07035ba2:06346fdd

# This file was auto-generated on Sun, 30 Jan 2011 23:39:27 -0500
# by mkconf $Id$

```

md0 is supposed to be my swap partition but it does not seem to be working at all (resource monitor also shows 0bytes), and the other partitions seem to just have one failed drive. 

I am some what new to RAID, the drives are about a month old and were working fine in RAID1 with arch linux, but I made the decision to switch to ubuntu for a bit more stability.

How can I further troubleshoot to solve this problem?

---

