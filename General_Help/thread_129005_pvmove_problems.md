---
title: "pvmove problems"
date: 2006-02-12
forum: General Help
---

### Post by ajoh on 2006-02-12
I am completely new to linux, however  I have managed to get a simply LVM up and running. However, one of my hardrives is starting to report bad sectors, so it has to go. In trying to do the pvmove operation to distribute the data on the drive to the rest of the LVM partition, I encounter the following error:

 mirror: Required device-mapper target(s) not detected in your kernel

I searched but all I found was reference to recompiling the kernel to include 'device mapper'. I have no idea how to go about this and have never compiled a kernel before.

I have made almost no changes to the stock 4.10 install.

Help is greatly appreciated. Thanks.

---

### Post by testingaccount on 2006-10-12
root@ubuntu:/home/ubuntu# pvmove /dev/hdd3
  mirror: Required device-mapper target(s) not detected in your kernel
root@ubuntu:/home/ubuntu# ls /dev/mapper/
casper-cow  casper-snapshot  control  lvmgroup0-lvm0
root@ubuntu:/home/ubuntu# modprobe dm-mirror
root@ubuntu:/home/ubuntu# pvmove /dev/hdd3
  /dev/hdd3: Moved: 3.2%
  /dev/hdd3: Moved: 6.2%
  /dev/hdd3: Moved: 9.2%
  /dev/hdd3: Moved: 12.0%
  /dev/hdd3: Moved: 14.8%


:-)

---

