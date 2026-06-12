---
title: "Cannot resize NTFS Partition with Ubuntu"
date: 2010-08-12
forum: General Help
---

### Post by schwabdale on 2010-08-12
I am trying to resize a Windows XP partition. The partition has 
plenty of space available. When I boot off the CD, I open Gparted. 
I try to move the partition down, but it does not move at all. 

Within this Windows installation, it only shows 1% fragmentation. 

Any ideas? I want to dual boot using two partitions.

---

### Post by schwabdale on 2010-08-12
Bump

---

### Post by plucky on 2010-08-12
Post a screenshot of your Gparted window.

---

### Post by efflandt on 2010-08-12
If that is your main WinXP partition there may be unmovable files, in particular its virtual memory (like swap).  If near the end of the partition, that can also limit how much you can shrink the ntfs partition.  In Windows under System > Advanced, make a note of virtual memory settings, disable virtual memory, and reboot Windows for that to take effect.  Then try the resize or move with gparted.

When you resize or move an ntfs partition, gparted will mark it as dirty so Windows will check the partition when it boots.  So you may want to reboot Windows and make sure that works fine before installing Ubuntu in the unallocated space.  Then you could also re-enable WinXP virtual memory.

When I first got my old desktop PC in 2004 I did not do that and could only free up about 24 GB of its 200 GB drive.  More recently when I disabled virtual memory I could have freed up more than 150 GB, but I did not need that much room for Ubuntu.

Note that if you get a newer PC with Vista or Win7, shrinking that partition is best done with Windows own utility under Computer Management.  But XP does not have that, and I have not had any trouble shrinking XP partitions with gparted.

---

### Post by Paul S on 2010-08-12
I've had problems in the past with gparted not working and one time it popped an error message about working on a suspended / hibernated partition.  So, try mounting your ntfs and manually deleting hyberfil.sys file, and then try gparted again.

I may have also deleted the pagefile.sys file too (can't remember for sure).

hth

---

### Post by schwabdale on 2010-08-12
Thanks, I will try those suggestions and post back!

---

### Post by schwabdale on 2010-08-12
no luck turning off windows swap

---

### Post by schwabdale on 2010-08-13
Even after a Bran new install of XP it does not allow me to shrink the hard drive. 
I know this cd works. I've used Gparted on it many times.

---

### Post by Mark Phelps on 2010-08-13
Try downloading and burning a current GParted LiveCD from distrowatch.com.  

The newer version might work better than the one bundled with Ubuntu.

---

