---
title: "Mounting .disk file in windows"
date: 2011-09-26
forum: General Help
---

### Post by iceman1991 on 2011-09-26
I installed ubuntu 11.04 inside Windows 7 sometimes back. Due to some reason my ubuntu crashed. Now i want to recover the files in my linux drive. Since ubuntu creates a root.disk file where it saves all the data, I want to know is there any I can recover that data or mount that file to browse the data in that file?

---

### Post by oldfred on 2011-09-26
Welcome to the forums,

You cannot mount if from Windows but should be able to mount if from a liveCD. If you installed directly into Windows you may not have liveCD but should have one anyway just for repairs. Also make a Windows repairCD or USB.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by bcbc on 2011-09-26
The answer also depends on why it's crashing. Most of the time (with 11.04) a crash usually involves a problem with the root.disk. e.g. see [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

If you have the root.disk you can view it from windows using this tool: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)  (the actual download is here: [http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/) )

---

