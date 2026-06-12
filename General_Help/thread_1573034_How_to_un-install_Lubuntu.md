---
title: "How to un-install Lubuntu"
date: 2010-09-12
forum: General Help
---

### Post by asifnaz on 2010-09-12
I have  installed Lubuntu dual boot with XP .
Waht does Lubuntu do is it makes a hidden partition inside the hard disk  so i cant access the installation files .
I am not going to uninstall Lubuntu rather I am looking to know how can  it be done .
An how can i get that HD space back .
I need your help
      [IMG]http://www.linuxforums.org/forum/linux2/statusicon/user_online.gif[/IMG] [[IMG]http://www.linuxforums.org/forum/linux2/buttons/report.gif[/IMG]]("http://www.linuxforums.org/forum/report.php?p=803914") 		 		  	     [IMG]http://www.linuxforums.org/forum/linux2/misc/progress.gif[/IMG] [[IMG]http://www.linuxforums.org/forum/linux2/buttons/edit-new.gif[/IMG]]("http://www.linuxforums.org/forum/editpost.php?do=editpost&p=803914")

---

### Post by TeoBigusGeekus on 2010-09-12
> **asifnaz said:**
> Waht does Lubuntu do is it makes a hidden partition inside the hard disk  so i cant access the installation files .
Could you please expand the above a bit more?

---

### Post by jre6 on 2010-09-12
> **asifnaz said:**
> I have  installed Lubuntu dual boot with XP .
Waht does Lubuntu do is it makes a hidden partition inside the hard disk  so i cant access the installation files .
I am not going to uninstall Lubuntu rather I am looking to know how can  it be done .
An how can i get that HD space back .


If you have created dual boot using Wubi, you should be able to get Lubuntu uninstalled from Contol Panel > Add and Remove programs in Windows XP.

When you uninstall Lubuntu, you will get your disk space back again.

---

### Post by asifnaz on 2010-09-12
> **TeoBigusGeekus said:**
> Could you please expand the above a bit more?

Well i can define it non-technical wording . I have a 20GB hardisk 4 partitions of 5 GB each .After installing Lubuntu my D: drive tells its 1 GB so now i assume 4 GB is consumed by Lubuntu .

If this hidden partition is not normal thing does it mean I have made some mistake during installation .

For other user I tried my best to find Wubi for lubuntu but I couldnt . So I installed from live CD

---

### Post by TeoBigusGeekus on 2010-09-12
> **asifnaz said:**
> After installing Lubuntu my D: drive tells its 1 GB so now i assume 4 GB is consumed by Lubuntu .

Says who? Windows or Ubuntu?

---

### Post by asifnaz on 2010-09-12
> **TeoBigusGeekus said:**
> Says who? Windows or Ubuntu?

Both . when I chekch the properties it tells total size 1gb 998 mb free (actully this drive is 5 gb)

---

### Post by TeoBigusGeekus on 2010-09-12
Well, it's absolutely normal for ubuntu to use something like 2~4 gigs, including swap.
You can't access linux partitions from windows (not without [help]("http://www.howtoforge.com/access-linux-partitions-from-windows") that is).
I don't understand what you mean by saying hidden partitions of lubuntu.
If you want to get rid of ubuntu, just format your d: drive from windows, boot up with a winxp cd, choose repair and give
```
fixmbr
```
in the dos prompt to get rid of grub.

---

### Post by FahadMKS on 2010-09-12
This answer of fixmbr is good and have helped me.

Thanks a lot.

---

### Post by asifnaz on 2010-09-13
> **TeoBigusGeekus said:**
> 
I don't understand what you mean by saying hidden partitions of lubuntu.
If you want to get rid of ubuntu, just format your d: drive from windows, boot up with a winxp cd, choose repair and give
```
fixmbr
```in the dos prompt to get rid of grub.


Well I have no access to the data of Lubuntu .That Lubuntu is only accessed by a Partition manager so if i format D: it will format only 1GB which is already empty .Rest of 4GB can not be accessed by XP or lubuntu thats why I called it a hidden partition

---

### Post by veggen on 2010-09-13
Well, it's normal that Windows doesn't see Linux's partition. It's in a filesystem unreadale to it (without special software at least). Anyway, to delete that partition, use some partitioning utility (someone else will have to suggest a good one as I'm still using an ancient copy of PartitionMagic 8 in Windows). From there, you'll also be able to re-attach the emtpy space back to your Win partition.

---

### Post by h4xor66 on 2010-11-10
if you really want to get rid of lubuntu boot with the live cd run the disk manager and delete the linux partitions then use the free space to re create a logical partition and format it as ntfs ... reboot and xp will now see the partition as usable

be very careful that what you are deleting is the linux partition or xp will go bye bye

---

