---
title: "chmod mistake"
date: 2010-07-27
forum: General Help
---

### Post by E MAN on 2010-07-27
Recently i was fixing a permissions error on my home folder. In the process i ran accidentally chmod 777 in the root directory. BIG mistake. Now i cant run sudo, or start network manager. I am currently on vacation and made a bootable version ov ubuntu on my flash drive, but i wouldn't boot. I think it is because i chmod'ed  the grub folder (with is in the root) I have a boot CD a home, but is there anyway to fix it beforehand?

Thanks

---

### Post by Bachstelze on 2010-07-27
If you have access to another computer, you can download an Ubuntu ISO and make a bootable Flash drive out of it.

---

### Post by E MAN on 2010-07-27
I already tried that, but it did not work. The computer went to a black screen with a blinking cursor for about 30 seconds, then the computer booted off the hard disk. I have also checked the boot order in the BIOS, USB is set to first, CD second, hard disk third, and network fourth.

---

### Post by mikewhatever on 2010-07-28
If you try booting from external media, files on the internal hard drives should play no role or interfere with the process. What did you use to make 'a bootable version ov ubuntu'?

---

### Post by E MAN on 2010-07-28
The only computer I had with me ws a mac so i did this:
> 
**Mac**
 
We would encourage Mac users to download Ubuntu Desktop Edition by burning a CD for the time being. But if you would prefer to use a USB, please follow the instructions below.
 
Note: this procedure requires an .img file that you will be required to create from the .iso file you download.
 
TIP: *Drag and Drop* a file from Finder to Terminal to 'paste' the full path without typing and risking type errors.

[LIST=1]
[*]Download the desired file
[*]Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
[*]Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert-format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
[*]**Note:** OS X tends to put the .dmg ending on the output file automatically.
[*]Run diskutil list to get the current list of devices
[*]Insert your flash media
[*]Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
[*]Run diskutil unmountDisk /dev/diskN (replace *N* with the disk number from the last command; in the previous example, *N* would be 2)
[*]Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
[*]
[LIST]
[*]Using /dev/rdisk instead of /dev/disk may be faster.
[*]If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
[*]If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
[/LIST]
[*]Run diskutil eject/dev/diskN and remove your flash media when the command completes
[*]Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick
[/LIST]
(Copied from ubuntu.com)
 
I will try it again today.

 
Thanks

---

### Post by hudsonl on 2010-07-28
You might want to try Knoppix for that .... burn a CD and boot to the CD.

It's debian based (like Ubuntu) ... and great for recoveries.

[http://www.knoppix.net/](http://www.knoppix.net/)

---

### Post by E MAN on 2010-07-28
Sorry, but i don't have a cd with me. Also, the computer still will not boot from my flash drive. It goes to a black screen with a blinking cursor. Then after about 15 seconds it boots off of the harddisk.

---

### Post by E MAN on 2010-08-01
i reinstalled from my cd

---

