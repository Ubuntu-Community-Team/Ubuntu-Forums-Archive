---
title: "X keyboard - wrong layout"
date: 2010-03-13
forum: General Help
---

### Post by Intrepid Ibex on 2010-03-13
I need to do: > setxkbmap fi every time I want my Finnish keyboard layout in X.

What's the config to have it changed otherwise?

---

### Post by Intrepid Ibex on 2010-03-16
bump

---

### Post by leorolla on 2010-03-16
For Gnome desktop, you need to go to System->Preferences->Keyboard

For KDE, there is a central configuration center

---

### Post by slakkie on 2010-03-16
Dunno if the package is only in Debian, but try this:

sudo dpkg-reconfigure keyboard-configuration

(if you don't have the package install, try installing it first).

Bummer, package is only in Debian.

---

### Post by Intrepid Ibex on 2010-03-19
Well the problem is that I don't want KDEmod to set my kbmap because it takes more resources than just having a .desktop file for "setxkbmap fi" in ~/.config/autostart.

Seccondly I use Arch, not Ubuntu or Debian :).

But I might've fixed this. I'll report later today whether it worked.

---

### Post by Intrepid Ibex on 2010-03-24
Okay, well evdev probably doesn't have the "XkbLayout" option, only the kbd driver does :p.

---

### Post by Intrepid Ibex on 2010-03-24
Oh well, I just put the part in ~/.xinitrc:
> setxkbmap fi

---

