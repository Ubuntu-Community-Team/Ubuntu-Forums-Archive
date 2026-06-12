---
title: "Plz help!!! Windows boot\bcd error"
date: 2010-11-03
forum: General Help
---

### Post by Manifest on 2010-11-03
Ok im gonna go crazy, i know this has absolutely nothing to do with ubuntu so dont start attacking me.
 
Right,Im looking to install windows vista on my computer I have a vista install disk that is scraped fortunatly I copied the contents of the disk to my other computer.
 
I copied the disk files to my pen drive and restarted.
I got ```
file: Boot\Bcd
``` and some other stuff
I checked my pen drive and /boot/bcd exists
 
Sorry for lack of info or anything else.

---

### Post by alphaamanitin on 2010-11-03
Will your computer even boot from a USB?  Personally it looks like you don't have a correctly formatted bootable USB pendrive.  Sorry I can't be more help.

AlphaA

---

### Post by yetiman64 on 2010-11-03
Sounds like you need to extract the Vista boot image file from the dvd, it is not copied when you copy the contents (files and folders) from the dvd to your computer.

This can be done under Windows, or less stably under Wine in Ubuntu, using Isobuster.

See the attached pic of a XP cd with Isobuster. The image is "Microsoft Corporation.img". The name may vary in Vista but the boot image setup is the same principle, IIRC. I only have a cdrom drive available at the moment otherwise I would have demonstrated with a Vista disc (a DVD). Note the XP folder structure (what you likely copied) is above the highlighted "Bootable Disc" section of the cd.

With the files and folders and the boot image a new bootable DVD can be burnt with the appropriate burning software.

Not too sure about usb installers and Vista, but I vaguely recall there is a utility that can create such, however I suspect it is far more involved than just copying the files to a usb stick (remember you're likely to be missing Vistas bootable image file for a start.).

---

### Post by alphaamanitin on 2010-11-03
WintoUSB is supposed to create a install USB from a DVD/CD of Windows.  I only had an ISO (legal) so I used VirtualCloneDrive to create a virtual drive and then used WintoUSB to make a USB that would install Windows 7.

AlphaA

---

### Post by howefield on 2010-11-04
Please find an appropriate windows forum for your windows support, eg

[http://www.sevenforums.com/](http://www.sevenforums.com/)

There are many more.

Thread closed.

---

