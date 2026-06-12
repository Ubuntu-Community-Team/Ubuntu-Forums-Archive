---
title: "Ubuntu 10.04 and disk space"
date: 2010-05-14
forum: General Help
---

### Post by newarkdanny on 2010-05-14
So i got my CD with Ubuntu on it, tried the demo first, liked it so deiced to install it as a dual boot with WIN7 on my laptop ( a dell insipron 15 series) everything went fine , until i tried using Firefox i got a message that disk space was low and ever since them i been try to find hot to fix this issue, i tried uninstalling some software and other things but nothing helps, and now i even get the message when tryin to install a simple add on for FF i did check and the /sda5 drive is 98% full :confused:


 any ideas what it could be? did i install Ubuntu wrong? is there a way of doing a fresh installation so i could change the partition size it uses or something?

---

### Post by dabl on 2010-05-14
If you can download the ISO and make a Parted Magic Live CD:

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

then you can boot that and use the partitioner to enlarge the /dev/sda1 partition.  Make it 10G or 15G and you should not have any problem, unless you go crazy downloading movies and such.

---

### Post by Sin@Sin-Sacrifice on 2010-05-14
You can do what newarkdanny suggested with the livecd you installed with and gparted. Not sure why deleting things didn't help though. Perhaps they were all small files?

---

### Post by newarkdanny on 2010-05-14
> **Sin@Sin-Sacrifice said:**
> You can do what newarkdanny suggested with the livecd you installed with and gparted. Not sure why deleting things didn't help though. Perhaps they were all small files?


well that is the other issue i installed gparted but and from what i have read i have to "unmount" the drive before i can resize it , when i right click and select unmount /sda5, it tells me that i have to do it manually which i have no idea how to do it

so i can use the livecd i installed i with to change the partition size?

---

### Post by dabl on 2010-05-14
> **newarkdanny said:**
> 

so i can use the livecd i installed i with to change the partition size?

Yes, if it has GParted on it.

The reason I suggested the Parted Magic Live CD is that there's no issue about mounting the drive (same as your Ubuntu Live CD).

The Parted Magic CD also has some nice utilities -- a GUI front end to the SMART hard drive analysis info, some benchmarking tools, etc.

---

### Post by newarkdanny on 2010-05-14
> **dabl said:**
> Yes, if it has GParted on it.

The reason I suggested the Parted Magic Live CD is that there's no issue about mounting the drive (same as your Ubuntu Live CD).

The Parted Magic CD also has some nice utilities -- a GUI front end to the SMART hard drive analysis info, some benchmarking tools, etc.

ok so am tryin to use gparted right from the OS not the cd, and when i select the partion and try to unmount so i can resize it i get this message

> The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

what can i do:confused:

also i just noticed something when i did a restart on my laptop the load screen that allows me to chose an OS i have 

2 OS's called  "Ubuntu-linux"  (there different versions) 

them 2 "ubuntu linux recovery mode" (one for each of the above versions)

and Windows 7 OS

is that normal?

---

### Post by newarkdanny on 2010-05-15
anybody? plz:(

---

### Post by jerome1232 on 2010-05-15
You can't work on your root partition while it's mounted, which means you can't run gparted while your os is running.


You need to use the live cd you used to install (it has gparted on it) or use a gparted live cd to edit your partition.

---

### Post by newarkdanny on 2010-05-15
> **jerome1232 said:**
> You can't work on your root partition while it's mounted, which means you can't run gparted while your os is running.


You need to use the live cd you used to install (it has gparted on it) or use a gparted live cd to edit your partition.

:) ok so i have gottten this far gparted from the livecd allows me to resize now how much size am i supposed to add:confused:? it only works in MB not gigs

---

### Post by jerome1232 on 2010-05-15
The answer is, that depends. 

If your keeping your personal media (pictures, videos, music) on another drive then 6 - 9 GB (or about 6000 to 9000 MB) is plenty of space for an Ubuntu installation with room to grow. Mine is about 4.8 GB's used with a few extra's installed.

If your going to be storing your music and pictures on the main Ubuntu partition then your needs will vary based on how much crap you have. I'd go with 20 - 40 GB's at least.

remember there are 1024 MB's in a GB, so if you want to know how many MB's makes a certain amount of GB just multiply the number of gigabytes by 1024.

edit: and by divide I meant multiply :)

---

### Post by newarkdanny on 2010-05-15
> **jerome1232 said:**
> The answer is, that depends. 

If your keeping your personal media (pictures, videos, music) on another drive then 6 - 9 GB (or about 6000 to 9000 MB) is plenty of space for an Ubuntu installation with room to grow. Mine is about 4.8 GB's used with a few extra's installed.

If your going to be storing your music and pictures on the main Ubuntu partition then your needs will vary based on how much crap you have. I'd go with 20 - 40 GB's at least.

remember there are 1024 MB's in a GB, so if you want to know how many MB's makes a certain amount of GB just divide the number of gigabytes by 1024.


Thanks for all the help but it is teling me that the maximum i can go on the partition is something like 2500mbs , and am already using 2450 , so i think my fears were correct i somehow installed ubuntu on a drive other than my C: drive

is there any way of just doing a fresh install like can i just put the live cd back in and install a fresh Ubuntu ?

---

### Post by jerome1232 on 2010-05-15
Are you wanting to just have Ubuntu or are you wanting to dual boot Windows/Ubuntu?

Why don't you toss a screen shot of Gparted so we can see what your talking about?

---

### Post by samg34 on 2010-05-15
make sure to back everything up first. Repartitioning is dangerous. I always used the LiveCD for that. Let me know if there is another way
also try making other partitions smaller

---

### Post by ryan858 on 2010-05-15
We need more information to figure out what's going on here...

But from what I can infer, you probably installed Ubuntu on the "Recovery" partition made by the computer's manufacturer. HP, Dell, Gateway, and companies like that tend to make a small partition, like 4GB or such, for data backups so they can use their recovery tool when you bork Windows...

---

### Post by newarkdanny on 2010-05-15
> **ryan858 said:**
> We need more information to figure out what's going on here...

But from what I can infer, you probably installed Ubuntu on the "Recovery" partition made by the computer's manufacturer. HP, Dell, Gateway, and companies like that tend to make a small partition, like 4GB or such, for data backups so they can use their recovery tool when you bork Windows...


this is what i think happened my dell recovery drive is 7 gigs, but when i go on my win7 os 5.9 gigs free, and there is no files that are named ubuntu or anything like that so i dunno :confused:

here is some screen shots of gparted and other system checks i did 

[http://i40.tinypic.com/bjg5s7.png](http://i40.tinypic.com/bjg5s7.png)

[http://i42.tinypic.com/34s5tmv.png](http://i42.tinypic.com/34s5tmv.png)

[http://i39.tinypic.com/zjcya8.png](http://i39.tinypic.com/zjcya8.png)

as you can see its "sda5" thats giving me issues , and when i try to resize there is no more room for me to make it bigger , so i want to put it on "sda3" which i am assuming is my C: drive , which as you can tell as plenty of space

> **jerome1232 said:**
> Are you wanting to just have Ubuntu or are you wanting to dual boot Windows/Ubuntu?

Why don't you toss a screen shot of Gparted so we can see what your talking about?


i want to dual boot

---

### Post by Sin@Sin-Sacrifice on 2010-05-16
Ok dude... the c: drive as windows calls it is /dev/sda3 according to the screen shot and unless you want to lose windows you don't want to install there. To be able to resize the ubuntu partition you're gonna have to take from the C: (/dev/sda3) so right click it and select shrink or resize or whatever it says. Shrink it down about 40 GB (40960 MB). In other words when the window comes up after selecting resize go to the box that says final drive size and type in the current drive size minus 40960 (Current Size is about 295208.96 so subtracting 40960 would give you 254248.96). The other boxes should adjust. Click Resize/Move and you'll see "Unallocated space". That you will add to you /dev/sda5 partition (this is where ubuntu is installed). Right click it and select resize, add the amount of unallocated space to the final size of /dev/sda5 and click resize/move. Once all changes are satisfactory to you... just click the checkmark. From there you should be golden.

---

### Post by john newbuntu on 2010-05-16
> **newarkdanny said:**
>  but when i go on my win7 os 5.9 gigs free

If I understand you correctly, if you have just 5.9 GB free in a 310 GB partition that houses Win7 and your linux partition is full and the recovery/utility partitions can not be messed with, it is time for a new disk.  Or, you might want to offload some of your win-7 data to another disk to create space.

In a 2.6GB linux install, there is little scope for space recovery, although, once you delete some of the archived/compressed log files in /var/log, you can install "bleachbit" and do more cleanups.

---

### Post by newarkdanny on 2010-05-16
> **Sin@Sin-Sacrifice said:**
> Ok dude... the c: drive as windows calls it is /dev/sda3 according to the screen shot and unless you want to lose windows you don't want to install there. To be able to resize the ubuntu partition you're gonna have to take from the C: (/dev/sda3) so right click it and select shrink or resize or whatever it says. Shrink it down about 40 GB (40960 MB). In other words when the window comes up after selecting resize go to the box that says final drive size and type in the current drive size minus 40960 (Current Size is about 295208.96 so subtracting 40960 would give you 254248.96). The other boxes should adjust. Click Resize/Move and you'll see "Unallocated space". That you will add to you /dev/sda5 partition (this is where ubuntu is installed). Right click it and select resize, add the amount of unallocated space to the final size of /dev/sda5 and click resize/move. Once all changes are satisfactory to you... just click the checkmark. From there you should be golden.

this is what i was looking for but now another issue , gparted is not letting me resize the SDA3 partition (yes i made sure it was unmounted and i was using gparted from the live cd ), so i did some research online and found out that win7 has a partitioning software and this is what its telling me

[http://i41.tinypic.com/xdxpw9.png](http://i41.tinypic.com/xdxpw9.png)

basically that i only have 3806 mbs worth of space to work with, i honestly dont even want to try to figure whats going on now

**someone just tell me this can i do a fresh install of ubuntu like just pop the cd in and start from scratch??, so them when i get to the parotiong step i can tell it how much space to use? and will it write over the one am using now**

---

### Post by jerome1232 on 2010-05-16
> **newarkdanny said:**
> this is what i was looking for but now another issue , gparted is not letting me resize the SDA3 partition (yes i made sure it was unmounted and i was using gparted from the live cd ), so i did some research online and found out that win7 has a partitioning software and this is what its telling me

[http://i41.tinypic.com/xdxpw9.png](http://i41.tinypic.com/xdxpw9.png)

basically that i only have 3806 mbs worth of space to work with, i honestly dont even want to try to figure whats going on now

**someone just tell me this can i do a fresh install of ubuntu like just pop the cd in and start from scratch??, so them when i get to the parotiong step i can tell it how much space to use? and will it write over the one am using now**

No you just don't have enough space left on that disk. Your Windows Partition is so full that you can barely resize it, and I wouldn't shrink it too much with it being that full.

You honestly need another disk if you want to run two OS's with that amount of data.

---

### Post by newarkdanny on 2010-05-16
> **jerome1232 said:**
> No you just don't have enough space left on that disk. Your Windows Partition is so full that you can barely resize it, and I wouldn't shrink it too much with it being that full.

You honestly need another disk if you want to run two OS's with that amount of data.

i know but this what "my computer" is telling me so am :confused:

[http://i44.tinypic.com/ncmpa9.png](http://i44.tinypic.com/ncmpa9.png)

218 gigs of 288 are free

so i just wanna move on and try to fresh reinstall Ubuntu , can i do that with it installing it self twice?

---

### Post by jerome1232 on 2010-05-16
In that case the reason you have so little wiggle room is the disk is fragmented, there is some data sitting about 3 GB's worth of cylinders away from the end of the partition.

The solution would be to defragment the thing. That should move that data away from the end of the partition.

If you can defrag from safe mode it will be a little more effective. I think there are some defrag tools out there that can try and cram as much stuff towards the front of the partition as possible, that will help considerably with wiggle room for resizing.

---

### Post by ryan858 on 2010-05-16
> **jerome1232 said:**
> I think there are some defrag tools out there that can try and cram as much stuff towards the front of the partition as possible, that will help considerably with wiggle room for resizing.
 
Doesn't GParted do that when resizing? I've never had any problems resizing a windows partition that is fragmented and has data near the end of the partition... GParted just squeezes it down as needed...

---

### Post by jerome1232 on 2010-05-16
> **ryan858 said:**
> Doesn't GParted do that when resizing? I've never had any problems resizing a windows partition that is fragmented and has data near the end of the partition... GParted just squeezes it down as needed...

I honestly don't know, I remember having problems with it in the past (this was probably 8.04 or 7.10 so a long time ago)

A defrag helped me then. It's definitely possible tools have improved since then, but this situation fits that issue to me.

(his disk has a good chunk of space left but it will barely let him resize)

---

### Post by ryan858 on 2010-05-16
It could have something to do with Win7's partitioning scheme... IIRC, Win7 by default, doesn't use the old DOS partitioning, or uses a new version of NTFS, or something like that.

---

### Post by ryan858 on 2010-05-16
As for how to get Ubuntu some space... I think resizing *sda3* is the thing to do, if it can be made to report the size correctly that is... Otherwise it would cause some serious problems, if you resized it without GParted having the right information... maybe you can try:

[B]$ fdisk /dev/sda
> x
> f
> w[/B]

(Enter 'M' in fdisk for commands listing) x is for* eXtra functions*, f is *Fix disk order*, w is *Write changes to disk and exit*... Press Q to quit without changes...

I don't know if that will do anything at all though...



Besides resizing *sda3*, you can also delete *sda1* and *sda2*. You don't need the recovery partitions to use Windows... You would only need them if you wanted to use the Dell Recovery tool or send the computer in to Dell's tech support... Of course, having removed them, Dell probably won't help you anymore, since it would probably void the any warranty... So think that through before you delete them.

Then, you can either resize *sda5*, or, what I personally would do if it was my drive, delete *sda4* since it's an extended partition, and you don't need one unless you already have 3 primary partitions. This would delete the ext4 and swap partitions (ubuntu and all), and leave only the Windows 7 partition. Then, create a new swap, then a new ext4. You'll have a good 8-10 GB for ubuntu and swap. Then install Ubuntu again, on the new ext4 using the new swap, and all done.

Deleting those other partitions (*sda1, sda2, sda4*) might also fix the size problem with *sda3*...

---

### Post by newarkdanny on 2010-05-16
> **ryan858 said:**
> .


**Besides resizing *sda3*, you can also delete *sda1* and *sda2*. You don't need the recovery partitions to use Windows... You would only need them if you wanted to use the Dell Recovery tool or send the computer in to Dell's tech support... Of course, having removed them, Dell probably won't help you anymore, since it would probably void the any warranty... So think that through before you delete them.**

**Then, you can either resize *sda5*, or, what I personally would do if it was my drive, delete *sda4* since it's an extended partition, and you don't need one unless you already have 3 primary partitions. This would delete the ext4 and swap partitions (ubuntu and all), and leave only the Windows 7 partition. Then, create a new swap, then a new ext4. You'll have a good 8-10 GB for ubuntu and swap. Then install Ubuntu again, on the new ext4 using the new swap, and all done.**

Deleting those other partitions (*sda1, sda2, sda4*) might also fix the size problem with *sda3*...

:) ok i ended up doing this and it all worked out so far , deleted the recovery so am using the recovery space + the sda5 space from before so thats gives me about 11gigs for Ubuntu which should be enough space from what you guys telling me right???

once again thats for all the help

---

