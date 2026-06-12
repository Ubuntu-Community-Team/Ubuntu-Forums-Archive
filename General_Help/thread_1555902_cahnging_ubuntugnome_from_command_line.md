---
title: "cahnging ubuntu/gnome from command line"
date: 2010-08-18
forum: General Help
---

### Post by gforster on 2010-08-18
I would like to make all of the computers in our lab look/behave the same. I have messed around with some of gconftool-2 to change the desktop backgrounds, but I can't figure out the following:

[LIST]
[*]deleting the bottom panel
[*]adding the window list to the top panel
[*]adding the force-quite applet to the top panel
[*]removing all menu items from the system/preferences menu but sound
[*]removing all menu items from the system/administration menu but printing and system monitor
[/LIST]

Again, this needs to be done from the command line so I can put it all into one script.  All help is appreciated.

---

### Post by silverglade00 on 2010-08-18
The default user profile settings are in /etc/skel. I think you might want to load up the sabayon package on one of the systems and get it the way you want then copy /etc/skel to the others.

---

