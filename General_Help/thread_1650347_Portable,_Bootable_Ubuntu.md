---
title: "Portable, Bootable Ubuntu"
date: 2010-12-21
forum: General Help
---

### Post by Offbeatmammal on 2010-12-21
I am trying to find a relibable/robust solution to, what is hopefully a simple problem. I'm not a regular Linux user but as I can't find a good Windows solution to this problem Linux has a chance to shine here :)

I want a current Ubuntu build that I can store on a USB Flashdrive (I have an 8GB key available, can go bigger if needed) that I want to be able to plug into any machine and boot from USB and be able to use it as though it was the native OS...

So I need to have a good collection of drivers already on there to cope with random WiFi and graphics cards without needing to download drivers/updates for every machine I use. I need to be able to upgrade it and keep it current. I need to be able to install apps and keep an offline copy of Google mail and calendar in Evolution as well as other documents.

I'd like to be able to set the user/password for logging in as a specific user (potentially might want more than one user)

The goal is to travel with at the bare minimum a virtual machine I can power up anywhere. I'm probably going to have a netbook with Windows on for general "stuff" that I will nomally run this from, but want the physical isolation of keeping the Ubuntu environment portable.

In an ideal world... I'd be able to have a VirtualBox (or similar) on the key as well so I can boot (with perf issues of course) from within a host Windows environment if rebooting isn't possible.

---

### Post by C.S.Cameron on 2010-12-21
You can do all the above with a Full install of Ubuntu to Flashdrive.
A step by step for 10.10 follows.
You may be optimistic if you are planning on running Windows 7 in Virtual Box on an 8GB flash drive, 7 bloats quickly, you will want a large virtual hard drive. 

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

### Post by Offbeatmammal on 2011-01-25
thanks! finally got around to trying it and it works perfectly.

first time I screwed up and managed to bork the MBR of the host machine (luckily a fairly easy fix), second attempt I pulled the drive to make sure and it worked fine.

I've actually got an 8GB key set up as 6GB for Ubuntu and 2GB for swap, looks like it even hibernates (though throws some scary errors both hibernating and starting up... might be because one of the machines I used had 4GB RAM?)

the idea about the Windows mount wasn't to be able to run Windows from the key, but to be able to mount the key in something like VirtualBox running on Windows so I could access the Ubuntu stuff

The one thing I'd love to do is pre-emptivly pull down a bunch of additional drivers so when I hope the Flash key to other machines it's all good to go (for instance one of the machines has a broadcom wifi driver that's not open source so to get that working I had to find a way to get it on to ethernet which was an unexpected hurdle ... is there a recommended way to grab a reasonable set of drivers to facilitate hopping around like that?

---

### Post by blueridgedog on 2011-01-25
Current Linux Journal ([http://www.linuxjournal.com/magazine](http://www.linuxjournal.com/magazine)) on news stands now has a great article on this.

---

### Post by Offbeatmammal on 2011-01-26
thanks - I'll hit the magazine store tomorrow to see what they have to say.

apart from the drivers it looks like it's working pretty well on each machine I've moved it to.

one other question I've got is... why on any machine I boot to this USB Key when I go back to Windows why is the clock there wrong? It's always about 11 hours forward! As long as the Windows machine is set to fix it's clock automatically it's not a huge problem but I'd love to sort it out ;)

Really please with how portable and reliable it's been so far, now got to play with VPN solutions to make it secure (ideally auto-login to a VPN connection so never make a connection over the unsecure interwebs...)

---

### Post by blueridgedog on 2011-01-26
Is the time and time zone correct while operating on the USB OS?

---

### Post by Offbeatmammal on 2011-01-26
> **blueridgedog said:**
> Is the time and time zone correct while operating on the USB OS?

yup, time is right in windows, reboot and start the USB OS and time is still right, reboot back to Windows and the time has jumped ahead. very weird but consistent now on three machines

---

