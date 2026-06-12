---
title: "Installing Ubuntu On USB Device"
date: 2011-01-06
forum: General Help
---

### Post by sandyp on 2011-01-06
I'd like to give Ubuntu a try.  Rather then using the LiveCD, is there a way to install it on a USB device and boot from this device (USB hard drive or stick)?

I'd also like to be able to ensure that I can do all of the necessary security updates as they become available.

Thank you.

---

### Post by TeoBigusGeekus on 2011-01-06
Try [this]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar").

---

### Post by Harrycrossxx on 2011-01-06
if you go here : [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

and follow the steps, step 2 shows you how you can create a live USB.

---

### Post by C.S.Cameron on 2011-01-06
The above methods do not allow making security updates.
You will need a Full install to do this.

Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the usb drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by sandyp on 2011-01-08
Thank you for the instructions, I'm downloading Ubuntu today and am going to give it a go this weekend.

I noticed one of the drives that I have supports both SATA and USB connections and the laptop I'm going to use has a SATA port and SATA HD.

1.  Is it possible to just pull the internal SATA drive out out of the laptop.
2.  Install Ubuntu on the SATA external drive (The laptop would see it as an internal drive)
3.  Once installation is complete, just use this external drive as a USB drive (would use it as an external SATA, but the connection is a bit flaky).

---

### Post by C.S.Cameron on 2011-01-08
> **sandyp said:**
> Thank you for the instructions, I'm downloading Ubuntu today and am going to give it a go this weekend.

I noticed one of the drives that I have supports both SATA and USB connections and the laptop I'm going to use has a SATA port and SATA HD.

1.  Is it possible to just pull the internal SATA drive out out of the laptop.
2.  Install Ubuntu on the SATA external drive (The laptop would see it as an internal drive)
3.  Once installation is complete, just use this external drive as a USB drive (would use it as an external SATA, but the connection is a bit flaky).

Sounds good to me.

---

### Post by sandyp on 2011-01-09
> **C.S.Cameron said:**
> Sounds good to me.

Long story short, I didn't use the SATA drive, but used a USB key that I had.

I removed the hard drive from the laptop, plugged in the USB key and installed from CD.  It took a while to install and do the updates, mostly because I guess it is USB 2.0, but it did finish.

I have two errors on boot up (modprobe: fatal could not load /lib/modules/2.6.35-24-generic-pae/modules.dep, no such file or directory), but it looks like others have this as well and it doesn't affect the function of Ubuntu.

Loading from USB stick is slow and I guess with time, the read/writes will affect the USB stick.  My laptop has 8GB of RAM.  Is there any way to load my Ubuntu build into RAM and just run it from there or do I have to use remastersys to make a custom livecd?

---

### Post by C.S.Cameron on 2011-01-09
> **sandyp said:**
> Long story short, I didn't use the SATA drive, but used a USB key that I had.

I removed the hard drive from the laptop, plugged in the USB key and installed from CD.  It took a while to install and do the updates, mostly because I guess it is USB 2.0, but it did finish.

I have two errors on boot up (modprobe: fatal could not load /lib/modules/2.6.35-24-generic-pae/modules.dep, no such file or directory), but it looks like others have this as well and it doesn't affect the function of Ubuntu.

Loading from USB stick is slow and I guess with time, the read/writes will affect the USB stick.  My laptop has 8GB of RAM.  Is there any way to load my Ubuntu build into RAM and just run it from there or do I have to use remastersys to make a custom livecd?

You could look here:
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

