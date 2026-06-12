---
title: "create a new logical partition to my Dual OS XP and Ubuntu"
date: 2009-08-14
forum: General Help
---

### Post by AnasZ on 2009-08-14
Hi, 
i have successfully installed Ubuntu 8.04 to my laptop toshiba satallite pro along with my XP. i selected the automatically ubunto partitioning, 
however now i have 50 GB out of 230GB hard disk to windows. 
i would like to create a new partition 150GB (logical one, FAT 32) in order to put all my data which comes from ubuntu and XP as well. 
i understood that in this way i can reach these data from both systems (UBUNTU AND XP) 
can anyone give me a step by step the way to create this new partition as i am new to Ubuntu. 
thank you,

---

### Post by ptn107 on 2009-08-14
You need an Ubuntu desktop CD either 8.04 or 9.04 to boot from.  The thing with your local partitions is that you cannot mess with them unless they are unmounted (not in use) so you can't do anything with your Ubuntu running.  So you need to boot a live CD and select 'Try Ubuntu without any change to your computer'.  Once at the live desktop you can open Gparted (System -> Administration -> Partition Editor) and mess around with your partitions.

[1] _[Gparted help]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html")_

---

