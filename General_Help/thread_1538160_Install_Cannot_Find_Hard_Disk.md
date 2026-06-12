---
title: "Install Cannot Find Hard Disk"
date: 2010-07-24
forum: General Help
---

### Post by Noah's Ark on 2010-07-24
**Dear Friends:**
 



 I am experiencing some difficulty in installing Ubuntu on a new desktop computer I just built.  I have been reading the Ubuntu help files and posts, and this seems to be a problem that others have also experienced.  However, none of the solution methods that have been successful for others, have worked for me. 





 The problem that I am experiencing is during Ubuntu installation, the installation does not recognize my hard disk, and cannot seem to find the partition that I have created for installing Ubuntu alongside Windows 7.
 

 **My setup is:**
 Motherboard: ASRock X58 Extreme 3
 CPU: I-7 930
 Hard Disk: Hitachi SATA Deskstar 1TB
 

 **What I have tried so far:**
 Tried also installation using older versions of Ubuntu (9.10, 9.10 Server)
 Tried each of the above from both the live disk, and directly.
 Tried each of the above after disabling dmraid.
 Tried changing CMOS configurations from IDE.
 Tried switching the SATA plug on my motherboard to another SATA 6 port.
 

 **What I currently suspect, but have no solution for:**
 Some of the other posts have found success to this predicament by temporarily plugging their SATA plug into the SATA3 port on their motherboard to facilitate installation.  I however have only SATA 6 ports on motherboard.   
 

 Any suggestions?

---

### Post by geoffjay on 2010-07-24
In the live CD can you see the disk using fdisk?

Is this the only HDD you have installed? I've had problems with the standard installation only being able to see a single drive but if you use the alternative CD you can see all drives there.

---

### Post by Noah's Ark on 2010-07-25
Using fdisk I cannot see the hard drive.  I also tried the same using each of the available options such as "-a".

There is only one hard disk, and no supplementals.

---

### Post by cascade9 on 2010-07-25
> **Noah's Ark said:**
> **My setup is:**
 Motherboard: ASRock X58 Extreme 3
 CPU: I-7 930
 Hard Disk: Hitachi SATA Deskstar 1TB
 

 **What I have tried so far:**
 Tried also installation using older versions of Ubuntu (9.10, 9.10 Server)
 Tried each of the above from both the live disk, and directly.
 Tried each of the above after disabling dmraid.
 Tried changing CMOS configurations from IDE.
 Tried switching the SATA plug on my motherboard to another SATA 6 port.
 

 **What I currently suspect, but have no solution for:**
 Some of the other posts have found success to this predicament by temporarily plugging their SATA plug into the SATA3 port on their motherboard to facilitate installation.  I however have only SATA 6 ports on motherboard.   
 

 Any suggestions?

You should have 2xSATAIII ports (6Gbit/sec) and 6SATAII (3GBit/sec) ports. 

[http://www.asrock.com/mb/overview.asp?Model=X58%20Extreme3&cat=Specifications](http://www.asrock.com/mb/overview.asp?Model=X58%20Extreme3&cat=Specifications)

The reason why you cant see the HDD attached to the SATAIII port is because it is controled by a Marvell SE9128 RAID controller. I dont known if there is even a driver for that controller for linux, and even if there is.....its not worth it. Running  a SATAII HDD on SATAIII ports wont make it any quicker. 

Try attaching the HDD to the SATAII ports, it should work then.

---

### Post by Noah's Ark on 2010-07-26
Cascade9, you are very cool!

I didn't know that I had those ports on my motherboard, but sure enough, I pulled out the manual, and they were there.  It totally corrected the problem!

Thanks much

---

### Post by cascade9 on 2010-07-26
Glad it helped ;)

---

