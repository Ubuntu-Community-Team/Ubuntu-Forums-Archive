---
title: "Can't increase partition size"
date: 2010-09-02
forum: General Help
---

### Post by rsodee on 2010-09-02
I'm having a problem with GParted. I'm trying to increase the size of an ext4 partition but the maximum is set to 9970 MiB. The option to increase its size is greyed out. How can I fix this?

---

### Post by ajgreeny on 2010-09-02
Make sure the partition is unmounted; right click on it in gparted and "unmount" if it is showing.

If that's not the answer, come back again.

---

### Post by garvinrick4 on 2010-09-02
> **rsodee said:**
> I'm having a problem with GParted. I'm trying to increase the size of an ext4 partition but the maximum is set to 9970 MiB. The option to increase its size is greyed out. How can I fix this?
Use your install CD and use Try Ubuntu not installing and then nothing will be mounted.
If you have trouble if you can take a screenshot of gparted and post it as an attachment
here we can help more.

---

### Post by rsodee on 2010-09-02
I'm running off a live USB right now. I can't unmount it either because the option to unmount it is grayed out too.

---

### Post by garvinrick4 on 2010-09-02
Your extended partition is to small and should be the size of unallocated space.
You do not need two swaps.
My suggestion is to start over.
Delete all the partitions. Have one big unallocated. You can format during install.
Make a primary partition in front of drive for Ubuntu install the size you want.
Make the rest of drive a extended partition.
When installing Ubuntu choose manual install.
Put in sda1 as ext4 format and /
sda2 would then be as extended partition.
Any other partitions would then be logical partitions inside of the extended.
Extended partition is basically a house for logical partitions.
In page 8 of install their is an advanced tab click on it and choose sda to install grub. 

Here are some links to read up on.

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
 [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 
 [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 
 [http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/) 
 [https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions) 
 [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by garvinrick4 on 2010-09-02
Notice I have Windows in primary and then a big extended partition with a lot of different linux logical partitions inside of the extended partition. Over time I just wanted to see what
the other types of linux were like. Ubuntu is what I use most all the time. 
 You are only allowed 4 primary partitions is why you need the extended partition. Linux can survive in a logical or primary where Windows likes only primary partitions. Once you get the hang of it, it go's quite smoothly. Learning to use gparted is essential.

---

### Post by rsodee on 2010-09-02
Thanks I'll try it out. It doesn't seem too complicated but I'm mostly used to Windows so this is a little new to me.

I'm not sure how to delete the partitions with a key next to them I can only delete the other ones.

---

### Post by garvinrick4 on 2010-09-02
> **rsodee said:**
> Thanks I'll try it out. It doesn't seem too complicated but I'm mostly used to Windows so this is a little new to me.

I'm not sure how to delete the partitions with a key next to them I can only delete the other ones. If you are using that parition it will have a key next to it. You have to
do all the work in gparted with a live cd. Take your install cd and choose try ubuntu and then nothing will be locked. You can then delete old partitions and make your new ones.
One for your Operating system which is going to be Primary, ext4 and / 
It will make itself called sda1
Then the rest of drive as an Extended partition and that is it.
It will call itself sda2
Then anything inside of Extended partition will be a logical partition and start at sda5
You always put your grub or bootmanager in sda and that is on page 8 of install.
/ means like C: drive in Windows. It is the file system. It is called /
ext4 is the format. Windows is NTSF. 
When you put the grub in sda it will put a boot flag in the proper partition. Always put grub in sda not sda1 or sda2 just sda
   So make your partitions with the Live Cd and then go straight into install and put your / and format to ext4 in the one you made for it. and so on and so on. 
 Remember a live cd is just an install cd but you choose to try it instead of install it that way nothing is mounted (keys in gparted) and you can work with that partition, you can never work with a partition that is in use.
 Any more questions just ask, that is what people are here for, they all started at one time themselves. Keep at it, it grows on you, it is like athletes foot or something you
cannot get rid of it once it starts. I do not want to be the only one up at 4 AM screwing around with config files.

---

