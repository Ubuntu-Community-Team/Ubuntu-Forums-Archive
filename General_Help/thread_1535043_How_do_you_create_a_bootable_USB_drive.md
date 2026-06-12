---
title: "How do you create a bootable USB drive?"
date: 2010-07-20
forum: General Help
---

### Post by justinsn95 on 2010-07-20
I saw the page that shows you how to put Ubuntu on a bootable drive, but I am not sure that is all I want to do. I do want make ubuntu installable from a flash drive, but I want to be able to put other things on the drive as well. So how do I create a drive, that can install ubuntu, yet still has memtest86 on it? I want to be able to run memtest from the drive without having to be in any OS. 

I would like to just enter a command line to start doing what I want. In my mind, it would go like this: First, I stick the drive in a USB port on the computer. Then I would turn on the computer and go into the boot menu. I would boot into the flash drive, and it would ask me to input command or something like that. Then, if I wanted to run memtest, I could simply enter the command that tells it to run memtest, and it runs memtest. Or, if I wanted to install ubuntu, I just enter the command line that tells it to start up the Ubuntu install, and it starts up the ubuntu install. 

How can I create such a bootable drive? Will all my little apps and OS's on it? There are many things which I would like to put on the drive, I was just using Memtest and the Ubuntu setup as an example.

EDIT: Sorry, I don't know why I chose 64bit as a thread prefix. Must have been a mistake.

---

### Post by oldfred on 2010-07-20
Grub2 as a boot loader will give you that. I have two flash drives. My 4GB has grub2 booting to a grub2 menu and loop mounts several ISO files. My 16GB flash drive has a standard full install of Ubuntu and about 8GB of storage.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Above solution looks very good but I did it manually:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

---

### Post by justinsn95 on 2010-07-20
Please forgive my noob ignorance, but I am afraid I did not understand very much of your post. Does loop mounting the ISO's actually install them on the target Hard disk drive? I don't want to just be able to run them from the flash drive, but rather install them permanently on the computer. I also wish to be able to do this with Windows installs as well. And also be able to run Memtest and a whole lot of other bootables.

---

### Post by C.S.Cameron on 2010-07-20
There are several methods of installing Ubuntu to flash drive, from full install, (Just like to internal drive), to Live install, (Like the Live USB), Live with persistence, and bootable iso.
The easiest way to get started is probably the Live with persistence.
Boot your Live CD and go to System/Administration/Startup Disk Creator.
You can select Stored in reserved extra space to get persistence.

I

---

### Post by techunit on 2010-07-20
[Here]("http://ubuntuvideotutorials.wordpress.com/category/utilities-2/bootable-flashdrive/") are two videos covering how to create a bootable Ubuntu USB drive... you can use them to install ubuntu...

---

### Post by justinsn95 on 2010-07-20
Can you still put a windows iso on there and memtest and a bunch of other stuff? I am imagining something that you would just enter a command line with the correct folder, and it would open and execute whatever was in that folder. Be it memtest, an ubuntu installer, or a windows installer. Like I said I don't just want an ubuntu specific drive, but rather a multipurpose drive.

---

### Post by mcduck on 2010-07-20
> **justinsn95 said:**
> Can you still put a windows iso on there and memtest and a bunch of other stuff? I am imagining something that you would just enter a command line with the correct folder, and it would open and execute whatever was in that folder. Be it memtest, an ubuntu installer, or a windows installer. Like I said I don't just want an ubuntu specific drive, but rather a multipurpose drive.

Yes, you can. At least if you don't use all the available extra space for the persistence file.

Also you should note that the Ubuntu install image already has memtest included (available from the boot menu), so there's no real reason to add it separately to the drive.

Personally I just installed Grub2 to the drive and now I can drop in disk images and boot from them with a simple edit of the config file, and the flash drive of course still works just like any other removable drive. It just happens to be able to boot into six different Linux installers and XBMC... :D

I'm not sure if there's any method that would allow you to boot a windows disk image that way, though. I've never tried. (and probably won't ever try either, considering that I don't play PC games or use any windows-only software.)

---

### Post by McRat on 2010-07-20
I've never booted Win from a USB, but here's a tutorial:
 
[http://www.tomshardware.com/reviews/windows-pocket,1113.html](http://www.tomshardware.com/reviews/windows-pocket,1113.html)

---

### Post by C.S.Cameron on 2010-07-20
If you want a Windows installer on the disk it needs to be on the first partition for windows to see it.
Make that partition NTFS, add a boot flag and copy the Windows 7 install disk to it.
I'm not sure if you can use grub2 to select between it and the other stuff you want on the disk, but I don't see why not.

---

### Post by justinsn95 on 2010-07-20
> **mcduck said:**
> Yes, you can. At least if you don't use all the available extra space for the persistence file.

Also you should note that the Ubuntu install image already has memtest included (available from the boot menu), so there's no real reason to add it separately to the drive.

Personally I just installed Grub2 to the drive and now I can drop in disk images and boot from them with a simple edit of the config file, and the flash drive of course still works just like any other removable drive. It just happens to be able to boot into six different Linux installers and XBMC... :D

I'm not sure if there's any method that would allow you to boot a windows disk image that way, though. I've never tried. (and probably won't ever try either, considering that I don't play PC games or use any windows-only software.)

> **McRat said:**
> I've never booted Win from a USB, but here's a tutorial:
 
[http://www.tomshardware.com/reviews/windows-pocket,1113.html](http://www.tomshardware.com/reviews/windows-pocket,1113.html)

Thanks a lot for the help. But to clarify, I am not trying to boot windows from the drive, only use the drive to install windows on a computer. Or am I? Perhaps they are one and the same and I just don't know it. Do you have to be able to do some kind of windows boot to be able to install it from a flash drive? It doesn't seem to me like a Windows 7 install would have the same resource requirements, as actually running windows 7. Then again, I am in new territory here so if anyone could explain that I would be very grateful. I am thinking of it more like Ubuntu, where all you really have to run is the installer.

Just in case anyone is curious, I fix computers locally for side work. That is why I am trying to come up with this all in one type of deal. I figure I can use one of those 32 or 64Gb flash drives, and not have to have all these different discs on hand, where ever I may be, when I am working on something. Plus its a challenge to create this USB stick, cause I don't know how to do it. :)

---

