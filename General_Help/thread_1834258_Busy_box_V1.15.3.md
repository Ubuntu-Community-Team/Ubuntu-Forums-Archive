---
title: "Busy box V1.15.3"
date: 2011-08-27
forum: General Help
---

### Post by najim on 2011-08-27
Hello All,

I encounter a No init found Try passing init= bootarg error and as any one could i moved on to search how to fix this problem, well i have seen several threads but up not i have been unable to fix my issue, several of the threads i have seen have fixed this problem. i have tried out options such as fdisk -l, fsck and gparted all in vain i also landed on a boot info script which still can not even output the result in my case 

this is what i get when i run it on a live CD

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info/boot_info_script*.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 

The terminal hangs at this point and the result text file is not created, i think someone here has ever encountered the same, my machine has alot of data and softwares installed which i dont  want to loose what can i do to solve my problem, Am only running on Ubuntu Linux 10.10 and no other OS installed except the Sun Virtual box which runs Win XP on top of Linux 

Thanks in Advance.

---

### Post by najim on 2011-08-27
Please kindly refer to this thread [http://ubuntuforums.org/showthread.php?t=1834263](http://ubuntuforums.org/showthread.php?t=1834263)

---

