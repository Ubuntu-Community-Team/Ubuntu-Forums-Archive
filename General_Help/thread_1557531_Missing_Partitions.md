---
title: "Missing Partitions"
date: 2010-08-20
forum: General Help
---

### Post by nim123 on 2010-08-20
I had 4 partitions on my drive; 2 for Ubuntu, 2 for swap.  I resized one of the Ubuntu ones using GParted to create some free space.  Then, I booted from a Windows XP CD, created another partition, and installed Windows XP there.  I am not able to select which partition to boot from anymore on start-up and when I run GParted, it shows the entire drive as being unallocated.

Is there anyway to access those partitions again?  They should still be there unless I formated the entire drive by accident.

---

### Post by anirudhtomer on 2010-08-20
if you have not formatted them by mistake then the only reason for a behavior is corrupted bootloader.

put the ubuntu CD & run it with try ubuntu without a change.
then open the terminal & follow the instructions from this link

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by Miljet on 2010-08-20
There are so many possibilities here that it is impossible to help without more information. For example, of the original 4 partitions, were they all primary partitions or were some logical partitions? You are only allowed 4 primary partitions on a hard disk. One of those primary partitions can be an extended partition, which can then contain other partitions, called logical partitions.

Any time that you install a version of Windows after having Ubuntu already installed, the Windows install will overwrite the MBR (Master Boot Record). That will erase your GRUB boot record and you will only be able to boot into Windows. This is easily correctable, but we first need to know which version of GRUB you had installed. Or at least the version of Ubuntu, which will give a clue as to which GRUB.

Also boot the Ubuntu live CD and open a terminal (Applications -> Accessories -> Terminal). Copy and paste in the following code
```
sudo fdisk -l 
```
Copy the results back here.

---

