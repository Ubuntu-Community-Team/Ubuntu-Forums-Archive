---
title: "Partition"
date: 2011-05-27
forum: General Help
---

### Post by ezroller on 2011-05-27
Hey guys, I'm trying to install ubuntu 11.04 on a fresh hard drive for the 1st time. I created 4 partition: 1. /boot with 500 MB 2. SWAP 2GB 3. / 20GB and 4. /home of aprox 250GB. My problem is that in My Computer i have only 1 partition "File System" with 15GB free space. Am i doing something wrong?! Thank you for your help.

---

### Post by LordNeo on 2011-05-27
Boot and Swap i think are not shown in your total space, other than that it looks like your "home" partition is not automounted on start.

Please show us your fstab (from terminal type: cat /etc/fstab)

---

### Post by coffeecat on 2011-05-27
> **ezroller said:**
>  Am i doing something wrong?! 

No, you are not doing anything wrong. You are just conditioned by Windows ways of thinking. "File system" shows you just that. It can be contained in one root partition or spread over several partitions, each mounted into the file system. If you look in the /boot and /home folders you will see the contents of your boot and home partitions with no distinction because they are part of the filesystem.

To see your mounted partitions, either... Open a terminal, and:

```
df -h
```or 

```
mount
```Or, in the GUI... Open System Monitor > File Systems tab.

---

### Post by ezroller on 2011-05-27
yes, when i do df -h in termial it shows me that home partition is really 290 GB. Thanks alot now i can stay calm. I have been a Windows user all my life (21 now) but besides games, lately, all i see are downsides to it. I just hope linux can erase my "windows way of thinking" :) Thank you for your quick replies :)

---

### Post by LordNeo on 2011-05-27
Just for the sake of being sure, please open the Disk Usage analizer and check it shows the full size (/ plus /home)

---

