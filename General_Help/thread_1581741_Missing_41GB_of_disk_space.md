---
title: "Missing 41GB of disk space"
date: 2010-09-25
forum: General Help
---

### Post by ronch79 on 2010-09-25
Hi. I've been using Ubuntu 10.04 since it came out and I was just wondering why 41GB of space is missing. You see, I did a complete repartition and reformat of my 320GB hard disk (already tried ext3 and ext4) and assigned 2GB for swap, 10GB for /, and 308GB for /home. Thing is, when I check the available disk space of, say, Videos or Documents (which, I understand, are contained in /home), only around 267GB of space is available. If I run the Disk Utility program it reports the capacities correctly (2GB, 10GB and 308GB). This didn't happen with Ubuntu 9.10. Where did my 41GB go and how can I get it back? I don't think it's accounted for by the differences in the way the OS counts bytes (powers of 2 or actual number of bytes), because 41GB is a big chunk of 308GB. Please help. Many thanks in advance.

---

### Post by luvshines on 2010-09-25
What does "df -h" command say ?

---

### Post by Elfy on 2010-09-25
Check all the trashes - including roots, [http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

Take into account the 5% which is kept by for root if the drive is full.

You can have a look at this - might help you - [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by ronch79 on 2010-09-27
Hi. df looks like this...

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             9843232   3077568   6265648  33% /
none                    993680       308    993372   1% /dev
none                    997904       100    997804   1% /dev/shm
none                    997904        84    997820   1% /var/run
none                    997904         0    997904   0% /var/lock
none                    997904         0    997904   0% /lib/init/rw
/dev/sda3            295852944 271834392   8990024  97% /home

I understand that my 320GB hard disk, the way WD counts it, is around 320,000,000,000 bytes. 320,000,000,000 / 1024 / 1024 / 1024 = 298GB as Ubuntu counts it. I allocated 308GB out of 320GB during setup, so 308 / 320 * 298 should be 286.8GB, but Ubuntu says only 267.6 of that is available.  Also, these look like actual byte counts. If 308GB (real byte count?) was allocated to /home, why is it that only 302,953,414.656 (295,852,944 * 1024) has been allocated? I may be missing something here...

Many thanks, fellas.

---

### Post by amauk on 2010-09-27
/dev/sda1 is not listed

do you by any chance have a 40Gb partition with another OS on?

---

### Post by ronch79 on 2010-09-27
Hi Amauk, my partitions are 2GB for swap, 10GB for /, and 308GB for /home. I reckon these are actual byte counts, not the powers of 2 way of counting.

---

