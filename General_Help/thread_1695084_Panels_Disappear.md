---
title: "Panels Disappear"
date: 2011-02-25
forum: General Help
---

### Post by SuperFreak on 2011-02-25
I have a problem where my top and bottom panels sometimes disappear. Last night I had terminal open and   that disappeared  and the panels disappeared. I have used a program called Panel Restore to return the panels although I am not able to reinstall a saved version of the panels only the default panel arrangement. Last night when terminal disappeared the Panel Restore would not work at all.
I have 10.10 64 bit on a dual boot with XP.

---

### Post by dino99 on 2011-02-25
either:

gnome-panel --replace &
compiz --replace &

depend on what is installed

---

### Post by SuperFreak on 2011-02-25
Thanks for your quick reply. I have attached two screenshots from Synaptic Package Man. that seem to indicate compiz is not installed but gnome panel is. Should I install compiz; is that the problem?

---

### Post by dino99 on 2011-02-25
> **SuperFreak said:**
> Thanks for your quick reply. I have attached two screenshots from Synaptic Package Man. that seem to indicate compiz is not installed but gnome panel is. Should I install compiz; is that the problem?

but compiz is already installed (compiz-core)

so, into a terminal:

compiz --replace &

You can clean the system too, use : gtkorphan, gconf-cleaner, bleachbit

sudo dpkg --configure -a

---

### Post by SuperFreak on 2011-02-25
$ compiz --replace &
results in :

[1] 6196
david@@@@@@@:~$ libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

terminal does not seem to go back to prompt

---

### Post by SuperFreak on 2011-02-26
bump

---

