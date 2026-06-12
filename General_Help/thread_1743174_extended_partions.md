---
title: "extended partions"
date: 2011-04-29
forum: General Help
---

### Post by Kwilson126 on 2011-04-29
I need to create several partitions and  several mounting location i.e. /, home, etc).
I am trying to create extended partition (using gparted and/or disk utility) and though the flip box on gparted shows extended, I can't choose it.  i only get primary options.
as of now, I have a primary and one extended partition that was created when installing ubuntu.
 
I have tried creating a primary and then going back and trying to break it into extended partitions.  I have also tried creating the remaining (unallocated partition) into a primary...but I am sure there is a step I am missing.
 
any suggestions as to the step(s) I am missing?

---

### Post by indytim on 2011-04-29
Within GParted, click on your extended partition, then create a new partition **within** the extended partition.

IndyTim / DataMan

---

### Post by indytim on 2011-04-29
I just re-read your post.  While booted to GParted:

1. From unallocated space on your hard drive, create an extended partition.  This comes after your already created partitions.  Click the apply button.

2.  Now select (by clicking) the extended partition.  Now you will create your new partition within the extended partition as a logical partition.  Click apply again.

Repeat #2 for each additional partition desired.

IndyTim / DataMan

---

### Post by wilee-nilee on 2011-04-29
> **Kwilson126 said:**
> I need to create several partitions and  several mounting location i.e. /, home, etc).
I am trying to create extended partition (using gparted and/or disk utility) and though the flip box on gparted shows extended, I can't choose it.  i only get primary options.
as of now, I have a primary and one extended partition that was created when installing ubuntu.
 
I have tried creating a primary and then going back and trying to break it into extended partitions.  I have also tried creating the remaining (unallocated partition) into a primary...but I am sure there is a step I am missing.
 
any suggestions as to the step(s) I am missing?

You can only have **one** extended partition on a single hd, and a additional 3 primaries, at the most. Post a screen shot of gparted and we can get you set up.

---

### Post by Kwilson126 on 2011-04-29
thanks for the extended partition help...
I figured out some of the partioning and with your help, managed to begin working on logical paritons...
 
still have an issue though.  i need to establish where the new partitions are mounted including root (/), /home, /future,  & /use.  i tried doing this through fdisk and it got ugly.  
 
through command line, I typed in fdisk -t  ext4 /dev sda6 /
 
in gparted, i showed / (root), but the partition was black and it wouldn't let me do anything, including delete.  I rebooted and it let me delete the partiions I put in.
 
i still need to establish where each mount point is for the partioons mentioned.
 
thanks for your help!
 
Kwilson126

---

### Post by wilee-nilee on 2011-04-29
> **Kwilson126 said:**
> thanks for the extended partition help...
I figured out some of the partioning and with your help, managed to begin working on logical paritons...
 
still have an issue though.  i need to establish where the new partitions are mounted including root (/), /home, /future,  & /use.  i tried doing this through fdisk and it got ugly.  
 
through command line, I typed in fdisk -t  ext4 /dev sda6 /
 
in gparted, i showed / (root), but the partition was black and it wouldn't let me do anything, including delete.  I rebooted and it let me delete the partiions I put in.
 
i still need to establish where each mount point is for the partioons mentioned.
 
thanks for your help!
 
Kwilson126

Are turning off the swap when your using gparted and is this a live cd of gparted or a distro your using? 

The problem here is that it is rather difficult to understand your set up without a picture. You also don't really fully explain what is going on. Are you making a new separate home, to transfer the one in a OS now, what are you actually trying to achieve here, in a complete full explanation and a picture of gparted.

If you trying to get auto mounts of partitions you need to edit the fstab probably but, it is hard to tell what is going on.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Be careful here wrong notations in fstab can brick your setup to the point of having to edit the fstab from a command line from recovery if you get that far, or chrooting in from a live cd.

---

