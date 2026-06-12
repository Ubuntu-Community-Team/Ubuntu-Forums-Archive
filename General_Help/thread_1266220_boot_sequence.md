---
title: "boot sequence"
date: 2009-09-14
forum: General Help
---

### Post by viralmeme on 2009-09-14
How do I get Ubuntu to automatically log in and skip this screen, specifically the F2 and F3 options

[http://commons.wikimedia.org/wiki/File:Ubuntu_options_boot_screen.png](http://commons.wikimedia.org/wiki/File:Ubuntu_options_boot_screen.png)

---

### Post by P4man on 2009-09-14
once you install it, it will no longer ask :)
Thats only for a live cd.

---

### Post by NoaHall on 2009-09-14
Remove the disk from the cd driver if you've installed it.

---

### Post by viralmeme on 2009-09-14
> **NoaHall said:**
> Remove the disk from the cd driver if you've installed it.
I am running Ubuntu from a USB, with no CD in the drive and it still boots to that screen ...

---

### Post by NoaHall on 2009-09-14
That's because you're using the USB as a install medium. You haven't accutally installed it to USB, instead, you're just running the live "disk" from it.

---

### Post by viralmeme on 2009-09-15
> **NoaHall said:**
> That's because you're using the USB as a install medium. You haven't accutally installed it to USB, instead, you're just running the live "disk" from it.
I used the System->Administration->USB Startup Disk Creator

---

### Post by 3rdalbum on 2009-09-15
> **ymitchell said:**
> I used the System->Administration->USB Startup Disk Creator

Yes. It creates a USB startup disk, based on the live CD. It does not install Ubuntu to your USB drive.

---

### Post by viralmeme on 2009-09-16
> **3rdalbum said:**
> Yes. It creates a USB startup disk, based on the live CD. It does not install Ubuntu to your USB drive.
Ahh, I see I must install it using the Install option .. thinks ...

OK, I installed Ubuntu to the USB stick. I removed it and rebooted. Got 'grub error 21' and had to reinstall the MBR on the main harddrive. So back to the 'USB startup disk'. It does save settings but does run out of space. I read somewhere of creating a separate casper-rw partition to save stuff, but there seem to be differing/conflicting instructions. This version Ubuntu 9.04 - Jaunty Jackalope. "No space left on device" installing Java ...
-------

OK, finally figured it out:

01. To customize the boot sequence edit the files in syslinux.

02. Running out of space:

Saves files/settings are stored in a casper-rw file in the main fat partition. Setting this too large results in a ramfs error on boot. Solution create two partitions, the first one 1GB fat32 and the second ext2 using up the remaining remaining space on the USB device. Label this casper-rw. Install Ubuntu to the first partition using the 'USB startup disk creator'. Select minium space for saved files. Delete the casper-rw file that is created here. Now when you boot, files are stored to the second partition. This includes updates to the system files as well as /home. You can make this as big as you like but on an 8GB USB it does seem to be a little sluggish compared to a 3GB device. I figure 3GB is a minium size. I GB for the system and 2GB for /home etc.

$df -h

/dev/sdb1             1.1G  645M  381M  63% /cdrom
tmpfs                 2.8G  343M  2.4G  13% /tmp

---

