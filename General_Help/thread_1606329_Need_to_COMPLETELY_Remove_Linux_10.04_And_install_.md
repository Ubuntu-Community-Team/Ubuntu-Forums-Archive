---
title: "Need to COMPLETELY Remove Linux 10.04 And install Windows"
date: 2010-10-26
forum: General Help
---

### Post by DavidFelix on 2010-10-26
Okay, this is like the 4th time I ask for help but I just really need this taken care of. I had Windows. Installed Linux 10.04 over it. I want to switch back to Windows. When I pop in my Windows XP disc I get and error after it loads a bunch of stuff. I tried booting from m 10.04 disc, going into Disk Utility and changing the file system to NTFS no luck. Tried burning another copy of XP and still same error. Now I burned a copy of Windows 7(desperate times call for desperate measures) but its on a DVD-R instead of a CD-R and every time I try to boot it, Linux just boots. Please, help!!

---

### Post by Bliepo32 on 2010-10-26
You could use the Gparted live cd to make it a NTFS partiton. Furthermore, I believe your BIOS options are set to boot the hard disk before the cd-drive.

---

### Post by Vaphell on 2010-10-26
maybe use ubuntu live cd to wipe all partitions and then try again with windows disc? windows installer can create partitions

---

### Post by DavidFelix on 2010-10-26
In BIOS I set it to boot from my CD Drive. But please explain this GParted idea.

---

### Post by Cityscape on 2010-10-26
> **DavidFelix said:**
> Okay, this is like the 4th time I ask for help but I just really need this taken care of. I had Windows. Installed Linux 10.04 over it. I want to switch back to Windows. When I pop in my Windows XP disc I get and error after it loads a bunch of stuff. I tried booting from m 10.04 disc, going into Disk Utility and changing the file system to NTFS no luck. Tried burning another copy of XP and still same error. Now I burned a copy of Windows 7(desperate times call for desperate measures) but its on a DVD-R instead of a CD-R and every time I try to boot it, Linux just boots. Please, help!!

Installing from your XP disc should work. If your drive is clean of stuff you want saved then I would recommend booting from an Ubuntu Live CD and going to System > Administration > Disk Utility. Find your hard disk from the left sidebar. You should see several partitions now (at least one ext4 and one swap). Click on a partition and chose the delete option. When it finishes delete the next one and do this until all your partitions are erased and you only have free space. If you have an extended partition you'll have to delete the sub-partitions before deleting the extended one.

After this is done boot from the XP disc and see if it will install. If it doesn't then boot back into Live CD and change all that free space to an NTFS partition.

---

### Post by ubudog on 2010-10-26
Boot the Ubuntu Live CD, go to System>Admin>Gparted.  Format everything you see (except for obvious stuff like flash drives), reboot, put in your Windows disc and see if it works.

---

### Post by Quackers on 2010-10-26
If GParted isn't in your menu you will need to install it through Synaptic.

---

### Post by ubudog on 2010-10-26
> **Quackers said:**
> If GParted isn't in your menu you will need to install it through Synaptic.

True, but on the 10.04 live cd it should be there by default.

---

### Post by Quackers on 2010-10-26
> **ubudog said:**
> True, but on the 10.04 live cd it should be there by default.


oops, of course, my bad :(

---

### Post by ugm6hr on 2010-10-26
If you want to completely remove Ubuntu, just wipe the Hard Drive completely using something like DBAN [http://www.dban.org/](http://www.dban.org/)

Once wiped with DBAN, the HD behaves as if completely new. Hence, you can install whatever Operating System (OS) you choose to.

If that doesn't work, then the problem relates to either the new OS, or your hardware (i.e. not Ubuntu).

If Windows XP is actually booting up, then clearly your BIOS must be set to boot from the CD/DVD drive. If W7 doesn't do the same, it is likely that there is a problem with your W7 disc, or your DVD drive.

---

### Post by Noah0504 on 2010-10-26
Are you getting a blue screen error when it tries loading the files for the install?  If so, I guarantee it's because you have your HDD interface set to AHCI or SATA.  Set it to IDE in the BIOS, install Windows and when all of your drivers are installed, you can change it back.

---

### Post by DavidFelix on 2010-10-26
I deleted all partions then made a new one with the NTFS format. But when I pop in any Windows XP disc I get a Stop Error :/ Idk what next. I used up all my discs :(

---

### Post by DavidFelix on 2010-10-26
> **Noah0504 said:**
> Are you getting a blue screen error when it tries loading the files for the install?  If so, I guarantee it's because you have your HDD interface set to AHCI or SATA.  Set it to IDE in the BIOS, install Windows and when all of your drivers are installed, you can change it back.

I'll try that!! And yes it is a blue screen error!

---

### Post by DavidFelix on 2010-10-26
I'm at the BIOS but I don't know how to switch from SATA or AHCU to IDE.

---

### Post by DavidFelix on 2010-10-26
My BIOS is running on InsydeH20 Rev. 3.5

---

### Post by tgm4883 on 2010-10-26
In case it hasn't been said before, and to eliminate confusion, this is a Windows issue. There isn't anything that Ubuntu is doing nor has done to prevent you from reinstalling windows. 

When you go to reinstall windows, how far do you get before it crashes? Have you checked your motherboard manufacturer? There may be a driver disk you need in order to install XP

---

