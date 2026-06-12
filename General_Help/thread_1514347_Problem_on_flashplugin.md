---
title: "Problem on flashplugin"
date: 2010-06-20
forum: General Help
---

### Post by satimis on 2010-06-20
Hi folks,

Ubuntu 10.04 64 bit

I have "flashplugin-nonfree" installed running on this OS


$ apt-cache policy flashplugin-nonfree```

flashplugin-nonfree:
  Installed: 10.1.53.64ubuntu0.10.04.1
  Candidate: 10.1.53.64ubuntu0.10.04.1
  Version table:
     10.1.53.64ubuntu0.10.04.1 0
.....

```


I download "persistence-lesson01.zip" on;
[https://sourceforge.net/projects/eclipsetutorial/files/2.%20Persistence%20Tutorial/](https://sourceforge.net/projects/eclipsetutorial/files/2.%20Persistence%20Tutorial/)

and decompress it.```

lesson01.html
lesson01.swf
ProductionInfo.xml
swfobject.js

```

On clicking "lesson01.html" it asks to "Download Adobe Flash Player".  On completion of installation it popup "adobe-flashplugin is virtual".


I found following link;
adobe-flashplugin is virtual on 64bit Ubuntu 10.04
[http://crimm.me/2010/05/adobe-flashplugin-is-virtual-on-64bit-ubuntu-10-04.html](http://crimm.me/2010/05/adobe-flashplugin-is-virtual-on-64bit-ubuntu-10-04.html)

and ran;
$ sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

and got the package installed.


On clicking "lesson01.html" it asks to "Download Adobe Flash Player" again.  Please help.  TIA


B.R.
satimis

---

### Post by lovinglinux on 2010-06-22
You shouldn't be using the 64bit version of flash, since it has a critical vulnerability and is not supported by Adobe anymore.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by XSAlliN on 2010-06-22
Don't know about Flash-AID since it didn't do any good for me, but the other link is good as in "all in one place"... I did almost the same, but had to dig a little. :)

An here is my conclusion so far (after trying anything - except going to 32 bit):

> Firefox + Flash under Linux = not a very good combination.

On the other hand Chromium works just fine, yet I wouldn't use it for everyday browsing (security related - which is he's weakest point) - I have it installed just for flash streaming or rare situations. Chrome being the spyware browser from Google that is, yet using it for YouTube can't hurt, since it's also part of Google.


... I quoted myself so I don't repeat the same thing over and over again. ):P

---

### Post by satimis on 2010-06-22
Hi folks,

Thanks for your advice.

I solved my problem according to following link;

Install Flash Player 10 on Ubuntu 10.04 64-bit Lucid Lynx
[http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html](http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html)

At end of installation following warning popup```

libflashplayer.so
Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it.

```

I just ignored it.  The link works as a charm.  Problem is now solved.

I did it twice, 
- on the host of VBox
- on a VM

both running Ubuntu 10.04 desktop 64 bit

B.R.
satimis

---

### Post by XSAlliN on 2010-06-23
They fixed some flash problems with FF 3.6.**4**.):P

---

### Post by Linuxforall on 2010-06-23
The flash used by OP is latest x32 version so he is not running the older x64 one. The symlink solved his issue.

---

