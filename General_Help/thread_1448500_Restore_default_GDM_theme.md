---
title: "Restore default GDM theme?"
date: 2010-04-06
forum: General Help
---

### Post by palz2015 on 2010-04-06
I have installed xubuntu-desktop and its dependencies and Xfce runs now on my Ubuntu Karmic system. I do not like the changed GDM theme or the mouse boot logo. How do I reset this?

---

### Post by duanedesign on 2010-04-06
Try gdm setup.

Type in a Terminal (Applications > Accessories > Terminal):

```
sudo gdmsetup
```

You can select 'As Default Session'

---

### Post by palz2015 on 2010-04-06
Umm, I only have this in the gdmsetup:

---

### Post by palz2015 on 2010-04-07
Help Please !

---

### Post by sisco311 on 2010-04-07
You can simply run the theme manager as user gdm:
```
sudo -u gdm dbus-launch gnome-appearance-properties
``` 

Or use this GUI tool:
[thread=1358026]GDM2 Configuration Tool[/thread]

Or 
[thread=1333683]HowTO: Comprehensive Guide to Customising GDM and XSplash[/thread]

For more information and advanced settings read [this]("http://library.gnome.org/admin/gdm/2.28/configuration.html.en").

---

### Post by palz2015 on 2010-04-07
Thank you, but I still have the Xfce icons and logo. Maybe I should restart...

---

