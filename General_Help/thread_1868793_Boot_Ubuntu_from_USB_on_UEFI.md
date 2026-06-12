---
title: "Boot Ubuntu from USB on UEFI"
date: 2011-10-24
forum: General Help
---

### Post by t_h on 2011-10-24
I just bought a Asus E35M1 Deluxe motherboard. Now I am struggling to get it to boot from USB since I don't have an optical drive.
I have managed to get it to boot simply by extracting the ubuntu-11.10-desktop-amd64.iso to the FAT32-formatted USB stick. When I boot I get some "GNU GRUB version 1.99-12ubuntu5" that tells me "no loaded kernel" when I type 'boot'.

What does this mean? Am I on the right path?

Ultimately I want to dual boot Ubuntu and Windows 7, if that matters.


I have googled for about 5 hours, and 99% of all the info I find concerns booting on a Mac... Maybe it's the same procedure for creating a bootable USB stick?

---

### Post by dcstar on 2011-10-25
> **t_h said:**
> I just bought a Asus E35M1 Deluxe motherboard. Now I am struggling to get it to boot from USB since I don't have an optical drive.
I have managed to get it to boot simply by extracting the ubuntu-11.10-desktop-amd64.iso to the FAT32-formatted USB stick. When I boot I get some "GNU GRUB version 1.99-12ubuntu5" that tells me "no loaded kernel" when I type 'boot'.

What does this mean? Am I on the right path?

Ultimately I want to dual boot Ubuntu and Windows 7, if that matters.


I have googled for about 5 hours, and 99% of all the info I find concerns booting on a Mac... Maybe it's the same procedure for creating a bootable USB stick?

So what is wrong with following the simple instructions on the Ubuntu download site for creating a bootable USB?

---

### Post by t_h on 2011-10-25
> **dcstar said:**
> So what is wrong with following the simple instructions on the Ubuntu download site for creating a bootable USB?

I was not aware that I was to use the same procedure for booting on a mac as on my Asus EFI motherboard. Now I know though. Thanks for the kind reply, and sorry if I bothered you with my silly question :)

Btw for everyone else. Here are the instructions for getting it to boot on a EFI or UEFI board, quoted from [http://www.ubuntu.com/download/ubuntu/download:](http://www.ubuntu.com/download/ubuntu/download:)
> Mac

We would encourage Mac users to download Ubuntu Desktop Edition by burning a CD for the time being. But if you would prefer to use a USB, please follow the instructions below.
 
Note: this procedure requires an .img file that you will be required to create from the .iso file you download.
 
TIP: Drag and Drop a file from Finder to Terminal to 'paste' the full path without typing and risking type errors.
 
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
Run diskutil eject /dev/diskN and remove your flash media when the command completes
Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick

---

