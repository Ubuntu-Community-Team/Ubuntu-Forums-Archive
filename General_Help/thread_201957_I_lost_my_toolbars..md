---
title: "I lost my toolbars."
date: 2006-06-22
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-22
I lost my toolbars, does anyone know how to get them back?

---

### Post by Ramses de Norre on 2006-06-22
Is gnome-panel running? I guess they are configured somewhere in .gnome2 or .gconf, so I'd search for the config file and delete it to start with the default settings.

---

### Post by johnc4510 on 2006-06-22
Try reinstalling: gnome-panel  in synaptic or 
sudo apt-get install gnome-panel

---

### Post by Ramses de Norre on 2006-06-22
You'll need to use the following in order to make aptitude remove all config files and install fresh ones, just reinstalling keeps the configs like they are```
sudo aptitude purge gnome-panel && sudo aptitude install gnome-panel
```

---

### Post by johnc4510 on 2006-06-22
Okay, that makes since, I also found the run icon for gnome-panel, it is in /usr/bin

---

### Post by mlind on 2006-06-22
if killall gnome-panel doesn't bring your panels back, you may have to let gnome
automatically merge back the default settings. You will lose your current panel settings

```

gconftool-2 --recursive-unset /apps/panel

```

then logout and login

---

### Post by Ulysses on 2006-10-30
Wow

Thought it was weird that I lost all of my toolbars but it seems that I am not alone

I lost the top and bottom toolbars as I was customizing them.
Xubuntu froze on me so I had to unplug my laptop battery and restart (not the smartest thing, but ubuntu and xubuntu tend to freeze up on me). And now I can't get them back.

Does this command line work for xubuntu as well as ubuntu to recover the toolbars?

sudo aptitude purge gnome-panel && sudo aptitude install gnome-panel

Or have I gone and done a bad thing?

Please help. Working with no toolbars is aggravating.

IBM Thinkpad X22
128MB RAM
Pentium 3, 566

---

