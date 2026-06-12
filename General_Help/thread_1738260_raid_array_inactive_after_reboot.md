---
title: "raid array inactive after reboot"
date: 2011-04-24
forum: General Help
---

### Post by roboa1983 on 2011-04-24
Hello,
I had some issues with my RAID6 array (with 15 disks), where 5 disks got disconnected (each five disks is connected to the motherboard via 1 SATA cable), which brought down the RAID array. I fixed this problem via readding the disks and running the array:
```
mdadm -R /dev/md1
```
However, after rebooting, the array appears inactive, and I have to go through the same motions to fix this and make it active.
The array is present in the /etc/mdadm/mdadm.conf, though also 2 other raid arrays (3 arrays total):

```
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# definitions of existing MD arrays
ARRAY /dev/md2 level=raid6 num-devices=15 UUID=91e626d3:4e41813c:b8115610:bb7c70eb
ARRAY /dev/md3 level=raid6 num-devices=15 UUID=e0f2f613:ff31f69d:b8115610:bb7c70eb
ARRAY /dev/md1 level=raid6 num-devices=15 UUID=61c4addf:2ae8f143:b8115610:bb7c70eb

```

I've tried to look in other sources. Most other issues have been solved via modyfing the /etc/mdadm/mdadm.conf file, but am not sure if it needs anything else other than the ARRAY specifications.

Thanks!

---

### Post by roboa1983 on 2011-04-25
After being successfully mounted an error-free for about 72 hours, a shutdown and reboot fully mounted the system, unlike past cases where the error was persistent.
I guess there's nothing else to add, but to keep an eye on this array to see if it is really stable.

---

