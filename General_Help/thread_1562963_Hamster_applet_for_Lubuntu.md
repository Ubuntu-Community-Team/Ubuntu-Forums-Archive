---
title: "Hamster applet for Lubuntu"
date: 2010-08-27
forum: General Help
---

### Post by ryu kun on 2010-08-27
> **firmit said:**
> Hmm - Xfce does not run gnome panel applets per se. Xfce has its own volume-manager etc. However, the System Tray lets you display the gnome-network-applet among other thins, and the update-notifier. 

LXDE may also show this - but not by default - however this is NOT the panel's fault. Every .desktop item have a listing called: OnlyShowIn=GNOME;XFCE;

Simply add LXDE to the list, and restart X. 
Example;
cp /etc/xdg/autostart/update-notifier.desktop  ~/.config/autostart

And add LXDE to OnlyShowIn:
```
[Desktop Entry]
Encoding=UTF-8
Name=Update Notifier
Comment=Update notification daemon
Icon=update-notifier
Exec=update-notifier
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;
X-Ubuntu-Gettext-Domain=update-notifier

```

Ctrl-Alt-Backspace - login and you'll see :)

I am trying to add "[hamster-applet]("http://projecthamster.wordpress.com/")" for gnome-panel to LXPanel 0.5.5 (I use Lubuntu 10.04). 

I made a search for .desktop files under /usb directory but only found a .desktop file under /usr/share/applications. Its name is hamster-standalone.desktop. Its content is as follows:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name=Time Tracker
GenericName=Time Tracker
Comment=Project Hamster desktop time tracking
Icon=hamster-applet
Exec=/usr/bin/gnome-time-tracker
Categories=GNOME;GTK;Utility;
X-Ubuntu-Gettext-Domain=hamster-applet
```

I have made the change you suggested but still I could not add it to LXPanel. Could you please give me more specific help?

---

### Post by Iowan on 2010-08-28
Moved to a new thread in support section.

---

