---
title: "Lucid-USB-Persistent &quot;Create Startup Disk&quot; works but fails update - Bug filedMake"
date: 2010-06-14
forum: General Help
---

### Post by emarkay on 2010-06-14
Second time I tried to make a boot USB with "Create Startup Disk" in an updated Lucid.
This is a 16GB USB with 4GB persistence.

Upon rebooting I get" "Kernel Panic. Not synching VFS. Unable to mount root on unknown block (8,1)" and the a hang.


 This happens when I update the  USB install with "Update manager". I did the same thing last night, and the same result this morning on a completely "erased" USB stick. I get a message at the end of the update in the "Details" section about 3 "Linux" installs - x.22 Kernel, -Generic) that even "Depmod" can't fix.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/593352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/593352)

---

### Post by C.S.Cameron on 2010-06-14
If you want to be able to update or upgrade a flash drive install do a full install.
A persistent install uses a compressed CD image. It is not easy to modify.
An upgrade will not modify the kernel and an update fills the drive with stuff that does not get deleted from the image.

---

### Post by emarkay on 2010-06-15
> **C.S.Cameron said:**
> If you want to be able to update or upgrade a flash drive install do a full install.
A persistent install uses a compressed CD image. It is not easy to modify.
An upgrade will not modify the kernel and an update fills the drive with stuff that does not get deleted from the image.


I have dine this before, albeit with a third party program - Can you confirm your information;  as the Lucid install does allow up to a 4 gig persistence. 
I know that, as I was able to change various settings add programs across multiple reboots.

It's not an install or persistence issue, it's an update one.

---

### Post by C.S.Cameron on 2010-06-15
I'm not sure how to confirm.
I'm only talking about updating and upgrading.
All changes are saved to a file named casper-rw, it is the only file on the live USB that changes.
Plug your pendrive into a running computer and check the Date Modified on the files inside it. Only the date on casper-rw changes.
If you want to see what is inside casper-rw delete the file and make an ext3 partition and label it casper-rw.
It will become populated with files and folders the next time you boot from the flash drive.
An update using Update manager may work once or twice but is not a good idea for a smoothly running flash drive install.

If you do a full install to your flash drive you can update and upgrade to your hearts content. Only the amount of space you are using will be taken up, your casper-rw file is taking 4GB whether you use it or not.

---

### Post by emarkay on 2010-06-17
Again, thanks but it's crashing at the Kernel Update.  It's got nothing to do with the Casper file

This also happens when I use the method from "PenDriveLinux".

I even updated (all 300 or so files from the past 48 days or so) new Lucid data using Update Manager, EXCEPT the x.22 Kernel files, then it booted OK - But then I updated the Kernel files with Update Manager, I got the "Kernel Panic" on reboot.

Look this is a serious problem - doesn't anyone else use Persistent Lucid USB's?

---

### Post by emarkay on 2010-06-17
Also: could it be because the Updater is trying to install and configure GRUB2?

I just thought that this may be an issue - I never had to install a GRUB on a USB stick before - it presents a list of the volumes in my PC as well as the USB volume.  Checking one or all does not work, and checking none just aborts the install of GRUB2, and the update continues.

---

### Post by C.S.Cameron on 2010-06-17
The kernel on a Live USB is read only, it can't be updated, honest!

The kernel is inside a file named filesystem.squashfs, This file is 671.9 MB for 10.04 32 bit, check it yourself.

---

### Post by garvinrick4 on 2010-06-17
Try partitioning the drive to sdb1 4 gig and sdb2 12 gig and install the Live USB on the 4 gig format the 12 gig to fat32 for data. Just see if that will work out the problems without over thinking the issue. Has allowed me to install what I need in packages, I always seem to stay about
at the 3.5 gig with the packages I install. Which is close to what it allows in persistence. As CS Cameron stated
I keep the same kernal as the image I use to make the USB.

---

### Post by emarkay on 2010-06-18
> **C.S.Cameron said:**
> The kernel on a Live USB is read only, it can't be updated, honest!

The kernel is inside a file named filesystem.squashfs, This file is 671.9 MB for 10.04 32 bit, check it yourself.

Dude, it is "updated "by being REPLACED...  :) 

The  "update/upgrade" process downloads and installs the next version number Kernel and in the process, then apparently removes the old kernel, it appears , in a non GRUB2 system.

---

### Post by emarkay on 2010-06-18
> **garvinrick4 said:**
> Try partitioning the drive to sdb1 4 gig and sdb2 12 gig and install the Live USB on the 4 gig format the 12 gig to fat32 for data. Just see if that will work out the problems without over thinking the issue. Has allowed me to install what I need in packages, I always seem to stay about at the 3.5 gig with the packages I install. Which is close to what it allows in persistence. As CS Cameron stated I keep the same kernal as the image I use to make the USB.

Interesting, but I fail to see how the partition size would affect the ability of a newer Kernel to install properly.  Plus, the "Casper" size itself is 4Gb, so that wouldn't leave any room for the data.

Also, how does one partition a USB drive - Gparted?  
Should I use EXT 2,3,or 4 for the Linux part?

---

### Post by Chame_Wizard on 2010-06-18
I was able to create a USB boot disk ,without any problem(on a 2 GiB).

---

### Post by emarkay on 2010-06-18
> **Chame_Wizard said:**
> I was able to create a USB boot disk ,without any problem(on a 2 GiB).

Did you also run "Update Manager" and get all (300+) updates, including the latest Kernel (2.6.32-23-generic), and then be able to boot back into the updated USB? 

That's the issue here.

---

### Post by C.S.Cameron on 2010-06-18
> Also, how does one partition a USB drive - Gparted?
Should I use EXT 2,3,or 4 for the Linux part?

Windows can only see data on the first partition of a flash drive and will only see FAT and NTFS.

Usb-creator will only work when installing to the first partition and requires FAT (16 or 32).

You can create persistent casper-rw and home-rw partitions as ext2, ext3, ext4 or reiserfs after the first partition. These are not limited to FAT32's 4GB as are persistent casper-rw and home-rw files.

If you are intent on upgrading the kernel I understand that you can decompress filesystem.squashfs, insert the new kernel and then re compress it. There used to be info on pendrivelinux.com about working with filesystem.squashfs.

---

### Post by emarkay on 2010-06-18
> **C.S.Cameron said:**
> Windows can only see data on the first partition of a flash drive and will only see FAT and NTFS.

Usb-creator will only work when installing to the first partition and requires FAT (16 or 32).

You can create persistent casper-rw and home-rw partitions as ext2, ext3, ext4 or reiserfs after the first partition. These are not limited to FAT32's 4GB as are persistent casper-rw and home-rw files.

If you are intent on upgrading the kernel I understand that you can decompress filesystem.squashfs, insert the new kernel and then re compress it. There used to be info on pendrivelinux.com about working with filesystem.squashfs.

So we are getting to a solution - The Kernel on a USB, apperantly can NOT be updated as with a "normal" install.  

Is this because this is a "hybrid"" A Live-CD (fixed image) that can be updated with new programs and updates; for all EXCEPT the Kernel?

Why am I almost 100% sure I used to update Jaunty and Kaemic USB's without problems?

---

### Post by oldfred on 2010-06-18
An example of full install to Flash or SSD.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by C.S.Cameron on 2010-06-18
When you update a persistent flash drive, all the old stuff stays on the drive taking up space but is masked by the new update stuff.

What kernel version shipped with the 10.04 Live CD? 
What kernel version is currently available?

---

### Post by emarkay on 2010-06-18
More clues pointing to a faulty memory (my head...) :
			 		   		 		 		On a persistent  thumbdrive made with usb-creator, unetbootin, etc you end up with a  bootable disk image. This image is not easily modified.
If you want to be able to update or upgrade you should do a full  install, that is:
Disable or unplug your internal hard drives.
Plug in your target fllash drive.
Boot your Live CD or Live USB.
Select Install Ubuntu at the second screen, (the one after language  options).
This will take more space than a "persistent" install" but will be act  just like a full install to hard drive."

[http://ubuntuforums.org/showthread.php?p=8671454](http://ubuntuforums.org/showthread.php?p=8671454)

---

### Post by emarkay on 2010-06-18
> **C.S.Cameron said:**
> When you update a persistent flash drive, all the old stuff stays on the drive taking up space but is masked by the new update stuff.
What kernel version shipped with the 10.04 Live CD? 
What kernel version is currently available?

2.6.32-20 or -21 as I recell, and the latest is now: 2.6.32-23-generic

---

### Post by C.S.Cameron on 2010-06-18
I do things a little different than Herman with a Full install, I like to keep the first partition as FAT 32 for Windows data and like a separate home partition:

Turn off and unplug the computer.
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
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning, and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

---

### Post by emarkay on 2010-06-18
Looks like I need an "USB install" not a "Persistent Live-CD USB"?

Just want to know for sure, as it's about an hour each time to install and update and then find "Panic"... :)

---

### Post by leorolla on 2010-06-18
> **emarkay said:**
> Looks like I need an "USB install" not a "Persistent Live-CD USB"?

Just want to know for sure, as it's about an hour each time to install and update and then find "Panic"... :)

Yes!!!

That's it.

I have installed to USB many times... it's a little slow but you don't need to stay there watching.

I just choose the USB, partition it, choose the install partition and it  installs there. It's just an install like any other.

For me it works withoug unplugging the HD. If it works for you, even better, you can skip the open-unplug-plug-close part.

----

As for what causes it not to work with the Persistent+LiveCD, I don't know. You may keep this academic discussion of what goes wrong...
Maybe there is some embedded Grub stuff that is chainloaded by the FAT32 syslinux type of boot and updating screws it up.
Maybe this trick of masking deleted content when mounting the persistent memory does not happen before the kernel is loaded.

---

### Post by emarkay on 2010-06-18
Thanks all!

That's what I did - just installed a new install over on the USB.

---

### Post by garvinrick4 on 2010-06-18
A install on a USB will have a mbr so if you put in a friends machine with Windows will over write Windows boot loader and install grub2. Will freak a Windows man out. I am sure you know this but had to say. The Live USB version will not touch mbr installed currently on machine but only 4 gig in persistence because of the Fat32 restrictions. Just to go over these things so someone does not format a 16 gig with /boot a / and a swap and stick in buddies machine to show him how cool Linux is. 
 And will make itself sdb or sdc or sdd according to where it stands in USB position and if you have a grub.conf of flash being sdb and you then insert as sdc have to update-grub and grub-mkconfig so is preferred to use as same sdx number. Unless you have no room left on hard drive I really have learned there is no reason to use over the 4 gig of a persistence install as Live USB with own boot than a Flash install. As stated you can partition in gparted to sdb1 4 gig and sdb2 as a 4 or gig data partition or 12 gig according to size of flash for anything you want to carry on flash drive and use no mbr in install.Plenty of room for nice install in 4 gig. Unless you just want to do it for kicks or to use a install with a different grub so you can practice reinstalling you grub to your machine for learning purposes. For instance make a Fedora with legacy and use it with your 10.04 Ubuntu on HDD. Will over write grub with legacy.  Just a reminder for those who try, be aware of mbr.

---

### Post by C.S.Cameron on 2010-06-18
> A install on a USB will have a mbr so if you put in a friends machine with Windows will over write Windows boot loader and install grub2

This has never ever happened to me in the last four years of using these things and I have never heard of it happening to anyone else.

---

### Post by oldfred on 2010-06-18
We have seen where on an update-grub from a USB hard drive (not sure about flash) that it may write to sda rather than sdb. 

These comments I copied from others:

Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by wilee-nilee on 2010-06-18
> **C.S.Cameron said:**
> This has never ever happened to me in the last four years of using these things and I have never heard of it happening to anyone else.

Same here I have a 16 gig running Maverick fully installed; with my aceraspire with XP no mbr overwrites on this or two other computers.

> 
We have seen where on an update-grub from a USB hard drive (not sure about flash) that it may write to sda rather than sdb.

These comments I copied from others:

Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+s...b2/+bug/496435](https://bugs.launchpad.net/ubuntu/+s...b2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

This makes sense.

---

### Post by garvinrick4 on 2010-06-18
> **wilee-nilee said:**
> Same here I have a 16 gig running Maverick fully installed; with my aceraspire with XP no mbr overwrites on this or two other computers.




How do you make choice of which to boot Maverick or XP? Does it automatically boot into the one you want to use when USB is installed, no you choose Ubuntu. And
then when you unplug the USB it automatically boots with Windows boot manager, yes but grub2.

  OldFred seems to have something going on. Otherwise I do believe others are using grub2 with grub2 on USB drive and do not know it was overwritten. Try to make an install on USB with grub legacy OS and see if you can get a grub2 to boot without reinstalling it. MIght just overwrite your HDD, just might.
  When Flash with XP installed grub was overwritten to grub2 but when USB is not installed grub2 automatically defaults to boot to single install 
without stopping at grub2 menu. But grub2 is there or USB install maverick would not boot.

---

### Post by C.S.Cameron on 2010-06-18
I don't think grub or grub2 overwrites anything with out being told to.

My laptop is dual boot with grub legacy, it gives the choice to boot XP, 10.04, memtest and flash drive. 

It boots my Full install thumbdrive without overwriting anything.

I can plug the thumbdrive, (10.04, grub2), into any other computer in the house without overwriting their MBRs.

I don't think grub runs around like some sort of virus overwriting things without permission, at least not in my house it doesn't.

---

### Post by garvinrick4 on 2010-06-19
> **C.S.Cameron said:**
> I don't think grub or grub2 overwrites anything with out being told to.

My laptop is dual boot with grub legacy, it gives the choice to boot XP, 10.04, memtest and flash drive. 

It boots my Full install thumbdrive without overwriting anything.

I can plug the thumbdrive, (10.04, grub2), into any other computer in the house without overwriting their MBRs.

I don't think grub runs around like some sort of virus overwriting things without permission, at least not in my house it doesn't.
So at one time it was a ubuntu install with legacy and when you upgraded to a version with grub2 you choose to leave the installed version of grub when prompted to by upgrade. And you already have a Ubuntu install on HDD. Makes more sense now. Just really surprised a fresh install of 10.04 on flash does not try to upgrade your legacy to grub2 but on to something new, good luck and have a nice day Sir.

---

### Post by wilee-nilee on 2010-06-19
wasted space and wasted time.

---

### Post by garvinrick4 on 2010-06-19
Got to involved in thread and was a bit over zealous. There are always things to learn
in Linux.

---

### Post by wilee-nilee on 2010-06-19
> **garvinrick4 said:**
> Got to involved in thread and was a bit over zealous. There are always things to learn
in Linux.

You to I thought it was just me.;)

---

### Post by leorolla on 2010-06-19
I'm the most newbie in this thread :o

I used to think that grub2 only writes stuff to any of MBR or PBR when you manually run grub-install or grub-setup.

So I was wrong...

Side comment: I'm already a bit disappointed that GNU/Linux with Grub2 is the only booting scheme that cannot be installed politely inside its own partition (the blocklist solution is really unreliable). I posted this on a LP bug report, but still need to take a deep breath and file a bug about this... though I have little hope that people will accept to call this a bug. This scheme already has deep roots in the whole grub2 design and in the developers' mentalities. "If grub2 is so good, why in earth would you want anything else in the MBR anyway?". Poor, limited view of things.

So where is this whole thing heading to?

I'm afraid more and more people will prefer the KISS technology and go back to lilo :(

Could some grub2 expert tell us exacly when and how grub2 writes data to MBR/PBR?

---

### Post by C.S.Cameron on 2010-06-20
I think I am terribly wrong.
I did a new Full install of 10.04 to flash drive using my laptop with the HDD plugged in.
The laptop is dual boot XP/Ubuntu with legacy grub.
I then booted my office computer which is XP only.
I can no longer boot Windows on it with or without the flash drive plugged in. I now need to find my Windows disk, LOL
I may have to rethink the wisdom of doing full installs to flash drive.


Edit:
Dang, I forgot to reset BIOS to give my XP HDD boot priority.
It was not case of grub overwriting windows mbr afterall.
I reset BIOS and everything is ok.

---

### Post by leorolla on 2010-06-21
> **garvinrick4 said:**
> A install on a USB will have a mbr so if you put in a friends machine with Windows will over write Windows boot loader and install grub2.

So you are saying that just by booting this USB in different machines will spread Grub2 to innocent people's MBR?

Do you know when and how it happens?

Could you quote links where we can confirm that this is what Grub2 does? It is very hard to find accessible documentation about what Grub2 really does at the low level.

---

