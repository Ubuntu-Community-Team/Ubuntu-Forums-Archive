---
title: "Mounting an external usb dvd/cd drive."
date: 2011-02-28
forum: General Help
---

### Post by DeviantGuy on 2011-02-28
I am the owner of a netbook (Namely, the Acer Aspire one.) With Ubuntu 10.10 netbook edition. I also own a External Usb CD drive. My question is, how do I mount it? K3B seems to find it. Sound juicer doesn't. Rhythm-Box doesn't. Suggestions?

---

### Post by blueridgedog on 2011-02-28
With it unplugged and then plugged in, what is the output of running the following each time:

```
sudo fdisk -l
```

---

### Post by DeviantGuy on 2011-02-28
The first command is when the drive was plugged in. The second one is when the drive was unplugged


personaluse@Aspire-One:~$ sudo fdisk -l
[sudo] password for personaluse: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241127424   83  Linux
/dev/sda2           30020       30402     3068929    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris
personaluse@Aspire-One:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241127424   83  Linux
/dev/sda2           30020       30402     3068929    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris
personaluse@Aspire-One:~$

---

### Post by blueridgedog on 2011-02-28
I think you used fdisk -1...it is hard to tell with the font that is used here...it is lower case L for "list"

---

