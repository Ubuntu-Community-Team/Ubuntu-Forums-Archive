---
title: "fstab is wrong"
date: 2010-08-06
forum: General Help
---

### Post by monkblah on 2010-08-06
Hi, I have been having some trouble with my /etc/fstab file. Specifically, fstab says that the partition /dev/sda1 should be my root mountpoint... but df and everything else indicates that /dev/sdb1 is in fact the mountpoint. Everything seems to work, but I wonder why such a discrepancy should exist. Why doesn't the system mount /dev/sda1 as instructed, and why mount /dev/sdb1 instead?

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            301725968  67101496 219297664  24% /
none                   1021152       416   1020736   1% /dev
none                   1028456       604   1027852   1% /dev/shm
none                   1028456        80   1028376   1% /var/run
none                   1028456         0   1028456   0% /var/lock
none                   1028456         0   1028456   0% /lib/init/rw
/dev/sdc1            484432112 382548152  77469984  84% /atlantic
/dev/sdc5            775093740 210955528 525075768  29% /pacific
/dev/sdc6            194065852    191952 184093532   1% /north
/home/me/.Private  301725968  67101496 219297664  24% /home/me



$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
#/dev/sdb1       /tubby       ext3    errors=remount-ro 0       1
#JK prob? UUID=e3f2a38d-9ee1-41db-b2fc-ee3ec0b25f43       /tubby       ext3    errors=remount-ro 0       1
/dev/sdc1       /atlantic       ext3    errors=remount-ro 0       1
/dev/sdc5       /pacific       ext3    errors=remount-ro 0       1
/dev/sdc6       /north       ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8478a5ea-1bba-4df2-a598-f8d163c446db none            swap    sw              0       0   #/dev/sda5
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



$ sudo blkid
/dev/sda1: UUID="e3f2a38d-9ee1-41db-b2fc-ee3ec0b25f43" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="c783a057-e114-41c5-842a-9c1a6ee1d6b9" TYPE="ext4" 
/dev/sdb5: UUID="8478a5ea-1bba-4df2-a598-f8d163c446db" TYPE="swap" 
/dev/sdc1: UUID="5c09cf51-6143-429b-a6b6-19ea81217148" TYPE="ext3" 
/dev/sdc5: UUID="f61abab2-264e-4837-818e-6d6957c01661" TYPE="ext3" 
/dev/sdc6: UUID="ccf6f6cc-8d63-443b-a71f-2b3b20450a0c" TYPE="ext3" 




```

Note that I have tried to use the UUID method in the fstab for all disks but this hasn't worked, had to boot with a dvd and change it back. Not sure if that's related to the current issue.

---

### Post by dino99 on 2010-08-06
mountmanager is the easy way to deal with partitions and devices, and you dont need to manually tweak fstab and/or mtab

(system admin mountmanager: set your prefs)

---

### Post by WorMzy on 2010-08-06
Have you read fstab's man page?

```
man fstab
```

For a start, you shouldn't have "1" for every line's pass value. Only / should have 1, everything else should have 0 or 2.

I've rewritten your fstab for you:

```
# <file system>                           <mount point> <type> <options>                  <dump> <pass>
proc                                      /proc         proc   nodev,noexec,nosuid        0      0
# swap
UUID=8478a5ea-1bba-4df2-a598-f8d163c446db swap          sw     defaults                   0      0
# root partition
UUID=c783a057-e114-41c5-842a-9c1a6ee1d6b9 /             ext4   defaults,errors=remount-ro 0      1
# atlantic
UUID=5c09cf51-6143-429b-a6b6-19ea81217148 /atlantic     ext3   defaults                   0      2
# pacific
UUID=f61abab2-264e-4837-818e-6d6957c01661 /pacific      ext3   defaults                   0      2
# north
UUID=ccf6f6cc-8d63-443b-a71f-2b3b20450a0c /north        ext3   defaults                   0      2
```

I think the reason UUIDs failed for you last time was that you had both the /dev/*** line AND the UUID line, causing the system to try and mount the same partition twice. UUIDs work fine in fstab, as illustrated by your swap partition's entry.

Oh, I removed your floppy line, because removable media should be detected and auto mounted by default in recent versions of Ubuntu. If you have issues, readd the line.
```

/dev/fd0                                  /media/floppy0 auto  rw,user,noauto,exec,utf8   0      0
```

---

### Post by monkblah on 2010-08-06
Thanks WorMzy! Your new fstab works! I just needed to slightly correct the 'swap' entry to set the mount point to 'none' and the options to 'sw'. See corrected version below.


```

$ cat /etc/fstab
# <file system>                           <mount point> <type> <options>                  <dump> <pass>
proc                                      /proc         proc   nodev,noexec,nosuid            0      0
# swap   -- was /dev/sdb5
UUID=8478a5ea-1bba-4df2-a598-f8d163c446db none          swap   sw                             0       0   #/dev/sda5
#UUID=8478a5ea-1bba-4df2-a598-f8d163c446db swap          sw     defaults                   0      0
# root partition  -- was /dev/sda1
UUID=c783a057-e114-41c5-842a-9c1a6ee1d6b9 /             ext4   defaults,errors=remount-ro     0      1
# atlantic -- was /dev/sdc1
UUID=5c09cf51-6143-429b-a6b6-19ea81217148 /atlantic     ext3   defaults                       0      2
# pacific  -- was /dev/sdc5
UUID=f61abab2-264e-4837-818e-6d6957c01661 /pacific      ext3   defaults                       0      2
# north -- was /dev/sdc6
UUID=ccf6f6cc-8d63-443b-a71f-2b3b20450a0c /north        ext3   defaults   

```

---

### Post by WorMzy on 2010-08-06
Ah, right you are. 

Glad it worked for you. Since UUIDs don't change (unless you force them to), you shouldn't encounter the problem any more. :)

---

