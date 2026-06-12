---
title: "Swap now working?"
date: 2009-11-08
forum: General Help
---

### Post by Limeni on 2009-11-08
Hi there, Im new on this forum and new to Linux, after playing around with dual boot with Windows I decided to use only Ubuntu.

But I have one problem, my swap is now working at all. I dont know is it beacuse i have enaugh RAM memory or is it joust not working?

I have ThinkPad Z60m Laptop with 2GB RAM memory & 250GB HDD. I have 3 partitions first ext3 with 20GB and with Ubuntu / on it, secund with 4GB for swap and it is partitioned for swap, and thrid NTFS with all other space.

When I go in terminal and type $ free -m i get this: 
```
limeni@ThinkPad:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1966         46          0        709        748
-/+ buffers/cache:        508       1503
Swap:         4094          0       4094
```So it means swap is not used at all.

But i have swap partition, when i type $ sudo fdisk -l to check my partitions i get this: 

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaddb20b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612        3133     4192965   82  Linux swap / Solaris
/dev/sda3            3134       30401   219029706    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf30dcc6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
```So I do have swap partition, but Ubuntu is not using it. I tried to run as much apps as I can, i used 1500mb of RAM memory but still Swap was at 0.

So what is this? Is it ok or my swap really is not working? 

Sorry if I missed category, admins can put this topic where they think it should be :)

---

### Post by Limeni on 2009-11-08
Is this normal? Maybe it is normal but i don know it? 

Is it normal that swap is not used at all??

---

### Post by raymondh on 2009-11-08
I consider SWAP as a spill-over, catch-basin for RAM.  I also consider it when I decide to hibernate. Given these 2 thoughts, maybe you do have enough RAM to run the apps you are running hence not needing SWAP at all.

---

### Post by Primefalcon on 2009-11-08
> **raymondhenson said:**
> I consider SWAP as a spill-over, catch-basin for RAM.  I also consider it when I decide to hibernate. Given these 2 thoughts, maybe you do have enough RAM to run the apps you are running hence not needing SWAP at all.
you can get it working regardless, sometiems if you repartition, you need to update the /etc/fstab file with the most current uuid, you can find the uuid in gparted by right clicking and info

---

### Post by slakkie on 2009-11-08
Swap is sometimes not needed, if you have 0 use what so ever you can simply decrease it, or not use it all together.

---

### Post by Limeni on 2009-11-08
I did clean install of Ubuntu 9.10, first partition ext3 for Ubuntu /, secund for swap and third for my files etc...

So I dont think there should be any problems...

But can you tell me guys, when you start ubuntu does your system uses swap? In windows it would always use like 300 or 400mb of swap, but here it is always at 0. 

Can you tell me how much swap is used on your system? When you boot it?

---

### Post by mcduck on 2009-11-08
The swap is recognized and working just fine. It's just that there's no reason to swap since you have plenty of RAM available. There's no reason to swap as long as there's enough memory available for all your applications, swapping would only allow using more memory than you have physical RAM available, but reading and writing to hard drive is about 1000 times slower than reading and writing to RAM. So you definitely don't want to use swap unless you really need to...

The "free -m" output tells you that the system has detected 4096 MB of swap, it will use it if it has to. But swapping is actually something you want  to avoid.

---

### Post by Limeni on 2009-11-08
I tryed this now, in terminal:

```
Filename                Type        Size    Used    Priority
/dev/sda2                               partition    4192956    0    -1
```

Priority -1, what this means?

And if I make swappiness=100 will ubuntu use swap then, no mather I have enaugh RAM?

---

### Post by Limeni on 2009-11-08
OK guys thank you all...

Im joust a little confused, this is first time i have single boot with only Ubuntu :D And it looks like it will stay like that :D

---

### Post by mcduck on 2009-11-08
> **Limeni said:**
> 
And if I make swappiness=100 will ubuntu use swap then, no mather I have enaugh RAM?
No, swappiness is just one of the factors that the Linux kernel uses to determine when to use swap. Setting swappiness to 100 doesn't force the system to use swap all the time, and even with swappiness set to 0 the kernel will use swap.

And no, you definitely wouldn't even want to get the system to use swap all the time. There are easier ways to make your system very slow and unresponsive.. :D

---

