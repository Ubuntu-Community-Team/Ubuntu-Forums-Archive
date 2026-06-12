---
title: "Permissions and program compiling on another partition"
date: 2011-12-11
forum: General Help
---

### Post by Bobhuber on 2011-12-11
Hi all,
I've ordered an SSD drive and decided to start compiling my programs on another partition or in ram to conserve write cycles on the SSD drive. After setting up fstab to utilize the memory I have no problems compiling programs in the ram drive /run/shm (used to be /dev/shm)  and storing temp files in /tmp as a tmpfs. The problem I've encountered is in trying to move and extract the program files I want to compile into another partition that I mount on boot. I keep getting errors either on loading dependencies or /bin/sh : Permission Denied when trying to compile.Are there any special mount considerations to consider when mounting additional partitions in order to compile programs there?? I store and recover backups from the same partition with no problems. 
Mount options > /dev/disk/by-uuid/b79ecd38-e648-4024-ae75-50a9fd9f5ef7 /media/backup     ext4     noatime,user     0     2
I've got permissions set to 777 and me as owner of the partition so that shouldn't be the problem.

---

### Post by searchfgold6789 on 2011-12-11
Try adding the 'exec' option.

---

### Post by Bobhuber on 2011-12-11
> **searchfgold6789 said:**
> Try adding the 'exec' option.
Thanks

---

