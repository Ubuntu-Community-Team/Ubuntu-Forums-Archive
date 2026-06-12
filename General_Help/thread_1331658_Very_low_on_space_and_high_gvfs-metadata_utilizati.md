---
title: "Very low on space and high gvfs-metadata utilization"
date: 2009-11-19
forum: General Help
---

### Post by pigphish on 2009-11-19
I am not sure if they are connected but I am missing some hard drive space. 

When i run df -h I am missing space:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             211G  201G  1.5G 100% /

Where is the 10G difference between size and used it reports? I am unable to locate it. Everytime I free space it slowly gets eaten up. 

Any ideas?

Thanks, George

---

### Post by philinux on 2009-11-19
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by nicoseb on 2010-01-09
> **pigphish said:**
> I am not sure if they are connected but I am missing some hard drive space. 

When i run df -h I am missing space:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             211G  201G  1.5G 100% /

Where is the 10G difference between size and used it reports? I am unable to locate it. Everytime I free space it slowly gets eaten up. 

Any ideas?

Thanks, George

I have been experiencing exactly the same thing for a few days. After filling totally the space with a program output, I moved a large file to another partition. Finished running my program and then 2G just disappeared.
I found that same file than you and just deleted it... that gives me some free space, but my 2G are still missing!

Did you find a solution?
Thank you

---

### Post by zeropointer on 2010-01-12
I'm having the same problem, I seem to be missing 10Gb of disk space.

  I've gone through  [https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
  and haven't found a solution.

I found a 3.5Gb file in the gvfs-metadata and deleted but that doesn't solve the missing 10Gb disk space problem.

---

### Post by rnerwein on 2010-01-12
> **pigphish said:**
> I am not sure if they are connected but I am missing some hard drive space. 

When i run df -h I am missing space:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             211G  201G  1.5G 100% /

Where is the 10G difference between size and used it reports? I am unable to locate it. Everytime I free space it slowly gets eaten up. 

Any ideas?

Thanks, George

hi
the 10 gb (5 % of 200 gb) are the default reseverd part when the filesystem is created. this is due to prevent deamonds of runing out of freespace when they are doing their logging jobs on critical events. you can change it to 1% i think. but don't set it to zero because that's your root partition.
use tune2fs -m  (see man tune2fs for more information)
ciao
:D

---

### Post by Ivan.Calderon on 2010-02-26
> **pigphish said:**
> I am not sure if they are connected but I am missing some hard drive space. 

When i run df -h I am missing space:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             211G  201G  1.5G 100% /

Where is the 10G difference between size and used it reports? I am unable to locate it. Everytime I free space it slowly gets eaten up. 

Any ideas?

Thanks, George
Look inside this dir
/home/<user>/.local/share/gvfs-metadata

---

