---
title: "booting from usb in osx"
date: 2010-12-23
forum: General Help
---

### Post by nbv4 on 2010-12-23
I followed the instructions [here](http://www.ubuntu.com/desktop/get-ubuntu/download) for installing the ubuntu iso onto a usb stick under osx. The instructions are here:

>  
Download the desired file
Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
Note: OS X tends to put the .dmg ending on the output file automatically.
Run diskutil list to get the current list of devices
Insert your flash media
Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
Using /dev/rdisk instead of /dev/disk may be faster.
If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
Run diskutil eject/dev/diskN and remove your flash media when the command completes
Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick

Everything went well until the second to last step. Why does it want me to remove the USB stick? I need to restart the computer with it in or it to install, correct? The why the bejesus does it want to me to reject the disk? Do I reject the disk and then re-insert it before rebooting? Do I reboot, press alt, then insert the usb stick?

Also, it tells me to press alt "while the mac is restarting". The restarting process takes a minute or two. WHEN am I supposed to press it? I pressed the alt (option) key once a second during the boot process, but nothing happened.

I know the usb stick creation went well because there were no errors durint eh process, and I can go into finder and browse around the files.

Could someone help me here?

---

