---
title: "Live USB won't save changes"
date: 2010-05-13
forum: General Help
---

### Post by otester on 2010-05-13
I tried the guide on pendrivelinux, using Universal USB Installer and the image and Ubuntu won't save the changes.

Creating a "start-up disk" using the Ubuntu disk creator just made an install disk even with the 4GB for saving stuff ticked.

I have an Intenso 16GB USB flash drive.


Any help would be great :popcorn:

otester

---

### Post by blazemore on 2010-05-13
If you have access to a Windows machine, try this utility: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

It is amazing, and will sort persistance out for you automatically.
IMO the guides on pendrivelinux are at best outdated and at worst actually damaging to flash drives (too many needless partitioning and formats)

---

### Post by wilee-nilee on 2010-05-13
> **otester said:**
> I tried the guide on pendrivelinux, using Universal USB Installer and the image and Ubuntu won't save the changes.

Creating a "start-up disk" using the Ubuntu disk creator just made an install disk even with the 4GB for saving stuff ticked.

I have an Intenso 16GB USB flash drive.


Any help would be great :popcorn:

otester

How full is the thumb? And did you use the slider to allow the 4 gigs or just tick on the stored in reserved extra space. 

All the thumb loaders work fine you just have to know what your doing. I think pendrivelinux seems outdated because you have so many choices and it is hard to wade through it to find what you want.

For example this will tell you how to make the persistent as large as you want.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)
Note that if you create a ext2 partition named casper-rw, that when you remove the one in home you will lose whatever has been done so far, but will now have a custom persistent size. Also you don't want to upgrade kernels or distro for this sort of portable to keep working.

---

### Post by otester on 2010-05-13
> **wilee-nilee said:**
> How full is the thumb? And did you use the slider to allow the 4 gigs or just tick on the stored in reserved extra space. 

All the thumb loaders work fine you just have to know what your doing. I think pendrivelinux seems outdated because you have so many choices and it is hard to wade through it to find what you want.

For example this will tell you how to make the persistent as large as you want.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)
Note that if you create a ext2 partition named casper-rw, that when you remove the one in home you will lose whatever has been done so far, but will now have a custom persistent size. Also you don't want to upgrade kernels or distro for this sort of portable to keep working.

Thanks for that link.

I forgot to set the 4GB persistence in Universal USB Installer to start with.

A bigger problem now is the errors I'm getting, fgrlx seems to be  stopping a lot of things from working (ATI driver?) :(

Can't really make a new partition without solving underlying problems can I?

---

### Post by wilee-nilee on 2010-05-13
> **otester said:**
> Thanks for that link.

I forgot to set the 4GB persistence in Universal USB Installer to start with.

A bigger problem now is the errors I'm getting, fgrlx seems to be  stopping a lot of things from working (ATI driver?) :(

Can't really make a new partition without solving underlying problems can I?

I think you want to realize that this type of install, has some limitations in customizing, in that the original ISO is still running the show basically. Not sure about driver issues though. 

It might be better to start over with the usb creator, by making a 1 gig fat32 partition, then using the slider so that you have the casper-rw persistent in home. Now you can build that 2nd ext2 named casper-rw before you install with the usb creator and once it is installed you just remove the casper-rw from home. You will have the persistent size you want if you want more then 4 gigs.

You could take the thumb your using at this time and build that 2nd partition, but once you remove casper-rw from home you will have a larger persistent, but only what was on the ISO will be available.

If it was me I would get the daily Lucid ISO and use that as a starting point. Any other distros will require a larger upgrade that will include kernels and other stuff that, may bork the install due to the original ISO being part of the OS.

---

