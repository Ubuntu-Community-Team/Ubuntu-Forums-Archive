---
title: "How do i uninstall ubuntu"
date: 2012-01-11
forum: General Help
---

### Post by willow370 on 2012-01-11
Hi guys, long story short im trying to uninstall ubuntu 11.10 and replace it with windows xp.

ive tried just running the windows installer from booting off the cd and it does the pre install driver checks or watever, and then restarts the laptop.

anyway, main question is how do i uninstall ubuntu 11.10 and ill figure out the windows xp problem after.

cheers.

---

### Post by TBABill on 2012-01-11
You can fire up an Ubuntu live CD and then use gparted to eliminate the EXT4 (or whatever you used) and swap partitions. Once you have done that you will probably have a whole drive of unallocated space. Windows should be able to install to that.

---

### Post by t0p on 2012-01-11
I'm not sure about this: but if you install XP, won't it just install itself over Ubuntu, giving you your  Windows-only environment?

---

### Post by Mark Phelps on 2012-01-11
It's likely that the XP installer, seeing only Linux filesystem partitions on the drive, gets confused and restarts.

Boot into an Ubuntu desktop CD, choose Try Ubuntu, open the Disk Utility -- and remove all the partitions.

Then, when you reboot using the Win XP CD, you should be able to install OK.

---

### Post by gandaran on 2012-01-11
> ive tried just running the windows installer from booting off the cd and it does the pre install driver checks or watever, and then restarts the laptop
hi
the laptop hardware is it SATA? (or IDE?) does the windows XP cd have SATA drivers included?
I don't believe the linux file system is the problem, from any windows install disk you should be able to delete every existing partition or format the entire disk and create NTFS partitions.

---

### Post by Carpentr on 2012-01-11
I've installed Windows multiple times on my Dell and all I had to do was format and delete the partition in the custom options menu and you'll have an entire hard drive to use for your XP installation. Like everyone said above, it shouldn't be a problem.

---

### Post by Mark Phelps on 2012-01-11
It's been a long time since I installed XP, but from what I recall, if there is no hard drive (or it can't find one), it will still start the installation -- and then complain when it can't find the drive.  It won't automatically restart part way into the installation.

---

### Post by Kslawdog on 2012-01-11
Phelps is right, I tried installing xp and it did the same thing to me... My hardware was too new for the install. Try getting an updated version of xp.

---

