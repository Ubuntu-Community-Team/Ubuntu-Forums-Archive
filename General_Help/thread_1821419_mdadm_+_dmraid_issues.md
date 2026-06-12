---
title: "mdadm + dmraid issues"
date: 2011-08-09
forum: General Help
---

### Post by olale on 2011-08-09
Hi!

After a power failure yesterday I began to receive information that one of the two disks in my server were failing:

```
This is an automatically generated mail message from mdadm
running on server

A DegradedArray event had been detected on md device /dev/md2.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 dm-2[0]
     2008000 blocks [2/1] [U_]

md1 : active raid1 dm-1[0]
     242187776 blocks [2/1] [U_]

unused devices: <none>
```

It seemed both md1 and md2 were missing one device, but which?

```
root@server:/var/log# ls -l /dev/mapper
totalt 0
crw------- 1 root root 10, 59 2011-08-08 11:58 control
lrwxrwxrwx 1 root root      7 2011-08-08 11:58 nvidia_hehbcabb -> ../dm-0
lrwxrwxrwx 1 root root      7 2011-08-08 13:55 nvidia_hehbcabb1 -> ../dm-1
lrwxrwxrwx 1 root root      7 2011-08-08 11:58 nvidia_hehbcabb2 -> ../dm-2
```

There are no other device-mapper devices in /dev/mapper than the two dmraid devices dm-1 (for /) and dm-2 (swap). Could it be that mdadm builds an array *on* dmraid arrays? I don't understand. Besides, dmraid seems to indicate that the RAID-1 array spanning the two disks is up and running alright:

```
root@server:/var/log# dmraid -r
/dev/sdb: nvidia, "nvidia_hehbcabb", mirror, ok, 488397166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_hehbcabb", mirror, ok, 488397166 sectors, data@ 0
```

So, what am I missing? How can it be that the Ubuntu installer installed both mdadm AND dmraid, and is using both somehow? And how can I fix the md arrays that are failing?

Thanks for any help!

---

