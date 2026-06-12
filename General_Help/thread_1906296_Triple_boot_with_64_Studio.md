---
title: "Triple boot with 64 Studio"
date: 2012-01-08
forum: General Help
---

### Post by sks24 on 2012-01-08
Does Ubuntu Studio 11.10 have the Unity interface?
Is there a performance/efficiency penalty for using Ubuntu Studio over 64 Studio?  

The reason I'm asking is because I purchased one of these used Dell D630 (PP18L) laptops which are coming off lease, and I want to do video editing on it.  The scenes shouldn't be longer than 2 minutes at 1080p.  The laptop is dual-core, 80GB, with 2 GB RAM - but supports up to 8 - and I think I might put Win 8 on it when the RTM for that comes out. (Right now it's running XP.)

I'm thinking that I would like to have three partitions on it.
One Windows, the other two Linux: Ubuntu 11.10 desktop, and 64 Studio.  Studio has out of the box real-time kernel support. I really don't know what that means(!), but I think it might help me with movie editing, which I would like to do with this machine.  Wikipedia says that Ubuntu Studio no longer has real-time kernel capability.  Moreover, 64 Studio offers paid email support.  Does Canonical offer paid support for Ubuntu Studio?

If I created two empty partitions in addition to the Windows which is on there now (there is no restore partition) would the(Debian) 64 Studio installer ask me which of the two empty partitions I wanted to put it on?  And I'm thinking I would finish with the Ubuntu 11.10 installation, which defaults to the empty partition?  Of course, I would want all the OS options to be in the GRUB menu.

I would end up, then, with three primary partitions, and then two swaps, I think.  

Does that installation scheme sound like it might work?

Is there a how-to anywhere on triple boot configurations/installations: Windows/Linux/Linux?  

Thanks in advance,
Scott

---

### Post by Double.J on 2012-01-08
Hi there! no, Studio won't be getting unity - you will ofcourse be able to install it if you so wish, but the plan of the project is to move over to XFCE4 instead of Gnome as this uses fewer resources, leaving more available for all the high ram editing it is intended for!

Okay next triple booting- 

Easiest way to do this is 
1 set up your drive (obviously) I recommend a number of partitions set up thus- 

1 primary for windows - it's unclear how many primary partitions windows 8 will use, as vista and 7 used 2 by default, but 8 is meant to be using secure boot, but I'd imagine it'll still be 2 - just make one formatted ntfs - the windows installer will split that up itself.

the rest of the drive you format as an extended partition using a [gparted live cd]("http://gparted.sourceforge.net/"). then into that extended partition you create your partitions. the minimum you'd need would be 2x 15GB for the ubuntu's and 2GB for a swap partition. I'd also recommend creating a data partition formatted ntfs - somewhere you can store all your docs and things that each OS can access.

in terms of using them - install windows first, then the ubuntu version you will use least. when you get to partitioning, choose "something else" and select one of your partitions for linux, format it as ext4 and mount point as /. Where it says where to put the bootloader - you need to change this to the /dev/sda number that you chose to format - not sda. after install, reboot - windows will load and you wont have an option for ubuntu - this is right.

the repeat the install for the ubuntu you will use primarily, format and mount the other partion the same as before, but this time let it install the bootloader to /dev/sda this time it will configure the bootloader for all three os and when you restart you should be tripple booting 

all the best :)

---

### Post by goofey24 on 2012-01-08
> **gnu/mirow said:**
> Hi there! no, Studio won't be getting unity - you will ofcourse be able to install it if you so wish, but the plan of the project is to move over to XFCE4 instead of Gnome as this uses fewer resources, leaving more available for all the high ram editing it is intended for!

Okay next triple booting- 

Easiest way to do this is 
1 set up your drive (obviously) I recommend a number of partitions set up thus- 

1 primary for windows - it's unclear how many primary partitions windows 8 will use, as vista and 7 used 2 by default, but 8 is meant to be using secure boot, but I'd imagine it'll still be 2 - just make one formatted ntfs - the windows installer will split that up itself.

the rest of the drive you format as an extended partition using a [gparted live cd]("http://gparted.sourceforge.net/"). then into that extended partition you create your partitions. the minimum you'd need would be 2x 15GB for the ubuntu's and 2GB for a swap partition. I'd also recommend creating a data partition formatted ntfs - somewhere you can store all your docs and things that each OS can access.

in terms of using them - install windows first, then the ubuntu version you will use least. when you get to partitioning, choose "something else" and select one of your partitions for linux, format it as ext4 and mount point as /. Where it says where to put the bootloader - you need to change this to the /dev/sda number that you chose to format - not sda. after install, reboot - windows will load and you wont have an option for ubuntu - this is right.

the repeat the install for the ubuntu you will use primarily, format and mount the other partion the same as before, but this time let it install the bootloader to /dev/sda this time it will configure the bootloader for all three os and when you restart you should be tripple booting 

all the best :)
Thanks, informative to me also :)

---

### Post by sks24 on 2012-01-12
thanks gnu/mirow, 

I had forgotten about files on a dedicated partition...I do want to learn how to set that up and execute it.  I’m shaky with “/dev/sda” and so forth.  I think I’ll set up the "new" Dell with a camera in front of it so that I can take shots of the screen and use the other laptop to post both the photographs and questions asking after what to type and so forth.  Probably the middle of next week.

Thanks again, 
Scott

---

