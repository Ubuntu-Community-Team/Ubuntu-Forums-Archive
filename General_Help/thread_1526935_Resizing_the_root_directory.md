---
title: "Resizing the root directory"
date: 2010-07-08
forum: General Help
---

### Post by stravant on 2010-07-08
I just started using Ubuntu about a month ago. Now it's telling me that I only have a small amount of disk space left. Looking at it, my / directory is only 6.5GB. I installed Ubuntu into an empty 80GB NTFS partition, but I must have done something wrong in telling it what size to use.

Now, I've done enough to the system that I would rather not have to re-install it completely. With some quick searches there doesn't seem to be any straightforwards answer, so how do I remedy this and expend the / directory to fill all of the available space left in the partition?

---

### Post by Thelasko on 2010-07-08
Fire up your LiveCD and run Gparted.  It's pretty straight forward and will allow you to re-size your partitions easily.  When you are done, just restart the computer.

You shouldn't lose any data.  However, it is a possibility (bad things can happen).  Back up your data.

---

### Post by stravant on 2010-07-08
Gparted is showing me a screen where I can edit the actual NTFS partitions. The NTFS partition is already the right size, Ubuntu just isn't using all of it for whatever reason.

Oh, and I installed with the windows-installer, not a live CD.

---

### Post by ajgreeny on 2010-07-08
For a wubi install see:-
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by stravant on 2010-07-08
As I just installed recently, I was using Wubi 10.04, and the LVPM states that it only works for 8.04. (add virtual disk isn't what I'm looking for, It's the system in general that needs more room)

Is there another way to do it? (If it helps, I have another disk besides the one Windows and Ubuntu are on to work with)

---

### Post by louieb on 2010-07-08
If you don't want to use a virtual disk then don't use wubi to install. - thats what it does - creates a virtual disk inside the windows installation.  lvpm is the only way I know to add disk space to an inside widows install. 

Do a normal dual boot install. IF you have an 80GB partition already set up - then when you install use manual partitioning and tell it to use the the partition for / (root). Be aware that everything in that partition will get wiped out and replaced with a new Linux installation.

---

