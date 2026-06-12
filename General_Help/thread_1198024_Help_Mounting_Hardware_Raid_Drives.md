---
title: "Help Mounting Hardware Raid Drives"
date: 2009-06-26
forum: General Help
---

### Post by Neckrom on 2009-06-26
[COLOR=black]First let me say I am new to Ubuntu and new to Linux. This is my first real install of the systems. I am a IT professional with about 11 years experience with windows and network support but I have worked in some heavy Unix environments. All of the Unix systems were in place so it was just maintenance. Clear print daemons, create users, change file permissions. That is about it. I consider my self a novice. Luckily my other experience will hopefully keep me from making terrible mistakes.[/COLOR]
 

[COLOR=black]I am trying to make a file server/ web server / and media streamer out of the same box. I have Ubuntu server 9.04 ((Jaunty Jackalope) love the name)installed on the machine in question and have been able to install a few things that will be needed like SSH and enabled a static IP. So far I am loving the system and I love learning the ins and out of Linux. I am waiting to install SAMBA till I get my first snag fixed. Ok now that I have that out of the way... So finally Here goes my questions![/COLOR]
 

[COLOR=black]I have a set of disks installed in hardware raid5 that I would like to mount or put a directory into so that I could install samba and share the space out between all of my machines. Windows / Xbox 360 / and future Linux machines. I also have space left on the disk that I installed the sever onto that I would not mind adding a directory to. So here is the novice part. How do I get all 4 of the 1000.2 GB drives setup? The raid controller shows them as one disk space with 2700ish GB available. Why does Ubuntu show them as 4 disks when I do a fdisk -l. I have listed the output of the fdisk -l below. [/COLOR]
 

[COLOR=black]Also any pointers on how to get the media server setup would be appreciated. I have searched the site and the web and have not been real productive on a how-to or walkthrough. THANKS IN ADVANCE FOR YOUR HELP.[/COLOR]
[COLOR=black] [/COLOR]

[COLOR=black]SORRY FOR THE LONG READ. I will try to keep my future posts shorter.[/COLOR]
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
 
Disk /dev/sda doesn't contain a valid partition table
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
 
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
 
Disk /dev/sdc doesn't contain a valid partition table
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
 
Disk /dev/sdd doesn't contain a valid partition table
Disk /dev/sde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00065201
 
Device Boot Start End Blocks Id System
/dev/sde1 1 30485 244870731 8e Linux LVM
/dev/sde2 30486 30515 240975 5 Extended
/dev/sde5 30486 30515 240943+ 83 Linux
 
FIRST POST :popcorn:

---

### Post by Neckrom on 2009-06-27
Bumping trying to get some coverage.

---

### Post by ronparent on 2009-06-27
First off, despite all the verbage I have no clear notion of what you are working with. Your post suggests that it a current implementation of raid on a mb? If that is the case it is actually what the ubuntu community refers to as 'fakeraid'. In a windows environment the raid would be accessed with a mb provided driver, which would actually perform many of the functions of a true hardware raid in software. The eqivalent in ubuntu is a program called dmraid which discovers the raid metadata created on the drives by the mb raid hardware, and, enables ubuntu to interface with a defined raid array (in your case raid5) for all your normal disk functions including partitioning, formating, reads/writes, etc. This would be your choice if you want to access the raid array with both windows and ubuntu/linux distro. The dmraid program is not included on the ubuntu live cd. Until it is installed, however, you have no access to a raid array defined by the mb raid chipset. 

I might mention that if you have no need to interface your array with windows you could use a pure software raid as implemented with through a program called mdadm. That choice would requre you to erase the metadata created by the mb chipset and turn-off the hardware raid. 

If you are in the mood for quick experimentation, initially through command line functions, you could with internet connectivity, install dmraid and explore the nature of your array. It may be currently all unallocated space. Once the array is activated by dmraid it may be partitioned and data moved to it in gui interface.

If you wish to study your options first, search for internet (or ubuntu forum) references on dmraid and mdadm. Have fun.

---

