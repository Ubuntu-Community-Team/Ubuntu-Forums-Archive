---
title: "Why can't i install Adobe Flash Player?"
date: 2009-12-06
forum: General Help
---

### Post by JoeyF on 2009-12-06
Ok, So i just installed 9.10 as the only OS on my computer.

I downloaded the deb, Installed and then restarted Firefox.
I tried Youtube again and it didn't work.

I tried the deb again and it says already installed, Need to reinstall. but then i get an error when i try to do it(Can't remember, Maybe the next error i get)

I tried the deb again and when i open it i get:

 "Could not open install_flash_player_10_linux.deb
The package might be corrupted or you are not allowed to open the file. Check the permissions."

What should i do?

Thanks,

---

### Post by bumanie on 2009-12-06
Try this in terminal > sudo apt-get install flashplugin-installer

---

### Post by JoeyF on 2009-12-06
> **bumanie said:**
> Try this in terminal

I got Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

Thanks,

---

### Post by bumanie on 2009-12-06
May be you don't have the multiverse repository enabled. Go to System --> Administration --> Software Sources and ensure universe and multiverse repositories have a tick next to them. If multiverse did not have a tick, try the command again once you fixed that. If that doesn't work have a look at [this]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html#more-2766").

---

### Post by LuisGMarine on 2009-12-06
Hmmm ... I don't get how you are experiencing problems.  On my 32-bit system all I did was just open up Firefox go to youtube.com and as soon as I loaded the page Firefox asked me to install the missing plugin and Ubuntu did the rest.  

As for my 64-bit system all I did was just run a script.  What version are you using, and just installing it from Firefox.  I can't say I've run into any problems when doing that on my or my friends computers.  

Cheers!:KS

---

### Post by aysiu on 2009-12-06
So go to the Adobe website and redownload the .deb and double-click it.

---

