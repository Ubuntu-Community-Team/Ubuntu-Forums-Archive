---
title: "Wiping a Hard Drive"
date: 2009-09-21
forum: General Help
---

### Post by TylerTheWonderfull on 2009-09-21
Hi

I was wondering how exactly I would completely wipe my hard drive clean of every thing

I'm using what ever the latest version of ubuntu is by the way...

---

### Post by badger_fruit on 2009-09-21
fdisk should do the trick but if you seriously want to loose all the data, smash it with a hammer.
1tb's are only £60 now anyway ...

**[http://unixhelp.ed.ac.uk/CGI/man-cgi?fdisk+8](http://unixhelp.ed.ac.uk/CGI/man-cgi?fdisk+8)**

---

### Post by TylerTheWonderfull on 2009-09-21
> **badger_fruit said:**
> fdisk should do the trick but if you seriously want to loose all the data, smash it with a hammer.
1tb's are only £60 now anyway ...


I already have one but I want to clear it of every thing... I'll try fdisk

---

### Post by oboedad55 on 2009-09-21
> **TylerTheWonderfull said:**
> I already have one but I want to clear it of every thing... I'll try fdisk

You can use this: [http://www.dban.org/](http://www.dban.org/)

---

### Post by badger_fruit on 2009-09-21
> **TylerTheWonderfull said:**
> I already have one but I want to clear it of every thing... I'll try fdisk
lol, sorry - that wasn't not my most useful post ... there's a number of tools out there but fdisk WILL erase the MBR and partition tables - thus erasing the disk totally.

Depends on how secure you want to do it really ... there's tools that will format it to US Govt standards, disk shredders and so on.  Unless you're truly paranoid about the previous data then fdisk will do for you.

---

### Post by fishyf on 2009-09-21
Don't use fdisk, that only overwrites the partition table. Just overwrite the entire contents of the disk once and you will be safe. No need to destroy the disk.

assuming /dev/sda is the disk you want to zap, type
```
sudo dd if=/dev/null of=/dev/sda
```
Beware, it will not be possible to recover the data. There are stories going around the net that you can still recover the data. Latest experiments show that is not the case.
By the way, that command will take a long time, allow a minute for every gigabyte (it should be faster than that ... but as a rough rule).

dcfldd is a better program than dd as it shows progress - it's really boring waiting hours when nothing is displayed on the screen. You can install it using apt-get.

> **TylerTheWonderfull said:**
> Hi

I was wondering how exactly I would completely wipe my hard drive clean of every thing

I'm using what ever the latest version of ubuntu is by the way...

---

### Post by TylerTheWonderfull on 2009-09-21
> **badger_fruit said:**
> lol, sorry - that wasn't not my most useful post ... there's a number of tools out there but fdisk WILL erase the MBR and partition tables - thus erasing the disk totally.

Depends on how secure you want to do it really ... there's tools that will format it to US Govt standards, disk shredders and so on.  Unless you're truly paranoid about the previous data then fdisk will do for you.

it was pretty funny though xD

well... I'm completely new to ubuntu so the fdisk thing is kinda hard to understand...

---

### Post by TylerTheWonderfull on 2009-09-21
> **fishyf said:**
> Don't use fdisk, that only overwrites the partition table. Just overwrite the entire contents of the disk once and you will be safe. No need to destroy the disk.

assuming /dev/sda is the disk you want to zap, type
```
sudo dd if=/dev/null of=/dev/sda
```Beware, it will not be possible to recover the data. There are stories going around the net that you can still recover the data. Latest experiments show that is not the case.
By the way, that command will take a long time, allow a minute for every gigabyte (it should be faster than that ... but as a rough rule).

dcfldd is a better program than dd as it shows progress - it's really boring waiting hours when nothing is displayed on the screen. You can install it using apt-get.

hey thanks

by 1 minute per GB is that GB of file being deleted or the amount of GB's the HD is? cuz if it was that 1000 minutes is a LLLLLLLLLLOOOOOOOOONNNNNNNGGGGGGG time

---

### Post by sideaway on 2009-09-21
you could just reformat with gparted, it's easy to understand, and will erase partitions. Data recovery is possible.

---

### Post by fishyf on 2009-09-21
> **TylerTheWonderfull said:**
> hey thanks

by 1 minute per GB is that GB of file being deleted or the amount of GB's the HD is? cuz if it was that 1000 minutes is a LLLLLLLLLLOOOOOOOOONNNNNNNGGGGGGG time

You will likely want to overwrite all the disk as otherwise files that are deleted by the file system are possibly recoverable. That means 1 minute per GB of every G on the hard disk. It is a long time, but depending on your setup, a minute a GB is very conservative. You will probably manage 2GB per minute.
Just do it overnight ... no problem. In the morning, your disk is clean.

---

### Post by dhughes on 2009-09-21
> **sideaway said:**
> you could just reformat with gparted, it's easy to understand, and will erase partitions. Data recovery is possible.

I second that, it's easiest way. Just make sure to unmount it first and not wipe the wrong drive!

---

### Post by scouser73 on 2009-09-21
I've not used it, but I have heard good things about [[COLOR="Red"]**DBAN - Darik's Boot And Nuke**[/COLOR]]("http://sourceforge.net/projects/dban/files/dban/dban-2.0.0/dban-2.0.0_buildroot.tar.bz2/download")

---

### Post by Jimmynemo2 on 2009-09-21
Have used many times, and add one vote for DBAN- burn the CD, boot computer, say yes, and watch as ALL DATA DIES. So long as thats your goal, this is the most direct and simple rout to do what you are seeking, and do it well.

---

### Post by TylerTheWonderfull on 2009-09-21
> **Jimmynemo2 said:**
> Have used many times, and add one vote for DBAN- burn the CD, boot computer, say yes, and watch as ALL DATA DIES. So long as thats your goal, this is the most direct and simple rout to do what you are seeking, and do it well.

hey thank! I think I'll do it that way

---

### Post by Jimmynemo2 on 2009-09-21
Any time, it's what we're here for.

---

### Post by denver on 2009-09-21
Formating your disk does not erase all data. It just rewrites the filesystem and marks the blocks as being "unused", when in reality the information is still there. The filesystem takes up just a little bit of space on your disk drive. Also, deleting the partition is also useless. All partition information is kept in the first 512 bytes of your disk, so fishyf's suggestion of using dd to overwrite everything is the way to go.

Personaly, I use /dev/urandom to overwrite the disk, but hey :) its a matter of personal preference.

---

### Post by Jimmynemo2 on 2009-09-21
FYI, dban does go through and overwrite all the drive, 7 times, randomly. It's not just deleting the partition table.

---

### Post by denver on 2009-09-21
Awesome! Will look into it. Thanks for the tip.

Up until now i've been using dd because it's readily available. But again, thanks for the tip :).

---

### Post by Jimmynemo2 on 2009-09-21
as one last thing I forgot- Dban is free in both ways, the source is hosted on sourceforge.

---

