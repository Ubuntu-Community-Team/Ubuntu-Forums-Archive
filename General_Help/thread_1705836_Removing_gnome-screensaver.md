---
title: "Removing gnome-screensaver"
date: 2011-03-12
forum: General Help
---

### Post by vaskark on 2011-03-12
The Gnome Screensaver preferences window is freezing my desktop. I went into synaptic and tried to remove it (to use xscreensaver instead). But synaptic, in removing gnome-screensaver package, wanted to ADD a bunch of packages, lots of KDE stuff (which I don't want). Is there any way around this? If not, is there a way to reset the gnome-screensaver config file (whatever it is) so that it doesn't freeze on startup? This problem arose after I selected a particular screensaver in the gui window.

Thanks. Hope I explained myself clearly.

---

### Post by stinkeye on 2011-03-12
In the terminal
```
gconftool-2 --unset /apps/gnome-screensaver/themes
```
will set your screensaver theme back to blank screen.

---

### Post by vaskark on 2011-03-12
Many thanks :)

---

### Post by Krytarik on 2011-03-13
See the first step of this guide on how to replace gnome-screensaver:
[http://ubuntuforums.org/showthread.php?t=1358946](http://ubuntuforums.org/showthread.php?t=1358946)
Maybe you are missing some additional xscreenserver packages. I also have xscreensaver installed (parallelly), and when I select gnome-screensaver for removal, Synaptic doesn't select other packages for installation.

---

