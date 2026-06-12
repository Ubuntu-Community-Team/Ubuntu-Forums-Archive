---
title: "Drive cloning software?"
date: 2011-06-07
forum: General Help
---

### Post by ssteve60 on 2011-06-07
I use Back In Time but nowhere does it mention full disaster recovery and restore that I've found.
I'd like to know if drive cloning software exists for Ubuntu home users in the vein of Norton Ghost.
I just went through the process of installing Ubuntu from a 10.04 ISO and upgrading several times to Natty. The reason I had to do that is that Java does not work in some websites on later versions and I haven't been able to get it to work. However, the early version works well even after upgrading to Natty. 
I'd like to be able to clone the disk so that when disaster happens again, I don't have to go through a several-day ordeal and the options online seem to be a horrendous price because they cater to business. Any suggestions or am I just reading the Back In Time manual incorrectly?

---

### Post by howefield on 2011-06-07
Clonezilla.

> What is Clonezilla?
You're probably familiar with the popular proprietary commercial package Norton Ghost®. The problem with these kind of software packages is that it takes a lot of time to massively clone systems to many computers. You've probably also heard of Symantec's solution to this problem, Symantec Ghost Corporate Edition® with multicasting. Well, now there is an OpenSource clone system (OCS) solution called Clonezilla with unicasting and multicasting!
Clonezilla, based on DRBL, Partclone and udpcast, allows you to do bare metal backup and recovery. Two types of Clonezilla are available, Clonezilla live and Clonezilla SE (server edition). Clonezilla live is suitable for single machine backup and restore. While Clonezilla SE is for massive deployment, it can clone many (40 plus!) computers simultaneously. Clonezilla saves and restores only used blocks in the harddisk. This increases the clone efficiency. At the NCHC's Classroom C, Clonezilla SE was used to clone 41 computers simultaneously. It took only about 10 minutes to clone a 5.6 GBytes system image to all 41 computers via multicasting!

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by ssteve60 on 2011-06-07
> **howefield said:**
> Clonezilla.
 
 
 
[http://clonezilla.org/](http://clonezilla.org/)
 
Thanks a lot. I'll check it out :D

---

