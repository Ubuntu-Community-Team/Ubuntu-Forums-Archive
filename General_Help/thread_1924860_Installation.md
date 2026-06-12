---
title: "Installation"
date: 2012-02-13
forum: General Help
---

### Post by sdcougar on 2012-02-13
I presently have a different distro, Mepis.  It has the boot loader that on start up lets me select windows or linux or if I do nothing it then starts in linux. Will this present any problem if I instlal Ubuntu to replace the Mepis? Any special instructions?

---

### Post by sunewbie on 2012-02-13
> **sdcougar said:**
> I presently have a different distro, Mepis.  It has the boot loader that on start up lets me select windows or linux or if I do nothing it then starts in linux. Will this present any problem if I instlal Ubuntu to replace the Mepis? Any special instructions?

Are you dual booting with win XP or Win 7 or Mepis is the only distro.

I always go for manual installation i.e. select third option 'something else' then format / create partitions and install any distro.

by default GRUB is installed in sdA, which has MBR. Please note that it is sdX and not sdXY i.e. sdA and not sdA1 or sdA5

I have installed XP, Xubuntu 11.10, Bodhi Linux 1.3, Linux Mint 12 and Pinguy 11.04 (too many distros :D )

I have a common /home partiton for all distros, but have different user name. I dont know if keeping same user name can be of help or not, mostly with profile and settings

Generall partitions are:

/ - root partition 20 GB to 50 GB or even more

/home - common home partition

/swap - 2x times RAM but not greater than 4 GB.

To enter size of partition, unit to be entered is in MB.

SO if you want to create 50 GB partition, then it will be 50 x 1024 = 51200 MB

If you have win XP, there will be NTFS partitions

My exp is that the boot loader of the last distro installed automatically takes over from older distro. I installed Pinguy as last distro, so I have the GRUB of Pinguy OS. it is not a problem. IF I login to Xubuntu and run

```
sudo update-grub
```

then GRUB of Xubuntu will overwrite GRUB of Pinguy OS, but will detect all Distros and XP. 

So it should not be a problem, even if you are replacing MEPIS with Ubuntu :) 

If you face any problems you can fix any Grub related problems, mostly with the help of LIVE CD of the same distro having same version that is installed.

---

