---
title: "Partition table damaged"
date: 2009-08-27
forum: General Help
---

### Post by demonicblue on 2009-08-27
Hi
Something wierd has happened to my partition table.
Earlier I deleted some partitions from a linux system i no longer needed (Arch).
My set up at that time was:
Win XP
Win 7
Arch Linux
Jolicloud

I no longer needed Arch so i deleted it. Turns out my GRUB settings was in there and now GRUB won't load.
I got the idea that i should recover the boot partition with TestDisk.

I booted Ubuntu Live-CD and used TestDisk to recover the Arch boot partition. I followed instructions on the TestDisk wiki and everything seemed fine until rebooted. GRUB still couldn't find the settings. I checked with gparted which said that the whole disk was unallocated. That's wierd..

Checked with
```
fdisk -l
```
It returned my partition table and everthing seemed fine there but gparted still showed the whole disk was unallocated.

Now, i don't know where to go from here so I figured I'd ask here. 
I would rahter not re-installation, all files and application.. :(

Pleaze help me :confused:

If i missed anything, just ask.

---

### Post by TeoBigusGeekus on 2009-08-27
Boot up with the Win7 dvd. After selecting the language, there is an option to recover/fix the mbr.

---

### Post by bchurchill on 2009-08-27
If you prefer a non-windows solution, then you could go to any ext3 formatted partition (or make a boot partition for this purpose) and install grub from the live cd: 

[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

---

### Post by ronparent on 2009-08-27
Was it only your grub setting (ie menu.lst) or all the files in grub? If you can find all the grub files in the filesystem of your new install then the prior post by bchurchill applies. If all the files were deleted you need to reinstall grub to /boot/grub on the new install. See following for instructions: **[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)**

---

### Post by demonicblue on 2009-08-27
> **bchurchill said:**
> If you prefer a non-windows solution, then you could go to any ext3 formatted partition (or make a boot partition for this purpose) and install grub from the live cd: 

[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

So first.. I think i didn't understand how testdisk worked, i did it again and recovered both windows partitions and jolicloud..
gparted prob didn't work cos i had testdrive running.

Then i used the instrcutions in the link together with what gparted said or just
```
sudo fdisk -l
```
to find the partition where /boot/grub resides, then easy as cake! :)
(jolicloud had replaced the Arch /boot/grub files but had them also in Joliclouds partition, I just told grub to look there instead)

And thanks for the link it was just what i needed. It's working now, just as i wanted.
Thanks all for the quick replies.

---

