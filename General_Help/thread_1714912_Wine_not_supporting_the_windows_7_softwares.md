---
title: "Wine not supporting the windows 7 softwares?"
date: 2011-03-26
forum: General Help
---

### Post by suresh_vandiyur on 2011-03-26
Hi All,

I am using ubuntu 10.10 i need to install windows 7 software in ubuntu 10.10 via wine. but wine supports only windows XP or how to upgrade the wine supports with the windows 7 softwares. please help me.

Thanks in advance.

---

### Post by hawthornso23 on 2011-03-26
Perhaps you should try the latest version of wine. 

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by spirit.986 on 2011-03-26
I've tried wine to install several programs like photoshop, notepad++, worms armagedon etc.. but I am not satisfied 

Judging from my experience it is better to install a virtual machine with windows in it (winxp should do fine) and run win programs from there (i work with Photoshop from time to time) then to install them with wine and then get nervous and frustrated because *"half of the buttons aren't working and everything is glichy and sometimes the program freezes and etc etc.."*

>  but wine supports only windows XP or how to upgrade the wine supports with the windows 7 softwares. please help me.
If you like to use windows softwares on linux perhaps it is better to work on windows as well.. you can consider dual booting windows/linuxs or like me install a virtual machine with xp on it.
**[Here is a good info]("http://ubuntuguide.net/installi-windows-xp-inside-ubuntu-using-virtualbox")** on how to install windowsxp inside ubuntu using **[Virtual Box]("https://help.ubuntu.com/community/VirtualBox")**.. 
The guide is made on an older version of ubuntu but it still works..

And last there is always an alternative and for almost 90% of all windows software there is an equivalent, more of it, IT IS FREE!
**[Table of equivalent software]("http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software")**

---

### Post by ronnielsen1 on 2011-03-26
What are you trying to run? If you're actually trying to run Windows 7 - use VirtualBox. If it's software designed for windows 7 - check winehq to see if anyone has tried to run it and offered pointers.
Also, I agree with hawthornso23, add the ppa to your sources list and wine will automatically update

[http://appdb.winehq.org/](http://appdb.winehq.org/)

[http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html](http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html)

---

### Post by Spyderkid on 2011-03-26
to use windows 7 apps on wine you need to go to Applications > Wine > Configure Wine

then scroll on the box that says windows version, and select windows 7 then click add application and the application you want to add.

---

### Post by rgb1701 on 2011-03-26
I didn't think there were apps that *required* Win7 yet.  The app probably supports XP, which you could run in VirtualBox as others suggested.

If the app gets a Gold or Platinum rating at the Wine Appdb, I would run it in Wine, v 1.2.x or 1.3.x, depedning on what Wine version is recommended for the app in the appdb reviews.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by dazman19 on 2011-03-26
why are you installing notepad++ for windows. 
There is a version for linux you can run natively. Go to their website. Alternatively just use gedit, you can download language packs for it.

Photoshop is in the wine appdb list & so is worms. There are guides in the appdb that help you with current problems. When you get specific errors you can post them here and people can assist.

I quite like GIMP, i am not an expert multimedia type person, but GIMP is usually sufficient replacement for photoshop.

---

### Post by spirit.986 on 2011-03-26
> **dazman19 said:**
> why are you installing notepad++ for windows. 
There is a version for linux you can run natively. Go to their website. Alternatively just use gedit, you can download language packs for it.

Photoshop is in the wine appdb list & so is worms. There are guides in the appdb that help you with current problems. When you get specific errors you can post them here and people can assist.

I quite like GIMP, i am not an expert multimedia type person, but GIMP is usually sufficient replacement for photoshop.

Well that was in the days when i started to use ubuntu.. now i use gPHPedit and CodeLite.. i also use Gimp but sometimes although rarely I need to use Photoshop for it's advanced filters and options.. There are linux software equivalents for almost every windows application so there is no need of them

thank you for reminding me to remove wine :D

---

