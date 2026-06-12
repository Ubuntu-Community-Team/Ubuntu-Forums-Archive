---
title: "brand new 500gig"
date: 2009-12-17
forum: General Help
---

### Post by ubunfreak on 2009-12-17
hi there you guys :) i just got a new hard drive for my ubuntu and i just installed it to my new 500gig. so why does it show 424 :confused:

---

### Post by Darael on 2009-12-17
Hard drive manufacturers use a definition of "gigabyte" that's significantly smaller than the one your computer uses. That means your drive will always look smaller in a computer than the size given on the box.

---

### Post by hwttdz on 2009-12-17
Ask, "sudo fdisk -l" and see what it says there?  And responding to above this is possibly in part true up to the 1024/1000 convention, however this doesn't explain all of the difference your seeing.  Also you've already used 3 gigs, so you're actually looking at an observed difference of 63 GB as opposed to the 76 you thought (this is still a lot), and if fdisk tells you the drive is actually quite a bit smaller than what the manufacturer said I might suggest calling them up.

---

### Post by Darael on 2009-12-17
> **hwttdz said:**
> Ask, "sudo fdisk -l" and see what it says there?

Good point, there may be a hidden partition or something. I don't think the definition discrepancy quite explains the magnitude of the "missing" space.

---

### Post by ubunfreak on 2009-12-17
> **hwttdz said:**
> Ask, "sudo fdisk -l" and see what it says there?

Disk /dev/sda: 500.1 GB, 500107862016 bytes

---

### Post by warfacegod on 2009-12-17
It also depends on what filesystem is being used i.e. ext4, NTFS, FAT32, etc.

When I looked at the attachment, I, like a dimwit, tried to close it with the Close button in the picture. Duh!

---

### Post by ubunfreak on 2009-12-17
i just hooked up my new hard drive and installed ubuntu 9.04 jaunty

i just want to know is this normal for a 500gig ? or is there something wrong ? can anyone confirm please and thanks.

---

### Post by hwttdz on 2009-12-17
So it looks like the drive is 500 GB, being the brilliant people we are, we all forgot that you have a swap partition (which is about 5 times the size it needs to be, I count that at 10 gigs (why is fdisk output so annoying)).  So you have a 500 GB drive, 10 GB of which is swap, and 490 of which is your actual system.

You can also look at "sudo gparted" which gives you a nice graphical representation of your partitions and whatnot.

---

### Post by ubunfreak on 2009-12-17
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59578   478560253+  83  Linux
/dev/sda2           59579       60801     9823747+   5  Extended
/dev/sda5           59579       60801     9823716   82  Linux swap / Solaris

---

### Post by cormano on 2009-12-17
Acording to my calculations, a 500GB drive has 465GB considering the 1024+-=1000 trick manufacturers use.
I dont know how much you are using for swap, but aside of that, ext and other unix filesystems reserve a percentage of blocks for exclusive use of the root user. In ubuntu this defaults to 5%, which steals you another 23GB(ive always found this default to be a little insane).

An easy way to change that is: 

sudo tune2fs -m 0 /dev/sda3 

where 0 is the percentage (0 in this case) that you reserve for the root, and /dev/sda3 is the partition you would like to adjust .

---

### Post by hwttdz on 2009-12-17
I had no idea so much space was reserved for root.  Is this only on / or does it also apply to other partitions?

---

### Post by ubunfreak on 2009-12-17
> **cormano said:**
> Acording to my calculations, a 500GB drive has 465GB considering the 1024+-=1000 trick manufacturers use.
I dont know how much you are using for swap, but aside of that, ext and other unix filesystems reserve a percentage of blocks for exclusive use of the root user. In ubuntu this defaults to 5%, which steals you another 23GB(ive always found this default to be a little insane).

An easy way to change that is: 

sudo tune2fs -m 0 /dev/sda3 

where 0 is the percentage (0 in this case) that you reserve for the root.

while installing i used the use entire disk install and just installed it, i just did a normal install from cd i had sent to me from ubuntu before. is something wrong with my drive? or does this look normal or what should i do?

---

### Post by hwttdz on 2009-12-17
Drive is absolutely fine.  There's just the 1024 thing and the space for root and swap that make it seem smaller.

---

### Post by cormano on 2009-12-17
> **hwttdz said:**
> I had no idea so much space was reserved for root.  Is this only on / or does it also apply to other partitions?

It applies, to all particions created from ubuntu.

---

### Post by ubunfreak on 2009-12-17
> **hwttdz said:**
> Drive is absolutely fine.  There's just the 1024 thing and the space for root and swap that make it seem smaller.

so nothing is defective? i was not sold a hard drive that was returned to the store with a virus and then resold to me? i sure hope not :(  so its ok to now go ahead with my ubuntu updates? thanks for helping me :)

---

### Post by Darael on 2009-12-17
No, you weren't! And even if you were, there are no viruses currently "in the wild" that target anything other than the Win32 API (ie Windows) so you're pretty safe anyway.

For anyone questioning my statistic, take a look at the wildlist. (wildlist.org)

---

### Post by scouser73 on 2009-12-17
> **Darael said:**
> Hard drive manufacturers use a definition of "gigabyte" that's significantly smaller than the one your computer uses. That means your drive will always look smaller in a computer than the size given on the box.

While **^That is true^**, a 500Gb hard drive formatted to NTFS will show as 465.7Gb's

If you don't have any data on the drive, reformat it to NTFS which doesn't use any space.

---

### Post by ubunfreak on 2009-12-17
> **scouser73 said:**
> While **^That is true^**, a 500Gb hard drive formatted to NTFS will show as 465.7Gb's

If you don't have any data on the drive, reformat it to NTFS which doesn't use any space.

so now im back to confused again :confused: is there something wrong with my hard drive? when i put the drive in my pc it was not formated to anything, it would be like using killdisk and then doing an install right after that with ubuntu.

---

### Post by ubunfreak on 2009-12-17
I was going to go download ubuntu 9.10 and only got to type u and get this screen :confused:

Anyone know ?

---

### Post by scouser73 on 2009-12-17
No, there is nothing wrong with your hard drive.

---

### Post by ubunfreak on 2009-12-17
> **scouser73 said:**
> No, there is nothing wrong with your hard drive.

you know what the above pic is caused from? thanks for reading my crap, im just trying to learn like the rest of the world :)

---

### Post by ubunfreak on 2009-12-18
> **ubunfreak said:**
> I was going to go download ubuntu 9.10 and only got to type u and get this screen :confused:

Anyone know ?
  
](*,)

---

