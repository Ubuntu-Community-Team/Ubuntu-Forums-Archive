---
title: "My computer is completely ruined"
date: 2009-12-17
forum: General Help
---

### Post by RideTheLight on 2009-12-17
Alright folks this is a long story so bear with me.

It all started with me having my nice little setup with XP on my primary 250GB HD and Karmic on a 80GB drive and all was well.

During a video card driver update XP decided it was completely and irreparably wrecked. I figured this would be a nice chance to install windows 7, so I hop over to ubuntu to prepare the necessary files.

At setup 7 tells me my 250gb HD has no windows 7 compatible partitions, which i think is very odd, so i assume some XP remnants are messing things up. I used DBAN on a 2 round swipe of the entire 250GB drive just to make sure nothing was left. I boot back into 7 and it still tells me no compatible partition even after i create one in the setup itself. 

This is where i really had to stop myself from smashing everything.

I boot back into ubuntu to seek help, and i read that windows 7 does not like grub at all, but thats weird since grub should only be on my 80gb drive and the 250 should have had ntdlr. I whipe the 250gb again with DBAN, unplug all other HDs, including ubuntu one. Figuring theres no way i can fail now. Same message, no compatible partitions. Why cant this damn installer create its own?

So i plug my ubuntu drive back in and boot up to find (ERROR READING OPERATING SYSTEM) in place of grub........So now ubuntu is gone for no reason like XP was greaaat.


To make a long story a bit shorter im having absolutely no luck getting either XP or 7 to install on my 250gb HD because of no compatible partition. Ive had 2 more ubuntu installs unexplainably die into (ERROR READING OPERATING SYSTEM)

Ive tried completely and utterly erasing both drives with gparted and dban to get rid of any trace of anything, but upon throwing in the live disk and activating an install it informs me i had windows XP on my 250 after many whipes and partitioning. 


So i sit here with no working operating system and google attempts to fix the ntdlr MBR are either completely wrong and useless or just dont work for what ever reason.

---

### Post by Lvcoyote on 2009-12-17
Use killdisk to write zero's to the hard drive, if that does not work then download a HDD utility from the manufacturer of the drive and check it, it could be as simple as a bad HDD.

---

### Post by LowSky on 2009-12-17
Without seeing you computer, you most likely did one of the following

1. Windows 7 will not install on FAT32, if you installed Windows XP on a FAT32 partition, then thats why, reformat to NTFS.

2. Ubuntu "disapeard" because you unpluged both drives, and proabably plugged the Ubuntu hard drive into the wrong port, the error happens becasue it looking for hd1,1 and your using hd0,1... 

3. I have no idea how you were erasing the drives, but if you reformated then Windows or Ubuntu would be gone

My suggestion install both drives.
Boot live CD into live desktop
format 250GB drive to NTFS
Format the 80GB drive to EXT4

Install windows 7
then install Ubuntu 9.10

your world will then be fine

---

### Post by RideTheLight on 2009-12-17
> **LowSky said:**
> Without seeing you computer, you most likely did one of the following

1. Windows 7 will not install on FAT32, if you installed Windows XP on a FAT32 partition, then thats why, reformat to NTFS.

2. Ubuntu "disapeard" because you unpluged both drives, and proabably plugged the Ubuntu hard drive into the wrong port, the error happens becasue it looking for hd1,1 and your using hd0,1... 

3. I have no idea how you were erasing the drives, but if you reformated then Windows or Ubuntu would be gone

My suggestion install both drives.
Boot live CD into live desktop
format 250GB drive to NTFS
Format the 80GB drive to EXT4

Install windows 7
then install Ubuntu 9.10

your world will then be fine

1. It was always ntfs until i wiped it
2. I made sure they were plugged in as they were before, my ubuntu drive is actually seperate from the other 3
3. You would think that but doing research into the vast and very confusing world of the MBR partition i have no idea whats goin on anymore.

Ive made the entire 250hd ntfs like 3 different times and 7 still tells me no compatible partition :/


Ill try 1 more time haha

---

### Post by stinger30au on 2009-12-17
out of interest when windows has a spit and says theres no compatable partition, does it even see *ANY* of the hard drives???

---

### Post by RideTheLight on 2009-12-17
> **stinger30au said:**
> out of interest when windows has a spit and says theres no compatable partition, does it even see *ANY* of the hard drives???

Sees all 4

---

### Post by Leppie on 2009-12-17
what does 7 say if you remove all partitions on the 250gig drive (or at least the xp system partition)?

---

### Post by lazychris2000 on 2009-12-17
Out of curiousity, if the drives are SATA, did you try loading the drivers during installation?  I think it is still F6 for windows 7 to load them.  All you gotta do is download them from the system manufacturer's website, copy them onto a USB drive (after extacting them of course).  As for ubuntu, you may need to reinstall grub ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)).  You will definately need to reinstall grub after installing win7.
Another thing to try would be boot from a karmic live cd/usb and run the disk utility and see if there are any problems with the drive.  Karmic has a utility that will check the SMART status of drives and let you know if it detects any problems.  This has saved me from a world of hurt caused by failing drives on quite a few occasions.  System-->Administration-->Disk Utility.  While you are in the live cd, you might try formatting the windows drive as ntfs (assuming it is not failing).

---

### Post by spydeyrch on 2009-12-17
During the win7 installation, does it give you a list of the 4 drives on your system? As I understand it, you rally only have 2 drives, a 25GB and an 80GB, right? correct me if I am wrong. And also, if I understand correctly, you have formatted both hdd multiple times, and there is currently no data on either of them, right?
 
If you can get to the part of the pre-installtion setup for win7 where it shows you the different drives/partitions, try to click on the advanced link/option down towards the bottom/center right. you should see delete, format, and maybe other options. if you have already formatted both drives and all partitions several times, then your data is all gone so do this:
 
single click on each of the partitions and drives, each time you click on one, take note of a possible exclimation mark in a yellow triangle. It will give you slight details to any issues that win7 might have with installing on that drive partition. Make note of them and come back with them to the forum.
 
Another thing. Win 7 requires a 100MB partition for system recovery and other stuff, being that all the space is possibly used, that may be the issue or an issue.
 
once you have single clicked on all the drives/partitions to take note of any yellow caution triangles, then go about deleting any and all partitions on the drives we want to end up with just the two drives that you have in your machine, one partition per drive.
 
select the 250GB drive, the entire drive, and format it (again), then select it to do your win7 install. Again, take note of any yellow triangle exclimation marks down below.
 
One other thing you could do, is just format it to RAW and not an actual file system.
 
Let me know if any of this works. :P
 
 
-spydey :guitar:

---

### Post by llawwehttam on 2009-12-17
Sounds like when your done you might have problems with your MBR so heres a helping hand. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by danielesil on 2009-12-17
> **lazychris2000 said:**
>  As for ubuntu, you may need to reinstall grub ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)). 

It seems to me that those instructions refer to Grub, and not to GRUB 2 which is the one used on the Karmic Koala.
There are some instructions out there specific for Grub 2

---

### Post by danielesil on 2009-12-17
On my Ubuntu One I have the files used to fix Windows' MBR .
They helped me when I had problems with my XP installation .
You can send me a message and I'll find a way to give them to you.

---

### Post by Leppie on 2009-12-17
> **danielesil said:**
> It seems to me that those instructions refer to Grub, and not to GRUB 2 which is the one used on the Karmic Koala.
There are some instructions out there specific for Grub 2

Instructions for [GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by RideTheLight on 2009-12-18
> **spydeyrch said:**
> During the win7 installation, does it give you a list of the 4 drives on your system? As I understand it, you rally only have 2 drives, a 25GB and an 80GB, right? correct me if I am wrong. And also, if I understand correctly, you have formatted both hdd multiple times, and there is currently no data on either of them, right?
 
If you can get to the part of the pre-installtion setup for win7 where it shows you the different drives/partitions, try to click on the advanced link/option down towards the bottom/center right. you should see delete, format, and maybe other options. if you have already formatted both drives and all partitions several times, then your data is all gone so do this:
 
single click on each of the partitions and drives, each time you click on one, take note of a possible exclimation mark in a yellow triangle. It will give you slight details to any issues that win7 might have with installing on that drive partition. Make note of them and come back with them to the forum.
 
Another thing. Win 7 requires a 100MB partition for system recovery and other stuff, being that all the space is possibly used, that may be the issue or an issue.
 
once you have single clicked on all the drives/partitions to take note of any yellow caution triangles, then go about deleting any and all partitions on the drives we want to end up with just the two drives that you have in your machine, one partition per drive.
 
select the 250GB drive, the entire drive, and format it (again), then select it to do your win7 install. Again, take note of any yellow triangle exclimation marks down below.
 
One other thing you could do, is just format it to RAW and not an actual file system.
 
Let me know if any of this works. :P
 
 
-spydey :guitar:

I have a 4 HDs, my two seagates are data drives. I dont know why this is happening but it sucks :/. The 250gb ive formatted with karmics disk utility, gparted on live disc and boot disc, DBAN(2 passes), and with the windows installers countless times in futile efforts. Ubuntu installs on the 250 but always ends in the OS error at boot after a couple hours by any restart or shutdown. This makes me think its a hardware problem.

When i try to install 7 it always says something like "No windows compatible partitions on this drive" whether there is a partition or not. Creating the partition itself with 7 installer yields the same effect. I have done this all a countless number of time changing every little thing I could do to maybe trick it into working. 

Im going to try tha subergrub thing as suggested by llawwehttam, Ill let you know how it turns out.

---

### Post by PRC09 on 2009-12-18
Is this a full install disk of Win7 or the upgrade disk.I think the Upgrade version requires a previously installed version of  Windows either XP or Vista to install....

---

### Post by RideTheLight on 2009-12-18
> **PRC09 said:**
> Is this a full install disk of Win7 or the upgrade disk.I think the Upgrade version requires a previously installed version of  Windows either XP or Vista to install....

To my knowledge its a full install. It doesnt matter anyway because XP still wont install either. 

Supergrub didnt really help so far. It did completely remove grub and i though that would help but apparently it didnt.


Still at a loss. I ordered a new HD. I feel defeated.

---

### Post by bkmfs on 2009-12-18
Would it be possible that perhaps you are trying to install windows on something other than what you computer would recognize as a primary partition?

---

### Post by Ordes on 2009-12-18
might be a hardware problem..and so far i dont see a different solution than already given..

however about your ubuntu / grub / mbr... its really hard to see your setup.. i reat it couple of times and still not sure. can u write it out more clearly..? definetaly helps for grub...

like  (thats how i think it is):

sda1  250, win
sdb1   80  ubu
sdc, sdd   data

in this case, when u completely wiped your first drive, grub is gone, even when ubu is on drive 2. But your ubu itself is safe, and u only need to work on grub. Unless you did some formating on sdb too
but as i said i am not sure of your hdd / partition set-up

---

### Post by RideTheLight on 2009-12-18
Supergrub got rid of grub but did not make it so windows 7 would install.


> **Ordes said:**
> might be a hardware problem..and so far i dont see a different solution than already given..

however about your ubuntu / grub / mbr... its really hard to see your setup.. i reat it couple of times and still not sure. can u write it out more clearly..? definetaly helps for grub...

like  (thats how i think it is):

sda1  250, win
sdb1   80  ubu
sdc, sdd   data

in this case, when u completely wiped your first drive, grub is gone, even when ubu is on drive 2. But your ubu itself is safe, and u only need to work on grub. Unless you did some formating on sdb too
but as i said i am not sure of your hdd / partition set-up
 
sda1 is the 250
sdb and c are my 320 and 500gb seagates
sdd is 80gb

As I said before ive formated both sda and sdd many times with various applications, XP and 7 refuse to install no matter what.

---

### Post by stinger30au on 2009-12-18
i did a quick google and found this

[http://forums.techguy.org/windows-xp/407793-disk-does-not-contain-windows.html](http://forums.techguy.org/windows-xp/407793-disk-does-not-contain-windows.html)


the last post sounds like the go:)

---

### Post by RideTheLight on 2009-12-19
> **stinger30au said:**
> i did a quick google and found this

[http://forums.techguy.org/windows-xp/407793-disk-does-not-contain-windows.html](http://forums.techguy.org/windows-xp/407793-disk-does-not-contain-windows.html)


the last post sounds like the go:)

Got it to work, thanks. I tried unplugging them before but i think using supergrub first did the trick. I was having a combination of 2 errors. Now i have to find a use for that new HD i ordered. Thanks for all your help guys.

---

