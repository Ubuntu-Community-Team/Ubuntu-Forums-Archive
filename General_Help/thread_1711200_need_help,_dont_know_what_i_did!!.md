---
title: "need help, dont know what i did!!"
date: 2011-03-21
forum: General Help
---

### Post by delux0 on 2011-03-21
Hi, so here are the details:  I originally had 500gb  for windows 7 and today i decided to intall ubuntu 10.10 so i did.  I did so following the instructions that are on the website thinking that clicking "install along side other operating system" would automatically format my drive and dual boot ubuntu and windows 7 so i allocated 120gb to ubuntu and went on with the installation.  Now, after the installation I cant figure out how to get back into windows 7.  So i am asking...did i screw up? and have to reinstall windows again?? or am i just not booting into windows correctly?  Please help me out!!  

Thanks

---

### Post by idoitprone on 2011-03-21
let see if the the windows 7 partition is still there

```
sudo fdisk -l
```

---

### Post by Sef on 2011-03-21
So you let Ubuntu partition your hard disk?  How big is it?

---

### Post by delux0 on 2011-03-21
its a 500gb harddrive and i partition ubuntu to 120gb.  Its was a fresh-install of windows 7 anyways so im not losing files, but i still would have to go through all of that updating processes and stuff; still hoping its there.

from sudo fdisk -l dont know what this means:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000088a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59675   479337472   83  Linux
/dev/sda2           59676       60802     9046017    5  Extended
/dev/sda5           59676       60802     9046016   82  Linux swap / Solaris

---

### Post by idoitprone on 2011-03-21
All it does is list your partition table. Yes i understand the man pages and usage are only friendly to those to know what it does. I just use fdisk to print the table. Thats all. If it still there lets hope it get fix simply by

```
sudo update-grub
```

If it does work there will be other problems d'oh

it should look something like this

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa144c1a2

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sda1   *           1         154     1228800    7  HPFS/NTFS
[/B]Partition 1 does not end on cylinder boundary.
/dev/sda2             154       31895   254962688    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           37639       38914    10240000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           31895       37639    46136321    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           31895       32417     4194304   82  Linux swap / Solaris
/dev/sda6           32417       35028    20971520   83  Linux
/dev/sda7           35028       37639    20968448   83  Linux


it looks bad ur sda1 is not ntfs. Windows does not have any support for linux file systems. So it looks like you have to reinstall

---

### Post by delux0 on 2011-03-21
ok, looks like i will have to wipe everything and do fresh windows....suggestions??  Can someone send me the best/easiest guide on how to do what i wanted to do in the first place which was partition by drive to 120gb dual boot with windows 7?  I guess i dont know how :(

---

### Post by idoitprone on 2011-03-21
> **delux0 said:**
> ok, looks like i will have to wipe everything and do fresh windows....suggestions??  Can someone send me the best/easiest guide on how to do what i wanted to do in the first place which was partition by drive to 120gb dual boot with windows 7?  I guess i dont know how :(

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
hope that helps? btw it seems that the installer reformated the windows partition into ext whatever. It has to be ntfs which is windows

btw i forgot to mention the other function of fdisk is meant for partitioning so dont use it unless u know what ur doing

next time use gparted - very good gui i love it

---

### Post by delux0 on 2011-03-21
ok, so let me re-confirm this so I dont mess up AGAIN!!  I am currently re-installing windows 7.  once i do should i then instert the ubuntu cd and when i get to the 3 install choices do i choose "Manually edit partition table" and partition the disk that way...OR do i go through windows disk management and partition through that??

---

### Post by idoitprone on 2011-03-21
> **delux0 said:**
> ok, so let me re-confirm this so I dont mess up AGAIN!!  I am currently re-installing windows 7.  once i do should i then instert the ubuntu cd and when i get to the 3 install choices do i choose "Manually edit partition table" and partition the disk that way...OR do i go through windows disk management and partition through that??

Better to pre-partition the disk before you install, less likely to make an mistake. When you do install, all you have to choose is the correct partition and press next.

hey i'm idoit prone i corrupted a few partition lol

---

### Post by delux0 on 2011-03-21
how do i partition before installation of windows?

What would 120gb be for mb??

---

### Post by idoitprone on 2011-03-21
> **delux0 said:**
> how do i partition before installation of windows?

get a live ubuntu cd and use a partition utility like gparted

---

### Post by delux0 on 2011-03-21
Iam on my way....currently installing windows 7!!!

BTW, i used the windows partition utility when i put the windows 7 disk in....is that ok??

---

### Post by idoitprone on 2011-03-21
> **delux0 said:**
> Iam on my way....currently installing windows 7!!!

BTW, i used the windows partition utility when i put the windows 7 disk in....is that ok??

sure i guess a partition utility for for any operating system. When you install ubuntu you will have to reformat that partition to file system like ext4. It does not matter since its a really easy thing to do. As long as you dont disturb windows. try not to touch it, since windows is like a child it like being first and irrate others. btw dynamic disk are evil

---

### Post by delux0 on 2011-03-21
ok,  ill keep that in mind!! So inorder to do that, when im installing ubuntu do i choose the "specifiy partitions manually" and format the partition through that?

---

### Post by idoitprone on 2011-03-21
> **delux0 said:**
> ok,  ill keep that in mind!! So inorder to do that, when im installing ubuntu do i choose the "specifiy partitions manually" and format the partition through that?

like i said try to prepartition-like seperating swap and home and root try to use logical partition since there is a 4 partition limit-your hardrive before installing. So it is a basic filesystem change and yes specifiy partition manually, since your dual booting

to understand logical partition you should google the problem, too lazy to explain.

---

