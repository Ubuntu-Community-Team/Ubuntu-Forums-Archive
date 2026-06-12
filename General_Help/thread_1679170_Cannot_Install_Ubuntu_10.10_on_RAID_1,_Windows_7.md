---
title: "Cannot Install Ubuntu 10.10 on RAID 1, Windows 7"
date: 2011-01-31
forum: General Help
---

### Post by waynerd769 on 2011-01-31
I have an I7 on an EVGA MB. I have hardware, Intel RAID 1 on 2, 1TB drives and a 500 GB drive. When I try to install Ubuntu 10.10, It doesn't see my 1 TB RAID drive. So, I tried to install Ubuntu on the 500 MB drive. Of course, that caused problems. The Ubuntu doesn't install and it messed-up my Windows 7 x64 boot. I figured out how to boot to Windows again but, given-up, so far on trying to get Ubuntu on my PC. Any Help???

---

### Post by clynn3 on 2012-04-10
I am having a similar issue.  I have 2 1TB hard drives with raid 1.  
when I start the installer, it doesn't recognize that i have windows and doesn't give me the option to create the partition for windows.  It also only lets me select the 2nd or "mirror" drive to install on.  btw, I have no data on the drives that I am set on keeping


sorry, total linux nub.

I will continue searching the forums.  if anyone can even point me to a forum with answers that would be great.

---

### Post by Mark Phelps on 2012-04-10
The standard Ubuntu Desktop installer does not understand RAID.

You have to download and use the Alternate Installer.  It's a text-based version, but it understands RAID setups.

---

