---
title: "Open Office 3.2??"
date: 2010-04-12
forum: General Help
---

### Post by oleink on 2010-04-12
Hey i recently installed the deb packages of openoffice 3.2 but for some reason when my openoffice loads it says 3.1  It opens to 3.2 interface though.  Any idea why this is hapenning??

---

### Post by fragos on 2010-04-12
I upgraded to 3.2 by adding a PPA repository and didn't see that problem. Perhaps there a deb specific to Gnome that you missed when you downloaded the debs.

---

### Post by claracc on 2010-04-13
I think you have to install openoffice 3.2 in the way adviced by this thread [http://ubuntuforums.org/showthread.php?t=1404156&highlight=openoffice](http://ubuntuforums.org/showthread.php?t=1404156&highlight=openoffice) (there are various ways to install or update from 3.1).

Regrads

---

### Post by oleink on 2010-04-13
Thats what i did. download the files remove 3.1. unpackage the debs and then install via terminal.

---

### Post by oleink on 2010-04-13
im trying ppa repositories to get upgrade.  That appears to be working!

---

### Post by oleink on 2010-04-13
that worked as far as i can tell:popcorn:


I'll get back to you on it

---

### Post by scouser73 on 2010-04-13
Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the **Linux .deb** file.

**1** - Once you have done that, extract the .deb file, 

> **OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz** 

Then you'll see a file called OOO320_m12_native_packed-1_en-US.9483

**2** - You can remove the existing version of OpenOffice if you wish with this command: 

> **sudo apt-get remove openoffice*.***

**3** - Copy and paste OOO320_m12_native_packed-1_en-US.9483 onto the desktop then open Terminal and paste this command: 

> **sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb**

**4** - Then paste this command: 

> **sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb**

Once you've done that you'll find OpenOffice 3.2 in Office.

---

### Post by oleink on 2010-04-13
> **scouser73 said:**
> Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the **Linux .deb** file.

**1** - Once you have done that, extract the .deb file, 



Then you'll see a file called OOO320_m12_native_packed-1_en-US.9483

**2** - You can remove the existing version of OpenOffice if you wish with this command: 



**3** - Copy and paste OOO320_m12_native_packed-1_en-US.9483 onto the desktop then open Terminal and paste this command: 



**4** - Then paste this command: 



Once you've done that you'll find OpenOffice 3.2 in Office.

Thats what i did at first and it still loaded as 3.1  I just added to ppa and it worked great.  THANKS GUYS!

---

### Post by gatorbrit on 2010-04-13
Just used the PPA and it works.   Finally a document in created in word that changed from landscape to portrait through out and has loads of tables opens beautifully in OO3.2.   Brilliant!!!

---

