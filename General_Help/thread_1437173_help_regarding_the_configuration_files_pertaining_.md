---
title: "help regarding the configuration files pertaining to wallpaper-tray"
date: 2010-03-23
forum: General Help
---

### Post by rahilm on 2010-03-23
I installed wallpaper-tray and pretty much messed it up in 5 minutes. I enables time change and put 0.1 there just for fun. Next thing I know is that the desktop is changing wallpapers like crazy and almost using all the resources. I can't even click on anything, just see the wallpapers changing.
So , i need to find where the config files are stored so i can alter them manually.
I tried:
find -iname '*tray*'
it showed a folder ~/.gconf/apps/wp_tray
i deleted the contents of the directory but of no use..

---

### Post by Johnny B on 2010-03-23
ctrl-alt-F1
$ sudo rm $(which wallpaper-tray) OR sudo apt-get remove wallpaper-tray
ctrl-alt-F7

---

### Post by rahilm on 2010-03-23
> **Johnny B said:**
> ctrl-alt-F1
$ sudo rm $(which wallpaper-tray) OR sudo apt-get remove wallpaper-tray
ctrl-alt-F7
i think you are not getting me. I don't want to uninstall the wallpaper-tray. I switched to virtual console and killed it. switched back. that's how i wrote this thread. I only want to reset the settings back.

---

### Post by 2hot6ft2 on 2010-03-23
It should be showing an applet in the top panel.
Right click on it and select either Settings or Preferences I forget which.
Change the settings and there you go.

---

### Post by rahilm on 2010-03-23
> **2hot6ft2 said:**
> It should be showing an applet in the top panel.
Right click on it and select either Settings or Preferences I forget which.
Change the settings and there you go.
No. i can't do that since wallpaper-tray uses almost all of my system's memory. If i right-click, it takes many minutes for just the outline of the menu to appear.

Never mind, i figured it out. After I delete the ~/.gconf/apps/wp_tray. i have to logout and login for the changes to take effect.

---

