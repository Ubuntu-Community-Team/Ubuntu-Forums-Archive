---
title: "Login/GNOME problem"
date: 2011-08-05
forum: General Help
---

### Post by Messyhair42 on 2011-08-05
Yesterday after a restart (firefox would freeze on certain webpages, not the problem i'm asking about) I got a different login screen, a very basic GNOME login that won't let me log in; put in my password, get sent back to the very same place.
something very similar to this has happened repeatedly in the past and it usually fixes itself or i use a usb installation to clear out /tmp after the fact. only this time at the login screen I get a HUD notification "The configuration defaults for GNOME power manager have not been installed correctly." any ideas on how to fix it?

---

### Post by Messyhair42 on 2011-08-05
I have considered a reinstall, while bumping my /tmp to about 10GB. I have backup across three drives, so if it isn't resolved soon I just may. but considering the past I have no reason to believe it won't be resolved

---

### Post by Messyhair42 on 2011-08-07
bump
I have been unable to fix the problem. using ```
dkpg-reconfigure gnome-desktop
```
only told me /sbin/gnome-desktop does not exist
I'm about to do a reinstall, and i have /, /tmp, /home, /usr, and /var as separate logical partitons. i'd like to only overwrite / and /tmp but i've never done anything but a clean installation, any known issues with only rewriting the core OS files?

---

