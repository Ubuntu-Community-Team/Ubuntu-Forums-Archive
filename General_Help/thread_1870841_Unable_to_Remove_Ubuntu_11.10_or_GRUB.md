---
title: "Unable to Remove Ubuntu 11.10 or GRUB"
date: 2011-10-28
forum: General Help
---

### Post by Player 3 on 2011-10-28
The backstory to this scenario is that I attempted to install Ubuntu again, but it apparently failed because A) after signing in, the OS refuses to go any further than a blank screen with the default wallpaper. That is why I wish to remove Ubuntu and GRUB to try again. This declares Ubuntu a waste of space for the moment. Heck, even reinstalling Ubuntu over that attempt brings up the same problem, each time.

But after a while of research, a simple method would just to backup anything I want and re-install Windows 7 from its installation disc, but my laptop provider did not supply me with a boot disc. Checking in Disk Management of Windows 7, there are three blank partitions, besides OS (C:) and Recovery, which I know are Windows's.

What do I need to do in order to remove Ubuntu **AND** GRUB without a Windows 7 installation disc? Finding out exactly happened with the Ubuntu installation to begin with would also be a plus.

---

### Post by fantab on 2011-10-28
> **Player 3 said:**
> The backstory to this scenario is that I attempted to install Ubuntu again, but it apparently failed because A) after signing in, the OS refuses to go any further than a blank screen with the default wallpaper. That is why I wish to remove Ubuntu and GRUB to try again. This declares Ubuntu a waste of space for the moment. Heck, even reinstalling Ubuntu over that attempt brings up the same problem, each time.

But after a while of research, a simple method would just to backup anything I want and re-install Windows 7 from its installation disc, but my laptop provider did not supply me with a boot disc. Checking in Disk Management of Windows 7, there are three blank partitions, besides OS (C:) and Recovery, which I know are Windows's.

What do I need to do in order to remove Ubuntu **AND** GRUB without a Windows 7 installation disc? Finding out exactly happened with the Ubuntu installation to begin with would also be a plus.

If you could tell us more about how you partitioned your Hard Disk we might be able to help. Post a screen shot of your partitions.

You don't have to reinstall Windows7 unless you have installed ubuntu over it... Have you? Can you boot into Windows 7?

---

### Post by Player 3 on 2011-10-28
Surely.

[IMG]http://i.imgur.com/nso8g.png[/IMG]

Yes, I am able to boot into Windows 7, since Ubuntu didn't work. The factor is more of removing GRUB and the other partitions. In the image, there are three blank partitions. I'm sure they are for Ubuntu.

---

### Post by oldfred on 2011-10-28
Your 100MB partition is a hidden Windows boot/recovery partition. Windows does not always show extended & logical partitions correctly so it is difficult to tell.

First make a Windows repair CD & the Vendor recovery DVDs. An dbackup anything you consider important.
Then you can use manual install or Something Else to reuse the existing partitions. I suggest adding a shared NTFS partition. It is best not to directly write into the Windows system partiiton. If you want you can mount the Windows system partition read only. 

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

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Blaqksheep on 2011-10-28
Actually, oldfred, that 100MB partition is just the bootloader.  The recovery partition is labeled as such.  <.<

[SIDE NOTE] If you want to mount those partitions inside of Windows 7, from your disk manager just right click and assign it a drive letter. [/SIDE NOTE]

There's another way to do what you want.  You can download and use [EasyBCD](http://cdn.neosmart.net/software/EasyBCD/community/EasyBCD%202.1.exe?AWSAccessKeyId=1HCB7Z221V5CV2K1ZDG2&Expires=1319822130&Signature=nxwEOEhGm%2FyJ7g3amJeXglnaBic%3D&response-content-disposition=attachment;%20filename=%22EasyBCD%202.1.exe%22) to remove grub via a GUI from within Windows and restore the Windows boot manager.  Restart your computer after this step to ensure that it restored correctly before removing the Ubuntu partition.  Then simply purge the Ubuntu partition using the tool you used to take that screenshot.  Do NOT do that in the reverse order though or you'll have a pain to deal with.

Once you purge and reinstall, if you have the same problem again just post it and it might be something we can fix.

---

### Post by Player 3 on 2011-11-24
> **Blaqksheep said:**
> Actually, oldfred, that 100MB partition is just the bootloader.  The recovery partition is labeled as such.  <.<

[SIDE NOTE] If you want to mount those partitions inside of Windows 7, from your disk manager just right click and assign it a drive letter. [/SIDE NOTE]

There's another way to do what you want.  You can download and use [EasyBCD](http://cdn.neosmart.net/software/EasyBCD/community/EasyBCD%202.1.exe?AWSAccessKeyId=1HCB7Z221V5CV2K1ZDG2&Expires=1319822130&Signature=nxwEOEhGm%2FyJ7g3amJeXglnaBic%3D&response-content-disposition=attachment;%20filename=%22EasyBCD%202.1.exe%22) to remove grub via a GUI from within Windows and restore the Windows boot manager.  Restart your computer after this step to ensure that it restored correctly before removing the Ubuntu partition.  Then simply purge the Ubuntu partition using the tool you used to take that screenshot.  Do NOT do that in the reverse order though or you'll have a pain to deal with.

Once you purge and reinstall, if you have the same problem again just post it and it might be something we can fix.

I have looked in EasyBCD. The setting only shows Windows with a couple of other partitions.

[IMG]http://i.imgur.com/XZHFi.png[/IMG]

No clue on what to do after this.

---

### Post by Mark Phelps on 2011-11-24
Click the BCD Backup/Repair button.

Then, click the Re-create/repair boot files radio button -- and click the Perform Action button.

---

### Post by Player 3 on 2011-11-25
> **Mark Phelps said:**
> Click the BCD Backup/Repair button.

Then, click the Re-create/repair boot files radio button -- and click the Perform Action button.

Worked. Removing the partition in the disk manager as stated before worked as well. I can now say this problem has been solved.

---

