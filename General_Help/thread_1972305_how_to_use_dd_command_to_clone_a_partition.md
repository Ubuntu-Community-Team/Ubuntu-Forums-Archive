---
title: "how to use dd command to clone a partition?"
date: 2012-05-03
forum: General Help
---

### Post by PheniX01 on 2012-05-03
My english is terribly poor, I hope you understand what I mean :(

Since my old 1TB hard disk is nearly dead, so I bought a brand new one of 2TB.
The both of two hard disks have only one partition.
I want to copy all data in the old hard disk to the new one, but the copying speed is very slow due to the corruption.
I then tried the dd command and it can still read the old hard disk very fast.
So I decide using dd to backup my data.
But I found that if I use dd to clone a partition, not only the data is copied to the new partition, even the properties is.
For example, if I have two following partitions:
1. label: aaa /dev/sda1 1TB
2. label: bbb /dev/sda2 2TB
If I enter the command "sudo dd if=/dev/sda1 of=/dev/sda2",then I get the following result:
1. label: aaa /dev/sda1 1TB
2. lable: aaa /dev/sda2 1TB (actually, the partition still occupy 2TB, but only 1TB can be used)
That's not good. Though I backup my data successfully, but the volume of new partition is shrinked.
I wonder is there any way to backup my data using dd without changing the properties of the new partition?
many thanks

---

### Post by makitso on 2012-05-03
You can clone a complete drive, dd if=/dev/sda of=/dev/sdb bs=1M 
You can also clone a partition which you described.  However, as noted, the destination partition will be the same size 1TB.  You will need to use gparted to expand the partition to a full 2TB.
I use luckybackup to backup individual files from one disk to the other.

---

### Post by PheniX01 on 2012-05-03
> **makitso said:**
> You can clone a complete drive, dd if=/dev/sda of=/dev/sdb bs=1M 
You can also clone a partition which you described.  However, as noted, the destination partition will be the same size 1TB.  You will need to use gparted to expand the partition to a full 2TB.
I use luckybackup to backup individual files from one disk to the other.


Thanks for your help.
You mean that I should create a 1TB partition in the new hard disk, clone the old partition to it using dd and then expand it to 2TB?

---

### Post by oldfred on 2012-05-03
Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)


dd is an exact to exact copy. It is working bit by bit so you cannot copy from smaller to larger. If you want to do that you can use rsync. You should be able to expand after you copy with dd. 

Are you planning on keeping old 1TB drive plugged in? If so you will have issues as with dd it copies the UUID also and you cannot have duplicate UUIDs in system.

If you copy with rsync all your data is copied, but you have to update fstab & grub to use new UUIDs.

---

