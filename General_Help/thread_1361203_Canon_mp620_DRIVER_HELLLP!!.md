---
title: "Canon mp620 DRIVER HELLLP!!"
date: 2009-12-21
forum: General Help
---

### Post by Cmills619 on 2009-12-21
DUDE I'm new to linux... well not that new...BUT I DIGRESS...

I'm trying to install my MP620 canon printer and the drivers aren't automaticly found, so i instaled a PPD I found that covers the gambit of canon printers and when it installed it said it needed a "program" called "pstocanonij" .... anywho unfortunately I can find the packages I need in Synaptic or when I use "apt-get"... and since I'm so darn new to Linux I'm at a loss of where ealse I can find this stuff... HELP PLEASE:confused:

---

### Post by Cmills619 on 2009-12-23
NVM.... I found the solution myself.... here is how I did it...
 
you can get most of the files you need from theis link from ubuntu [https://help.ubuntu.com/community/HardwareSupportComponentsPrintersCanonPrintersCanonMP620#Connecting](https://help.ubuntu.com/community/HardwareSupportComponentsPrintersCanonPrintersCanonMP620#Connecting) via USB cable
 
And get the Dummy file for libcupsys2 here : [http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)
 
 
1.make sure your printer is disconnected
2.install the dummy file
3.install [FONT=Courier New]cnijfilter-common_2.80-1_i386.deb[/FONT]
4.install [FONT=Courier New]cnijfilter-mp610series_2.80-1_i386.deb[/FONT]
5.Read the Readme that comes with the PPD archive and disperse the files as it says...
6.plug in your printer turn it on and watch it work
 
Karmic comes with the new version of cups... unfortunately the driver still points to the out dated cubs libraries the truble I was having was due to the lack of CANON telling you of this fact (why mention your own faults)... THANK YOU UBUNTU for making it easy to fix (only 4 hours of reading and clickity clacking):guitar:

---

### Post by Mega_Mike on 2011-03-18
I weeded out all that complicated dependency garbage and came up with a simple clean install method:

[http://ubuntuforums.org/showthread.php?p=10575009#post10575009](http://ubuntuforums.org/showthread.php?p=10575009#post10575009)

---

