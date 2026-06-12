---
title: "How to install nVIDIA drivers on bootable ubuntu 10.10 USB"
date: 2010-12-16
forum: General Help
---

### Post by sniper7137 on 2010-12-16
Hi i am totally new to linux and ubuntu (10.10 is the first release i have used)

I have successfully managed to create a persistent ubuntu 10.10 bootable usb drive.

I really want to enable the advanced 3d effects that ubuntu offers but I'm having trouble installing the drivers for my geforce 6600LE on the persistent usb.

I attempted an install from the Appearance window, the package failed to install after downloading. So i used the following commands someone posted:
[FONT=monospace]
[/FONT]sudo apt-get install nvidia-current[FONT=monospace]

then after reboot:

[/FONT]sudo nvidia-xconfig

i again rebooted to save the changes but this time ubuntu's desktop did not load. Instead i got a terminal...with loads of gibberish (for me at least).

I am stuck here:confused:

Any help will would be much appreciated.

---

### Post by cariboo on 2010-12-16
There seems to be q bug in getting persistence to work on usb drives. There is a large thread about it [here]("http://ubuntuforums.org/showthread.php?t=1636650"). but nobody has come up with a easy working setup. I just did a regular install on an 8Gb stick, and can use it on  any system that can boot from USB.

---

### Post by C.S.Cameron on 2010-12-16
Nvidia drivers will not work on a persistent disk image install.
If you want to use proprietary video drivers you can do a Full install to your USB drive.

You might not need Nvidia drivers to get special effects such as rotating cube etc.

Install Compiz Settings Manager from the Software Center or Synaptic.

With a persistent install you will probably need to add "compiz" to Preferences / Startup Applications.

---

### Post by efflandt on 2010-12-16
While you cannot install nvidia drivers on iso on USB even with persistent data (because video driver loads from fixed data before persistent data is mounted), you can probably get GL by entering "experimental" in Quick search of Synaptic and install **libgl1-mesa-dri-experimental**.  It will not be nearly as fast as nvidia drivers, but may allow you to enable special effects.

---

### Post by sniper7137 on 2010-12-17
Please tell me what you mean by a Full Install to a USB.

Does it mean that i install Ubuntu to my USB as if it were a hard drive??

---

### Post by C.S.Cameron on 2010-12-17
> **sniper7137 said:**
> Please tell me what you mean by a Full Install to a USB.

Does it mean that i install Ubuntu to my USB as if it were a hard drive??

Yes, exactly.

Here is a step by step for 10.10, adjust partition size to suit:

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
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
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

### Post by sniper7137 on 2010-12-17
Thanks for the quick reply. I would try it but problem is. I dont own a 8gb usb. Just 4gb.

---

### Post by C.S.Cameron on 2010-12-17
> **sniper7137 said:**
> Thanks for the quick reply. I would try it but problem is. I dont own a 8gb usb. Just 4gb.

Try it on the 4GB with just the / partition, not the optional ones.

---

### Post by sniper7137 on 2010-12-17
Thanks C.S. Cameron. I did not install to the usb for the fear of messing up my hard drives and data. I share the PC with my dad so I cant open up the casing as i am not allowed to. But i managed to install ubuntu on one of my hard drives alongside windows. Your instructions helped. I am replying from within ubuntu with all effects enabled and nvidia drivers installed.

Others: If u want to enable nvidia device drivers you will have to disable the Nouveau Kernel. Follow the instructions here:
[http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html](http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html)

Thanks everyone for helping.

---

