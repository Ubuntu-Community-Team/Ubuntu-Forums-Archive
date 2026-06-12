---
title: "how do i prevent KDE from taking over gnome login screen?"
date: 2006-04-16
forum: General Help
---

### Post by mandrakethepenguin on 2006-04-16
I want to install KDE on my Breezy x86 machine.  But the last time I tried, KDE took over the gnome-login screen.  How do I prevent this or fix it if it happens?

---

### Post by aysiu on 2006-04-16
Usually when you install KDE, it should ask you whether you want KDM or GDM to be the default. You can then choose GDM to be the default.

If, for some reason, that doesn't happen, you can manually choose which one is the default: ```
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager_backup
sudo gedit /etc/X11/default-display-manager
``` Change it from ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
```

---

### Post by mandrakethepenguin on 2006-04-16
Thanks again aysiu!

---

### Post by az on 2006-04-16
It would be better to reconfigure the package in synaptic or through the command line.  Whether kdm or gdm.  You will get prompted to chose one as default.  It is best to do it that way so that the choice gets to be part of debconf and the package manager knows about it.  

Let the package manager change config files for you so that your don't have all your changes reverted by upgrading one day.

---

### Post by Sutekh on 2006-04-16
Just to further azz's suggestion (which I'd recommend)

To reconfigure the display manager from the command line you would need to use
```
sudo dpkg-reconfigure gdm
```
to use the GNOME display manager, or
```
sudo dpkg-reconifigure kdm
```
to use the K display manager

---

