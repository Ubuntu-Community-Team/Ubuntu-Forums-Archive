---
title: "mdadm RAID 5 missing space while reserved blocks at 0%"
date: 2009-11-20
forum: General Help
---

### Post by Drelaz on 2009-11-20
First here are the specs of my server:
OS: Ubuntu server edition 9.10 64-bit
OS HDD: Samsung F2 1TB
Raid HDD's: 4x Samsung F2 1.5TB

I've created a RAID 5 array with mdadm. Since i have a seperate HDD for the OS i set the reserved blocks to 0% with the -m 0 parameter.

```
sudo fdisk -l /dev/md0

Disk /dev/md0: 4500.9 GB, 4500905263104 bytes
2 heads, 4 sectors/track, 1098853824 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

As you can see fdisk shows the array to be 4500GB which is correct. However when i do df i see something else:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             907G  565G  297G  66% /
udev                  1.9G  184K  1.9G   1% /dev
none                  1.9G     0  1.9G   0% /dev/shm
none                  1.9G  500K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/md0              4.1T   13G  4.1T   1% /raid

```

There is quite a few space missing which i don't understand. Here is the normal df output:

```
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            950473864 591478516 310714004  66% /
udev                   1900092       184   1899908   1% /dev
none                   1900092         0   1900092   0% /dev/shm
none                   1900092       500   1899592   1% /var/run
none                   1900092         0   1900092   0% /var/lock
none                   1900092         0   1900092   0% /lib/init/rw
/dev/md0             4326444192  13029440 4313414752   1% /raid

```

To check if reserved blocks was really 0% i umount my raid array and runned the following command:

```
sudo tune2fs -m 0 /dev/md0
tune2fs 1.41.9 (22-Aug-2009)
Setting reserved blocks percentage to 0% (0 blocks)

```

After remounting it still showed the same size. Does anyone know why i'm missing so much space?

---

### Post by Cheesemill on 2009-11-20
What does
```
df -H
```
show?

(note the capital H)

You may just be seeing the difference between GB and GiB

---

### Post by Drelaz on 2009-11-20
```
df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              974G   606G   319G  66% /
udev                   2.0G   189k   2.0G   1% /dev
none                   2.0G      0   2.0G   0% /dev/shm
none                   2.0G   512k   2.0G   1% /var/run
none                   2.0G      0   2.0G   0% /var/lock
none                   2.0G      0   2.0G   0% /lib/init/rw
/dev/md0               4.5T    14G   4.5T   1% /raid

```

I guess it was just and display issue then. Thank you.

---

