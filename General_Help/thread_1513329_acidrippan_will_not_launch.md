---
title: "acidrip/pan will not launch"
date: 2010-06-19
forum: General Help
---

### Post by carl801 on 2010-06-19
Having trouble getting both Pan and Acidrip to launch.  Using the dropdown menu Applications>Internet>pan or acidrip, neither application will launch.

When I run them from terminal, I get the following (and a lot more, but this is representative.


** (pan:5777): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed

AcidRip message - No configuration file found, nevermind.
CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed at /usr/share/perl5/AcidRip/interface.pm line 143.

Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-
deprecated at /usr/share/perl5/AcidRip/interface.pm line 175.


If I use sudo pan or sudo acidrip from the terminal, the program seems to work normally, so perhaps I have a permissions problem that I have no clue how to fix.

I'm running Lucid.  Any ideas?

---

### Post by IAmNotAUser on 2010-06-19
From here: [https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/593474](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/593474)

Try removing appmenu-gtk:

```
sudo aptitude remove appmenu-gtk
```

and see if you can now open the program without using sudo :)

---

### Post by carl801 on 2010-06-19
Hey, Thanks!  That did it.  Both programs run as they should

Thanks Again
C

---

