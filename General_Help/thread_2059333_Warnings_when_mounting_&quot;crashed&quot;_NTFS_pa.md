---
title: "Warnings when mounting &quot;crashed&quot; NTFS partition"
date: 2012-09-17
forum: General Help
---

### Post by FishLeg on 2012-09-17
So my little home server died on me after about 8 years. It was running Windows, so all the drives are NTFS. As the machine just died while running, the partitions seem to not be closed properly or something.
Now I tried to set up a new server using ubuntu, and when I mount any of the partitions I get this warning:> NTFS-fs warning (device dm-0): load_system_files(): $LogFile is not clean.  Will not be able to remount read-write.  Mount in Windows.What exactly does it mean? As a precaution, I unmounted the volumes and remounted read only. I get the same warning, but then I checked most of the files and directories, and everything seems to be fine. I don't think the server did anything when it stopped working, so there should be no damaged files that were about to be written or something. Still I don't really know what to make of this warning. Is there any tool for Linux to fix this $LogFile or whatever else might be wrong? The message seems to suggest there is no other way but to fix the drives using a Windows computer, but I don't really wanna do that. The server really was the only Windows machine left in my home, simply because it kept working for so long. ;)
I  really don't wanna lose any files by randomly trying some tools, so I thought I might ask here to make sure.

---

### Post by Mark Phelps on 2012-09-18
What it generally means is the the NTFS filesystem(s) got corrupted and Linux won't mount them read/write -- to prevent any further damage.

The general way to fix this is to mount the filesystems in an MS Windows PC and run CHKDSK on each of the partitions -- which is basically what it is telling you to do.

Some folks have had success using NTFSFIX -- but that only repairs the most basic of NTFS problems and is not a substitute for CHKDSK.

Sorry, but you will have to attach these drives to a working MS Windows PC to fix them.

---

### Post by oldfred on 2012-09-18
I have used a Windows 7 repair USB to run chkdsk on my XP install, so if you have an XP install disk or can make a Windows 7 repairCD or USB you can use those.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

