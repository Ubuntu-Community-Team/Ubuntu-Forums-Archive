---
title: "How to make a bootable Windows7 usb drive from Ubuntu"
date: 2010-07-03
forum: General Help
---

### Post by iulianpojar on 2010-07-03
How to make a bootable Windows7 usb drive from Ubuntu?
I have a netbook, so there is no dvdrom drive, and need to reinstall on it Windows 7  how to make a bootable usb drive  with windows 7 if i have Windows 7 ISO on my computer with Ubuntu.

---

### Post by MooPi on 2010-07-03
All the documentation I've seen so far points to needing a DVD drive to create the usb install. If you had a full desktop with Ubuntu you could try setting it up in a virtualbox Windows install. Your best and easiest route is with a Windows install using Microsofts tool for creating a usb drive.[http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars]("http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars")
If you have a friend or access to a Windows system this would be your best situation.

---

### Post by bumanie on 2010-07-03
I think win 7 has the ability to install itself to a usb pendrive, but it will not (without mucking about a lot) install to a usb hard drive. Hmm...just found a [link]("http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/") for you to follow. Not sure that it can be done form ubuntu - think you need to use win 7 and as it seems you don't have it installed that makes things difficult.

---

### Post by C.S.Cameron on 2010-07-03
See post #7:
[http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb](http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb)

---

### Post by bumanie on 2010-07-03
Well done C.S.Cameron finding that and congrats to amedec who has a method that works from within ubuntu. Must try it sometime.

---

### Post by Mark Phelps on 2010-07-03
I'm not sure what you're asking for ... but you do realize that creates a USB from which to INSTALL Win7, not from which to RUN Win7 ... right?  There is no way to create a USB from which to RUN Win7 -- because it will deactivate itself as soon as it determines the hardware is different from that under which it was originally installed.

Besides which, what really gets loaded to the USB and what really runs is WinPE, not Win7.  That is a minimal MS Windows environment that can be used to INSTALL MS Windows, boot a command line, and do other limited stuff.  It is NOT a running version of Windows 7.

---

