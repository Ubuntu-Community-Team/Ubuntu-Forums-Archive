---
title: "Creating a usb bootable Windows XP install stick"
date: 2011-03-27
forum: General Help
---

### Post by pod25 on 2011-03-27
I no longer have access to a Windows machine.

I have been trying for days now to successfully create a usb bootable Windows XP install, but without success.

So, is it possible ?
If so, HOW ?

Tools used so far without success:
UNetbootin
And
Startup Disk Creator.

---

### Post by oldfred on 2011-03-27
I saved these links.

Copy Windows XP to usb
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)


You may do better on a windows forum.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

### Post by pod25 on 2011-03-27
Thanks for the reply oldfred.
But all those links are based on the fact that I am using a Windows machine to create the bootable usb stick.
I am not not using a Windows machine, I am using Ubuntu because I do not have access to a Windows machine.

I have tried and tested cmd programs in WINE, but all failed.

I need to make the XP usb bootable stick using Ubuntu.

---

### Post by dragonfly41 on 2011-03-27
I made a bootable FreeDOS on USB as in this thread ..

[http://ubuntuforums.org/showthread.php?t=1712971](http://ubuntuforums.org/showthread.php?t=1712971)

The problem is I can't find a way of accessing the internal drives to run a chkdsk on a failed Vista partition.

But you might for example be able to install Windows XP on a bootable USB drive to get you going.

Copy the XP installation files onto the USB then run startup.exe in FreeDOS command line.

---

### Post by oldfred on 2011-03-27
I only have XP, but wanted to create a Vista or 7 USB flash repair drive. I downloaded the repairCD, but could not get the flash drive to boot from any Ubuntu type installs. I then created the CD and booted the CD. From the CD, I was able to create/copy itself to the USB flash drive that was then bootable. 

You can run chkdsk on any NTFS partition from the Vista or 7 repair CDs.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by pod25 on 2011-03-28
> **dragonfly41 said:**
> I made a bootable FreeDOS on USB as in this thread ..

[http://ubuntuforums.org/showthread.php?t=1712971](http://ubuntuforums.org/showthread.php?t=1712971)

The problem is I can't find a way of accessing the internal drives to run a chkdsk on a failed Vista partition.

But you might for example be able to install Windows XP on a bootable USB drive to get you going.

Copy the XP installation files onto the USB then run startup.exe in FreeDOS command line.

I have now tried this method a million times, but nothing works.
I used dd to copy the FreeDOS image onto my stick /dev/sdb
I also tried /dev/sdb1

Where does the FreeDOS image go ?
And where does my XP install files go ?

---

### Post by pod25 on 2011-03-28
> **oldfred said:**
> I only have XP, but wanted to create a Vista or 7 USB flash repair drive. I downloaded the repairCD, but could not get the flash drive to boot from any Ubuntu type installs. I then created the CD and booted the CD. From the CD, I was able to create/copy itself to the USB flash drive that was then bootable. 

You can run chkdsk on any NTFS partition from the Vista or 7 repair CDs.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I don't think this reply was meant for me, was it ?

I don't have ANY WINDOWS MACHINES.
I do not have VISTA or WINDOWS 7, so why would I want to download a repair disk for them ?
I do not have a CD drive, which is why I need a XP Bootable USB stick.

---

### Post by pod25 on 2011-03-28
Here is what I have now done.
Installed FreeDOS onto /dev/sdb

Then using gparted, I created a NTFS partition and put the XP install files onto the partition.

It now boots into FreeDOS.
However, I am not sure what to do now.

---

### Post by dragonfly41 on 2011-03-29
What if you now run in FreeDOS command line ..

c> c:\startup.exe    (assuming that startup.exe from XP installation disk is in the same location on the USB as the two FreeDOS  files command.com and kernel.sys)

Does XP start installing into the USB?

It may be that two partitions are needed in the USB.

One partition for FreeDOS + XP installation files 
The other partition for the XP installation created by running startup.exe.

---

### Post by pod25 on 2011-03-29
> **dragonfly41 said:**
> What if you now run in FreeDOS command line ..

c> c:\startup.exe    (assuming that startup.exe from XP installation disk is in the same location on the USB as the two FreeDOS  files command.com and kernel.sys)

Does XP start installing into the USB?

It may be that two partitions are needed in the USB.

One partition for FreeDOS + XP installation files 
The other partition for the XP installation created by running startup.exe.

I tried using c:\startup.exe also c:\setup.exe but both failed.
I assumed it was because I created a partition for the xp install files.
But without knowing the drive letter for the new install partition, I could not cd into it.

This is driving me nuts now and I really miss my music in the car.
Yes, this is for my car pc, which was running XP, but stupidly decided to install Ubuntu, but I can't get anything to run or find a decent front end system, so I'm putting XP back on. Its really hard work not having a cd drive.

---

### Post by dragonfly41 on 2011-03-29
I think it might be winnt.exe

[http://www.petri.co.il/install_windows_xp_pro.htm](http://www.petri.co.il/install_windows_xp_pro.htm)

other ideas here ..

[http://liliputing.com/2008/04/install-windows-xp-on-mini-note-usb.html](http://liliputing.com/2008/04/install-windows-xp-on-mini-note-usb.html)


EDIT:

correction .. this writeup ..

[http://www.vandomburg.net/installing-windows-xp-from-usb/](http://www.vandomburg.net/installing-windows-xp-from-usb/)

at step 6 suggests

Run D:\i386\winnt32.exe /syspart:C: /tempdrive:C: /makelocalsource 

Replace C: with the drive you want to install Windows to.

---

