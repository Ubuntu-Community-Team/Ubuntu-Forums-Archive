---
title: "Strange Jaunty Compulsive Auto Mounting USB Hard Drives"
date: 2009-06-27
forum: General Help
---

### Post by ravious on 2009-06-27
I plugged a usb hard disk formatted to ext3 into the system, Drive is ALWAYS able to be accessed from that system.

But when left unattended, you will come back to find multiple icons for the drive on the desktop, and multiple instances of nautilus open to the drive. All remote shares are broken at this point and require that either smb or nfs server be restarted to allow remote clients to access the share. all the extra icons have to be manually umounted and remounted from fstab with sudo mount -a.

I do have the drive setup to auto mount in the fstab, so i have no idea why they UI is freaking out and thinking it has to obsessively compulsively mount the drive..

My only idea is that it might have something to do with a sleep mode either in the drive or an ubuntu power setting, but im not sure. Its almost like the drive goes to sleep, then wakes up and the OS freaks out thinking a new device has been installed and then auto mounts it again. I did try putting a text file on the drive, then setup a cron job to touch the file once a minute to try to keep it from going to sleep incase that was the issue, but it didnt help.

I am still fairly new to linux and i really have no idea where to begin tracking this down, anyone have any ideas?

--------------------------------
UPDATE
--------------------------------

It seems this is an issue with the usb hard drive's auto sleep feature. There seems to be a bug where the OS is unable to detect the sleep mode, then remounts the drive as if its a new device.

I'm still testing this fix, but so far its working.

I've added the hard drive to my fstab with the following line:

UUID=d72adc3c-7eea-43cd-8274-8ec78aefca74  /media/FILE-SERV  ext3  user,suid,errors=continue,dev,exec,relatime  0  0

then to get rid of the compulsive mounting, i edited the following settings in gconf-editor:

/apps/nautilus/preferences/media_automount (uncheck)

Then to prevent the drive from going to sleep, I setup a cron job to touch a file on the drive once a minute.

This is kinda a janky fix because now no other devices will be auto mounted when plugged it, but atlease my samba and nfs shares no longer break every 20 minutes and the drive is in constant use, so i may end up burning it up bypassing the auto sleep feature, but untill this bug is fixed in nautilus or where ever its at, this will have to do.

----------------
ADDITIONAL UPDATE
----------------

Above Fix did not work. Drive still re-automounts.. Im at a loss.. Anyone have any clue?


-----------------
FINAL UPDATE
-----------------

After all my trial and error, i have been unable to prevent jaunty from obsessively compulsively auto mounting and remounting my usb hard disk.. So in a fit of rage, i have torn the usb enclosure open, removed the SATA hard drive inside, smashed the enclosure to pieces with a hammer and installed the hard disk directly into the system. Its amazing how well bashing things with a hammer makes you feel after days of trial and error.

This is the final fix for this issue (atleast for me).  No further errors after USB has been removed from the picture and the hard drive has yet to give me any issues after being installed.

-----------------


BTW.. This is the evil drive in question.. So if you have Jaunty and are getting a new usb drive.. Dont get this one.. because it'll piss you off and you'll end up smashing it anyways.

[IMG]http://images.tigerdirect.com/skuimages/large/H450-8004-Main-JH.jpg[/IMG]

---

### Post by strider22 on 2010-03-31
I have the same problem with a Western Digital ebook. I haven't worried too much about it though so my observations are casual.

I find that the issue is not with the drive going to sleep but with ubuntu going to sleep.
uname -a
Linux *computername* 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

Right now I have 6 "My Book" icons on the desktop. Only 1 works.

When you open up the file browser there are increasing underscores added to the name;
/media/My Book
/media/My Book_
/media/My Book__
etc.
None of the underscored names work.

With regards to Ubuntu and sleep. I configured using the tools to not sleep however when I first reboot, Ubuntu will go to sleep when left alone. After a few wakeups, with no system adjustments at all, Ubuntu will remember and never goes to sleep again. (until the next reboot)

The number of wakeups I need to respond to varies from none to I'd guess about 6. There are clearly some issues with sleep and Ubuntu. It's not like I put in confusing system commands; I used the system/preferences, power monitor and screen saver tools.

I cannot unmount the extra drives as a user.

Going into a shell and umounting My* from /media removes all icons from the desktop.
Mounting does not work as there is no fstab entry.
Unplug/repluging the drive puts one icon on the desktop. In the file browser it has 7 underscores (prob because of the entries in /media)

---

