---
title: "Changing GRUB2 Source"
date: 2011-02-07
forum: General Help
---

### Post by Cthulhu_Dreams on 2011-02-07
I had installed the Natty Narwhal Alpha 2 on a tiny partition and would now like to remove it.  However it occurred to me that during the install Ubuntu rewrote my GRUB so that the partition containing Natty would be where it looks for the GRUB files.  How can I make it so Grub looks to my main Ubuntu partition rather than the Natty one?

---

### Post by Cthulhu_Dreams on 2011-02-07
Bump

---

### Post by oldfred on 2011-02-07
If you can boot your main install, just reinstall grub2 from that to the MBR. Otherwise you have to use liveCD.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by Mark Phelps on 2011-02-07
First of all -- STOP bumping!  The rule around here is bumping once a day, not once every few hours.

Second, remove the partition containing Natty and reinstall GRUB from an Ubuntu LiveCD.

To do the first, boot from a LiveCD, open Partition Editor, confirm the Natty partition is unmounted, and delete it.

To do the second, read Section 12 in the link below:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by glene77is on 2011-02-07
OldFred, 
I had a similar problem, and the solution is similar to yours.
A SOLUTION was pasted at: 
     [http://paste.ubuntu.com/563657/](http://paste.ubuntu.com/563657/)
The Solution pasted is the long way around the tree.
The notes which Nathan726 wrote in are very helpful in understanding GRUB. 
The notes are worth the read. 

My MBR pointed into sda3, a fresh install of Ubuntu, for testing. 
I wanted the MBR to be repointed into sda7, my old working install, with all configs, etc. 

I have read other comments by you, and they are good.   Thanks for the effort.

---

