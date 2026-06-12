---
title: "xsession-errors: Multiple calls to startxfce4 and xfce4-panel"
date: 2010-06-08
forum: General Help
---

### Post by eev2 on 2010-06-08
Hi all. I get the following messages while starting up. This also delays my desktop initialisation.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
xfce4-panel-Message: Xfce4-panel already running
xfdesktop[1815]: starting up
xfce4-panel-Message: Xfce4-panel already running
xfce4-panel-Message: Xfce4-panel already running
xfce4-panel-Message: Xfce4-panel already running
xfce4-panel-Message: Xfce4-panel already running
xfce4-panel-Message: Xfce4-panel already running
```

If I run in terminal [FONT="Courier New"]tail -f .xsession-errors[/FONT] while my system initialises, I see these messages appearing every 5 sec. Any ideas where to look? Thanks in advance.

---

### Post by Brandon Williams on 2010-06-09
Do you have a custom init file in $HOME/.config/xfce4/xinitrc? If so, what are the differences between it and the one in /etc/xdg/xfce4/xinitrc?

If you don't have a custom xinitrc file, then you might want to reinitialize your config. Log out from the GUI session and log in to a console session. Then do:
```
mv .cache .cache.bkup
mv .config .config.bkup
```
Now log out of the console session and log in to a GUI session. You will have to reset all the configuration settings that you want, but it should clear up this specific problem.

Note that '/usr/bin/startxfce4: X server already running on display :0' is to be expected when you log in via a graphical desktop manager.

---

### Post by eev2 on 2010-06-09
Hi Brandon. Thanks for your reply. You are right, there was something with my configuration. Thanks a lot.

---

