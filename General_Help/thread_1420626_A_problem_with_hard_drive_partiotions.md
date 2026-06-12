---
title: "A problem with hard drive partiotions"
date: 2010-03-03
forum: General Help
---

### Post by sudhanshu1990 on 2010-03-03
Hello there, 
Yesterday I installed ubuntu 9.10 in my laptop removing windows 7 and since then I am facing a lot of problems some of them are listed below

1. During Installation I formatted my C:sad:20 gb) to ext4 but still it kept on asking for extra swap space,Accidently I gave my whole 40 gb partition as swap space.
2. Later it installed sucessfully and I tried to reduce the swap space from the disk utility provided, I was able to devide the swap partition into two parts one 4gb for swap and another 36gb.
3. The serious problem i am facing is that I am not able to use that 36 gb space, disk utility shows it as unallocated space but when I tried to format it, Disk utility shows some error(Ms dosmagic found something..) I tried with fdsk -l n but says no read sector available.
I am new to ubuntu so can someone help me here...
[IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG] [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8903788")   [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by ratcheer on 2010-03-03
You probably need to start over from scratch. I would reset the partition table of the disk, then create a swap partition that is about as much as your machine has RAM (or 1GB, whichever is smaller), then a 20 GB root partition, and finally the rest of the disk space as /home. You can do this from the Ubuntu LiveCD.

Note that this procedure will destroy anything you currently have on your disk, so don't do it unless you really mean to.

Tim

---

### Post by jsriz on 2010-03-03
If you already have 4 primary partitions then do as ratcheer said cos it would be better.
Else try gparted to create a new partition out of this and post any errors that might popup..:P

---

