---
title: "Sessions-&gt;Startup Programs config file"
date: 2006-03-13
forum: General Help
---

### Post by Darkriser on 2006-03-13
The question is very simple. When I add new entries in System->Preferences->Sessions->Startup Programs, where these changes are stored?
Or in other words, what cfg file do I have to edit directly, to avoid clicking the path mentioned above? (just to explain - i'm pretty new to linux and would like to UNDERSTAND how it works, i don't want just to "click" on icons without knowing what's going on)

Thanx a lot.
Marcel

---

### Post by 5-HT on 2006-03-13
I believe the user config file is ~/.gnome2/session.

The syntax is not really intuitive though...
While I admire your desire to understand the underpinnings of the system, in this case it would probably save time to just do it from the GUI.

XFCE and KDE (and maybe some WMs) have a nice way in which   ~/Desktop/Autostart is sourced for executables to run on boot, but AFAIK gnome currently does not have that ability or it wasn't deemed important to have (it's a breeze to do it via GUI, so maybe that's why?).

HTH

---

### Post by benevolent on 2007-08-27
from the GUI doesn't work, i do not know why...

where can i find the config file so i can (1) make autostart desklets and (2) stop beagle??? :)

---

### Post by kellemes on 2007-08-27
> **Darkriser said:**
> The question is very simple. When I add new entries in System->Preferences->Sessions->Startup Programs, where these changes are stored?
Or in other words, what cfg file do I have to edit directly, to avoid clicking the path mentioned above? (just to explain - i'm pretty new to linux and would like to UNDERSTAND how it works, i don't want just to "click" on icons without knowing what's going on)

Thanx a lot.
Marcel

I see what you mean..
For folks like you (and me) there are other distro's I guess..
Try ArchLinux, Zenwalk or Gentoo or something, even Debian gives you a little more insight into the system. Trust me, you'll have much fun setting up these system, and you'll learn a lot doing it.

---

