---
title: "Is WINE included with 9.10?"
date: 2009-11-05
forum: General Help
---

### Post by wavery on 2009-11-05
I'm brand new to Ubuntu and just installed 9.10 on an old computer.  I understand Wine is a Windows emulater.  I went to the Wine website to download and the first thing it says to do is unload old versions, and that Wine is typically packaged with Ubuntu.  I've looked at the menus and don't see it, but I don't see an easy way to confirm that it's not included otherwise.   So, is Wine included with 9.10?  Thank you.

---

### Post by Aearenda on 2009-11-05
It's not installed by default. You can add it using the Ubuntu Software Centre among other ways, but the version on Wine's website will be newer (and perhaps less stable). Installing Wine is easy, installing Windows programs with it less so - are you sure you need it?

---

### Post by sexyclient on 2009-11-05
You misunderstand: Wine Is Not an Emulator (W.I.N.E.)

But you can install it by going to the main menu in "Applications" > "Ubuntu Software Center" > and then searching for "wine".  Double-click that, then hit "install."  I don't recall whether it is installed by default or not, but it's quite simple to get it once you've got ubuntu 9.10.  You don't need to go to the wine website.

---

### Post by PaulInBHC on 2009-11-05
Go to Applications> Ubuntu Software Center> type wine into the search window. There will be two Wine choices, 1.0.1 stable and 1.1.31 beta. 
Since you are new to Ubuntu, be aware that Wine is not the be all end all to running Windows programs in linux. I've tried a few games and had poor results. If you want office apps, Open Office is much better than MS Office, IMO, and can export files into common types.

---

### Post by wavery on 2009-11-05
Ya, I know it's not technically a Windows emulator, and yes I do need it.  There is one program I know I want to have installed that needs Wine to run.  I did a little homework before installing and learned that the program should run fine with Wine.  Fingers crossed.  Any recommendations on the stable version vs. beta?  Thanks.

---

### Post by berman56 on 2009-11-05
WINE is not installed by default.  The easiest way is to install from the "Ubuntu Software Center."  First, go to Edit - Software Sources - Other Software - Check the box next to [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic parter - and then click close.  Your repositories will update.  

Then, you can search WINE in the Ubuntu Software Center.  This will install that latest stable release.  If for some reason you want to experiment with the development version, you can download in the synaptic package manager or through the instructions at:  [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by wildweathel on 2009-11-05
Well, since you know what app you want to run, look in the appdb [http://appdb.winehq.org/](http://appdb.winehq.org/) and see what people say it does on different versions.  You might have to try them both.  Good luck.

---

