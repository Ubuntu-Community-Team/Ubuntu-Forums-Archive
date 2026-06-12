---
title: "HP pavilion DV6-2113 partitioning problem"
date: 2010-05-02
forum: General Help
---

### Post by mykulz1 on 2010-05-02
Hey, I have been trying to dual boot windows 7 with ubuntu 10.04, but my laptop has already got 4 primary partitions. One is windows, one is recovery, one is HP_TOOLS, and the last is something to to with windows 7 booting. So how am I supposed to create a partition without having to delete and create an extended partition? Any help appreciated, thanks in advance.

---

### Post by mykulz1 on 2010-05-02
Also my wubi installs have been failing after grub. is this connected?

---

### Post by itiswhatitis on 2010-05-02
The Live CD has an option to resize partitions.  It will make a recommendation, when you accept it will move your files around, shrink your windows partition, and make a new partition for Ubuntu.

Here is a doc that explains the process:  [https://help.ubuntu.com/9.10/switching/installing-partitioning.html](https://help.ubuntu.com/9.10/switching/installing-partitioning.html)

---

### Post by mykulz1 on 2010-05-02
Thanks, but as it says in the link you gave me it says i can only have 4 primary partitions. i would delete one of the partitions to create a logical partition but i don't know how safe its is since there are system files in each.

---

### Post by mugetsu37 on 2010-05-02
I'd say delete the HP_TOOLS partition (after making a recovery cd if you wish). I have an HP dv6000 and I remember that my laptop came with that partition as well. I deleted it when I first installed a dual-boot on this system with 9.04, I haven't had any problems I needed HP_TOOLS for.

Here's some of the same problem you're having: 
[http://www.sevenforums.com/general-discussion/41178-too-many-primary-partitions.html](http://www.sevenforums.com/general-discussion/41178-too-many-primary-partitions.html)

This post also goes over creating an extended partition for logical partitions: 
[http://ubuntuforums.org/showthread.php?t=1400095](http://ubuntuforums.org/showthread.php?t=1400095)

---

### Post by mykulz1 on 2010-05-03
Ok, I suppose i should make a backup of HP_TOOLS just incase, but I will try this thank you.

---

