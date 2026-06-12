---
title: "windows 7 dual boot problems"
date: 2012-02-22
forum: General Help
---

### Post by dan0804smith on 2012-02-22
hey im trying to do a dual boot with 10.04 and windows 7.  linux doesnt allow for any more that 4 partitions.  my laptop already came with 4 partitions, recovery, os, hp tools ,and systme.  so how should i go about instaling ubuntu?

---

### Post by oldfred on 2012-02-22
It is not Linux that only allows 4 partitions but all PCs with MBR partitions.

You have to decide to backup & delete one or more partitions. Both vendor recovery after making the recovery DVDs and the Vendor tools after backing them up are candidates. You cannot delete the hidden 100MB Windows boot partition nor the main c: drive partition.

Best to make recovery DVDs whether you delete it or not. Also make a full backup of your Windows partition and make a Windows repairCD as with any system changes you may need it to repair Windows later. The site we used to recommend for a Windows repairCD now charges $10, so make that CD yourself first.

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

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Someone posted that copying the HP tools the a new partition in the extended partition you create still works. So if you really want to keep them, backup, delete partition, and create an extra partiton in the extended partition for the HP tools.

Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

