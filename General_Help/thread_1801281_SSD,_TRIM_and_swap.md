---
title: "SSD, TRIM and swap"
date: 2011-07-10
forum: General Help
---

### Post by olejon on 2011-07-10
Hi! I am using the option "discard" on my EXT4 partition in /etc/fstab (SSD disk) to get TRIM working. My question is: Should I add "discard" to the swap partition as well? Or is it only possible with EXT4?

---

### Post by pqwoerituytrueiwoq on 2011-07-10
i would not use a swap partition on a ssd since it has a write limit
think about it like using a flash drive as swap 
you can use the noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition
/tmp is not a good thing to has on the ssd either i dont even have /var on it
the 16 gig is a ssd
```
Disk /dev/sda: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5c56

   Device Boot      Start         End      Blocks   Id  System               Label
/dev/sda1   *           1        1946    15631213+  83  Linux                Root

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System               Label
/dev/sdb1               1         261     2096451   83  Linux                Var
/dev/sdb2             262        4865    36981599+   5  Extended
/dev/sdb5             262        3037    22298188+  83  Linux                Home
/dev/sdb6            3038        4290    10064691   83  Linux                Virtual_Machines
/dev/sdb7            4291        4865     4618656   82  Linux swap / Solaris Swap 
```
/tmp is on my ram

---

### Post by olejon on 2011-07-30
Thanks for your answer. I already have /tmp on my RAM. My SSD disk is a brand new Corsair 120 GB Force series 3, which I think can live for many, many years no matter how much I write to it.

I just wondered if swap could use TRIM. Since I have 4 GB RAM, the swap partition is rarely used anyway.

---

### Post by pqwoerituytrueiwoq on 2011-07-30
i am using trim here
swap on a ssd is not a good idea cause of the write limit
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4    discard,errors=remount-ro,noatime,nodiratime 0       1
# /home was on /dev/sda5 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults                             0       2
# /mnt/HardDisks was on /dev/sda6 during installation
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /mnt/HardDisks  ext4    defaults                             0       2
# /var was on /dev/sda1 during installation
UUID=5cae72de-be5c-4586-90ec-c65ce056555b /var            ext4    defaults                             0       2
# /tmp was made a ram disk after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777           0       0
# swap was on /dev/sda7 during installation
UUID=4455f38b-2151-4243-831e-ebc2298b865f none            swap    sw                                   0       0
```

---

### Post by dcstar on 2011-07-30
> **pqwoerituytrueiwoq said:**
> i am using trim here
.........

Only on the root filesystem.

---

### Post by pqwoerituytrueiwoq on 2011-07-31
> **dcstar said:**
> Only on the root filesystem.
only the root partition is on a ssd :roll:

---

