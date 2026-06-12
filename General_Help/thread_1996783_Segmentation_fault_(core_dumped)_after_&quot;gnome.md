---
title: "Segmentation fault (core dumped) after &quot;gnome-shell --replace&quot;"
date: 2012-06-04
forum: General Help
---

### Post by erik1001 on 2012-06-04
Hello. After one of the updates I have some serious problems with my graphical environments. I successfully made Unity and Gnome-panel to work, but I still have problem with Gnome3. 
After logging or typing "gnome-shell --replace" in terminal I see my wallpaper or the opened programs, without window border, titlebar or buttons (Metacity isn't working). When I type "gnome-shell --replace" in Gnome terminal, it returns "Segmentation fault (core dumped)". When I type it in Ctrl+Alt+F1 terminal (sorry, I don't know how it's called) it returns me "Window manager error: Unable to open X display".
I've tried complete removing of gnome-* and gnome-shell stuff, also found 
```
sudo apt-get install alacarte cups-pk-helper gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6 gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-applets gnome-applets-data gnome-contacts gnome-icon-theme-full gnome-panel gnome-panel-data gnome-session-fallback gnome-shell gnome-shell-common gnome-themes-standard indicator-applet-complete libcaribou-common libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common libcogl-pango0 libcogl9 libgjs0c libmozjs185-1.0 libmutter0 libpanel-applet-4-0 mutter-common python-gmenuC
```
but the result is still the same - nothing. 
What's the problem? Thanks in advance. :)

---

### Post by cam3roon on 2012-06-06
I have the same problem.

---

### Post by zombifier25 on 2012-06-06
The problem happens in the GNOME Shell session, no?

---

### Post by erik1001 on 2012-06-06
The problem is in Gnome3 Shell, yes. Doesn't matter if I choose Gnome Shell from desktop environments list at login panel or type "gnome-shell --replace" in the terminal after login with different DE (unity/gnome panel).

---

### Post by erik1001 on 2012-06-08
There are even more problems. 
After typing:
```

sudo dpkg-reconfigure -phigh -a

```
The terminal returns:
```

** (accounts-daemon:7108): WARNING **: Failed to acquire org.freedesktop.Accounts

** (accounts-daemon:7108): WARNING **: Could not acquire name
```

---

### Post by erik1001 on 2012-06-10
Anyone help? 
```
user@home-PC:~$ gnome-shell --replace
Window manager error: Unable to open X display
```
I think about formatting Linux and reinstalling it. What do you think?

---

