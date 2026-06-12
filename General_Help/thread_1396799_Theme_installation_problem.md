---
title: "Theme installation problem"
date: 2010-02-02
forum: General Help
---

### Post by arnab_das on 2010-02-02
Just wanted to ask u guys something. havent really faced this prob in a long time (since jaunty), whenever i try and install themes, the appearance editor tells me "XYZ does not appear to be a valid theme". for example, i tried to install this perfectly normal looking theme here: 

[http://gnome-look.org/content/show.php/Crisp+Clear+Morning?content=48994](http://gnome-look.org/content/show.php/Crisp+Clear+Morning?content=48994)

and i got the error. if u can, could u try checking if this theme is working for u (its just a few kbs)?

thanks.

---

### Post by Psumi on 2010-02-02
karmic doesn't install GDM themes the same way as metacity/icon/mouse themes. In fact, there is no GDM Configurator in the default ubuntu install to change the theme.

That theme is also for GDM1 I believe.

GDM2 uses GTK.

---

### Post by arnab_das on 2010-02-02
> **Psumi said:**
> karmic doesn't install GDM themes the same way as metacity/icon/mouse themes. In fact, there is no GDM Configurator in the default ubuntu install to change the theme.

That theme is also for GDM1 I believe.

GDM2 uses GTK.

ah thanks. looking at the GTK 1 and GTK 2 sections of gnome-look now. :)

---

### Post by Psumi on 2010-02-02
> **arnab_das said:**
> ah thanks. looking at the GTK 1 and GTK 2 sections of gnome-look now. :)

You'll need to google search on how to configure GDM2 as well, the "Login Screen" application no longer changes the login screen theme/background/mouse/icons.

jaunty however should still be using GDM1. To install that theme on GDM1, you need to do so from the login screen application in administration or whatever.

---

