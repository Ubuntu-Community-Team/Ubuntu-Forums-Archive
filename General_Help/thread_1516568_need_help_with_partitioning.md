---
title: "need help with partitioning"
date: 2010-06-23
forum: General Help
---

### Post by insomniac otaku on 2010-06-23
im running ubuntu 10.04 now and have been trying to create a partition so that I can dual boot between ubuntu and backtrack,  but i cant  figure out how to do this. when i start gparted it searches for /dev/sda/ or somthing and the it just goes away i read somthing about a gparted menu but i cant find it nevermind. i dont know what im talking about:confused:
if someone could point me in the right direction I WILL BE YOUR SLAVE (not really)but please post a link or something im new to using computers and my head is going to EXPLODE!!  if anyone can help or point out possible mistakes i made please do so

---

### Post by Smart Viking on 2010-06-23
You should boot with a live CD to partition the hard disk, boot from a live cd, go into gparted and partition there. I am sorry if i misunderstood and that is what you did. :)

---

### Post by SoFl W on 2010-06-23
Was just looking at this earlier... **[Partitioning basics]("http://ubuntuforums.org/showthread.php?t=282018")**

also...[check out]("http://linuxplanet.com/linuxplanet/tutorials/3174/1/")

---

### Post by lordskid on 2010-06-23
Try checking the disks for errors. Also try reinstalling gparted.

---

### Post by garvinrick4 on 2010-06-24
Use the Ubuntu install Cd and pick Try Ubuntu and go to gparted and make
your partitions there. You cannot partition a mounted drive and if you are running Ubuntu and only have one install of it, it is mounted.

---

### Post by pxr on 2010-06-24
First need to know what partitions and/or free space you've got, in a terminal type

sudo fdisk -l /dev/sd*


and post the output

---

### Post by wilee-nilee on 2010-06-24
> **pxr said:**
> First need to know what partitions and/or free space you've got, in a terminal type

sudo fdisk -l /dev/sd*


and post the output

This 
and make sure backtrack is using the same Grub version, unless you know how to fix any possible problems that may arise.

---

