---
title: "Backing up dual boot system with tar"
date: 2011-11-25
forum: General Help
---

### Post by unckybob on 2011-11-25
I have a dual boot system using grub2 to boot Win7 and Ubuntu.

I want to insure myself against the hard drive breaking down completely.

My plan is to backup the root linux filesystem with tar, and then to backup the Win7 filesystem under /media with tar. Then I plan to backup the MBR. I plan to do all the backups to an external drive. 

I have a small drive that I plan to practice reinstalling the system with. 

Once I have made the backups to the external drive, I plan to take out the old working drive and install the smaller empty drive. I will start up with an Ubuntu Live CD. I will restore the MBR from the external drive to the smaller HD. I will create an NTFS partition, an extended partition with an ext4 and linux-swap partition. Then I will restore the respective filesystems. 

My question is: will this work? 

If not, I suspect the case is, that I don't really know enough about this topic. And I suspect that it may be too broad a topic for someone to address properly to answer my question here. 

If so, I would really appreciate it if someone would give me a little background on what I need to do and what I need to study more about to do it. Any links or keywords would be greatly appreciated.

---

### Post by oldfred on 2011-11-26
I do not use tar, but see some issues with reinstalling to a smaller drive.

HowTo: Full backup with tar (older but tar has not changed)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

The issues are the MBR is both a boot loader usually grub or windows and the partition table. If a different drive the partition table will be different.
Also both grub & fstab now use UUIDs to make sure it boots the correct partition. But if you reinstall to a different partiiton then the UUID is wrong. I think Windows works similarly. Windows also has info in the MBR & PBR that has to match the partition table & drive size, so at the minimum you would have to repair it and it may call home as it sees a new install. Or it may not work.

You should have a current repairCD or liveCD  for every system you have installed.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by unckybob on 2011-12-06
Thanks for letting me know some of the issues on my proposed backup. I'm going to study on those things and then see if I still can't make it work. I'll continue to post what I learn and what happens. I hope you'll check back and let me know what you think.

---

