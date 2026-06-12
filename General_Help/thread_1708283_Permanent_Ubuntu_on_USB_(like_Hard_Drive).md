---
title: "Permanent Ubuntu on USB (like Hard Drive)"
date: 2011-03-16
forum: General Help
---

### Post by wrichtmyer on 2011-03-16
Hey guys,

For an English project we're supposed to make a George Orwell desktop environment (wallpaper, games, photos, etc.) and I wanted to do this with Ubuntu. The part where I'm stuck is that I have to submit it to the teacher via USB, and whenever I use the USB it will not save changes.

I downloaded Ubuntu and formatted it so I can live-boot off the USB. Now when I edit appearances, desktop backgrounds, and other things in this liveboot I am unable to KEEP THE SAVED CHANGES because every time I reboot it clears to a "fresh install." How can I change Ubuntu so that it'll be able to save the changes and work essentially as a Hard Drive and save the changes, instead of a CD?

Thanks for your help! :D

-Will

---

### Post by flaak_monkey on 2011-03-16
this site should have al your answers for portable linux needs, including persitant enviorment. 

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by C.S.Cameron on 2011-03-16
Use USB Startup Disk Creator from the Live USB and select Extra Space to get a persistent flash drive.

You can also extract usb-creator from the iso if you want to run in Windows.

---

### Post by khaos1985 on 2011-03-16
Actually if you are able to do a full install to a USB drive(thumb drive) is a lot better and more efficient on the OS and any systems hardware.  I have truthfully done this for myself to repair some of my personal friends and families windows based virus ridden PC's. It allows you to save stuff, like wallpapers and other settings plus personal "items" if need be.

---

### Post by lithopsian on 2011-03-16
It sounds like you just copied an ISO image to a bootable USB?

A full install to the USB drive is by far the simplest way but you'll need about 4GB minimum, maybe more.  You'll also need to make sure it has Grub on the USB so that it is truly portable, so you might end up making your main machine unbootable without the USB (until you reinstall Grub on it).

Most of the fancy workaround tutorials are to enable you to have a persistent USB on a smaller drive.

---

### Post by C.S.Cameron on 2011-03-16
If yo should actually want a Full install here is a step by step for a 4GB drive:

Check MD5SUM of the Ubuntu iso file.
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 400MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2.77GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 600MB, Beginning, Ext2, and Mount point = "/home" then OK.
[B](Important)
Confirm "Device for boot loader installation" points to the USB drive. [/B]Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by I2k4 on 2011-03-16
Everything you need to know is right here in simple steps with pictures:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

At Step 2, for USB, at Show Me How step 8, look at the dialog box at the optional step to create  "Persistence" - do it.  Be sure to use half your USB drive's space for persistence.  A 4GB drive with 2GB Persistence is plenty for installing most packages and saving all preferences and settings between boots - Ubuntu Desktop 10.10 can run reasonably well, even on a netbook.  

(Don't know why Ubuntu doesn't refer to the Persistence option in their instructions, as it's the ideal way to "shop" different versions without risking repeated hard drive installations.)

The main thing to know about running from USB drive,apart from it being slower than an HDD, is that the HDD does not immediately mount during the boot - the delay in mounting can confuse applications that may be set to automatically boot with the system but need folders on the HDD (DropBox, for example.)

---

### Post by wrichtmyer on 2013-02-28
Hey everyone, I know this is (2 years) late but I got it working! Thanks again.

---

