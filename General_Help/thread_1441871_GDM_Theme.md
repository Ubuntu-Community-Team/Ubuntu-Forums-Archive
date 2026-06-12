---
title: "GDM Theme"
date: 2010-03-29
forum: General Help
---

### Post by f37u5g0d on 2010-03-29
I can't change my GDM theme any more nore will I be able to in the next version of Ubuntu!  I know why (the gnome developers took the feature out in the re-write of GDM).  I have two questions.  Why is GDM so bloated that they can't re-write all of the features?  It also seems to take a lot of resources (more than the others).  My second question.  When, if ever, will I be able to customize my gdm theme again?

---

### Post by sisco311 on 2010-03-29
GDM now uses GTK themes. To change the theme, you can simply run the theme manager as user gdm:
```
sudo -u gdm dbus-launch gnome-appearance-properties
``` 

Or use this GUI tool:
[thread=1358026]GDM2 Configuration Tool[/thread]

Or 
[thread=1333683]HowTO: Comprehensive Guide to Customising GDM and XSplash[/thread]

For more information and advanced settings read [this]("http://library.gnome.org/admin/gdm/2.28/configuration.html.en").

---

