---
title: "How to merge two hard drives"
date: 2009-11-29
forum: General Help
---

### Post by Garofoli on 2009-11-29
Hello,
I know there are threads about this but I want to get answers specifically for my set-up. I have a dell laptop with 2x320gb hdds in it and I am only using one of them as it is set as my C. Under Gparted these appear as different devices and I am unable to combine the two. How would I go about making these register as one. I am planning losing all data and reseting my computer. Thank you! :D

---

### Post by Bucky Ball on 2009-11-29
If you have two physical drives in your machine I don't think you can make them appear as one. Not sure of your thinking here. Little more detail as to what you are attempting to achieve with this process. :)

---

### Post by Garofoli on 2009-11-29
> **Bucky Ball said:**
> If you have two physical drives in your machine I don't think you can make them appear as one. Not sure of your thinking here. Little more detail as to what you are attempting to achieve with this process. :)

That is pretty much the situation I have, two drives that are physically separate. I am just trying to have them appear as a single 640gb drive. I thought this was possible. Thank you.

---

### Post by Agent ME on 2009-11-29
Yes, what you want is possible.

Use the Alternate Install disc, and when it asks you, tell it you want to use LVM. You'll be able to do exactly what you want - put both discs in the same volume group, and then your files will be transparently distributed on both discs. If you have two 320 gb hard drives, you'll be able to make your / filesystem be 640 gb (well, probably 630-ish since some will go to swap and /boot partitions as usual).

Here's a [good webpage on LVM](http://www.linux.org/docs/ldp/howto/LVM-HOWTO/) that you can read up at if you need to know what certain LVM terms mean.

---

### Post by Garofoli on 2009-11-29
> **Agent ME said:**
> Yes, what you want is possible.

Use the Alternate Install disc, and when it asks you, tell it you want to use LVM. You'll be able to do exactly what you want - put both discs in the same volume group, and then your files will be transparently distributed on both discs. If you have two 320 gb hard drives, you'll be able to make your / filesystem be 640 gb (well, probably 630-ish since some will go to swap and /boot partitions as usual).

Here's a [good webpage on LVM](http://www.linux.org/docs/ldp/howto/LVM-HOWTO/) that you can read up at if you need to know what certain LVM terms mean.

Awesome! Can this be done when installing Windows 7 and not linux? Linux might come later.

---

### Post by Agent ME on 2009-11-29
LVM is linux only (linux volume manager), but I think some sort of RAID on Windows can do what you want. I'd google "windows setting up software raid" or such if I were you to find out more since I don't know much about it.

---

### Post by Garofoli on 2009-11-29
> **Agent ME said:**
> LVM is linux only (linux volume manager), but I think some sort of RAID on Windows can do what you want. I'd google "windows setting up software raid" or such if I were you to find out more since I don't know much about it.

Does anyone know a simple RAID guide for my purposes? What I found seemed incredibly difficult as it also assumed that I was running windows when I'd like to use raid as I'm installing.

---

### Post by dcstar on 2009-11-29
> **Garofoli said:**
> Hello,
I know there are threads about this but I want to get answers specifically for my set-up. I have a dell laptop with 2x320gb hdds in it and I am only using one of them as it is set as my C. Under Gparted these appear as different devices and I am unable to combine the two. How would I go about making these register as one. I am planning losing all data and reseting my computer. Thank you! :D

Using two physical drives as one logical device - the misnamed "RAID 0" because it is the exact opposite of RAID - effectively halves the reliability of the logical device and means that if one drive fails, you lose **all** the data on both drives.

Unless there is a truly compelling reason for you to require all the combined disk space, it just make your system more vulnerable to data loss.

---

### Post by Garofoli on 2009-11-29
> **dcstar said:**
> Using two physical drives as one logical device - the misnamed "RAID 0" because it is the exact opposite of RAID - effectively halves the reliability of the logical device and means that if one drive fails, you lose **all** the data on both drives.

Unless there is a truly compelling reason for you to require all the combined disk space, it just make your system more vulnerable to data loss.

That would suck terribly, but honestly before this PC I've been used to that risk so I wouldn't mind it again. I just have a lot of data in gigantic folders (ie. music) that I wouldn't want split over two drives. I'm assuming it is possible to install ubuntu and use LVM to combine the drives, install windows and I'll be good. Right? Thank you!

---

### Post by Garofoli on 2009-11-30
> **Garofoli said:**
> That would suck terribly, but honestly before this PC I've been used to that risk so I wouldn't mind it again. I just have a lot of data in gigantic folders (ie. music) that I wouldn't want split over two drives. I'm assuming it is possible to install ubuntu and use LVM to combine the drives, install windows and I'll be good. Right? Thank you!

Any update?

---

### Post by bodhi.zazen on 2009-11-30
for Linux use LVM.

Windows will not use LVM, so for Windows support please use a Windows forums.

---

### Post by Garofoli on 2009-11-30
> **bodhi.zazen said:**
> for Linux use LVM.

Windows will not use LVM, so for Windows support please use a Windows forums.

I'm curious if I could use LVM for ubuntu and then install Windows ontop of that and retain the single hard drive. Thank you

---

### Post by teward on 2009-11-30
If you have questions revolving around doing this with Windows (sorry for sending people to another site), you can check out forums.windrivers.com and post there.  They can help with almost any issue.  But I think my thoughts below are correct, and you won't need their help.

As for the general idea of merging two drives, unless you use a really-really-difficult-to-setup-and-manage hardware interface, you're stuck with it reading as two separate drives.  This is because the two drives are physically separate from one another.  Also, if you're putting files there, and the file(s) get fragmented onto both drives, and one is down, you're screwed.

---

### Post by bodhi.zazen on 2009-11-30
> **Garofoli said:**
> I'm curious if I could use LVM for ubuntu and then install Windows ontop of that and retain the single hard drive. Thank you

What is it you are wanting to do exactly ?

The explore2fs claims it will mount LVM :

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

See the features list (LVM2 is on the list).

That is not the same as saying you  can install Windows into a LVM driver.

I will ask the unasked question, why the bother ? Why is it so important to see this as a single hard drive ? If you are not taking advantage of the features of LVM it really does not matter that it is 2 hard drivers.

---

### Post by seeker5528 on 2009-11-30
> **dcstar said:**
> Using two physical drives as one logical device - the misnamed "RAID 0" because it is the exact opposite of RAID - effectively halves the reliability of the logical device and means that if one drive fails, you lose **all** the data on both drives.

While not part of the originally intended purpose, RAID 0 is not the opposite of raid, just a different option you have with RAID.

Either you can go for extra speed or you can go for extra reliability or more recently [both](http://www.acnc.com/04_01_10.html).

Later, Seeker

---

### Post by Garofoli on 2009-11-30
I suppose you are all right. I shouldn't be worrying about combining them. Sorry to waste everyone's time, haha. Thanks all!

---

### Post by Bucky Ball on 2009-11-30
This thread has a achieved one thing. I now know about LVM and stand corrected. :)

---

### Post by dcstar on 2009-12-01
> **seeker5528 said:**
> While not part of the originally intended purpose, RAID 0 is not the opposite of raid, just a different option you have with RAID.


NO. The first "R" in RAID stands for Redundancy (Redundant Array of Inexpensive Disks) - every other RAID setup increases redundancy except "RAID 0" which halves it.

There is absolutely NO redundancy in RAID 0, it is a travesty of language categorising such a configuration with things that actually increase redundancy.

Striping (RAID 0) may well be an Array of Inexpensive Disks, but there is no "R" whatsoever and whoever was responsible for initially having it grouped with redundant configurations should get the proverbial size-9 up the coit!

If simple striping needs an acronym, then it should probably be "FAID 0" - Fragile Array of Inexpensive Disks.

---

### Post by jbrown96 on 2009-12-01
you don't want to do RAID0. Do LVM.

LVM is really cool because it works on partitions and not disks. I believe that grub2 (used in Ubuntu 9.10) can boot directly from lvm without a separate /boot. 

You need an alternate install disk to setup lvm. 
1) create your windows partition. Just setup the size and don't bother formatting it (windows will re-format it anyways) for a file system ("don't use"). We will assume that this is /dev/sda1. Then create a new partition on that same disk for lvm. Then use /dev/sdb entirely for lvm. Set them up to be in the same lvm. All your disk space will appear as one large partition.

I generally recommend creating /home as a separate partition. It makes it much easier if you need to reinstall Ubuntu. Once you create the lvm, you create partitions in it. Just make one for / and another for /home. 10GB for / would be plently of room.

---

### Post by seeker5528 on 2009-12-01
> **dcstar said:**
> Striping (RAID 0) may well be an Array of Inexpensive Disks, but there is no "R" whatsoever and whoever was responsible for initially having it grouped with redundant configurations should get the proverbial size-9 up the coit!

Maybe they figured the zero was a clue.

Maybe if they had to do it again they would call it 'RAID... Naught!!!'. :p

Later, Seeker

---

### Post by bodhi.zazen on 2009-12-01
> **dcstar said:**
> If simple striping needs an acronym, then it should probably be "FAID 0" - Fragile Array of Inexpensive Disks.

LOL !!!!!


> **jbrown96 said:**
> you don't want to do RAID0. Do LVM.

No, but people often combine LVM with either RAID or Encryption.

> LVM is really cool because it works on partitions and not disks. I believe that grub2 (used in Ubuntu 9.10) can boot directly from lvm without a separate /boot. 

You need an alternate install disk to setup lvm. 
1) create your windows partition. Just setup the size and don't bother formatting it (windows will re-format it anyways) for a file system ("don't use"). We will assume that this is /dev/sda1. Then create a new partition on that same disk for lvm. Then use /dev/sdb entirely for lvm. Set them up to be in the same lvm. All your disk space will appear as one large partition.

I generally recommend creating /home as a separate partition. It makes it much easier if you need to reinstall Ubuntu. Once you create the lvm, you create partitions in it. Just make one for / and another for /home. 10GB for / would be plently of room.LVM is fantastic and has a ton of cool features including snapshots.

LVM can be problematic, however, when 1 HD fails :( (which is why people often combined LVM with RAID).

Your solution will work, but not quite as the OP requested as both OS will see two HD still. I believe the question is , can you install Windows in to LVM ?

See post 5 :

> Awesome! Can this be done when installing Windows 7 and not linux? Linux might come later.

---

