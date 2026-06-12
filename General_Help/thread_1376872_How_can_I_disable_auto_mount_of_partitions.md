---
title: "How can I disable auto mount of partitions?"
date: 2010-01-09
forum: General Help
---

### Post by zanetu on 2010-01-09
Hi, 

I just installed kubuntu 9.10 and noticed that several partitions (fat32 and ntfs) are mounted automatically after I login. I searched /etc/fstab but found no entries for those partitions. So I guess there may be something like start-up scripts that automatically detect and mount all partitions on the hard disk at boot/login. Does anybody know the location of those scripts (if any)? I want to disable that auto mount.

Thanks.

---

### Post by SecretCode on 2010-01-09
I'm not aware of another way of automounting ... in order to start understanding your layout, could you post the contents of */etc/fstab* and the output of *sudo fdisk -l*  ?

Meanwhile if you want to go hunting, look in /etc/init and /etc/init.d, and /etc/rc*.d ... and /etc/profile ... and probably lots of other places.

---

### Post by zanetu on 2010-01-09
> **SecretCode said:**
> I'm not aware of another way of automounting ... in order to start understanding your layout, could you post the contents of */etc/fstab* and the output of *sudo fdisk -l*  ?

Meanwhile if you want to go hunting, look in /etc/init and /etc/init.d, and /etc/rc*.d ... and /etc/profile ... and probably lots of other places.

Hi SecretCode,

I just did some research and found out that I made a mistake. I falsely thought that a partition was mounted when its label appeared in the "Places" column of Dolphin (ie the file manager), which was not necessarily the case. Now it's clear that no such start-up scripts exist on my hard disk and those partitions will not be mounted until I click on their labels in Dolphin.
But thank you anyway for your reply! :)

---

### Post by SuperSonic4 on 2010-01-09
You can arrange to hide the icons by right clicking the device and selecting hide

---

### Post by zanetu on 2010-01-09
> **SuperSonic4 said:**
> You can arrange to hide the icons by right clicking the device and selecting hide

Got it. Thanks for the hint. :)

---

