---
title: "gnome-display-properties / amdcccle - 9.04"
date: 2009-07-08
forum: General Help
---

### Post by resorb on 2009-07-08
OS: Linux/Ubuntu 9.04
Libglade: 2.6.1

After a recent upgrade of my ubuntu system, I lost my dual screen ability. The AMD/ATI Catalyst Control system no longer recognizes multi-display as an option and the gnome-display-properties command will not load. My system becomes sluggish and the secondary monitor (which defaulted to "Clone") begins to flicker as if something is trying to render, but can't, so dies horribly (but too quick to read or even see).

Running the command in a terminal session gives me this:

kxpx@corsair:~$ gnome-display-properties 

(gnome-display-properties:4376): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:4376): libglade-WARNING **: could not find a parent that handles internal children for `vbox'

The "Display Preferences" window is created, but no buttons or text appear. Simply a gray box with a cyan rectangle in the middle, however, the window is non-responsive to the close dialogue.

I've attempted to recreate the libglade-WARNING running the 'amdcccle' command but it renders perfectly, it simply will not let me enable multi-display.

---

### Post by ajgreeny on 2009-07-08
Did your recent upgrade include a new kernel?  Or are you perhaps talking of a distro upgrade?  If it was just an update not a distro upgrade it is possible you need to reinstall the graphics driver.

If it was a distro upgrade, I'm afraid I will be no help at all to you; sorry.

---

### Post by resorb on 2009-07-08
Sorry for the terminology mixup, it was an automatic software update. It would be the kind that you do via "System -> Administration -> Update Manager".

I'm not sure where this logs to so I'm not sure exactly what was upgraded - I hadn't upgraded in apprx. 3 weeks due to being on vacation and away from my PC. It did require a reboot.

---

