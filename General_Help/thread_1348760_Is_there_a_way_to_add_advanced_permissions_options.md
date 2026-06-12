---
title: "Is there a way to add advanced permissions options to Nautilus' Gui?"
date: 2009-12-07
forum: General Help
---

### Post by Roasted on 2009-12-07
Since I've been playing around with KDE, one thing I like is Dolphin has the ability to set the GID of the directory. Yes I know I can do this in terminal, but it's nice having that option in the GUI.

Although I've been pretending I haven't been noticing it, KDE seems more sluggish on my computers than Gnome, so I may be playing with Gnome more as time goes on. But I was curious - I really like those GUI options to set the GID for the folder right there in Dolphin.

Is there a way I can do that in Nautilus? Perhaps an extra package to install that allows Nautilus to have more advanced permissions options like Dolphin has built in?

---

### Post by t0p on 2009-12-07
If you hit **Alt+F2** and type into the box that appears

```
gksudo nautilus
```

that will give you a Nautilus window with admin privileges.

---

### Post by bluelamp999 on 2009-12-07
Or see here to add 'Open as administrator...' to Nautilus context menu - [http://www.watchingthenet.com/ubuntu-tips-for-windows-users-add-open-as-administrator-to-nautilus-right-click-menu.html](http://www.watchingthenet.com/ubuntu-tips-for-windows-users-add-open-as-administrator-to-nautilus-right-click-menu.html)

---

### Post by t0p on 2009-12-07
You can also install the package **nautilus-gksu** which will add an option *Open as administrator* to your right-click options.

**EDIT:** oop, thats what bluelamp999's link is about.

---

### Post by Roasted on 2009-12-08
I'm not asking about opening nautilus as root. I know about that.

Dolphin has MORE options for permission adjustments than Nautilus does. I'm curious if you can possibly add them to the menu with Nautilus and avoid having a few extra commands to run in terminal.

---

### Post by Jive Turkey on 2009-12-08
The 3rd party package ubuntu-tweak exposes an option to make that available I think.  I have it and these are the options I have in the screenshot below

---

### Post by ankspo71 on 2009-12-08
Hi,
I'm using gnome's configuration editor to get the permissions like the picture shown above.  Press Alt + F2, type in gconf-editor, then when the editor opens up, navigate to Apps > Nautilus > Preferences > then enable "show advanced permissions". 
James

---

### Post by Roasted on 2009-12-08
> **Jive Turkey said:**
> The 3rd party package ubuntu-tweak exposes an option to make that available I think.  I have it and these are the options I have in the screenshot below

Yeah - that's exactly what I'm looking for. Although most of my machines are KDE now I'd still like to be aware of what's out there in case I'm ever on Gnome again. Do you recall what package that was that you added?

Also - Do you guys think Thunar (Xubuntu) would have this option? I tried Xubuntu the other night and if I ever need a gui-oriented server I may run Xubuntu before Ubuntu, so it'd be nice to know on all platforms how to do this. Thanks!

---

