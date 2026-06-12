---
title: "Trying to move and expand partitions"
date: 2011-05-07
forum: General Help
---

### Post by JohnElway on 2011-05-07
I currently have a dual boot setup with Windows Vista and Ubuntu 10.04. Here is how everything is divided:

<------------Windows 200GB------------><--Swap 4GB--><--/ 13GB--><--/home 3GB-->


After going on a game install spree in Ubuntu, I basically ran out of room in my /home partition and am now trying to expand both / and /home. I defragmented and shrunk the Windows partition by about 20GB so now it looks like this:

<--Windows 180GB--><--free 20GB--><--Swap 4GB--><--/ 13GB--><--/home 3GB-->

So basically I want to use that free 20GB by adding about 10GB to both / and /home. Any idea how I could do this? Is it even possible?

---

### Post by RJ12 on 2011-05-07
I believe you are going to have to move your partitions around using GParted on your liveusb/cd (if you just install it, your partition will be mounted and you can't do anything to a mounted partition), just be aware to make sure your data is backed up, and the operation could take awhile.

---

### Post by LostFarmer on 2011-05-07
From linux post output of 'fdisk -l' Note -l is a small L not a 1, run command in a terminal with root privileges.  Need to see how partitions are on the hdd, primary/extended/logical volumes.

 It will not be easy, and will have to be done with a live linux cd. 
 Basically you will need to delete swap, move and expand /, then move and expand /home, make new swap.  Dueing any move or resizing can result in a corrupt system.

---

### Post by JohnElway on 2011-05-08
> **LostFarmer said:**
> From linux post output of 'fdisk -l' Note -l is a small L not a 1, run command in a terminal with root privileges.  Need to see how partitions are on the hdd, primary/extended/logical volumes.

 It will not be easy, and will have to be done with a live linux cd. 
 Basically you will need to delete swap, move and expand /, then move and expand /home, make new swap.  Dueing any move or resizing can result in a corrupt system.

"fdisk -l" doesn't output anything by itself. Am I supposed to append anything to this command?

---

### Post by plucky on 2011-05-08
> "fdisk -l" doesn't output anything by itself. Am I supposed to append anything to this command? 

```
sudo fdisk -l
```

Better to post a picture of Gparted if you have it installed.

> <--Windows 180GB--><--free 20GB--><--Swap 4GB--><--/ 13GB--><--/home 3GB-->


Personally I would add all the 20Gb to the /Home partition as 13Gb is more than adequate for the /root partition.

Good Luck

---

### Post by LostFarmer on 2011-05-08
The easiest would be make the free 20g your /home partition and then add the old /home to /.  As [plucky]("http://ubuntuforums.org/member.php?u=317619") says your / is likely OK in size.

---

