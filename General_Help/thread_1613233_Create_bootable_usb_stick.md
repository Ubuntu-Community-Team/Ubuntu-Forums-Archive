---
title: "Create bootable usb stick"
date: 2010-11-04
forum: General Help
---

### Post by plusle on 2010-11-04
Running: Ubuntu 9.04 32 bits


Hey, i'm currently in a big problem. I'm trying to create an bootable usb drive for installing windows 7 so i took this release
"Microsoft.Windows.7.Enterprise.x64.Integrated.October.2010-BIE"

1. Extracted to get the iso
2. Formated my 8gb usb flash drive with gparted
3. Extracted all the files from the iso with UNetbootin to my usb stick
4. Restarted and selected boot from removable drive in the bios options

After step 4 nothing worked i tried to remove booting from the hdd to force the computer to boot from the usb drive but just get the message that i need to insert an bootable media or restart.

Tried several times and the usb worked propperly while installing ubuntu 9.04 which I run this writing moment. I'm out of ideas and I don't have an cd/dvd reader to boot an dvd from either so via usb is the only thing my knowledge is capable to.

---

### Post by plusle on 2010-11-05
No one who can help? Tried to do this on a windows 7 machine to without any results.

---

### Post by udinnet on 2010-11-05
are you sure that image is a bootable? and again check your boot record on USB stick. There might some problems with USB boot.

---

### Post by phredbull on 2010-11-05
I've never heard of a Live Win or Live Mac session, only Linux. Are you sure this is even possible?

---

### Post by sikander3786 on 2010-11-05
You need to make your partition active to boot from it.

Try putting the boot flag on your partition from gparted and try booting again.

If you can do it from Windows, it would be easier.

There is an official Windows 7 USB creation tool

[http://store.microsoft.com/help/iso-tool](http://store.microsoft.com/help/iso-tool)

If you want to do it manually, here are the instructions.

[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)


Edit: Following website mentions that it can be done from unetbootin (which is in the Ubuntu repositories), but I strongly doubt because unetbootin is Linux specific software. But you can give it a try.

[http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/](http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/)

---

### Post by C.S.Cameron on 2010-11-05
Format flash drive NTFS and set boot flag with gparted.
Extract iso or copy disk to flash drive.

---

### Post by celldweller1591 on 2010-11-05
Download win2flash and try it with wine. if it works you are good to go. Just google for download links.

---

### Post by plusle on 2010-11-08
There was nothing wrong with my usb stick since it worked on another computer.

Now the problem is when I try to boot Windows 7 from usb drive it won't  boot. Have checked bios that removeable dev is prio 1 and I even tried  to delete any other option then boot from usb.

Tried the usb stick on my HP desktop and it booted from the usb stick  without any problems. I have an ATI motherboard and i'm quite new in  linux so can't realy provide any information about the motherboard but  I'll show a pic.

Don't know what i'm doing wrong since I can boot another computer with the usb stick.



Motherboard: [http://data.fuskbugg.se/dipdip/motherboard.png](http://data.fuskbugg.se/dipdip/motherboard.png)

---

### Post by RoyLongbottom on 2010-11-08
[FONT=Verdana]You might need two USB sticks and firstly transfer the Installer from the ISO file to one of the sticks using:[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana][http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]I did this for 32-Bit Ubuntu 10.10. It was bootable but I had to press F8 following power on to select the boot drive. The USB stick booted OK and, after a while, came up with Try and Install options. Try worked fine on PCs with 64-Bit Vista, 64-Bit Win7 and a 32-Bit Vista based laptop, where even the wireless connection worked. For Install, I assumed that a second USB stick would be needed. I copied the ISO file to a DVD and used that. [/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]On installing on the USB stick from DVD, using default option, the hard drive boot sector is changed, producing options for Windows or Ubuntu following power on, and the USB stick not being bootable on another PC. I did not want this and restored the disk Master Boot Record via the Windows DVD repair option.[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]On the next go, I used advanced Ubuntu install options, where the USB stick can be selected as the booting source. The snag is that partitions/space has to be manually allocated. For my 4 GB stick I had around 3 GB Ext4 format Mount Point / (root), 500 MB FAT 32 MP /windows (in root folder) and the remainder as for paging. It is all new to me and someone else might say what the settings should be. For a later 16 GB USB stick, I had to use an earlier Advanced Setting option and allocated a 6.8 GB FAT partition outside the Ubuntu space (don&#8217;t know how).[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]The end product boots on different PCs, mainly after pressing F8 after power on, giving selections of Ubuntu or Windows booting. With no USB stick, Windows is booted automatically.[/FONT]
 
[FONT=Verdana]Roy[/FONT]

---

