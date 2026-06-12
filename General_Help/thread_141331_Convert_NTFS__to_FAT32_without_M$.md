---
title: "Convert NTFS  to FAT32 without M$?"
date: 2006-03-08
forum: General Help
---

### Post by justleen on 2006-03-08
Hey there Ubuntus

Im running ubuntu quite happily at the moment, and going for the 100% Ubuntu without Windows. Luckily for me i manager to screw up my windows install when installing Ubuntu. So far i havent missed it, i simply mounted the NTFS partitions read only for my data.
How ever, if i go 100%, i would like write access as well. Now i dont have enough free space to copy data to one partition, create ext partitions, and copy it back. So i reckon the easiest way is to use the MS convert util, and convert NTFS to FAT. But, as said, i dont have a working windows install at the moment.. And to be honest, i really dont want to fix XP just to convert my drives

Does anyone here know wether i can convert them with any other tool?

---

### Post by somerville32 on 2006-03-08
I recommend searching google.

---

### Post by beast2k on 2006-03-08
Did you try gparted? you can format any type as whatever filesystem you want. Just use synaptic and install as usuall.

---

### Post by justleen on 2006-03-08
[QUOTE=beast2k]Did you try gparted? you can format any type as whatever filesystem you want. Just use synaptic and install as usuall.[/QUOTE]
i cant really format, since my data is still on there..

Googling only finds me (as a good option) windows CONVERT.. Or partition magic.. Both requiring windows to run..

THink im best of by burning some data, to free up one partition, en start to create spanking brandnew ext3 partitions (now that i think of it, that might actually add to the fun of getting rid ogf windows :)

---

### Post by beast2k on 2006-03-08
[QUOTE=justleen]i cant really format, since my data is still on there..

Googling only finds me (as a good option) windows CONVERT.. Or partition magic.. Both requiring windows to run..

THink im best of by burning some data, to free up one partition, en start to create spanking brandnew ext3 partitions (now that i think of it, that might actually add to the fun of getting rid ogf windows :)[/QUOTE]

Okay I see, that is a problem, but only a little one. Partition magic comes on a bootable CD so you boot from it, just like a linux live CD . Speaking of live CD's  Gparted is available as an ISO that you burn to CD and use just like partition magic here's the link [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) (actually I think I'm going to download it as well just in case)
Edit: I just downloaded it, it's a 29MB .iso

---

### Post by justleen on 2006-03-09
[QUOTE=beast2k]Okay I see, that is a problem, but only a little one. Partition magic comes on a bootable CD so you boot from it, just like a linux live CD . Speaking of live CD's  Gparted is available as an ISO that you burn to CD and use just like partition magic here's the link [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) (actually I think I'm going to download it as well just in case)
Edit: I just downloaded it, it's a 29MB .iso[/QUOTE]


Cheers for that info. I've been looking at the docs for gparted, but i cant seem to find that it can convert partitions? just move/ copy/ create etc.

Looks like a nice tool though!

I did find another solution to the problem though:
- run to the nearest blanc media dealer
- sit down with a 100blanc dvds
- start burning the data :)

---

### Post by dcstar on 2006-03-09
[QUOTE=justleen]Hey there Ubuntus

Im running ubuntu quite happily at the moment, and going for the 100% Ubuntu without Windows. Luckily for me i manager to screw up my windows install when installing Ubuntu. So far i havent missed it, i simply mounted the NTFS partitions read only for my data.
How ever, if i go 100%, i would like write access as well. Now i dont have enough free space to copy data to one partition, create ext partitions, and copy it back. So i reckon the easiest way is to use the MS convert util, and convert NTFS to FAT. But, as said, i dont have a working windows install at the moment.. And to be honest, i really dont want to fix XP just to convert my drives

Does anyone here know wether i can convert them with any other tool?[/QUOTE]
If you can shrink the Windows partition (to make some space for a new partition), use one of the Linux tools to do that (qtparted, gparted).

---

### Post by incubus on 2006-03-09
Yeah, if you can, don't use Fat32. Personally I have only bad memories about it. Also, remember it has a size limit of 32Gb. I would take the extra effort to backup data (which is always good) and then format the partition as Ext2 or Ext3.

Then if you need to use it in windows, you can install this very nice driver:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Just my opinion.

incubus

PS: Now that I read again, you said 100 blank disks. That partition size would probably exceed Fat32's limit. What about getting your hard drive to a friend's place and copying it over?

---

### Post by justleen on 2006-03-09
[QUOTE=incubus]

Then if you need to use it in windows, you can install this very nice driver:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")


What about getting your hard drive to a friend's place and copying it over?[/QUOTE]

Great thnx for that driver for windows. i was wondering how to read ext from windows (just-in-case!).

And thnx for the reminder of the 32gb limit! your absolutly right, the smallest partition is 40GB.. 
Copying at a friends would be an option i guess - dont know if i have friends who have that much of free space though (do you?? :D )

---

### Post by frodon on 2006-03-09
[QUOTE=incubus]Yeah, if you can, don't use Fat32. Personally I have only bad memories about it. Also, remember it has a size limit of 32Gb. I would take the extra effort to backup data (which is always good) and then format the partition as Ext2 or Ext3.

Then if you need to use it in windows, you can install this very nice driver:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
[/QUOTE]That's wrong FAT32 is not limited to 32Go, i have a 70Go FAT32 partition !!!
However you can't write file larger than 4Go on a FAT32 partition and it's annoying if you wish to rip some dvds.

About the ext3 windows drivers there's no problem with the read support but the write support is not 100% reliable so i do not recommend this drivers for an intensive write use under windows.

To create your partitions you could also use *fdisk *and *mkfs* commands, some examples : [http://www.oracle.com/technology/pub/articles/calish_filesys.html:](http://www.oracle.com/technology/pub/articles/calish_filesys.html:)

---

### Post by lamego on 2006-03-09
If you want to have  a good level of interoperability FAT32 IS a good choice. The limit of 32GB is imposed by the W2K/XP OSes format utility, if you format on another os/tool capable of formating fat32 it can handle until 2TB.

---

### Post by frodon on 2006-03-09
Hey, i didn't know that Iamego, i always wondered why so much people say that there's a 32Go limit while i have a 70Go FAT32 partition for 2 years now.
Glad to know why, thanks ;)

---

### Post by ronmarley1 on 2006-03-09
[QUOTE=somerville32]I recommend searching google.[/QUOTE]

somerville32,
I don't mean to be a jerk, but please read this forum thread ([http://www.ubuntuforums.org/showthread.php?t=72130](http://www.ubuntuforums.org/showthread.php?t=72130)) for information concerning your reply.
Thanks

---

### Post by qb4ever on 2006-03-09
I'm having the same stumbling block converting my fileserver, I have a 120gb drive formatted NTFS with 34.6gb used. Also a 40gb drive formatted NTFS with 14.7gb used. I don't have a dvd burner or partition magic but an looking into gparted live cd.

No way to convert ntfs to fat32? :-k

---

### Post by beast2k on 2006-03-09
[QUOTE=justleen]
I did find another solution to the problem though:
- run to the nearest blanc media dealer
- sit down with a 100blanc dvds
- start burning the data :)[/QUOTE]
LOL, that's the easyest way but for the price of the CD's you could buy a copy of partition magic:D

---

### Post by RAOF on 2006-03-09
[QUOTE=qb4ever]I'm having the same stumbling block converting my fileserver, I have a 120gb drive formatted NTFS with 34.6gb used. Also a 40gb drive formatted NTFS with 14.7gb used. I don't have a dvd burner or partition magic but an looking into gparted live cd.

No way to convert ntfs to fat32? :-k[/QUOTE]
Last time I checked, Microsoft tools could take you fat32->NTFS, but not the other way.

But since you've got lots of free space on that drive, you could just shrink the parittion, make an ext3 partition in the free space, copy the NTFS contents across...

---

