---
title: "Cloning One Partition in a Dual Boot - possible?"
date: 2010-10-16
forum: General Help
---

### Post by listerdl on 2010-10-16
Hi I have a dual boot and every program I try to clone the ubuntu partition seems to want to have the entire hard drive to clone to.

In other words, if I attach an external hard drive and select the ext4 Ubuntu Linux to clone to a purposefully made ext4 partition in an external drive - every program wants to copy to the entire external hard drive.

Any suggestions?

I think that clonezilla allows more freedom but I just dont quite get it - the options seem a little confusing in that I am worried that I will copy the partition back to my actual machine.

I am probably being a bit paranoid, but if anyone can think of a simple program that allows me to simply copy one partition to another purpose made (external) partition then please let me know!!

Thanks!

---

### Post by jonnymccullagh on 2010-10-16
I'm not sure I am fully following your line of thought as you intended but have you read anything about the 'dd' command?

For example, if you wanted to copy sda1(internal) to sdb3 (external) you could try:
dd if=/dev/sda1 of=/dev/sdb3
if meaning input file and of meaning output file. 
You would have to check the correct names for your partitions as you could easily get something wrong and blow your data away. Also the dd command has many other options but a bit of reading about th at command may help you.

---

### Post by listerdl on 2010-10-17
thanks for that - sounds like a nice simple plan.

I was relying on a GUI

---

### Post by Quackers on 2010-10-17
Clonezilla has done that for me.

---

