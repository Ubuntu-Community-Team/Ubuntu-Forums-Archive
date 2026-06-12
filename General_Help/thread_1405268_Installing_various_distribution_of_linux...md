---
title: "Installing various distribution of linux.."
date: 2010-02-12
forum: General Help
---

### Post by karthick87 on 2010-02-12
Windows users used to install different releases of OS in different partitions in a single hardrive such as they will install **Windows XP** and **Windows 7** or watever they need..Like that is it possible to install another linux distribution???For example already i am using **Ubuntu 9.04  **andnow i like to install **Fedora** or some other linux distribution,is that possible??If so how to do it??

---

### Post by jken146 on 2010-02-12
Yes, you can do exactly the same thing with multiple OSs of any kind (Windows, Linux, BSD, ...).

To edit the partitions on your hard disk(s), use gparted:
```
sudo apt-get install gparted
```
Be very careful when working on partitions, as you risk losing data. It is good practice to back up what you are not prepared to lose.

Also bear in mind that you can have a maximum of four primary partitions on any one disk (although you can have many logical partitions within an extended partition). That'll become clear when you look at gparted.

Then just go ahead and install another OS. Be aware of bootloaders (usually [GRUB]("https://help.ubuntu.com/community/GrubHowto")).

---

### Post by 311005901 on 2010-02-12
Hello getyourkarthick!
If you don't want to mess with a ton of resizing, partitioning, and backups, give [VirtualBox]("http://www.virtualbox.org/wiki/Linux_Downloads") a try. You can still run your native desktop OS, but run another OS without moving files. :)

---

### Post by karthick87 on 2010-02-12
Sorry to ask silly question,i am a beginner..Can you give me some more information..What is the difference between primary partition,Extended partition and Logical Partitions???

---

### Post by oldfred on 2010-02-12
MBR systems can have only 4 primary partitions. When that became not enough they modified it to allow one primary to be converted to an extended which is just a container for many logical partitions.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by hissyfut on 2010-02-13
> **oldfred said:**
> MBR systems can have only 4 primary partitions. When that became not enough they modified it to allow one primary to be converted to an extended which is just a container for many logical partitions.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)


hermans grub2 pages say that grub 1.97 is grub2. karmic has 1.97 and uses no grub.cfg. why is this? in fact his grub2 info looks more complicated.

btw the 145 rocks.

---

### Post by jken146 on 2010-02-13
> **hissyfut said:**
> hermans grub2 pages say that grub 1.97 is grub2. karmic has 1.97 and uses no grub.cfg. why is this? in fact his grub2 info looks more complicated.

btw the 145 rocks.

karmic *does* have /boot/grub/grub.cfg

---

### Post by hissyfut on 2010-02-13
> **jken146 said:**
> karmic *does* have /boot/grub/grub.cfg

yep, noticed it was from upgrade and does not upgrade to grub 2

---

