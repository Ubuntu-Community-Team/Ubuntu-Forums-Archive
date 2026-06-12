---
title: "Wacom Mouse"
date: 2011-12-26
forum: General Help
---

### Post by Duffasaurus on 2011-12-26
I just installed the most recent version of Ubuntu, and am very new to all of this. (last time I used Ubuntu was in 2007 for my slow computer, but I got a new computer and switched back to windows.) The settings for tracking seem to only work for the pen, and I need relative tracking for my mouse, when it seems to be stuck on absolute. I found out that this is a normal issue on this thread:
[http://ubuntuforums.org/showthread.php?t=1844541](http://ubuntuforums.org/showthread.php?t=1844541)

and the guy said he fixed it by "setting org/gnome/settings-daemon/peripherals/wacom/cursor/is-absolute to false in dconf-editor"

but I have no idea what this means. Any help would be appreciated.

---

### Post by Favux on 2011-12-26
Hi Duffasaurus,

Since I don't think dconf-editor is installed by default so you have to install it.  Then enter *dconf-editor* in a terminal and the gui will pop up.  Then follow the path given to the key values you want to change.  The Wacom tablet applet in System Settings is brand new with Oneiric's Gnome 3.2 and still doesn't have all of the gnome-setteings-daemon's Wacom key values accessible through it.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)  From:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by Duffasaurus on 2011-12-26
> **Favux said:**
> Hi Duffasaurus,

Since I don't think dconf-editor is installed by default so you have to install it.  Then enter *dconf-editor* in a terminal and the gui will pop up.  Then follow the path given to the key values you want to change.  The Wacom tablet applet in System Settings is brand new with Oneiric's Gnome 3.2 and still doesn't have all of the gnome-setteings-daemon's Wacom key values accessible through it.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)  From:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)Thank you so much, it works perfectly now

---

