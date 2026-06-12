---
title: "installing ubuntu on desktop with win 7 and win 8 (developers edition)"
date: 2012-02-26
forum: General Help
---

### Post by Delsos on 2012-02-26
I have windows 7 and windows 8 (developers preview) installed on my desktop, I want to install Ubuntu on it though. So can i go ahead and just install via partition and it will let me select win 7 win 8 and ubuntu?

I tried doing the "wubi" method of installing inside of windows as a program, but during the initial installation, it starts downloading random files up to 600mb and im like dang it!!!

so if i boot from ubuntu cd, and proceed to install ubuntu via partition, will everything be ok? 

thanks

---

### Post by DeathShot on 2012-02-26
If I remember correctly the Ubuntu installer will let you have the chose between installing over everything, a certain partition, installing next to windows (it will use the free space on your HDD to create a Linux partition) or an advanced option, basically letting you use Gparted to do what ever you want. If it doesn't work out you can always cancel the installation.

Though personally, I always partition my HDD before installing an operating system to make sure everything is how I like it.

Edit: Also Ubuntu comes with Grub so if you install it and install the Grub boot loader you can select all your operating systems on boot no problem- I think this is what you were actually asking about

---

### Post by Mark Phelps on 2012-02-27
> **Delsos said:**
> so if i boot from ubuntu cd, and proceed to install ubuntu via partition, will everything be ok? 

thanks

Absolutely ... NOT!

Wubi doesn't work with Win8 DP.  Whether it will work with Win8 CP (Consumer Preview), only time will tell.

The Ubuntu installer will offer you the option to install side-by-side which will SHRINK your Win7 or Win8 OS partition -- which is likely to result in filesystem corruption and render Win7 or Win8 unbootable.

If you are SERIOUS about multi-boot, then read through the material below ...

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

