---
title: "How to change the Screensaver idle time via gconf-editor?"
date: 2011-01-11
forum: General Help
---

### Post by Azdour on 2011-01-11
Hi,

I can use the gconf-editor to disable the screen-saver lock and set it to activate when its idle. But no matter what I change  /apps/gnome-screensaver/idle_delay to, the ScreenSaver UI is never updated and stays at the default 5 minutes. There seems to be no link between the slider bar in the ScreenSaver Preferences and the value that lies at /apps/gnome-screensaver/idle_delay...

The reason why I'm doing it through gconf-editor is so a start-up script I have created can use gconftool-2 to alter settings for certain users on login.

Is this broken in Ubunto 10.04 or am I looking in the wrong place. Thanks in advance.

---

### Post by Azdour on 2011-01-11
Ok, after I have done some more digging in gconf-editor seems the /apps/gnome-screensaver/idle_delay is no longer used. Instead you need to use /desktop/gnome/session/idle_delay...

---

