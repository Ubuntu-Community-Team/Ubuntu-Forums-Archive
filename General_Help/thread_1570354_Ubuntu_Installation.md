---
title: "Ubuntu Installation"
date: 2010-09-08
forum: General Help
---

### Post by mohdshahnawaz on 2010-09-08
I have a CD of Ubuntu 9.0 
Please guide me what is the standard procedure to install Ubuntu on my PC. 
I have 2 PCs. I want to create partitions in 1 PC and 1 PC without partition. 
Please help me what steps should i talk while selecting entire disk or manually partition.

---

### Post by sikander3786 on 2010-09-08
You said "CD of Ubuntu 9.0" I'm assuming that it is "9.10". So you can stay with it if you want to or download the latest 10.04.1 from [http://www.ubuntu.com](http://www.ubuntu.com) in order to use the latest and in my opinion, better software.

Is there any data you want to save? How much data is there on both of the HDDs? How are they partitioned and do you want to dual boot or simply install Ubuntu only?

I'll recommend that you go through the following link before posting back.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by mohdshahnawaz on 2010-09-09
Thanks for your interest. 
I have created backup of both the hard drives in DVDs. so there is no data on hard disks which i want to save. 
My original problem is that earlier i installed ubuntu on my systems but it was not working good. sometimes i used to lost my word document due to power failure. I mean, if the file is on and certainly the power of the system is off, the file used to be converted into zero kb including backup files. 
But now i want to be confident with the installation system before going back for ubuntu. 
So i just need the complete steps for creating partitions during installation and installing on entire disk. 
Please help.......

---

### Post by giddyup306 on 2010-09-09
There's an extremely detailed tutorial in my signature.  I used Mint, but the instructions will be thew same.

---

### Post by sikander3786 on 2010-09-09
The simplest partitioning setup is of course to select "Erase and use the entire disk". It will delete all partitions, create a single root partition and format the drive automatically. No hassle there.

Still if you want to start with a little advanced setup, here is what you can do.

512MB > Primary Partition > ext3 > Flagged Boot

10GB (or whatever size) > Primary Partition > ext3/ext4 > Flagged / (root)

Optional: "Whatever size you want" > Primary/Logical Partition > ext3/ext4 > Flagged /home

(RAM X 2)GB > Logical Partition > Swap > Flagged Swap


You can specify a separate /home partition or if you don't want to, just expand the size of / partition according to your needs. In that case /home will be on the same partition as root.

You can have a much more advanced setup. This is the one I use and recommend.

---

