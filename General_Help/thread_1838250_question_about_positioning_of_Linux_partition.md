---
title: "question about positioning of Linux partition"
date: 2011-09-03
forum: General Help
---

### Post by texas.chef94 on 2011-09-03
My new notebook has some Linux incomparability even as evidenced by goggling. I have tried wubi as well as a dedicated partition for Ubuntu and eventually I end up having to go into recovery. My most recent effort as of 2 weeks ago was to position an extended, plus data partition, and 10.04 at the very bottom. So far I have had no difficulty and that is unusual based on my past difficulty. So simply stated does it make any difference where the Linux partition is located in terms of the windows partition.
Just for information this is a L675D which out of the box comes with 3 NTFS
partitions. I am merely curious

---

### Post by mike555 on 2011-09-03
If you open gparted and send us a screenshot we can help you better,   but sounds like your only choice is an extended partition with a / and a swap partition in it.

---

### Post by lmarmisa on 2011-09-03
If you get more difficulties running Ubuntu on your computer, consider to use a virtualization solution. I like VirtualBox:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Sin@Sin-Sacrifice on 2011-09-03
The only problem I could think of is that you can only have 4 primary partitions on a single hard drive (not sure if you can boot from an extended partition...). Not sure if that has anything to do with your issues or not. Otherwise it shouldn't matter.

---

### Post by Zimmer on 2011-09-03
Some reading might help you  understand the partitioning requirements a bit better.
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)


[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

It sounds like you have created an extended partition and installed Ubuntu on a Logical within it. If you installed GRUB to the MBR then you get a GRUB menu on boot to select your OS to boot with... no problem... as long as Windows has enough space in its own Primary partition to grow into with Windows updates etc...

---

