---
title: "Windows xp sp3 beside Ubuntu 10.04 LTS"
date: 2011-03-24
forum: General Help
---

### Post by anEarthCitizen on 2011-03-24
Hi, 

Currently I have ubuntu 10.04 LTS as the only OS.

I have two partitions one for ubuntu and it is ext by default for ubuntu's files.

The other is empty NTFS. (yes, it is formatted in NTFS but I haven't saved anything yet on it).

The problem is:

I want to install win xp sp3 on this empty ntfs partition safely (without losing ubuntu).:)

My friend told me ubuntu will be lost even if I didn't touch its own partition.

Sorry for this long post but I am trying to specify accurately my issue.

Thanks.

---

### Post by wilee-nilee on 2011-03-24
Installing xp into a pre-formatted partition or one made with a custom install from the xp install disc will only overwrite the boot=mbr. This can be fixed by reloading the grub bootloader to the mbr.

I have not had xp install to an gparted formatted ntfs, others claim success, but in a custom install on the disc you can make one if needed, just be careful.

---

### Post by Rubi1200 on 2011-03-24
As wilee-nilee said, as long as you point the Windows installer to the correct partition the only thing that will be overwritten is the MBR.

Reinstalling GRUB afterwards to continue dual-booting can be done with just 3 commands.

---

### Post by anEarthCitizen on 2011-03-25
@Rubi1200,

Are these steps what you mean?

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

and if so, then are they correct and sufficient?

thanks guys for help! :D

---

### Post by wilee-nilee on 2011-03-25
> **anEarthCitizen said:**
> @Rubi1200,

Are these steps what you mean?

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

and if so, then are they correct and sufficient?

thanks guys for help! :D

To old and to many posts to have any real relevance.

With the XP choose the custom install and the disc will show you the empty space make sure there is one. Choose quick format of a ntfs there and install to it. You can try the ntfs that is there already without installing and if it doesn't show, and quit the install to blank it for a format from the XP install disc.

Boot to Xp make sure it is working update reboot it again to make sure its working then follow this link to put grub2 back in the mbr from the live Ubuntu cd. 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I am pretty sure you can custom build that partition from the xp install disc. Back up the Ubuntu image it with clonezilla on a external if you want to be real sure.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Jerry N on 2011-03-25
> **wilee-nilee said:**
> 
I have not had xp install to an gparted formatted ntfs, others claim success,.....

I have installed XP and Win 7 on gparted formatted NTFS partitions several times and haven't had a bit of trouble.  That said, I recommend backing up any important data before fiddling with the partitions.  Of course I am sure the OP has already taken care of this.

Jerry

---

