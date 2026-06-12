---
title: "how do I show cpu applet and volume - fluxbox"
date: 2009-07-17
forum: General Help
---

### Post by maestrobwh1 on 2009-07-17
I have an eee-pc 701.  I sometimes like to use fluxbox rather than gnome because it is somewhat faster on this machine, and I have added network manager, and a few other things to the startup file in /.fluxbox so that they show up in the tray in fluxbox.

Gnome is also completely installed - 

what command do I add in the same file to have the volume applet to show in the tray?  It isn't gmix (like kmix in kde)

is it possible to get the cpu applet to show up or am I limited to using cpufreq from the terminal to regulate this?

---

### Post by stanca on 2009-07-27
```
gnome-volume-manager &
```
in the startup file,I think.:popcorn:

---

### Post by maestrobwh1 on 2009-07-28
There is no command in jaunty.  I can launch "gnome-volume-control" but this brings up the mixer panel (so I just added it to the fluxbox menu instead).  I know for the network manager, the command is "nm-applet," as I checked the startup files.

---

### Post by kerry_s on 2009-07-28
in fluxbox, i believe most of us used keyboard shortcuts.
you can also use dock apps in the slit, there are lots of them in the repo.

wmix, wmmixer, etc... ?

---

### Post by maestrobwh1 on 2009-07-28
Cool, i will try those out.

---

