---
title: "External hardware automounts on Gnome session but not on XFCE session"
date: 2006-05-27
forum: General Help
---

### Post by harisund on 2006-05-27
So I have both Gnome and XFCE  ( {ubuntu-xubuntu}-desktop )installed and working fine. 

For some reason, when I plug in a external USB drive, Gnome mounts it and shows an icon on the desktop. But when in XFCE I get nothing.
 
dmesg shows it is recognized, and the command line can still be used to mount the drive. But why not automatically?

---

### Post by psychicdragon on 2006-05-28
The version of Xfce in breezy doesn't support desktop icons or automount. You can add gnome-volume-manager to your Xfce session for automount support.

---

### Post by Sutekh on 2006-05-28
Try installing the [gnome-volume-manager]("http://packages.ubuntu.com/breezy/gnome/gnome-volume-manager")
```

sudo apt-get install gnome-volume-manager
``` This handles automounting in GNOME.  

Or [ivman]("http://packages.ubuntu.com/breezy/utils/ivman") (less GNOME dependancies)
```
sudo apt-get install ivman
```

---

### Post by harisund on 2006-05-28
Oh interesting. What does it mean when you say 'Ubuntu's version' ?

Also, if I add gnome-volume-manager, there still will be no desktop right? Does it mean I have to run 

nautilus --no-default-window --sm-client-id default2

To show the desktop?

---

### Post by psychicdragon on 2006-05-28
It doesn't really matter what arguments you pass to nautilus. It takes over the desktop by default unless you tell it not to.

The current development version of Xfce 4.3, which will become 4.4 when it's stable, has a new file manager that can do automount and desktop icons. Xfce 4.3 is in Ubuntu Dapper right now.

---

### Post by Sutekh on 2006-05-28
[quote=psychicdragon]
The current development version of Xfce 4.3, which will become 4.4 when it's stable, has a new file manager that can do automount and desktop icons. Xfce 4.3 is in Ubuntu Dapper right now.[/quote]
Which does a nice job of it too, if I might add.  Xubuntu Dapper is really tops.

---

