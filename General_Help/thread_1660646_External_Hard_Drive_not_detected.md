---
title: "External Hard Drive not detected"
date: 2011-01-05
forum: General Help
---

### Post by mentalzoom on 2011-01-05
I have 1tb Seagate Freeagent NTFS External HD.
I have Windows Vista Ultimate SP1 with dual boot as Ubuntu.
i'm primarily a windows user, since i'm not that well acquainted with linux.

Problem-
External Hard Drive does not detect- when i connect it..it just gives a whirring sound and the "MY COMPUTER" window hangs.

figured out the cause- and temporary solution- The drive should do principle mount automatically. It won't if the file system is not "clean". That is possible if the drive was connected while you hibernated Windows, or if you did not properly disconnect the drive.


I booted with ubuntu 
and did the following-

*sudo fdisk -l*

and got the following:

[INDENT]Disk /dev/sdb: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x396e2b4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS[/INDENT]



Then i typed:

[I]sudo mkdir /media/FreeAgent
sudo chmod 777 /media/FreeAgent[/I]


And wrapped it up with editing fstab with the following code:

[I]#FreeAgent USB Drive
/dev/sdf1 /media/FreeAgent ntfs defaults 0 0[/I]


Now the browser window for the freeagent hard drive pops up and i can access everything.

I try to shutdown the computer but it won't as long as the hard disk is connected. So i have to pull the usb out. And the problem remains the same.

I want the hard disk to be detected normally on my windows/linux (like normal usbs work-plug it in and it works). 
Also have no clue how to work a temporary solution like this with windows yet. I have boot with ubuntu everytime and repeat these steps when i want to access it.


Additional info- i found the help/steps to do what i did here- [http://ubuntuforums.org/showthread.php?t=651929](http://ubuntuforums.org/showthread.php?t=651929)

Any help is appreciated.:confused:

---

### Post by johnalexrob on 2011-01-05
I dont know if I can be of much help, but I'll try. 
So it won't work on windows at all? Do other devices do the same?

---

### Post by mentalzoom on 2011-01-06
> **johnalexrob said:**
> I dont know if I can be of much help, but I'll try. 
So it won't work on windows at all? Do other devices do the same?
No, it won't work on windows. I have to repeat all the steps over again in ubuntu everytime i want to access it. I tried to connect it to other window computers, but the problem is the same.

The other devices work fine on my laptop.

Thanks for the help.

---

### Post by Mark Phelps on 2011-01-06
> **mentalzoom said:**
> ... So i have to pull the usb out. And the problem remains the same.

When you pull out the USB connection, you are CAUSING the problem -- because that is an "unclean shutdown" of the drive -- and whey you then plug it back in when running MS Windows, it won't open it.

You NEVER want to just pull out a USB drive or stick.

Also, I would advise against mounting it in your FSTAB.

So, you first need to plugin the drive with MS Windows and see if you can run a chdsk on the drive to fix the partition.

IF that works, CLEANLY unmount the drive in MS Windows.

Then, go into Ubuntu and comment out that drive entry in the FSTAB file.

Plugin the drive.  There may or may not be an icon popup on your desktop.

If there is no icon, open Places and see if the drive is shown there.  IF it is, double-click the drive to mount it.

IF it is not shown there,  you may have to go back to mounting it via FSTAB.  But if you do that, you would have to unmount it using the "sudo umount xxxx" command.  OR, leave it connected when you shutdown the machine and only unplug it AFTER your machine is turned off.

---

