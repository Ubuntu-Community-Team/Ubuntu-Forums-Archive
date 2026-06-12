---
title: "wireless drivers for wubi"
date: 2011-03-11
forum: General Help
---

### Post by Vladimir Tripp on 2011-03-11
Hi-
I am a total ubuntu novice and not very Computer literate. I dowloaded Ubuntu 10.10 onto CD the other day, after years of being frustrated with Windows, played around with the CD edition without installing, loved it, read up a bit and decided I would like to try Wubi -- that way I don't run the risk of losing any of my Windows stuff when I carve up my hard-drive, but can work with Ubuntu whenever I want.
The trouble is this: Ubuntu 10.10 comes with a wireless driver from Broadcoast (802.11 Linux STA wireless-driver) which works with my HP wireless card.  The Wubi download does not come with this driver and while I managed to download the driver through windows, and then locate it when I am running ubuntu, there is no equivalent of an .exe file that would simply install it. Most of the forum posts on this issue are too technical for me.  Is there a simple way of fixing this problem?
Any help would be much appreciated!
Vladimir

---

### Post by Davaross on 2011-03-11
If you search in the ubuntu software centre for a piece of software called "Windows Wireless Drivers" (NDIS Wrapper with a GUI) it will allow you to install the standard windows drivers for the wifi card in your hp. To install the Windows Wireless Drivers software you will need an ethernet network connection or your ubuntu install cd.

---

### Post by bcbc on 2011-03-11
You can also install it from your install CD if you don't have an available ethernet connection. If you want to use the ndiswrapper you'll need the XP version of the driver (*.inf file).

Either run from command line (change path as appropriate)
sudo dpkg -i /media/cdrom/pool/main/n/ndiswrapper/*.deb
sudo dpkg -i /media/cdrom/pool/main/n/ndisgtk/*.deb

Or browse the CD and install .deb packages one by one. In pool/main/n/ndiswrapper there are two packages and the order is important - I think common, then utils (if it complains just switch)

Then go to System, Administration, Windows Wireless Drivers and point it at your XP driver

---

### Post by Vladimir Tripp on 2011-03-11
Thank you Davaross, but this does not work for some reason.  When I search the Software Center for Windows Wireless Drivers, the program locates a "Source", then asks me to "Authenticate" -- I type in my password, but nothing happens.  Presumably this is so, because I have not internet connection.  The ethernet connection also does not work, I don't know why. I will have a look at bcbc's suggestion now, though it looks a little complicated...  
Thanks for the help in any case!

---

### Post by Vladimir Tripp on 2011-03-11
Hm, I have been digging around for the wireless driver in Windows, and what I find is something called bcmwl6.inf_3c230eb8.  No idea whether this is the XP version (presumably not, I am running Vista) and what the numbers after .inf mean.  
So if I follow your instructions, bcbc, is this where I go afterwards, or should I download a new driver from somewhere -- which presumably will be an exe file -- and then install it in Windows first?
Sorry if this is all a little confused.  It matches my state of mind...
Cheers! Vladimir

---

### Post by bcbc on 2011-03-11
That authenticate issue is a bug, just click on the window X to close. once you run updates it will be fixed.

You need the XP .inf not an exe - and nothing to install on windows

---

### Post by Vladimir Tripp on 2011-03-11
Thanks again.  I am leaving windows to give things another whirl in ubuntu.  All drivers I can find are .exe files, however; maybe I am looking in the wrong sort of place. I am clearly not very good at this.
V.

---

### Post by Vladimir Tripp on 2011-03-12
OK, somewhere along the line while unpacking the .deb files from the CD manually and installing them, Ubuntu recognised the driver...  and that was that.  I am up and running. Thanks again for the help. V.

---

