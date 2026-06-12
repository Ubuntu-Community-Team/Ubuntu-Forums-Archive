---
title: "Primary or Extended Partition for 2nd partition on USB pen drive?"
date: 2011-03-13
forum: General Help
---

### Post by Rytron on 2011-03-13
Hi.

I formatted a 16GB USB flash drive via right click. Then I ran [COLOR="Indigo"]gparted[/COLOR] and got as far as this [image attached]
Do I choose **Primary Partition** or **Extended Partition** for this second partition?

Thanks.

---

### Post by coffeecat on 2011-03-13
> **Rytron said:**
> Hi.

I formatted a 16GB USB flash drive via right click. Then I ran [COLOR=Indigo]gparted[/COLOR] and got as far as this [image attached]
Do I choose **Primary Partition** or **Extended Partition** for this second partition?

Thanks.

Unless you want more than four partitions, go for a primary. The mbr partition table limits you to four primary partitions. An extended partition is a special type of primary which is used only as a placeholder for a number of logical partitions so that you can exceed the 4 limitation. If you create an extended partition, you will have to create one or more logical partitions before you can store data. You don't store data in an extended partition.

---

### Post by srs5694 on 2011-03-13
Either a primary or a logical (inside an extended, as coffeecat notes) will work; however, you should be aware that Windows will only give you access to the first partition on the disk. This is because Windows treats USB flash drives as "superfloppies," which are either unpartitioned or have a single partition. Your decision of primary or logical for the second partition doesn't matter as far as the Windows limitation is concerned. Linux, FreeBSD, OS X, and most other OSes can access multiple partitions on a USB flash drive (primary or logical). Depending on your needs, this limitation of Windows could be important, so you should be aware of it.

---

### Post by Hedgehog1 on 2011-03-13
Here is the gparted view of my **Ubuntu-On-A-Stick!**

***I have one FAT32 partition for moving data between Windows PCs***

[IMG]http://img837.imageshack.us/img837/3226/ubuntuonastickgparted.png[/IMG]

All said and done, these could have been three primary partitions instead.

***The Hedge***

:KS

---

### Post by Rytron on 2011-03-14
Thanks guys. :)

---

