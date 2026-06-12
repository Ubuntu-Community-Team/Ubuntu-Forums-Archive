---
title: "increasing ubuntu's disk space on windows 7 machine"
date: 2010-08-14
forum: General Help
---

### Post by Zimbobo on 2010-08-14
Hello,

I have installed ubuntu on  my windows 7 machine. I am very happy with ubuntu and want to do more with it, but I have only about 20GB of 300GB for ubuntu. What is the best way to increase disk space for ubuntu. Can I start from CD again and install over it so to speak? Should I un-install ubuntu (what's the best way for that?) and start all over? I would be happy with that too, I have a backup of my stuff, I just want to make sure I don't mess anything up. Thanks a lot in advance.

---

### Post by drs305 on 2010-08-14
Take a look at this post I wrote for resizing an Ubuntu system partition. It was in response to a bug but the second half of the first post provides tips and recommendations.

[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

If you would rather reinstall, which can be just as fast or faster than repartitioning if you don't mind losing any Ubuntu customizations, I'd recommend making your new partition first, then use the manual partitioning option during the installation.

---

### Post by oldfred on 2010-08-14
Welcome to the forums. Yes you can just start over if you like. But use windows tools to shrink the win7 partition and reboot several times to make sure it is ok with its new size. It usually wants to run chkdsk or other repairs after shrinking. Then you can use gparted to create partitions before hand and manual install or just delete existing partitions and install to largest free space.

I prefer manual install as when you create partitions in advance you can also easily set up /home.

Depending on how many primary partitions you have used:


1. 10-20 GB Mountpoint / primary (or logical) beginning ext4(or ext3)
2. all of the space remaining that you want to use but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

All the partitions can be logical if you only have one primary left after deleting your current Ubuntu.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions")
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I also like to have another partition for shared data as NTFS. Then you do not have to write into the windows partition. Ubuntu can and usually it is ok, but sometimes windows does not like too much of someone else writing into its system partition. Even windows only users often suggest a separate data partition so when you have to reinstall windows you do not loose all your data.

---

