---
title: "Delete Ubuntu with GParted?"
date: 2011-03-19
forum: General Help
---

### Post by 321olos on 2011-03-19
Ok so i figured i would delete everything off both my partitions (4GB and 8GB) and do a fresh reinstall. So once i used GParted for both my partitions it should 1 line saying unallocated with a number at the end.

Im not sure if thats right casue when i reinstalled Ubuntu and rebooted it showed "Geom Error" and i couldnt do anything.

My laptop is an Asus EEE PC 900 designed for windows xp but i have ran Ubuntu on it many times.

If i am doing something wrong in GParted can someone please help me as i do not have a windows xp install cd.

Thanks

---

### Post by lithopsian on 2011-03-19
Forget gparted.  Boot from Live CD and start install.  When you get to the pretty picture of your partitions, let Ubuntu have the whole disk (no windows, right?) and then go from there.  Anything already on the disks will automatically get wiped.

---

### Post by 321olos on 2011-03-19
> **lithopsian said:**
> Forget gparted.  Boot from Live CD and start install.  When you get to the pretty picture of your partitions, let Ubuntu have the whole disk (no windows, right?) and then go from there.  Anything already on the disks will automatically get wiped.

Ok well i made a bootable USB made by the universal USB Installer.

I pick "Erase and use the enite disk". Then where it says select drive it has 2 options (my 4GB and 8GB). When i select the 8GB it says 2 partitions will be deleted, use the advanced partitioning tool for more control but i click Install Now.

I fill out all the stuff needed. I let it install and click restart now. But when it loads up nothing happens now.

---

### Post by wojox on 2011-03-19
Have you upgraded the memory in that 700 or are you still using the stock 512 mb that came installed? I have the same netbook.

---

### Post by 321olos on 2011-03-19
I havent touched the memory and i dont think that would be the problem cause i installed ubuntu 10.10 yesterday but on the 4GB partition but now i want to install it on the 8GB and delete the 4GB.

---

### Post by dcstar on 2011-03-19
> **321olos said:**
> Ok so i figured i would delete everything off both my partitions (4GB and 8GB) and do a fresh reinstall. So once i used GParted for both my partitions it should 1 line saying unallocated with a number at the end.

Im not sure if thats right casue when i reinstalled Ubuntu and rebooted it showed "Geom Error" and i couldnt do anything.

My laptop is an Asus EEE PC 900 designed for windows xp but i have ran Ubuntu on it many times.

If i am doing something wrong in GParted can someone please help me as i do not have a windows xp install cd.

Thanks

In gparted use "Device-Create Partition Table". that will create a totally fresh (and correct) dfive.

---

### Post by lithopsian on 2011-03-19
"Geom Error" is typically a BIOS problem.  If it happens on a new install and you are sure the BIOS is correct then your MBR probably got nuked.  It could be something to do with the way that Grub was installed.

One of the simplest ways to fix this is to reformat but you just did that on the install.  Can you run up gparted from your installation USB and see what it says about those two drives now?

---

### Post by 321olos on 2011-03-19
> **dcstar said:**
> In gparted use "Device-Create Partition Table". that will create a totally fresh (and correct) dfive.

I will give that a go. Thanks!


> **lithopsian said:**
> "Geom Error" is typically a BIOS problem.  If it happens on a new install and you are sure the BIOS is correct then your MBR probably got nuked.  It could be something to do with the way that Grub was installed.

One of the simplest ways to fix this is to reformat but you just did that on the install.  Can you run up gparted from your installation USB and see what it says about those two drives now?

Im installing Ubuntu again one more time just to see what errors come up then i will see what the two drives say.

---

### Post by 321olos on 2011-03-19
Ok it finished installing and i got the Geom Error again so im gonna load up GParted now.

---

### Post by dcstar on 2011-03-19
> **321olos said:**
> Ok it finished installing and i got the Geom Error again so im gonna load up GParted now.

If your device uses an internal SSD then it is possible that the SSD now has a fault in the area where the partition data is stored.

SSD's do not last forever - especially the early generation ones.

---

### Post by Hedgehog1 on 2011-03-19
> **321olos said:**
> Ok it finished installing and i got the Geom Error again so im gonna load up GParted now.

I am confused; are the 4gig and 8 gig units separate flash drives/SD cards?

If so, you can combine them for a total of 12 useful gigs:

It works like this (in your case, the '/' would be the 4 gig and the '/home' would be the 8 gig):

[IMG]http://img863.imageshack.us/img863/6315/netbooksd.png[/IMG]

Could we get a look at your disk partition layout?

From the LiveUSB, select 'try' and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by 321olos on 2011-03-19
> **dcstar said:**
> If your device uses an internal SSD then it is possible that the SSD now has a fault in the area where the partition data is stored.

SSD's do not last forever - especially the early generation ones.

I dont know if it does. But i loaded up GParted and i made a new partition table and im reinstalling Ubuntu to see if it works.

---

### Post by 321olos on 2011-03-19
No luck i keep getting Geom Error. What should i do cause ive tried everything.

---

### Post by 321olos on 2011-03-19
> **Hedgehog1 said:**
> I am confused; are the 4gig and 8 gig units separate flash drives/SD cards?

If so, you can combine them for a total of 12 useful gigs:

It works like this (in your case, the '/' would be the 4 gig and the '/home' would be the 8 gig):

[IMG]http://img863.imageshack.us/img863/6315/netbooksd.png[/IMG]

Could we get a look at your disk partition layout?

From the LiveUSB, select 'try' and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS
[PHP]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009883b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00077c65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    14983167     7490560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2        14985214    15759359      387073    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sdb5        14985216    15759359      387072   82  Linux swap / Solaris

Disk /dev/sdc: 1001 MB, 1001914368 bytes
31 heads, 62 sectors/track, 1018 cylinders, total 1956864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e87d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3223366752  3470046675   123339962   f4  SpeedStor
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(793, 22, 13) logical=(1677089, 27, 21)
Partition 1 has different physical/logical endings:
     phys=(870, 235, 61) logical=(1805435, 9, 48)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   378192737   710426324   166116794   10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(196770, 12, 54)
Partition 2 has different physical/logical endings:
     phys=(870, 235, 50) logical=(369628, 21, 7)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225603442   225603451           5   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(367, 66, 47) logical=(117379, 16, 13)
Partition 3 has different physical/logical endings:
     phys=(370, 32, 37) logical=(117379, 16, 22)
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
[/PHP]

Thats what it came up with,

---

### Post by Hedgehog1 on 2011-03-19
This means you do have two flash drives:

/dev/sda  4 gig
/dev/sdb  8 gig

And the reason your install on the 8 gig fails is the netbook wants to boot off the 4 gig.

But that is OK!

Using gparted, make two patitions on sda:

sda1 - 3 gig ext4 , to be '/'
sda2 - 1 gig swap **

 (** this assumes you want a whole gig of swap; if you use less swap, you can increase the size of sda1)

And one partition out of sdb:

sdb1 - 8 gig ext4, to be '/home'

Then reinstall, assigning sda1 as '/', sda2 as swap, sdb1 as '/home'

Please be sure your device for bootloader is /dev/sda.

This will give you a total of 12 gig file system, 4 used for OS and swap, the other 8 for your music, documents and videos.

***The Hedge***

:KS

p.s. Here is a link with more file system pictures: [http://ubuntuforums.org/showthread.php?t=1705788]("http://ubuntuforums.org/showthread.php?t=1705788")

---

### Post by 321olos on 2011-03-19
> **Hedgehog1 said:**
> This means you do have two flash drives:

/dev/sda  4 gig
/dev/sdb  8 gig

And the reason your install on the 8 gig fails is the netbook wants to boot off the 4 gig.

But that is OK!

Using gparted, make two patitions on sda:

sda1 - 3 gig ext4 , to be '/'
sda2 - 1 gig swap

And one partition out of sdb:

sdb1 - 8 gig ext4, to be '/home'

Then reinstall, assigning sda1 as '/', sda2 as swap, sdb1 as '/home'

Please be sure your device for bootloader is /dev/sda.

This will give you a total of 12 gig file system, 4 used for OS and swap, the other 8 for your music, documents and videos.

***The Hedge***

:KS

p.s. here is a link with more file system pictures: [http://ubuntuforums.org/showthread.php?t=1705788]("http://ubuntuforums.org/showthread.php?t=1705788")

Thanks so much for helping il try it now.

---

