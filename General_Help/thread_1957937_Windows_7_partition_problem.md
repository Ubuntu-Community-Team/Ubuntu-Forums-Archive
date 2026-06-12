---
title: "Windows 7 partition problem"
date: 2012-04-13
forum: General Help
---

### Post by adeee on 2012-04-13
Guys i have 320 gb hard and i want dual boot with ubuntu. unfortunately there is a problem. for install ubuntu as a separate i need to install windows first. so i tried to install windows7. but its accept only 4 partitions. 
One is reserved for windows something boot process but three are available for creating partitions. so i create 2 for 100 gb and 1 for 50 gb but there is still 50 gb space remains. so i tried to install ubuntu but even ubuntu can't make any new 50 gb partition so can u help me to make new partition. 
i tried to make partition from 10.10 ubuntu cd. and i also try 10.04 ubuntu cd for making partition. but nothing happen.

---

### Post by cryptotheslow on 2012-04-13
You will need to delete one of the partitions you have now and then create an extended partition filling the free disk space. Then you can create many new logical partitions inside the extended partition.

Ubuntu will be happy installing and running in a logical partition.

Before deleting any partition, make sure you have backed up any contents and be sure you know which one you are deleting.

---

### Post by oldfred on 2012-04-13
A default install of Windows 7 is a 100MB boot/repair (hidden) partition and the main install. The boot partition has to be a primary partition.

But if dual booting it is best not to write into the Windows 7 partition (read-only is ok) and create a separate NTFS shared data partition (d: drive in Windows). All the Linux partitions can be logical in the extended partition. Do not use Windows to create partitions as it may convert to dynamic which causes big problems, but use Windows only to resize its own partition if need be.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

