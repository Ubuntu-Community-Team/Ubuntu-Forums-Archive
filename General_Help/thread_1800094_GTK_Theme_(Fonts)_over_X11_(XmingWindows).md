---
title: "GTK Theme (Fonts) over X11 (Xming/Windows)"
date: 2011-07-08
forum: General Help
---

### Post by h41cyon on 2011-07-08
I've got an Natty box running an ssh server that I connect to from Windows running a combination of Putty/Xming.  If I launch anything that uses X11 window forwarding, I'm greeted with a pretty ugly basic GTK theme.

The one solution I've found to this, is to first open "gnome-appearance-properties" first.  Just opening this application and closing it again, seems to 'set' the GTK windowing and font theme for that Xming connection, so following windows have that silky smooth Ubuntu look and feel.

Question is, is there a better way to do this other than launching "gnome-appearance-properties" each time I start up xming?

I also found I could do this via launching lxappearance.

Thanks!

---

### Post by h41cyon on 2011-07-18
bump^

---

### Post by daanmidd on 2011-09-22
Create a new file in your home directory: .gtkrc2.0

With: 
gtk-theme-name = "Ambiance"

---

### Post by kriegaex on 2012-03-04
Same setup here (Xming, all X windows of remote Ubuntu box displayed on Windows box).

I tried on Ubuntu Oneiric 11.10, creating *~/.gtkrc-2.0* (not the hyphen in the file name) via LXAppearance. The weird thing is that it affects apps like my editor (SciTE), but is ignored by gnome-terminal-3 and Synaptic. Is this a problem of the old GTK version number, but Ubuntu using Gnome 3 now? Sorry, I am experienced at the console, but not with GUI.

---

