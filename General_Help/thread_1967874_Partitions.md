---
title: "Partitions"
date: 2012-04-28
forum: General Help
---

### Post by jafu53 on 2012-04-28
I have 2 partitions, C: and D: , when i make a ubuntu partition, i will lose all the things in the selected partition (D: )?

If i lose my things, can i do a new partition without losing my things?

Thanks

---

### Post by PhantomTurtle on 2012-04-28
If you do not delete them and just shrink it IN WINDOWS, then you will not loose any data.

---

### Post by oldfred on 2012-04-28
Backups are always a good idea.

Are you install wubi or a full install to a new partition?

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by jafu53 on 2012-04-28
i want a full install of ubuntu

---

### Post by PhantomTurtle on 2012-04-28
> **jafu53 said:**
> i want a full install of ubuntu

You just need to shrink your partition then in Windows. Shrink your C or D partition by opening run or searching in the start menu for diskmgmt.msc. Next right click on the partition you want to resize and click on shrink. Choose your size and shrink. Next boot into an Ubuntu live CD/USB and start to install. Here is a tutorial with screenshots that has the same stuff I just wrote down: [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/").

---

