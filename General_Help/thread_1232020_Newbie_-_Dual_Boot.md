---
title: "Newbie - Dual Boot"
date: 2009-08-05
forum: General Help
---

### Post by dollisp_uk on 2009-08-05
Since getting an aspire a110 I have been dabbling in the Linux world for the first time.

I was really impressed with Ubuntu NBR with most things working straight out of the box.

I spent some time setting it up as I like it and installing all the programs that I will use on a daily basis and once I have done this took an image of the drive with partimage so I can restore in future which has worked fine.

Now my question is my brother has a a110 with XP installed on the only partition on the drive and would like this setting up as a dual boot.

Can I just split his windows partition in two (defrag first ?) and restore my image which is already configured onto the second partition ?

And if I can do that how do I set up the dual boot once its done ?

Any help would be greatly appriciated :D

---

### Post by Katalog on 2009-08-05
Check out the free [Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/index_main.html"). Covers every topic from paritioning to dual booting to common terminal commands. Very handy little download.

---

### Post by dollisp_uk on 2009-08-05
Thanks a bit of light readin for me :)

I think I more or less know what i'm doing with regards to re-partitioning the drive and restoring my image to it.

Boot from Ubuntu NBR usb stick
Resize the partition using Gparted
Format new partition to ext3
Use partimage to restore my backup to new ext3 partition

Thing i'm not sure about is how to set up the actual multiboot menu, thinking about it now would it need to be set up in windows as that is the primary OS ? or can something be done with GRUB ?

Hopefully i'm not way off here but I am trying to learn !!!

---

