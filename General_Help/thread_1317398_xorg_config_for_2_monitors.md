---
title: "xorg config for 2 monitors"
date: 2009-11-06
forum: General Help
---

### Post by buckley310 on 2009-11-06
could anybody send me an xorg.conf file for a machine with 2 monitors? im setting mine up and one of my monitors reports that it can only show 1280x960 even though it can display 1280x1024. i would like to manually exit the config file but it is missing in 9.10

---

### Post by cowcow1212 on 2009-11-06
You would have to edit xorg.conf, but I am pretty sure that this new version does not use xorg.conf to determine any settings. I am almost sure of this.

I have edited the file myself, multiple times with a manual configuration (after reading "man xorg.conf") and it did not change any of my results. Your results may vary though. If you can access your desktop view, you can change it from:

"Preferences->Advanced View->Displays" There you can change what the resolution is and what is viewed on what screen, like a mirror (which it sounds like you want) or otherwise).

---

