---
title: "New  Laptop!"
date: 2009-12-12
forum: General Help
---

### Post by Tuxaby on 2009-12-12
Looked everywhere for help with this with no luck.  Maybe someone here will know.

                                                                           I am going to wipe and partition my hard drive to two partitions and install Win 7 and Ubuntu 9.1 side by side.  Before I do this  I *will transfer Recovery to a flash drive using the* [ HP USB Recovery Flash Disk Utility]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-77449-1&lc=en&dlc=en&cc=us&lang=en&os=4063&product=4041781")* I downloaded from HP.  Looking at the size of Recovery on the disk manager it appears a 4 gb  flash drive will be needed.  I couldn't find any info on size needed.   Also, is the Hp Tools partition installed from recovery or is it necessary to transfer  and save it as well?* 



I'm not real impressed with Win 7 and it's many problems, but want to keep it to learn more about it before upgrading my wife's desktop to it.  She refuses to use anything else.  

I am anxious to install Ubuntu 9.1, but will have to resolve this before I can do so as win 7 uses 4 partitions making it impossible to install Ubuntu.  Wiping and splitting the drive before any install is the only way I see to do this.  Thanks in advance, Lee

---

### Post by Tuxaby on 2009-12-12
bump

---

### Post by Shazaam on 2009-12-12
How big is the hard drive in your new laptop? Ubuntu will happily reside in a partition 10gigs or larger.
If you have a roomy hard drive, find the proper (Windows) way to resize/shrink the main Win7 partition. When done use either the Ubuntu or Gparted livecd to make an Extended partition to fill the unallocated space. Then install Ubuntu inside the Extended partition (including swap).
If you end up having to use the oem restore application beware as this usually nukes the drive back to relatively factory fresh partitions. Best idea then is to make the Extended partition (and everything inside) hidden from Windows before restoration if you can.

---

### Post by Tuxaby on 2009-12-13
Thats why I want to save the restore to a flash.Then make two logical partitions, then set up on each as seperate drives .  current problem is that the current win 7 installation uses 4 partitions which is all that is allowed according to Gparted.

---

### Post by audiomick on 2009-12-13
I am not sure, but I think windows has to be in a Primary partition, and I have the impression from what I have read here that Win 7 uses two partitions.

Your basic procedure, without going into details I am not sure about, is to install windows first, either into a partition you have created of the size you want it to have or onto the whole drive then shrink the windows partition, then install Ubuntu.

---

### Post by wilee-nilee on 2009-12-13
It sounds like the HP version of W7 will make the 4 partitions, normally the standard install should only be a 100Mib boot/recovery and the OS on the 2nd. Are you using a copy of the W7 already on the laptop or a standard install DVD. So after looking at the disc recovery page it just looks like it will install as you suggest with 4 partitions if that is what is on there now. You might see if you can get a standard install DVD from MS for 30$ to avoid all the extra work and end up with the 2 partition setup if that is what works for you. Maybe HP will let you have a standard install DVD otherwise.

---

### Post by justin_guerin on 2009-12-13
> **Tuxaby said:**
> Thats why I want to save the restore to a flash.Then make two logical partitions, then set up on each as seperate drives .  current problem is that the current win 7 installation uses 4 partitions which is all that is allowed according to Gparted.

You are only allowed 4 primary partitions, but any one of the 4 primary partitions can be replaced by an extended partition, allowing you to create many logical partitions.  However, it sounds like you've already got 4 primary partitions defined and in use, so you'd have to remove one of them to create logical partitions for Linux anyway.

---

### Post by Tuxaby on 2009-12-13
Thats what I face.  Now,  I can save recovery on a flash drive ,using a utilityn I have downloaded.  What I don't know is if the HP tools partition also present will be recreated from recovery or do I need to find a way tom save it also?  If I can answer this I will completely wipe the drive, 500 gigs by the way, and partition to accomodate both systems.

---

### Post by garvinrick4 on 2009-12-13
I have a new HP and it is a breeze to partition. Leave the 7 OS where it is. Use a live CD
and boot from it. It will go into gparted and tell it what size of a Partition you would like.
It will put the grub in the boot partition called System. Take whatever size you want and
put it in the extended partition and put your linux and swap inside. D: in Windows which will
say Vista, it just does and Windows thing. And that will get its own partition in a primary.
I actually just made 2 partitions inside the extended so I can have 9.10 and the Alpha of 10.04.   Adust any which way you want boot order in startup-manager in Ubuntu.



I can only imagine 3 partitions for Windows 7.  Boot, OS and D:    the recovery is just an
option in OS grub but does not get a partition. Just a boot option in Grub if desired. And Boot partition is where linux grub resides. 

Show your fdisk -l

---

### Post by garvinrick4 on 2009-12-13
If you are trying to save D in 7 it takes 3 DVD's and you get one chance to make a copy
or OS.
Make as many recovery disc's as desired 1 Cd disc. so less than 700 meg. 

If I understand what you want to do? Just got through doing it all so it is fresh in my mind.
Seems to last for about a week or 2 then a forget what I did or where I put my notes.

---

### Post by garvinrick4 on 2009-12-13
Here is what mine looks like.




Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Tuxaby on 2009-12-13
Mine has 4, 2 for win 7, system and boot, the two additional are recovery and HP tools.  Want to save recovery and tools if not in recovery and start from scratch with a clean drive.  Also still need to know how much space recovery requires to save so I use the correct capacity flash drive.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Looking at [this]("http://h30434.www3.hp.com/t5/Operating-systems-and-software/Hard-Disk-Partition/m-p/175903#U175903") it looks like the recovery partition itself can be almost 16 GB. The tools are only a few hundred MB. I wouldn't go by his though... have a look in your own Disk Management tool and see...

---

### Post by Tuxaby on 2009-12-13
So, if I use a 32 gb flash I should be ok.  Great, that's what I'll do.  Thanks and kudos to all of you for your responses.  Gotta go now as I leave for work soon.   Will check back later in the week.   Many Thanks Lee

---

### Post by garvinrick4 on 2009-12-13
You get one chance to back up recovery it is an image produced
by Windows 7. It makes the image the one time only to be backed up to 3 DVD's. It is your OS they do not send Discs anymore you make your own. I do not believe you can back up the D: drive or make an
image but the ONE time. It says you just have this ONE time when you make your disc's.
  In the GRUB there is a VISTA boot and that is your D: image and you can put your Windows 7 back to factory condition at anytime by
booting their. Linux reports it as Vista because for the time being
it cannot tell the difference between 7 and Vista.

---

### Post by Tuxaby on 2009-12-31
Bought HP Win 7 recovery DVDs, deleted all partitions , repartitioned to two logical partitions and booted to recovery DVD.  There was no option to choose which partition to install Win 7 to.   Result was the entire drive was formated and used to install Win 7.   I understand that there is a way to wipe and partition the drive to two partitions and then hide one so Win 7 can only see the one it is to install to.  Looked on Google, but found nothing to address this.  Help!   What type of partitions should I create and how do I hide the one to be used for Ubuntu?

---

### Post by Tuxaby on 2009-12-31
Bump

---

### Post by Sef on 2009-12-31
Windows needs to be installed on the first primary parition.

When I did my set up, I made one parition for NTFS and the rest were either ext4 or swap.   Windows only saw the NTFS, so it installed there.   I used [GParted]("http://gparted.sourceforge.net") to make the partitions.

---

### Post by Tuxaby on 2010-01-01
Will give it a try in the morning.  The recovery disks they sent me are unlike any I have ever seen.   Will set 2 partitions, one ntfs and the other to ext 4. and see what happens.  Thanks for the input Sef, simple solution to hiding the partition for Ubuntu.

---

### Post by Sef on 2010-01-01
I put more than two partitions on.  Here is what I did - 

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e929b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12779   102647286    7  HPFS/NTFS
/dev/sda2   *       12780       14691    15358140   83  Linux
/dev/sda3           14692       60801   370378575    5  Extended
/dev/sda5           14692       16603    15358108+  83  Linux
/dev/sda6           16604       16730     1020096   82  Linux swap / Solaris
/dev/sda7           16731       60801   354000276   83  Linux


I created two primary partitions:

Windows 7 is 100 gb, so I could save anything that I need to it, but rarely use it.

Stable Ubuntu version.

Extended partitions:

Development version of Ubuntu.

Linux swap

Home partition since I prefer to separate root from my files.

---

