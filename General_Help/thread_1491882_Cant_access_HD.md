---
title: "Can\t access HD"
date: 2010-05-24
forum: General Help
---

### Post by Nidding on 2010-05-24
As I woke up this morning my laptop had went black screen. So I rebooted, or at least tried to. I can get to the grub screen, and choose either ubuntu or xp, but none of them seems to want to let me boot. I can run ubuntu through live cd, and here it seems to recognise the partitions on my HD, but access is very, very slow at least. What could be wrong?

---

### Post by rob-ward on 2010-05-24
When you say your hard disk seems to be running slowly when you mount it using the ubuntu live cd do you have a value for the speed?. Can you test the speed of the HDD to see what speed it is running using hdparm?.
```
sudo hdparm -tT /dev/YOURDRIVE
```

It could be that your HDD is failing although I would have thought you would have then either been able to boot an OS or not boot GRUB, it seems strange that you can have one not the other.

what does 
```
sudo fdisk -l
```

show you?

---

### Post by Nidding on 2010-05-24
> **rob-ward said:**
> When you say your hard disk seems to be running slowly when you mount it using the ubuntu live cd do you have a value for the speed?. Can you test the speed of the HDD to see what speed it is running using hdparm?.
```
sudo hdparm -tT /dev/YOURDRIVE
```

It could be that your HDD is failing although I would have thought you would have then either been able to boot an OS or not boot GRUB, it seems strange that you can have one not the other.

what does 
```
sudo fdisk -l
```

show you?
That`s kinda what`s bugging me as well. I`ve tried to do a clean install, but it tells me that there`s a problem with the HD. The  fdisk says
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9dbdbb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16414       17021     4883760    5  Extended
/dev/sda2            2433       16413   112302382+   b  W95 FAT32
/dev/sda3               1        2432    19535008+  83  Linux
/dev/sda4   *       17022       19457    19567170    c  W95 FAT32 (LBA)
/dev/sda5           16414       17021     4883728+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by rob-ward on 2010-05-24
what output do you get if you do
```
sudo hdparm -tT /dev/sda3

```
It should tell you the speed that your HDD is running at(ish)

However I would say that if you are having issues with your HDD and the Ubuntu installer is telling you that your HDD has problems then it might be worthwhile looking into getting a replacement as it could stop working at any time which is a pain if you have files that you need. A the very least it might be worthwhile backing up anything important onto a penstick or other HDD in case it does just stop working.

Unfortunetly I don't really know a way of debugging the HDD further to find out what the issue with it is(or definitely confirm it is the HDD and not something more serious), however if a new OS install isn't working and 2 OS's are failing to boot then it would appear to be serious.

---

