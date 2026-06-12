---
title: "Grr...install to entire Partition erased entire disk."
date: 2010-11-22
forum: General Help
---

### Post by jehiva on 2010-11-22
So...I previously had a dual boot install of Windows 7 and Ubuntu 10.10 - both the 32 bit versions.  I decided my project for the weekend would be to update to the 64 bit versions.

On a 300gb hard drive, I started by freeing up 100gb of space for the new Ubuntu 10.10 64 bit install.

As I was using the wizard that comes up for the install it had defaulted to my 100gb of free space and labelled it as nearly a 50/50 split between Files and Ubuntu.  Since I don't really care to keep data/os on separate partitions I instead clicked "Install to Entire Partition" (as opposed to the "Install to Entire Disk" option).  The bar that previously showed the 50/50 split now showed a single Ubuntu logo, with no gb size listing next to it.

I eagerly clicked Forward and began the install.

Well, come to find out as the computer rebooted that Ubuntu 10.10 64 bit had installed itself to my entire hard drive.  No more GRUB menu, no more Windows 7, no more Ubuntu 10.10 32 bit.

Quite frustrated, I decided there would be no way to recover any of my data (I had planned on moving it from Windows 7 to my new Ubuntu install and then back again after re-installing Windows), so I started up Ubuntu, ran Gparted to shrink the partition from 300gb to 150gb and formatted the other 150gb as NTFS.

I installed Windows 7 64 bit only to still not have a GRUB menu.  Finally got that by once again re-installing Ubuntu 10.10 64 bit from the Live CD.

Anyways, my problem now is that when I type:
```
df -h
``` I only see the 150gb Ubuntu partition.  

Can anyone explain how to get it to see the other 150gb partition so that I can mount my NTFS partition and once again freely move files between the two?

---

### Post by Mark Phelps on 2010-11-22
> **jehiva said:**
> As I was using the wizard that comes up for the install it had defaulted to my 100gb of free space and labelled it as nearly a 50/50 split between Files and Ubuntu. 
First mistake -- don't use the Installer to shrink NTFS partitions.  Filesystem corruption can occur as a result.

>  I instead clicked "Install to Entire Partition" (as opposed to the "Install to Entire Disk" option).  The bar that previously showed the 50/50 split now showed a single Ubuntu logo, with no gb size listing next to it.

I eagerly clicked Forward and began the install.
The fact that only ONE partition showed now should have been a clue that Ubuntu was going to take the entire drive.  But agree, the new installer is confusing -- at best.

> I installed Windows 7 64 bit only to still not have a GRUB menu.  Finally got that by once again re-installing Ubuntu 10.10 64 bit from the Live CD.
Installing any MS Windows OS will wipe GRUB from the MBR -- which is what you saw.

Suggest you open an terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one) to list off all the partitions present on your drive.

---

### Post by jehiva on 2010-11-22
Hi Mark, thank you for your response.

I have actually gotten my GRUB back and can boot to Win7 or Ubuntu, however when I go to use the ntfs-config program (to allow read/write on my NTFS partition) it fails to start.

Furthermore, when I look under Places my NTFS partition is not listed (previously before I did all my re-installations it was shown under there without doing anything).

Finally, when typing ```
df -h
``` only my 150gb Ubuntu partition is listed - the NTFS one is missing.

How do I make the NTFS partition show up?

---

