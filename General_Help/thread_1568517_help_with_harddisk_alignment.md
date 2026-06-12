---
title: "help with harddisk alignment"
date: 2010-09-05
forum: General Help
---

### Post by benny999 on 2010-09-05
he when im trying to install ubuntu 10.04 64bit on my laptop it comes up with this error and being a linux newbie im not sure on what to do this is what it says

the partition /dev/sda1 assigned to / starts at an offset of 3072 bytes from the minimum alignment for this disk, which may lead to very poor performance


since you are formatting this partition, you should correct this problem now by realigning the partition, as it will be difficult to change later. to do this, go back to the main partitioning menu, delete partition, and recreate it in the same position with the same settings. this will cause the partition to start at a point best suited for this disk


yeah thats what it says im not sure on how to fix this any help is good thank you :)

---

### Post by srs5694 on 2010-09-05
See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote for IBM developerWorks for information on the issues involved. The article focuses on Western Digital "Advanced Format" and similar drives, but there are similar issues with some RAID arrays, as noted in the "Aligning RAID Partitions" sidebar.

I don't know offhand what sort of checks the Ubuntu 10.04 installer does, and you haven't said what type of hard disk you've got, so I don't know whether the warning is reasonable or is a false alarm. It probably won't hurt to re-create the partition as the warning suggests, though. I do know that the 10.04 installer aligns partitions on 1MB (2048-sector) boundaries by default, in order to optimize performance on as wide a variety of modern hardware as possible.

---

### Post by benny999 on 2010-09-06
its a seagate momentus 640gb st9640322as if that helps :)

and thanks for the input

---

### Post by srs5694 on 2010-09-06
To the best of my knowledge, Seagate has not yet released an Advanced Format disk, so you probably don't need to worry about partition alignment. My conclusion is that the message you saw was being overly pessimistic. Partitioning tools have recently begun erring on the side of caution on this score because of the potentially very bad consequences of doing the wrong thing on Advanced Format disks or hardware RAID arrays.

---

### Post by benny999 on 2010-09-07
ah ok thanks well i got it to work i used gparted and but 1mb of nothing before the first parition

---

