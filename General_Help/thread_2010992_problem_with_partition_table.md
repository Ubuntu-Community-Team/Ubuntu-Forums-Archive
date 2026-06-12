---
title: "problem with partition table"
date: 2012-06-26
forum: General Help
---

### Post by varu038 on 2012-06-26
Hello guys,

I am in big mess.

Here is my output of command 
sudo sfdisk -d /dev/sda

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

I have actually 4 partitions in first I had windows and then ubuntu and  swap and then 2 ntfs partions in which i have around 500GB of data that i  cannot afford to lose.

Currently i am using live ubuntu cd to post this comment.
If i use Disk utility tool check my partitions I am able to see all the partitions but when i try to install the whole partition is coming as one big partion. even if i use Gparted to check my partitions i cannot see th 4 partitions i mentioned above it shows the whole harddisk as one big 1TB partition.

and one more thing i am afraid that if i reboot my system as in i switch off and reboot the PC using live ubuntu as i dont have any operating system running both the os are messed up i ll not see the partitions. is it the case or i will be able see my partitions .?

Please help.

---

### Post by howefield on 2012-07-01
Thread moved to "*General Help*" forum.

---

### Post by oldfred on 2012-07-01
Welcome to forums.

I do not understand why Disk Utility would show partitions if sfdisk does not. 

Post this also 

sudo fdisk -lu

---

