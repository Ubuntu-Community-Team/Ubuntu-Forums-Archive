---
title: "How to interpret &quot;fdisk&quot; and &quot;df&quot; (seems conflicting)?"
date: 2011-04-25
forum: General Help
---

### Post by wazz on 2011-04-25
Could someone help me understand these results? It looks like I have one hard drive (30 GB) with three partitions, but *df* says my primary partition is under 9 GB? Shouldn't it be much larger?

```
$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004b8d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3618    29061553+  8e  Linux LVM
/dev/sda2            3619        3649      249007+   5  Extended
/dev/sda5            3619        3649      248976   83  Linux
``````
$ df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/<hostname>-root
                      8.8G  1.2G  7.2G  15% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
udev                  245M  172K  245M   1% /dev
none                     0     0     0   -  /dev/pts
none                  245M     0  245M   0% /dev/shm
none                  245M  260K  245M   1% /var/run
none                  245M     0  245M   0% /var/lock
none                  245M     0  245M   0% /lib/init/rw
/dev/sda5             228M   14M  202M   7% /boot
```

---

### Post by chellrose on 2011-04-26
I believe fdisk is giving you information about the partitions on your hard drive, whereas df is giving you information about various locations _only on your Ubuntu partition_.

---

### Post by wazz on 2011-04-26
> **Sissy13 said:**
> I believe fdisk is giving you information about the partitions on your hard drive, whereas df is giving you information about various locations _only on your Ubuntu partition_.
I guess my question is: if the primary partition is 11670% the size of the other two (based on blocks), shouldn't it be a larger portion of that 30 GB?

---

### Post by plucky on 2011-04-26
```
/dev/sda1   *           1        3618    29061553+  8e  Linux [color=red]LVM[/color]
```

Did you specify to use LVM when you created the partition?

I have never seen that as an output for fdisk.

Id=8e???

This is what my drive looks like ```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1f55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20971488+  83  Linux
/dev/sdb3            2612        9729    57175335    5  Extended
/dev/sdb5            2612        9729    57175303+  83  Linux

```

**20971488+ = 20G partition**

Notice the Id is different and the blocks actually correspond to the size of the partition.

Yours doesn't 29061553+ should be 29G

---

### Post by wazz on 2011-04-26
> **plucky said:**
> ```
/dev/sda1   *           1        3618    29061553+  8e  Linux [COLOR=red]LVM[/COLOR]
```Did you specify to use LVM when you created the partition?

I have never seen that as an output for fdisk.

Id=8e???
Hmm, I suppose so. Haven't really used this machine in 6 months,  probably set it up 1-2 years ago. Is LVM some sort of dynamic drive  allocation?

> **plucky said:**
> Yours doesn't 29061553+ should be 29G
I was planning to shred the disk until I noticed the discrepancy. Is this all harmless and related to LVM? Rather not lose any files I stashed away somewhere.

---

