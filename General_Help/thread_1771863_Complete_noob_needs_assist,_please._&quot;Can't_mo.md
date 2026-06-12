---
title: "Complete noob needs assist, please. &quot;Can't mount location&quot;"
date: 2011-05-30
forum: General Help
---

### Post by senselocke on 2011-05-30
Hello.

I have a dead Seagate Blackarmor 1TB NAS 110 drive, which, of course, has rather important work files on it. Seagate tells me the drive has a Linux partition. Luckily, I had just made a bootable USB stick with Ubuntu 11.04, and have a tower with SATA drives. Cracked open NAS 110, pull out and hook up SATA drive inside, it spins up when power is applied--yay!

So... I set the PC to boot USB, I get into Ubuntu, no problem... and have no idea what to do. I go up to Places, Computer, and I see "2.2gb casper -rw", "Array", and "File System". It's a 4GB stick, so the first and last are on that--"file system" brings me to the same things I see when I explore, so they're on the 4GB. I assume "Array" is the SATA drive, but when I click it, I get "unable to mount location"/"can't mount file".

I have 700GB or so on that NAS drive, and I have a fresh Hitachi 2TB external to transfer it all to. But Ubuntu can't connect to the SATA drive, and won't see the Hitachi at all, and I am beyond lost :confused: 

Before I take a crash course in how Ubuntu works, I need to get that data onto a safe drive. Any help would be enormously appreciated. So... halp?

---

### Post by wildmanne39 on 2011-05-30
> **senselocke said:**
> Hello.

I have a dead Seagate Blackarmor 1TB NAS 110 drive, which, of course, has rather important work files on it. Seagate tells me the drive has a Linux partition. Luckily, I had just made a bootable USB stick with Ubuntu 11.04, and have a tower with SATA drives. Cracked open NAS 110, pull out and hook up SATA drive inside, it spins up when power is applied--yay!

So... I set the PC to boot USB, I get into Ubuntu, no problem... and have no idea what to do. I go up to Places, Computer, and I see "2.2gb casper -rw", "Array", and "File System". It's a 4GB stick, so the first and last are on that--"file system" brings me to the same things I see when I explore, so they're on the 4GB. I assume "Array" is the SATA drive, but when I click it, I get "unable to mount location"/"can't mount file".

I have 700GB or so on that NAS drive, and I have a fresh Hitachi 2TB external to transfer it all to. But Ubuntu can't connect to the SATA drive, and won't see the Hitachi at all, and I am beyond lost :confused: 

Before I take a crash course in how Ubuntu works, I need to get that data onto a safe drive. Any help would be enormously appreciated. So... halp?
Hi,click on applications in  launcher then in the box that says search type disk utililty and click on it if your drive is there on the left click on it then mount it in that program, that is assuming the drive is working enough to mount.

---

### Post by senselocke on 2011-05-30
> **wildmanne39 said:**
> Hi,click on applications in  launcher then in the box that says search type disk utililty and click on it if your drive is there on the left click on it then mount it in that program, that is assuming the drive is working enough to mount.

Yay, a reply!

Okay, I found "disk utility", and I found the drive (it's not the "array" after all) and it says it's healthy--another yay!--but I can't find an interface to Mount it there. It shows three buttons, the disk partitions (I think), then three more, like this:

:Format Drive:      :Smart Data:
:Benchmark:
|RAID C...|RAID C...|RAID C...|RAID Component        |<--biggest
:Format Volume:     :Edit Partition:
:Delete Partition:

I don't see an option to "mount" anywhere, I'm sorry. Little more help, please?

EDIT: There's also a clickable link titled "Go To Array", and the disk type is Linux RAID Partition

---

### Post by wildmanne39 on 2011-05-30
> **senselocke said:**
> Yay, a reply!

Okay, I found "disk utility", and I found the drive (it's not the "array" after all) and it says it's healthy--another yay!--but I can't find an interface to Mount it there. It shows three buttons, the disk partitions (I think), then three more, like this:

:Format Drive:      :Smart Data:
:Benchmark:
|RAID C...|RAID C...|RAID C...|RAID Component        |<--biggest
:Format Volume:     :Edit Partition:
:Delete Partition:

I don't see an option to "mount" anywhere, I'm sorry. Little more help, please?

EDIT: There's also a clickable link titled "Go To Array", and the disk type is Linux RAID Partition
Hi, make sure the window for disk utility is maximazed then the lower down under volume lit says mount drive.

---

### Post by senselocke on 2011-05-30
Sorry to say, it doesn't say that anywhere. I took screenshots (click to embiggenate).

Here's the Disk Utility screen:
[[IMG]http://i1238.photobucket.com/albums/ff491/senselocke/Ubuntu/th_0530112155.jpg[/IMG]](http://s1238.photobucket.com/albums/ff491/senselocke/Ubuntu/?action=view&current=0530112155.jpg)

Here's what it showed when I tried the proper mounting instructions:
[[IMG]http://i1238.photobucket.com/albums/ff491/senselocke/Ubuntu/th_0530112156.jpg[/IMG]](http://s1238.photobucket.com/albums/ff491/senselocke/Ubuntu/?action=view&current=0530112156.jpg)
(found at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive))

And here's what happens when I "Go to Array":
[[IMG]http://i1238.photobucket.com/albums/ff491/senselocke/Ubuntu/th_0530112157.jpg[/IMG]](http://s1238.photobucket.com/albums/ff491/senselocke/Ubuntu/?action=view&current=0530112157.jpg)

---

### Post by wildmanne39 on 2011-05-31
> **senselocke said:**
> Sorry to say, it doesn't say that anywhere. I took screenshots (click to embiggenate).

Here's the Disk Utility screen:
[[IMG]http://i1238.photobucket.com/albums/ff491/senselocke/Ubuntu/th_0530112155.jpg[/IMG]](http://s1238.photobucket.com/albums/ff491/senselocke/Ubuntu/?action=view&current=0530112155.jpg)

Here's what it showed when I tried the proper mounting instructions:
[[IMG]http://i1238.photobucket.com/albums/ff491/senselocke/Ubuntu/th_0530112156.jpg[/IMG]](http://s1238.photobucket.com/albums/ff491/senselocke/Ubuntu/?action=view&current=0530112156.jpg)
(found at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive))

And here's what happens when I "Go to Array":
[[IMG]http://i1238.photobucket.com/albums/ff491/senselocke/Ubuntu/th_0530112157.jpg[/IMG]](http://s1238.photobucket.com/albums/ff491/senselocke/Ubuntu/?action=view&current=0530112157.jpg)
Hi, that could be because it is a raid drive but I do not know why it would not have it there. Here is a screen shot of mine. Hopefully someone with more experience with your setup will come and help out.

---

### Post by senselocke on 2011-05-31
Okie dokie, thanks for trying!

I changed the thread title to mention the Array/RAID drive. Hoping someone can help--I'd like to not have to pay someone just to transfer data over.

---

### Post by wildmanne39 on 2011-05-31
> **senselocke said:**
> Okie dokie, thanks for trying!

I changed the thread title to mention the Array/RAID drive. Hoping someone can help--I'd like to not have to pay someone just to transfer data over.hi, your welcome sorry I ran out of ideas.

---

