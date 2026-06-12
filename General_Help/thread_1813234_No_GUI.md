---
title: "No GUI"
date: 2011-07-27
forum: General Help
---

### Post by carlson.lance on 2011-07-27
I tried to install some drivers for a graphics card (Nvidea) and when i reinstalled it was a just my background. I found out how to install a terminal shortcut and installed gnome3. then i decided i wanted the ubuntu classic and was in the middle of the purge to uninstall gnome3 and the computer was turned off. now i have a terminal and thats it, it will not boot to anything but that. i have tried to restart the purge, but it will not let me. 
whenever i try to install unity i get "unable to fetch some archives, maybe run apt-get update or try with --fix-missing"
if i try with fix missing it says 
unable to correct missing packages E: aborting install"
i decided to try "sudo apt-get install ubuntu desktop" and it just says broken packages.

---

### Post by magical2hobo on 2011-07-27
I would try typing in the command "startx" to get xserver going and that should give you a better idea of what exactly if broken. But in the meantime you could try to install the kubuntu or xubuntu desktops just so you can have some sort of gui and if that works then you know that the issue is in the gnome files themselves and can just purge and reinstall them from your temporary gui.

---

### Post by carlson.lance on 2011-07-27
i didnt think about other desktops like those two. i am fairly new to this, and have learned as many commands and things as one can learn in a few hours a day for 3 days. i will give those a shot and see if that works. thank you a lot.

---

### Post by seawolf167 on 2011-07-27
So you started with Unity, then installed Gnome3, then decided you didn't want it and tried to install Gnome2 after the computer was shutdown in the middle of a purge of Gnome3?

Sorry to say it, but Gnome3 on Ubuntu is experimental and any site showing you the PPAs to use to install Gnome3 should have big red letters saying something to effect that it is experimental and will break Unity, possibly your install and is not down-gradable at the moment.

You'll need to do a fresh install.

---

