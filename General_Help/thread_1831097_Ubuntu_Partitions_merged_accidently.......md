---
title: "Ubuntu Partitions merged accidently......?"
date: 2011-08-22
forum: General Help
---

### Post by vkvashistha on 2011-08-22
The problem occur when I was repairing Master Boot Records of "Windows Server 2008 R2". Windows Repairing Disk have utility, which changes the partition table entries, during startup repair (if required).
Now my Windows server is working, but when I tried to reinstall Grub2, to repair Ubuntu 10.10, startup, I ran fdisk utility as follows:-

$fdisk -l

/dev/sda7               52 GB
.....................
....................

My "/dev/sda7" was actually 20 GB  "/home"   partition   and 30 GB for "/root" Ubuntu installation. and 2GB for "/swap" partition.
But now all get merged. When I further checked from "Disk Utiliy" program (pre installed in ubuntu 10.10), it shows 52GB extended partition free and unmounted.

I've very critical data in my "/home" partition. I don't much care about "/root". 

So is there any way that I can recreate the partition table without loosing my data. Or should I use any "Data Recovery" program to recover it, if yes, which program is best?.......Any other suggestions if you have are also appreciated.......
Thank you

---

