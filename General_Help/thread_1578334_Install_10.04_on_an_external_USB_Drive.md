---
title: "Install 10.04 on an external USB Drive"
date: 2010-09-20
forum: General Help
---

### Post by Steve00 on 2010-09-20
I am trying to install Ubuntu 10.04 on a Segate USB 2.0 external drive. While Ubuntu did install on the external drive, it will only boot from the laptop on which I did the original install. This was a machine that I had set up to dual boot Win XP and Ubuntu 8.04. When I boot up with my external drive plugged in, I get the GRUB menu on the laptop and can pick and choose whether to boot into Win, Ubuntu 8.04 (on the laptop) or into Ubuntu 10.04 on the external drive. As long as I'm using the original laptop, everything works as advertised.

However, I want a full bootable Unbuntu 10.04 on the external drive so I can use it on multiple machines. Now, when I move to a different machine and try to boot, all I get is a black screen with a white flashing cursor in the upper left hand corner of the screen.

I tried it on multiple machines and get the same result. The machines I tried it on were set to allow a USB storage device to be first in the boot order.

I assume the problem is somewhere in the install where I did not tell GRUB where to load and it, instead, defaulted to my primary hard drive on my original machine.

Any suggestions as to what settings I need to do at the time of install?

Thanks!

--Steve

---

### Post by C.S.Cameron on 2010-09-20
It is best to install Ubuntu to USB using a machine with the internal drive removed or disabled.
If you can't disable the internal HDD you should use the Advanced option after partitioning.


Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
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
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by Steve00 on 2010-09-26
Following the steps above worked for Ubuntu 10.04 installed on the Seagate external hard drive and I could boot it from different computers. I reinstalled the hard drive and when I booted directly to the external drive, I boot directly into Ubuntu 10.04; that is the Grub menu did not pop up offering me any OS choices.

Several problems then arose after I reinstalled the laptop's HD. First, my original laptop would no longer boot (a minor annoyance at most since I had already backed it up and was planning to reformat anyway.) When I tried to boot directly into the laptop, I get a grub rescue> prompt. When the external drive is plugged in I am able to boot into Ubuntu.

All data on the laptop's HD is intact since I could mount all of the drives from Ubuntu 10.04 while running off the external drive.

A day or two later, I ran Ubuntu's system update. I ran the update on the same laptop with the laptop's HD still in place. After the update, I had my OLD grub menu back with Win XP, Ubuntu 8.04 and 10.04. However, the menu is apparently on the EXTERNAL drive. I still get grub rescue> when I try to boot just the laptop.

In addition, the external drive will no longer boot on different machines. Only on the laptop.

Several questions:

How to fix the laptop's grub menu so it will boot the machine's internal HD. All of the data and OS are intact, so it must be a matter of tweaking grub somehow.

How to fix the external drive so it will also continue to boot Ubuntu 10.04 (the only OS on the external drive) from different machines.

How to run future 10.04 updates on the external drive without pulling the laptop's hard drive?

Thanks for your help!

--Steve

---

### Post by C.S.Cameron on 2010-09-26
Update grub on the laptop with the internal drive plugged in and the external drive unplugged.
Update grub on the external drive with it plugged in and the internal drive unplugged.
You can add menuentries in 40_custom for other drives that you wish to boot from grub.

---

### Post by efflandt on 2010-09-26
You have everything mixed up now and I am not sure how to correct it.

There is no need to disconnect the internal drive when installing to a USB drive as long as you know enough to use the **Advanced** button in one of the last install steps to put grub in the mbr of the USB drive instead of mbr of your main hard drive.  You now have grub on both your internal and external hard drives and probably got grub confused as to which it should actually update.

I have Ubuntu on several USB hard drives and they never touch grub during updates except on their own drive.

Installing to an external drive will be easier and more intuitive in future Ubuntu versions because when I put / for 10.10 beta on a USB drive it automatically defaulted to putting grub on the mbr of that drive.

---

### Post by Steve00 on 2010-09-26
Yep. I'm sure I've got Grub throughly confused. I tried updating grub with the internal drive disabled. Despite the fact it was disabled, update-grub still found the 8.04 and WinXP partitions. I did not try physically pulling the HD. Might try that when I get a chance.

Running update-grub with the external drive physically disconnected (after I booted into 8.04 on the internal drive) had no effect. I still get grub rescue> prompt when I then try to boot the internal drive. Interestingly, the commands such as 'cat' or 'boot' do not work from 'grub rescue>' the ls command does work but that is pretty much it.

I'll ultimately do a clean install, but I'd like to figure out how to fix this in case I inadvertently recreate the problem in the future.

Thanks!

--Steve

---

### Post by C.S.Cameron on 2010-09-26
8.04 uses grub legacy and 10.04 uses grub2.

Following shows how to reinstall grub legacy, you should use the 8.04 CD:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Steve00 on 2010-09-26
When I physically removed the internal drive and then ran update-grub, that fixed the external drive.

I'll try the grub legacy fix on the internal drive .... once I find my 8.04 live CD :P

Thanks for the help!

--Steve

---

