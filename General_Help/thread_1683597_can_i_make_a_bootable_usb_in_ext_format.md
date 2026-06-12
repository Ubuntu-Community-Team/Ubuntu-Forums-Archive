---
title: "can i make a bootable usb in ext format?"
date: 2011-02-07
forum: General Help
---

### Post by dci on 2011-02-07
I'd like to make a bootable usb that can save more than 4gb of changes, but I don't see a way to use anything other than FAT format when using the disk creator. I can format the hard drive in ext, but creator always reformats in FAT.

---

### Post by josh6190 on 2011-02-07
I've made alot of USB lives and persistents in Windows, and some in Ubuntu using start-up disk creator. I, personally can not see the problem of why you couldn't do that, but if it is being reformatting, it probably doesn't want you to do it. My internet research also suggests that this is not possible. I'll be looking into this for you, as I'm beginning to grow very curious about this too. It would appear as though this is not possible using the start-up disk creator. Perhaps we may need to turn to third-party software.

---

### Post by dci on 2011-02-07
Thanks for the help. Anything that will allow me to have more than 4gb space will do. As far as I know, using another format would be the only way to do that though, since the casper-rw file can't be bigger than that in FAT32, which is the only format that disk creator uses unless there's something I'm missing.

---

### Post by josh6190 on 2011-02-07
Ok, well lets just see here..... I know for a fact Universal USB Installer for windows platforms can be formatted as a FAT (probably 32) and I believe you can have an 8GB Casper-RW. Only problem is it is Windows only. My Dell is a Win7 Ubuntu 10.10 dual-boot, so lemme boot in to Windows, download it, and give it a shot. I might not post my results until tommorow. Fingers crossed for an 8GB Casper!

---

### Post by dci on 2011-02-07
Actually, windows would also be fine for my purposes. I didn't realise there was any good software for making bootable windows USB. When I tried looking it up before, I seem to remember it looking very hard to do.

---

### Post by Rhizoid on 2011-02-07
You can install directly to a USB key formatted to ext.  However, Grub2 doesn't seem to play as nicely with it as Grub does, in my experience at least - would be happy to be corrected - so chrooting into the new install from a liveCD and replacing Grub2 with Grub and building yourself a menu.lst which suits the USB is the best way I've found to do it.

There's some advantages to a direct install over a liveUSB - it's faster, for a start.  Everything is written to individual files instead of a single casper file, ext partitions cannot be written to by windows machines so you're a lot safer plugging your USB stick into a potentially infected Windows box than you are a liveUSB formatted to FAT32.

The biggest disadvantage is the size of the install.  You have a minimum of a 4GB stick to be able to install this to as the whole OS will be approx 3GB plus applications/modifications.

Hope that helps,

---

### Post by dci on 2011-02-07
I tried installing directly to USB, but when I did, it didn't work. 

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faultdy cd/dvd disk or drive, or a faulty hard disk, etc.


I also tried following the steps in this tutorial [http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/) to create a casper-rw ext partitian. I was able to do that, but it didn't work very well either. I'm unable to boot from it using my desktop "Boot Error". My laptop boots it, and it works fine, but it doesn't work the same as with disk creator. Since the caspwer-rw is its own partitian, you also need to allocate extra space to the main partitian.

---

### Post by dci on 2011-02-08
Alright, I was able to do a direct install once I enabled downloading components during install, but like you said, it doesn't boot up as is. I am pretty new to Linux, so I'm not sure how well i'd do replacing Grub2 with Grub. What is the last version of Ubuntu that uses Grub?

---

### Post by mcduck on 2011-02-08
> **dci said:**
> Alright, I was able to do a direct install once I enabled downloading components during install, but like you said, it doesn't boot up as is. I am pretty new to Linux, so I'm not sure how well i'd do replacing Grub2 with Grub. What is the last version of Ubuntu that uses Grub?

Why would you need to do that? Grub2 works just fine from a USB drive. :D I use it all the time with flash rives and portable hard drives....

Are you sure you actually installed Grub to the USB drive (and not, for example, to your hard drive) during the Ubuntu install?

---

### Post by dci on 2011-02-08
Yes, you are right. That is what happened aparently. I had to repair startup for windows on my desktop afterwards. Why is grub installed to desktop hd when I am installing Ubuntu to the flash drive, and how do I correct that?

---

### Post by josh6190 on 2011-02-08
Hi again sorry for the absence, the latest version of Universal USB  Installer only has an 800MB Casper-RW but older version could go up to  8GB. So I will be sifting through the versions of the software sometime  today.  Unfortunately this does not help with the ext, yet if we get an 8GB  Casper, do you still need ext @dci? If not, I can find the appropriate  release of the installer to use for an 8GB Casper, formatted as FAT32. Seriously guys, all this stuff with GRUB2, we won't need it if we use Universal USB Installer. It seems a bit too much for something which is supposed to be relatively simple to complete. We'll let the discussion go onwards, but I don't think we need to do all this.

---

### Post by Rhizoid on 2011-02-08
FAT32 has a maximum file size limit of 4GB... that's any file, not just a casper file.

You don't need such a large casper unless you're installing large applications onto your USB install - for storage you can use the native FAT32 partition, just stick it in fstab with a mount point in, for example, /home/fat32 and you're laughing.

---

### Post by josh6190 on 2011-02-09
Well If you have a larger USB Drive theoretically speaking you can have a larger Casper. Universal USB Installer DID used to support an 8GB Casper-RW. So i don't know what the 4GB limit for FAT32 is about.

---

### Post by Rhizoid on 2011-02-09
The 4GB limit is a limitation of the file system, not of the USB installer.  You just can't make a file of greater than 4GB on a FAT32 partition.  Same as you can't make a file of more than 2GB on a FAT16 partition.

NTFS and EXT are, for all intents and purposes, unlimited as the upper limits far exceed what is available in terms of USB sticks.  Maybe the older version used one or other of those and a different boot loader to syslinux to create 8GB caspers.  It would seem a bit of a backward step to then go to FAT32 and syslinux though eh?

---

### Post by josh6190 on 2011-02-09
indeed.... this is quite a puzzle I have to say...

---

### Post by C.S.Cameron on 2011-02-09
The reason for the 4GB limit is the casper-rw file in FAT32.
You can use a ext2, 3 or 4 partition named casper-rw, instead of this file, then there is no limit.
Partition before installing, use min extra space and delete the casper-rw file after.

---

