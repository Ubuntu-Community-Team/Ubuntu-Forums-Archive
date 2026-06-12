---
title: "Problem installing SimCity under wine/10.10"
date: 2010-10-27
forum: General Help
---

### Post by lonewolf454 on 2010-10-27
I have clean install of Ubuntu 10.10 and set up wine beta release.  I have tried to install SimCity (Win95 ver) under wine, there is no setup.exe on cd though, there is only bootme.exe which doesn't seem to install simcity.  I did this from terminal and drag the icon to the terminal after adding sudo wine (and space). 

Any ideas?

---

### Post by 3Miro on 2010-10-27
NEVER USE SUDO WINE! [-X

Have you checked the winehq database:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10343](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10343), there are other entries as well I believe.

I am not sure why there is no "setup.exe" file on the disk. It is possible that it is not mounted correctly. Checkout the Starcraft II and WoW installation instructions on how to mount a "special" disk. This may help only if a setup.exe file appears in windows?

---

### Post by lonewolf454 on 2010-10-28
Well, seems bootme.exe is a floppy boot disc maker for the -DOS- based game.  I know that I used to play this on Win95 and I dont recall making a boot disc, but anyway mystery solved.  Guess WINE wont work on this one.  I did find an open source version Micropolis so I'll try it instead for now.

---

