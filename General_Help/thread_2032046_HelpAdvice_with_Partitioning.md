---
title: "Help/Advice with Partitioning"
date: 2012-07-23
forum: General Help
---

### Post by mblack3nd on 2012-07-23
Hello, 

I have searched around and haven't quite found anything that helps figure out what I want to do/am hoping to do.

I just got a new Samsung laptop with those hybrid drives: 750 GB + 24GB (SSD) Express Cache. 

It has Windows 7 and I want to install Ubuntu also. 

Last time (I think I had a thread about this), I had:
Windows partition
extended Partition
   /
   /home
   /swap
Files partition

I am curious if I can do that again. I don't want to screw up the Express Cache stuff for Windows and I am afraid of doing that. I have seen some people saying to install Ubuntu on the SSD but won't that jack up the EC stuff?

Thanks for your help. As far as I can see in Windows, I have:

Disc 0 -
    System (100 mb)
    C: (675 gb)
    Recovery partition (23.55 gb)

Disc 1 -
    Primary Partition (19.36 gb)
    Hibernation Partition (3 gb)

Is the Disc 1 the ExpressCache drive? Do I need to use a /swap partition or could I use that Hibernation Partition???

Thanks for all your help.

---

### Post by oldfred on 2012-07-23
I have always been leery of hibernation with dual boot as any writing from one system into the other will corrupt it.

Before I did anything I would want good backups. Both system recovery to DVDs and an image of Windows. And a Windows repairCD.

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


Some links on similar systems.

[http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/](http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/)

Looks like you could use SSD separately.
[http://ubuntuforums.org/showthread.php?t=1982997](http://ubuntuforums.org/showthread.php?t=1982997)

---

### Post by mblack3nd on 2012-07-24
Thanks for the links!

To be honest there wasn't too much bloatware with this machine and I haven't really deleted anything, I wouldn't have an issue with just going back to the the way I received it if something went awry. None of my files are even on here.

---

