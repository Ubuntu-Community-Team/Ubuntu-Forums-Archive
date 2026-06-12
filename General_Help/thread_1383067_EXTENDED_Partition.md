---
title: "EXTENDED Partition"
date: 2010-01-16
forum: General Help
---

### Post by dontgetshocked on 2010-01-16
1. I have my MBR partition 160gb
2. 157gb linux extension 4
3. 3.1gb Extended contains logical partitions
4. 3.1 swap space

Is #3 necessary?

---

### Post by zvacet on 2010-01-16
```
sudo fdisk -l
```

Post output here.

---

### Post by dontgetshocked on 2010-01-16
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x843d9350

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris
david@david-laptop:~$

---

### Post by zvacet on 2010-01-17
It look like you have only 3 partitions; first is root second extended and inside of extended is swap.You don´t need to change anything.

---

### Post by Leppie on 2010-01-17
> **dontgetshocked said:**
> 1. I have my MBR partition 160gb
2. 157gb linux extension 4
3. 3.1gb Extended contains logical partitions
4. 3.1 swap space

Is #3 necessary?
you don't need an extended partition, it is used to bypass the 4 primary partitions limit. since you have only 2 real partitions, you didn't need to create an extended one. however, it doesn't make your system slower or anything having an extended partition.

---

### Post by garvinrick4 on 2010-01-17
> **dontgetshocked said:**
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x843d9350

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris
david@david-laptop:~$

This looks like sda1 is / and /boot and sda2 is extended with only swap residing
in a logical inside of sda2. Only using 2 primary have room for lots more. You could
throw in a partition of 8 gig or so to do bug testing on Alpha's with Ubuntu. No need
for a anything in /home so 8 gig is cool for testing. And you get a jump on whats coming
up next. Is fun to do.

---

