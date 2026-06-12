---
title: "How do you make more space for linux?"
date: 2012-07-27
forum: General Help
---

### Post by Parkman123 on 2012-07-27
I am installing ubuntu using wubi, the windows installer, but I am going to need more than 30GB which seems to be the max, because I am making Android Roms, and those are massive files. Is there a way to give it more space than the 30GB, I have like 570GB open on the HD...

---

### Post by CatKiller on 2012-07-27
You could always dual-boot & install Linux natively. Wubi is really just for trying things out.

---

### Post by Parkman123 on 2012-07-27
> **CatKiller said:**
> You could always dual-boot & install Linux natively. Wubi is really just for trying things out.

thanks, but I can not partition my hard drive, not sure why, but i can't!

---

### Post by CatKiller on 2012-07-27
I'd imagine it's because you already have too many Primary partitions. Or you're trying to change a partition that's already mounted. Those are the obvious ones.

---

### Post by Parkman123 on 2012-07-27
> **CatKiller said:**
> I'd imagine it's because you already have too many Primary partitions. Or you're trying to change a partition that's already mounted. Those are the obvious ones.

Ohh yeah thats probably it. I have the (C,H,E, and D) All the ones that came on the computer... Should i get rid of HP_Tools, or do you know if thats needed? If you don't know, thats fine! I wouldn't think you are a HP Technician :)

---

### Post by CatKiller on 2012-07-27
Yeah, I've come across HP's stupidity before. One of the partitions is tiny & just contains utilities that you'll never use. I copied them to a directory on another partition before I blew that partition away, since it wasn't my computer, but they're unlikely to ever do anyone any good.

Once you've got rid of that partition you can create an Extended partition. Linux is perfectly happy to use logical partitions in an Extended partition for everything.

You'll probably want to resize the other partitions too. You can't do it from within Windows, since the partitions would necessarily be mounted. GParted on the Ubuntu cd should be fine, though. Backup your important stuff in case it isn't.

---

### Post by Rob_H on 2012-07-27
> **Parkman123 said:**
> Ohh yeah thats probably it. I have the (C,H,E, and D) All the ones that came on the computer... Should i get rid of HP_Tools, or do you know if thats needed? If you don't know, thats fine! I wouldn't think you are a HP Technician :)

You'll need it if you need to reinstall Windows someday.

The next best thing to having a dedicated partition and dual-booting is running Ubuntu in a virtual machine. Take a look at [VirtualBox]("https://www.virtualbox.org/").

---

### Post by CatKiller on 2012-07-27
> **Rob_H said:**
> You'll need it if you need to reinstall Windows someday.


Not really. They don't give you an install disc (meaning you might as well acquire one from somewhere else) & the image that they do give you is on a different stupid and unnecessary partition.

---

### Post by oldfred on 2012-07-27
First have good backups, particularily the repairCd and some way to reinstall Windows.

Backups ---------
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
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Parkman123 on 2012-07-27
Thanks everyone! I moved my HP TOOL's stuff all to my primary partition, just incase I screw myself over, and I am going to delete that partition. Then,  I am going mess around with it, and make it 100gb, for linux!

---

