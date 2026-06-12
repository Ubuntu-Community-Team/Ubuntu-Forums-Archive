---
title: "Installing ubuntu (how to use half the HDD?)"
date: 2010-10-03
forum: General Help
---

### Post by jinba.ittai on 2010-10-03
Im trying to dual boot my system again after uninstalling 10.10. I have 2 HDDs and want to put linux on the HDD that doesnt have windows on it, but instead of using the whole drive, just about half. I know i am going to have to go into the "specify partitions" options but what next? and will it still install grub right? or will i have to install when i get booted into linux? or will it even boot into linux?!

---

### Post by spiky001 on 2010-10-03
do I have this right you have a hdd you wnat ubuntu on half ubuntu on 2nd half your other drive is windows? you dont want to touch

---

### Post by jinba.ittai on 2010-10-03
> **spiky001 said:**
> do I have this right you have a hdd you want ubuntu on half ubuntu on 2nd half your other drive is windows? you dont want to touch
I have a 750 GB drive, with windows 7 on it, i cant boot to it cause i just uninstalled 10.10 from my 2nd HDD which is 350gb. Now im trying to put ubuntu back on my 350 but only using half the memory on the 350. Sorry, i should have specified that bit.

---

### Post by spiky001 on 2010-10-03
ok I would remove the window hdd then load ubuntu when you get to the 2nd ubuntu install choose side by side refit 1st drive update grub should do it

---

### Post by jinba.ittai on 2010-10-03
> **spiky001 said:**
> ok I would remove the window hdd then load ubuntu when you get to the 2nd ubuntu install choose side by side refit 1st drive update grub should do it


Would this work if the other drive is not formatted with any partitions yet?

---

### Post by spiky001 on 2010-10-03
I think so why not boot the cd there is option to format when you get to the partition part,if not boot live cd open gparted you can format there and partition then load OS

---

### Post by efflandt on 2010-10-03
Are you really asking about 2 physical drives, and not just a D: drive (partition) in Windows?

Assuming the 2nd drive is a totally separate hard drive new with nothing on it, I would boot the Ubuntu install CD to a live system and use System > Administration > Gparted to partition the drive like you want it.  Although, if it is brand new (or zeroed out) you will first need to create an msdos partition table on it.  Then you can crate your Linux partition(s) with your file system of choice (ext4 or ext3) and a swap partition.  You can leave the rest of the drive unallocated for now.

Then during install, used Advanced to select the partition(s) you made and where you want to mount them (you need at least / ).  It will automatically pick up any swap partition.

One other decision is where to put grub, on the drive you installed Linux or your main hard drive.  If you put it on the Linux drive it will not interfere with or get messed up by Windows, but then you either need to change BIOS boot order to boot that drive first, or press a key in the BIOS splash screen to select boot drive (which you sometimes still have to do if not booting the primary drive).

Not sure how RC handles grub location, but with previous Ubuntu versions you had to look for an Advanced button in one of the last steps before installation proceeded.  But in 10.10 beta the setting for grub location was more intuitive because it was a visible drop down list a the bottom of a window (which automatically defaulted to a USB drive where I put / ).

PS: Just saw your other reply.  If you cannot boot Windows I assume you previously put grub on mbr of your main drive (/dev/sda), so that is where you should put it when reinstalling Ubuntu.

---

### Post by jinba.ittai on 2010-10-03
> **efflandt said:**
> Are you really asking about 2 physical drives, and not just a D: drive (partition) in Windows?

Assuming the 2nd drive is a totally separate hard drive new with nothing on it, I would boot the Ubuntu install CD to a live system and use System > Administration > Gparted to partition the drive like you want it.  Although, if it is brand new (or zeroed out) you will first need to create an msdos partition table on it.  Then you can crate your Linux partition(s) with your file system of choice (ext4 or ext3) and a swap partition.  You can leave the rest of the drive unallocated for now.

Then during install, used Advanced to select the partition(s) you made and where you want to mount them (you need at least / ).  It will automatically pick up any swap partition.

One other decision is where to put grub, on the drive you installed Linux or your main hard drive.  If you put it on the Linux drive it will not interfere with or get messed up by Windows, but then you either need to change BIOS boot order to boot that drive first, or press a key in the BIOS splash screen to select boot drive (which you sometimes still have to do if not booting the primary drive).

Not sure how RC handles grub location, but with previous Ubuntu versions you had to look for an Advanced button in one of the last steps before installation proceeded.  But in 10.10 beta the setting for grub location was more intuitive because it was a visible drop down list a the bottom of a window (which automatically defaulted to a USB drive where I put / ).

PS: Just saw your other reply.  If you cannot boot Windows I assume you previously put grub on mbr of your main drive (/dev/sda), so that is where you should put it when reinstalling Ubuntu.



i<3 You

---

