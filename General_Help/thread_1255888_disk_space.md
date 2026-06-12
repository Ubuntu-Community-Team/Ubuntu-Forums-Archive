---
title: "disk space"
date: 2009-09-02
forum: General Help
---

### Post by Tadcrazio on 2009-09-02
I installed ubuntu on my vista rig, just did the automatic run side by side.. But now ubuntu wants me to install the updates and it says i dont have enough free space. how do i change it in the partition to allow me to have more space on the Ubuntu partition

---

### Post by nikhilk on 2009-09-02
> **Tadcrazio said:**
> I installed ubuntu on my vista rig, just did the automatic run side by side.. But now ubuntu wants me to install the updates and it says i dont have enough free space. how do i change it in the partition to allow me to have more space on the Ubuntu partition

To resize the relevant partitions on your machine use [GParted]("http://gparted.sourceforge.net/") live cd.

But first could give some more information about the partitions you have? For starters post back the output of
```
df -H
```

---

### Post by Tadcrazio on 2009-09-02
anthony@Tadcrazio-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5              2.5G   2.5G      0 100% /
tmpfs                  2.0G      0   2.0G   0% /lib/init/rw
varrun                 2.0G   107k   2.0G   1% /var/run
varlock                2.0G      0   2.0G   0% /var/lock
udev                   2.0G   160k   2.0G   1% /dev
tmpfs                  2.0G    78k   2.0G   1% /dev/shm
lrm                    2.0G   2.9M   2.0G   1% /lib/modules/2.6.28-11-generic/volatile

---

### Post by drs305 on 2009-09-02
I´m afraid you have run into a ´bug´ in Ubuntu´s installation process - you have a 2.3-2.5GB / partition, which is not large enough to support a normal Ubuntu installation.
 
I have written two guides about this problem and the ways to correct it. 

Here are two solutions:

Reinstall and make the partition larger:
[2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

Resize your existing / partition:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

Both will take about the same amount of time with normal download speeds.

The developers are working on a fix and I´m sorry this is your first experience with Ubuntu.

---

### Post by Tadcrazio on 2009-09-02
thank you

---

