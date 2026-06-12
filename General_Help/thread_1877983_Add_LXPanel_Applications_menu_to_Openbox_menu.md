---
title: "Add LXPanel Applications menu to Openbox menu"
date: 2011-11-09
forum: General Help
---

### Post by mistacool on 2011-11-09
I tried creating the same pipemenu as used in Archbang with

ID: desktop-app-menu
Execute: openbox-menu

This didn't work.

How do I add the Applications Menu from the LXPanel to the Openbox Menu? Thanks.


#Update: Solved by Installing Openbox-xdgmenu via Synaptic

Then with Obmenu I created a new pipemenu with

ID: desktop-app-menu
Execute: openbox-xdgmenu "/etc/xdg/menus/lxde-applications.menu"

---

### Post by Rodney9 on 2011-11-09
To add applications to the menu you can follow this thread - [http://ubuntuforums.org/showthread.php?t=1529870](http://ubuntuforums.org/showthread.php?t=1529870)
on page 2 there are instructions from the wonderful amjjawad.

For How to's Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Rodney

---

### Post by mistacool on 2011-11-09
hi, I know how to add apps to the Openbox menu. What I'm trying to figure out is how to add the lxde-applications.menu to it?

---

### Post by croque on 2011-11-18
Thanks! I was trying to figure out how to do this. Works perfectly.

---

