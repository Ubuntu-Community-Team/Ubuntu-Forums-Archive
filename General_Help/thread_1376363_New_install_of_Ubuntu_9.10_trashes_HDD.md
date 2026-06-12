---
title: "New install of Ubuntu 9.10 trashes HDD"
date: 2010-01-09
forum: General Help
---

### Post by dguildford on 2010-01-09
I have experienced this problem twice in the past three days. I want to build a Ubuntu system onto a USB stick so that I can do private work after hours on a work laptop while travelling.
With both 9.04 and then 9.10 installs, the install writes the GRUB to the desktop's HDD on which I am building the system. This has two effects,
1. The HDD won't boot, without the USB stick in the drive. This makes the reliability of the computer depend upon the stick and
2. The laptop will not boot from the stick because it is not a bootable drive.

Both the desktop and the laptop are XP Professional systems.

To get my desktop back the first time I had to replace the Main Boot Record. Changing from 9.04 to 9.10 did not make a difference. I now have to replace the MBR again.

What gives? I believed that installing Ubuntu is supposed to be easy and non-destructive.

I had formatted the 8GB USB stick with HP USB Format Tool with FAT32.

During the install, I chose the USB stick as the sole recipient of the system.

I like using Linux and have had a Mint6 build for years for just this purpose. However, as I want to now connect with a pre-paid NextG modem, I found it necessary to have a new system. By the way, the Sierra Wireless USB301 NextG modem connected easily when I was running the 9.10 Live CD on the desktop prior to building the USB system.

 I am very annoyed, but would appreciate any advice to get the USB system working.

Frank

---

### Post by Leppie on 2010-01-09
in System>Administration you can find the tool "USB Startup Disk Creator", have you tried using it?

---

### Post by OldGrantonian on 2010-01-09
I saw this link:

[http://www.debuntu.org/book/export/html/160](http://www.debuntu.org/book/export/html/160)

If it works, can you give some feedback :)
.

---

### Post by ankspo71 on 2010-01-09
Hi,
I don't have any personal experience with this, but I have seen the following link mentioned alot...
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)  (has tutorials for what you need to do)
Hope it helps.

---

### Post by dguildford on 2010-01-09
Thanks, all.

Further research has found a number of interesting links. I was not aware of the USB Startup Disk Creator within the LiveCD.

I guess I am most cranky about having to do a recovery on my desktop system. I think this is a dangerous bug.

I'll have a go with this tool.

In the meantime, the attached list is essential reading for someone contemplating making a bootable system on a USB stick.

THIS IS THE ONE!
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

KEEP PERSISTENT STORAGE BELOW 1MB
[http://www.mail-archive.com/plug-applications@lists.plug.phoenix.az.us/msg00080.html](http://www.mail-archive.com/plug-applications@lists.plug.phoenix.az.us/msg00080.html)

FAILURES
[http://ubuntuforums.org/showthread.php?t=1305897](http://ubuntuforums.org/showthread.php?t=1305897)

RECOMMENDED TO DISABLE THE HARD DRIVE
[http://www.ghacks.net/2009/09/24/how-to-create-a-bootable-usb-ubuntu-drive/](http://www.ghacks.net/2009/09/24/how-to-create-a-bootable-usb-ubuntu-drive/)

Frank

---

### Post by Mark Phelps on 2010-01-09
> **dguildford said:**
>  ...During the install, I chose the USB stick as the sole recipient of the system...
While that's true, the default is to install GRUB to the first hard drive it finds. This is something that the installer should make MUCH clearer, as folks installing dual-boot to existing MS Windows systems unknowingly then wipe out their MBR with GRUB.
>  I am very annoyed ...
Don't blame you.

---

### Post by Leppie on 2010-01-09
your system should be easily restored if grub2 is installed.
booting off the karmic livecd issue these commands in a terminal:
```
sudo mount /dev/sda5 /mnt  ##most dual boot systems use sda5 as the linux partition, but amend if different for you
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

easy as that.

---

### Post by dguildford on 2010-01-09
Hello Leppie
I did not attempt a dual boot. I want to boot from an 8MB USB stick.

During installation I saw "SCSI7 (0,0,0) sdb" and then "/dev/sdb1"

Monkey see, monkey do to your code is:

sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda

OK?

Thanks Frank

---

