---
title: "Getting rid of Windows - a couple questions"
date: 2011-11-05
forum: General Help
---

### Post by Musmanno on 2011-11-05
I currently have Ubuntu 11.10 installed on my laptop, which also has Win 7 installed. The laptop has a windows recovery partition that can be used to return it to Toshiba factory condition. Here are my questions:

1. I currently have /root and /home on the same partition; once I remove Windows, I'd like to put /home on its own partition. Is there a way to do this without reinstalling the OS? I'm trying to avoid having to reconfigure my setting, reinstall all my software etc.; and

2. Right now GRUB recognizes the Toshiba recovery partition and I can choose it from GRUB if I wanted to do a restore of the laptop to factory settings. If I remove Windows from the computer, will that recovery partition still be there in case I have need of it?

Thanks!

---

### Post by lykwydchykyn on 2011-11-05
> **Musmanno said:**
> I currently have Ubuntu 11.10 installed on my laptop, which also has Win 7 installed. The laptop has a windows recovery partition that can be used to return it to Toshiba factory condition. Here are my questions:

1. I currently have /root and /home on the same partition; once I remove Windows, I'd like to put /home on its own partition. Is there a way to do this without reinstalling the OS? I'm trying to avoid having to reconfigure my setting, reinstall all my software etc.; and


It's quite possible, and fairly simple in concept; but the only way I know of to actually do it involves some command-line work and hacking the fstab. 

Basically, you need to:
- format the partition
- boot to a recovery prompt
- move the contents of /home to the new partition
- edit fstab to map /home to the new partition
- reboot and hope it works :)

Don't know how comfortable you are with those sorts of things, but that's the process in a nutshell.

> 
2. Right now GRUB recognizes the Toshiba recovery partition and I can choose it from GRUB if I wanted to do a restore of the laptop to factory settings. If I remove Windows from the computer, will that recovery partition still be there in case I have need of it?

Thanks!

Those partitions are typically separate from the windows partition.  If you open up a partitioning tool like GParted, you should see a small FAT32 partition, which is where the recovery system is.  If you leave it alone, grub should still detect it.

---

### Post by satanselbow on 2011-11-05
Moving your home partition is relatively painless - as said above it is a command line job but nothing too terrifying. I did that exact job on my machine yesterday without heart attack or data loss.

This link is excellent : [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I also had to chroot my grub as I had actually forgot that I had banged it to the partition not mbr... my bad!

If it were my machine... I would not concern myself with the factory partition... I can live without losing a day uninstalling all the crapware if I ever have to reinstall. You also lose a lot of control - some Windows recovery solutions still insist on formatting the whole drive with no regard to dualboots or linux installs... very rude.

Find a proper ISO of the Windows version on your machine and reinstall from that if you have to using the key stamped on the bottom of your lappy ;)

I really can't comment how a recovery partition might behave if you completely remove the current windows partition - never tried it :( My guess would be that booting that recovery would either fail altogether - or grab the entire drive for itself. Also remember that there are typically 2 partitions for Windows recovery - one with the actual image the other with the Windows Recovery Environment...

---

### Post by oldfred on 2011-11-05
Just do a full backup.

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Musmanno on 2011-11-05
Thanks guys, I appreciate the info. I don't plan to use Windows any time soon, but I thought I'd keep the recovery partition around so when it is time to sell this laptop and get a new one I can restore Windows onto it.

---

### Post by Musmanno on 2011-11-08
Hey guys - thanks for the info. I screwed something up somewhere along the line, being a relative novice to linux and all. I don't mind being in the command line, but most of the time I'm just copying instructions from somewhere without fully understanding what I'm doing.

In any event, after trying the instructions to move the /home directory to a new partition, I couldn't log into the system. I got the normal login screen after starting the computer, but when I put in my password the screen went blank for a moment and then the login screen came back.

No big deal in the grand scheme of things. My data was all backed up, so I just did a fresh install of 11.10 and then reconfigured things how I like them and reinstalled some software.

Thanks for taking the time to respond to my question.

---

