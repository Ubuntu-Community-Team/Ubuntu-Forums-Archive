---
title: "Breaking RAID1"
date: 2009-10-21
forum: General Help
---

### Post by XCan on 2009-10-21
I have just cleaned out a server that happens to have raid1 on both / and /home comprising of two drives. However, I recently decided to remove the raid1 and use the extra drive for storage instead. Is there any simple way to do this? I was thinking of simply using mdadm to remove one of the partitions (drives) from the software raid and reformat the removed partition. But I may very well be totally lost as I have not played around too much with raid.

```

$ cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [multipath] [faulty]
md1 : active raid1 sdb1[1] sda1[0]
      5242816 blocks [2/2] [UU]

md2 : active raid1 sdb2[1] sda2[0]
      1459366848 blocks [2/2] [UU]

```

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              5.0G  544M  4.2G  12% /
tmpfs                 995M     0  995M   0% /lib/init/rw
udev                   10M  100K   10M   1% /dev
tmpfs                 995M     0  995M   0% /dev/shm
/dev/md2              1.4T  198M  1.3T   1% /home

```

```

fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c655

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         653     5242880   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sda2             653      182336  1459366912   fd  Linux raid autodetect
/dev/sda3          182336      182401      526240   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00036bb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         653     5242880   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2             653      182336  1459366912   fd  Linux raid autodetect
/dev/sdb3          182336      182401      526240   82  Linux swap / Solaris

```

---

### Post by XCan on 2009-10-22
bump

---

### Post by XCan on 2009-10-23
bump

---

### Post by realjaja on 2010-05-11
> **XCan said:**
> bump

you ever solve your problem?

---

