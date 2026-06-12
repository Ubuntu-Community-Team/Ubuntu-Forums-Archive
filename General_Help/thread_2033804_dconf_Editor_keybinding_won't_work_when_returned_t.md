---
title: "dconf Editor keybinding won't work when returned to default"
date: 2012-07-27
forum: General Help
---

### Post by Ralph L on 2012-07-27
I am installing 12.04 Precise.  I have installed gnome-panel and am running Classic (no effects).  I want to change the keybinding for "panel cycling".  I installed dconf-tools and went to dconf Editor>org>gnome>desktop>wm>keybindings and set cycle-panels to ['<Super>Right'].  Whereas cycle-panel worked fine originally, it didn't work with the change I made.  I don't know why.  So I changed it back to the default setting by  clicking on "Set to default" at the bottom of window.  The problem is that it still doesn't work even when set back to the orginal default value..  It seems that the act of changing it and then changing it back to default somehow breaks it.

I uninstalled dconf-tools and reinstalled it.  This didn't help.  There must be a configuration file for dconf someplace that doesn't get removed, when dconf-tools is uninstalled.

Can anybody explain what is going on and how I can fix it?  I'd like to make a number of other keybinding changes, but I am afraid of breaking more of the current keybindings.

Thanks in advance.

---

