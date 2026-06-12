---
title: "xubuntu 9.10 and no networking? really... common."
date: 2010-01-09
forum: General Help
---

### Post by rmausser on 2010-01-09
So I cant figure out how to access folders on my Xubuntu 9.10 laptop from a desktop with Ubuntu 9.10 on it.

Ubuntu setup was a cinch. 

Xubuntu... no networking GUI to be found.

Its the year 2010. Really? no networking native in Xubuntu. 

Give me a break. I think that was possible in, erm, Windows 95?

---

### Post by Brandon Williams on 2010-01-10
There's a bug in the desktop file that provides the network connection editor menu entry. It says Xfce where it should say XFCE. Run these commands in a terminal to get the necessary menu entry to appear:
```
[ ! -d ~/.local/share/applications ] && mkdir -p ~/.local/share/applications
sed 's/^OnlyShowIn=.*$/OnlyShowIn=GNOME;XFCE;/' /usr/share/applications/nm-connection-editor.desktop \
          > ~/.local/share/applications/nm-connection-editor.desktop
```

There should be an icon in your system tray for networking. You should also be able to open nm-connection-editor by right clicking on that icon and selecting 'Edit Connetions ...'.

Is there anything specific that you're trying to do that can't be done from that dialog?

---

