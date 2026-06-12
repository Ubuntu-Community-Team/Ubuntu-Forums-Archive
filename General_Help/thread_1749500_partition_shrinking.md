---
title: "partition shrinking"
date: 2011-05-04
forum: General Help
---

### Post by K4NEB on 2011-05-04
Hey everyone. 

just been trying ubuntu out on wubi, and now im going to install it into a partition.

just went to partition my hard disk (on windows) and was hoping to split it straight down the middle, its 225gb and i have 158gb free

but it will only let me shrink it down by 11 gb or so.

how do i arrange all the files on the hardrive so i can shrink it down smaller so i can get the max amount of disk space to install unbuntu onto?

help will be very much appreciated as i have unbuntu downloaded ready to install :( i want to use it now! lol :D

regards

---

### Post by oldfred on 2011-05-04
What version of windows? How many partitions have you already used?

You should use windows MMC for Vista or 7. Windows has nothing for XP, so gparted is fine for that. Do not use windows to create new partitions as it cannot see nor create Linux partitions.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by K4NEB on 2011-05-04
Vista. the worst one :( lol

Currently it is in two partitons one i cant do anything with the only option on it is help, im guessing that a boot system or something. the second is my c drive.

so i want to slpit my c drive down the middle.

what do you mean when you say "Do not use windows to create new partitions as it cannot see nor create Linux partitions"

thanks for the links btw :D

---

### Post by oldfred on 2011-05-04
Some have used the MMC from Vista or win7 to create extra partitions thinking Ubuntu would use them. If you exceed the 4 primary partitions windows does not add an extended, but converts to a logical volume manager called dynamic partitions. Windows standard partitions are basic. 

If drive is converted to dynamic then it can be difficult to convert back. Windows official policy is backup, delete everything, reinstall and restore all data. Or one click to convert to dynamic and days to convert back.

There are some third party tools that may work on converting dynamic to basic.

---

### Post by VanR on 2011-05-04
I suggest defragging that drive in Windows. That might give you some more free space. Ask me how I know? I just enlarged my Zorin OS 4 partition with about 100 GB's I stole from Windows 7 this morning.
I Used Disk Mangement in Windows 7 to shrink the Windows partition. Don't know what Vista has though.

---

### Post by sdc444 on 2011-05-04
VanR is right, defragging generally gives you a lot more space (but maybe not in Vista)

Don't bother with Windows' built in tool, use something like Defraggler that takes less time and gets out more fragmentation.

---

### Post by VanR on 2011-05-04
> **sdc444 said:**
> VanR is right, defragging generally gives you a lot more space (but maybe not in Vista)

Don't bother with Windows' built in tool, use something like Defraggler that takes less time and gets out more fragmentation.

Sometimes defragmenting helps and sometimes you just get what you get.

---

### Post by K4NEB on 2011-05-05
yes yes i know how to defrag :P lol :D

i used perfectdisk 11 last night and it took forever, but it decided it wanted to move an unmovanle file right to edge of my hardrive!

so i am now unable to shrink it! :(

extremely annoyed atm, as i cant shrink it to create a new partition :(.

anyway what i was trying to get accors in my first post is that i can only shrink the c drive by 60gb

i want to shrink it more!

but i cant as i have files on the hardrive stopping it shrink any smaller.

so i can only make my new partition 60gb, which is where i want to install ubuntu.

is that abit more clear? im not really fantastic at explaining. :confused:

---

### Post by oldfred on 2011-05-05
Some more links. Some have used other third party windows tools, but I do not have links.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

Generally it is best to use windows tools for windows & Linux tools for Linux. But new versions of gparted do work. Older versions sometimes moved the start from sector 2048 to sector 63 (old style start for XP) and then Vista/7 had to be repaired to get it to work. So generally we have not recommended gparted as we do not know what version you are using and want to avoid repairs if possible.
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by VanR on 2011-05-05
Personally I wouldn't play with Windows partitions from outside of Windows. In my experience it doesn't like it too much. YMMV though.

---

### Post by K4NEB on 2011-05-05
im using windows vista. i have not even installed ubuntu yet lol.

i did have it on wubi to try it but i have now unistalled it as i want to install it properly.



well i guess the new question is;

will 60gb be enough space to install unbuntu on?

---

### Post by oldfred on 2011-05-05
Plenty, unless you are also storing lots of data.

My root install in a 20GB partition is about 6-7GB used with lots of programs installed. Default install is <4GB. Swap should be same size as RAM unless you have lots of RAM & do not hibernate then 2GB or even none will work. Then you can make the remaining 35GB /home for user settings and your data.

---

### Post by kpuz on 2011-05-05
> **K4NEB said:**
> yes yes i know how to defrag :P lol :D

i used perfectdisk 11 last night and it took forever, but it decided it wanted to move an unmovanle file right to edge of my hardrive!

so i am now unable to shrink it! :(

extremely annoyed atm, as i cant shrink it to create a new partition :(.

anyway what i was trying to get accors in my first post is that i can only shrink the c drive by 60gb

i want to shrink it more!

but i cant as i have files on the hardrive stopping it shrink any smaller.

so i can only make my new partition 60gb, which is where i want to install ubuntu.

is that abit more clear? im not really fantastic at explaining. :confused:

In perfectdisk 11, do a defrag with the 'Consolidate free space' option selected. If you still cannot increase the shrink volume you will need to defrag on boot time (perfect disk 11 can do that too). This is how I bypassed this problem.

---

### Post by K4NEB on 2011-05-06
yep boot defragging was exaclt y what i was looking for :D found that out yesterday.

cool beans. just need to go to the shop and get some disks.

anyone got any reccomendations for the best type of disk to use for creating the unbuntu live cd?

---

### Post by oldfred on 2011-05-06
If your computer supports USB booting, buy a flash drive (or two). Flash drives have dropped dramatically in the last year or two. I converted from using CDs to flash when they got down to about $2/GB and now they are about $1+ per GB.

Flash is faster than CD and reusable. Larger one's (8GB or more) can have a full install or just be another way to backup data.

---

### Post by K4NEB on 2011-05-06
> **oldfred said:**
> If your computer supports USB booting, buy a flash drive (or two). Flash drives have dropped dramatically in the last year or two. I converted from using CDs to flash when they got down to about $2/GB and now they are about $1+ per GB.

Flash is faster than CD and reusable. Larger one's (8GB or more) can have a full install or just be another way to backup data.

i was thinking of this but i dont reall have a need for one. so im just going to use a disk for the install

---

