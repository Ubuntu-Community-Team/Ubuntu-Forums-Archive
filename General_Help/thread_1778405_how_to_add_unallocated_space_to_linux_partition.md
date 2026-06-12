---
title: "how to add unallocated space to linux partition"
date: 2011-06-09
forum: General Help
---

### Post by fafu on 2011-06-09
I am new to linux.....
I am not able to add unallocated space created by shrink volume in windows into existing linux partition....


Screenshots
[ATTACH]194610[/ATTACH]

[ATTACH]194611[/ATTACH]



Please help.........

---

### Post by jramshu on 2011-06-09
It has to be directly in front of, or behind the existing linux partition.

> In addition, the position of free space determines how it can be used.  Free space can only be added to an existing partition if it is next to  ("touching") that partition.

[http://ubuntuguide.org/wiki/Manipulating_Partitions](http://ubuntuguide.org/wiki/Manipulating_Partitions)

---

### Post by Bucky Ball on 2011-06-09
> **jramshu said:**
> It has to be directly in front of, or behind the existing linux partition.

Yep, you are going to need to backup then remove /movies, the NTFS partition, and /swap to get to the unallocated space.

You will need to unmount those, delete, expand, put swap right at the end. You could recreate the /movies NTFS before swap then expand into the free space up to the beginning of /movies, if you follow. This would leave you with:

.... Hold it. You have two /swaps there? Where exactly do you have / installed? And do you have a separate /home partition?

I would backup /movies, delete everything after sda7 which is marked EXT4, stretch sda7 to where you want, put /swap at the end. 

Welcome to the forums. ;)

---

### Post by linuxinstalledfromhdd on 2011-06-09
Are they trying to do this from a live disc or live flash drive of Ubuntu?

---

### Post by fafu on 2011-06-09
doing it from live flash drive of Ubuntu 11.04

---

### Post by linuxinstalledfromhdd on 2011-06-09
Are you trying to create space to install another Ubuntu system?

You can use Ubiquity to automatically do this for you.  When I do my installs, that's when I do resizing, because it's just easier that way. :)

---

### Post by fafu on 2011-06-09
@linuxinstalledfromhdd
No,I am trying create more space in existing linux system to store data.

---

### Post by prshah on 2011-06-09
> **fafu said:**
> I am not able to add unallocated space created by shrink volume in windows into existing linux partition.

Hello,

You are not able to make changes because your swap partitions are active (see the "key" icon next to each swap partition and /dev/sda3).

You will have to right click each swap partition, and choose "swapoff" before you can make changes.

Note that moving partitions is a difficult business and best and risky at worst.  Please post back if you want tips specific to your case.

---

### Post by jramshu on 2011-06-09
It doesn't matter whether you are using flash or livecd, or if the swap is mounted or not the rules still remain. The free space can only be added to an existing partition if it is next to  ("touching") that partition. It is true the you can not expand the extended partition if swap is mounted, but they must still be touching.
Read the info in this link.

[http://ubuntuguide.org/wiki/Manipulating_Partitions](http://ubuntuguide.org/wiki/Manipulating_Partitions)

---

### Post by Bucky Ball on 2011-06-09
> **jramshu said:**
> It doesn't matter whether you are using flash or livecd, or if the swap is mounted or not the rules still remain. The free space can only be added to an existing partition if it is next to  ("touching") that partition. 

+1. Exactly. This issue was covered in our posts #2, #3. ;)

---

### Post by egalvan on 2011-06-09
Two ways to go on this...

first option...

from a LiveCD environment

"swapoff" each swap partition,
 then 
un-mount the extended partition (sda3)
then
"move" (slide) the ntfs "Movies" partition to the far right
(this will leave the un-allocated space on the "left side")
then
in turn "move" (slide) each swap partition to the far right
(again, this will leave un-allocated space on the "left side")
then
"expand" your ext4 partition into the empty space
realize this has dangers, messing with partitions can cause problems,
**back up important data**
it will also take some time, so patience is needed.


second option...
since you stated you wanted to **store data** in this empty space..
then
format the un-allocated space using a Linux fs (ext2, ext3, ext44, etc)
give it a descriptive label, such as "data_drive"
mount it.
all done.

---

### Post by fafu on 2011-06-09
if condition is like this....

[ATTACH]194710[/ATTACH]

is there any difference......

---

### Post by oldfred on 2011-06-09
The little keys say you have not swap-offed yet. 

From liveCD click on swap partition and right click swap off on both swap partitions as posted before.

---

### Post by fafu on 2011-06-09
if we swap off it....
will it cause any problem to existing partitions.........

---

### Post by Bucky Ball on 2011-06-09
> **fafu said:**
> if we swap off it....
will it cause any problem to existing partitions.........

No. Doubtful the swap is being used anyhow. Doing this using Gparted in a LiveCD rather than a running hard drive install is the other option and you will need to do this to expand the /home partition anyhow (you can't unmount that to expand it while it is in use so you need to run from the CD, not hard drive).

---

### Post by fafu on 2011-06-10
@bucky ball
i swapped off....now wat shuld i do........
i am running it from live usb flash drive....

---

### Post by oldfred on 2011-06-10
Now you can move/delete/expand partitions. Understand there is always some risk, so you do have good backups.

If you want to include space outside the extended partition to the adjacent partition inside the extended you have to first move the extended partition. Suggest you do it in small steps. 

More info:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

