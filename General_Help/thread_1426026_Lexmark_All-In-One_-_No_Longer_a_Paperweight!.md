---
title: "Lexmark All-In-One - No Longer a Paperweight!"
date: 2010-03-09
forum: General Help
---

### Post by larrys4227 on 2010-03-09
Linux/Ubuntu users have been frustrated in getting their Lexmark All-In-One printers to work .... basically turning them into paperweights.  Well, as of 3-4-2010 .... dust them off, and load the drivers!

[http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523](http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523)

I havent seen this posted anywhere on these forums .... did a search on Lexmark, and nothing came up.

Check the remarks for the driver .... only good for a series of Lexmark All-In-Ones ... and only certain versions of Ubuntu.

I have 9.10, and was frustrated with having to boot to Windows to print something.  As of 5 minutes ago, and even less install time ... I now have a fully functioning printer!  My printer is the x3650 and it prints great!

I DL'd the deb file, extracted it to my desktop. You then have to run the extracted file from a ROOT console.  Do this right from your desktop, and a GUI will pop up.  Follow the simple directions, and drivers are installed!  Thats it ... all I had to do.  Took longer to write this than it did to install.

Thanks Lexmark!  You made me a real happy camper!

Larry

---

### Post by Bradj47 on 2010-03-09
> **larrys4227 said:**
> Linux/Ubuntu users have been frustrated in getting their Lexmark All-In-One printers to work .... basically turning them into paperweights.  Well, as of 3-4-2010 .... dust them off, and load the drivers!

[http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523](http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523)

I havent seen this posted anywhere on these forums .... did a search on Lexmark, and nothing came up.

Check the remarks for the driver .... only good for a series of Lexmark All-In-Ones ... and only certain versions of Ubuntu.

I have 9.10, and was frustrated with having to boot to Windows to print something.  As of 5 minutes ago, and even less install time ... I now have a fully functioning printer!  My printer is the x3650 and it prints great!

I DL'd the deb file, extracted it to my desktop. You then have to run the extracted file from a ROOT console.  Do this right from your desktop, and a GUI will pop up.  Follow the simple directions, and drivers are installed!  Thats it ... all I had to do.  Took longer to write this than it did to install.

Thanks Lexmark!  You made me a real happy camper!

Larry

You probably should have put a [SOLVED] prefix in front of the title of this post and put it on this board: [http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

---

### Post by zman36 on 2010-03-14
Thanks Larry! This driver worked very well. We had to use the sudo commands, but all is great now with my Lexmark X3650 printer.

Have a wonderful night.

Roger

---

### Post by davepimp00 on 2010-06-11
> **larrys4227 said:**
> Linux/Ubuntu users have been frustrated in getting their Lexmark All-In-One printers to work .... basically turning them into paperweights.  Well, as of 3-4-2010 .... dust them off, and load the drivers!

[http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523](http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523)

I havent seen this posted anywhere on these forums .... did a search on Lexmark, and nothing came up.

Check the remarks for the driver .... only good for a series of Lexmark All-In-Ones ... and only certain versions of Ubuntu.

I have 9.10, and was frustrated with having to boot to Windows to print something.  As of 5 minutes ago, and even less install time ... I now have a fully functioning printer!  My printer is the x3650 and it prints great!

I DL'd the deb file, extracted it to my desktop. You then have to run the extracted file from a ROOT console.  Do this right from your desktop, and a GUI will pop up.  Follow the simple directions, and drivers are installed!  Thats it ... all I had to do.  Took longer to write this than it did to install.

Thanks Lexmark!  You made me a real happy camper!

Larry

yeah but how are you using the scanner that comes with the X3650??  is that not possible?

---

### Post by nrabett on 2010-11-23
The scanner works without problems. Install Xsane from U Software Center, open it, press "scan" on the X3650, and press the "scan" button in Xsane.

---

### Post by wbar2 on 2010-11-23
Simple-Scan should be able to be used as well.

---

### Post by nickpj on 2010-12-02
No success with the Lexmark x3650 on Ubuntu 10.10 on amd64.

During installation, it said this in the GUI installation log:
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz9234/pkg/files/dpkg_msgs

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
=============================

Also in the console, it had some GTK warnings:
=============================
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
Gtk-Message: Failed to load module "gnomesegvhandler": /usr/lib/gtk-2.0/modules/libgnomesegvhandler.so: wrong ELF class: ELFCLASS64

(gtk:10692): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(gtk:10692): Gtk-WARNING **: Loading IM context type 'ibus' failed

(gtk:10692): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
=============================

Then after installation, I could not get anything to print. Attempting to "Print Test" page from the printer's properties gave me an error, and no printer output.

Also it would not recognise the printer in either Xsane or in Simple-scan. Scanning was the main thing I wanted to do.

Things I might have done wrong:
* wrong architecture (amd64 not i386) [Geez I wish drivers would be made available for both architectures]
* wrong distro release (10.10 not 9.10)
* I plugged in the USB cable before realising that there was even a driver issue, and finding this page through google. I removed the cable then, and only inserted it when prompted by the GUI during installation.

Any suggestions on how to get the printer & scanner to work from this point?

---

### Post by psychok7 on 2011-06-17
> **nickpj said:**
> No success with the Lexmark x3650 on Ubuntu 10.10 on amd64.

During installation, it said this in the GUI installation log:
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz9234/pkg/files/dpkg_msgs

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
=============================

Also in the console, it had some GTK warnings:
=============================
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
Gtk-Message: Failed to load module "gnomesegvhandler": /usr/lib/gtk-2.0/modules/libgnomesegvhandler.so: wrong ELF class: ELFCLASS64

(gtk:10692): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(gtk:10692): Gtk-WARNING **: Loading IM context type 'ibus' failed

(gtk:10692): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
=============================

Then after installation, I could not get anything to print. Attempting to "Print Test" page from the printer's properties gave me an error, and no printer output.

Also it would not recognise the printer in either Xsane or in Simple-scan. Scanning was the main thing I wanted to do.

Things I might have done wrong:
* wrong architecture (amd64 not i386) [Geez I wish drivers would be made available for both architectures]
* wrong distro release (10.10 not 9.10)
* I plugged in the USB cable before realising that there was even a driver issue, and finding this page through google. I removed the cable then, and only inserted it when prompted by the GUI during installation.

Any suggestions on how to get the printer & scanner to work from this point?

is it working already for x64 on ubuntu 11.04? got any cheap printers that you know that will definitely work?

---

### Post by Frankiebond on 2011-09-07
"You then have to run the extracted file from a ROOT console.  Do this right from your desktop, and a GUI will pop up."

How do I do this? I am new with linux and I don't know how to open the file using root can you tell me how? please and thank you.

---

### Post by RevNomad on 2011-10-05
Anxiously awaiting an answer as I have encountered the same problem. The Lexmark software is not recognizing my password. The password is correct, btw.

---

### Post by larrys4227 on 2012-09-24
Been almost 2 years since I started this thread .... have been happy with my Lexmark and 10.04.  (For some reason, I missed the [SOLVED] part ... I check in quite frequently .... apologies.)

With my interest to once again update my PC, my Lexmark x3650 no longer works with 12.04 .... any version.  Mint, PinguyOS, or UbuntuUNITY all wont run my printer.

Sigh ... I can deal with this by using my wifes laptop that WON'T be upgraded from 10.04, but if converts from windows are to stay with any form of linux, then printing has gotta work without hassle

---

### Post by kurt18947 on 2012-09-25
You know Lexmark is getting out of the inkjet printer business?  

[http://www.zdnet.com/lexmark-to-exit-inkjet-printers-cut-1700-jobs-7000003303/](http://www.zdnet.com/lexmark-to-exit-inkjet-printers-cut-1700-jobs-7000003303/)

There are nice choices for printing under linux.  HP is commonly recommended, I've had quite good luck with Brother multi-functions.

---

### Post by larrys4227 on 2012-09-25
Thanks for the link. I cant say its been a bad printer, but I always thought cartridges were overpriced.  Multiple times I've noticed HP/Brother as the choice for Linux.

Thanks again ....:p

---

### Post by kurt18947 on 2012-09-26
> **larrys4227 said:**
> Thanks for the link. I cant say its been a bad printer, but I always thought cartridges were overpriced.  Multiple times I've noticed HP/Brother as the choice for Linux.

Thanks again ....:p

Over priced cartridges are a common affliction.  We have a perfectly functioning HP Deskjet. 1 new black & 1 new color cartridge were $70.  A new Brother MFC-430W with wireless networking was $69 and will take refillable ink cartridges.

---

