---
title: "Eye of Gnome theme"
date: 2011-11-02
forum: General Help
---

### Post by Nonno Bassotto on 2011-11-02
I am using Gnome Shell on Ubuntu 11.10 with the default Adwaita theme.

The only thing that is a little annoying is that, unlike other applications, Eye of Gnome (the default photo visualizer) seems to use a dark version of the Adwaita theme that does not blend well.

I was not able to find any relevant option in the DConf editor under org.gnome.eog. Is there a way to make Eye of Gnome use the default light theme?

---

### Post by darthpenguin on 2011-12-06
I second this. I'm running Arch with Gnome 3 and Gnome Shell. Eye of Gnome seems to be useing a dark Adwaita GTK theme. Why?! how can I fix this?

---

### Post by darthpenguin on 2011-12-06
OK. I just found an older version on eog on AUR and installed that. AUR is Arch specific but perhapse you could install eog-2.* on Ubuntu from source.

---

### Post by darthpenguin on 2011-12-06
This also works, acctually it is better because it fixes all apps including Totem. Just remove or rename the *dark.css files in /usr/share/themes/Adwaita/gtk-3.0 like so

---------------------------------------------------------------------
assets                  gtk-widgets-assets-dark.css.backup
gnome-applications.css  gtk-widgets.css
gtk.css                 gtk-widgets-dark-overrides.css.backup
gtk-dark.css.backup     settings.ini
gtk-widgets-assets.css
---------------------------------------------------------------------

this disables the dark themes so apps are forced to use the default Adwaita theme.

---

### Post by Nonno Bassotto on 2011-12-08
Thank you for the tip!

---

