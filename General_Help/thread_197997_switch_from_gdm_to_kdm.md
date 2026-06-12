---
title: "switch from gdm to kdm"
date: 2006-06-16
forum: General Help
---

### Post by waldorf on 2006-06-16
How do I switch from using kdm to using gdm?

Thanks in advance

---

### Post by th3james on 2006-06-16
Do you mean that you wish to start using gnome instead of KDE?
if so

sudo apt-get install ubuntu-desktop

---

### Post by bruce89 on 2006-06-16
AFAIK ```
sudo dpkg-reconfigure gdm
``` will do it

---

### Post by maniacmusician on 2006-06-16
I'm not entirely sure, as I'm pretty new to it myself...but when i installed gdm, i first installed it:

sudo apt-get install gdm

then I used this:

sudo /etc/init.d/gdm start

This starts the gdm graphical login screen, and I think it also sets as the default (hopefully). 

hope that works for you.

---

### Post by aysiu on 2006-06-16
[QUOTE=th3james]Do you mean that you wish to start using gnome instead of KDE?
if so

sudo apt-get install ubuntu-desktop[/QUOTE]
Except that you'd really do ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` Otherwise Gnome would be a pain to uninstall later.

But Gnome and GDM are not the same thing.

Assuming you have both GDM and KDM installed but you just want to switch which one you use: ```
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager_backup
sudo nano /etc/X11/default-display-manager
``` Change this line ```
/usr/bin/kdm
``` to this line ```
/usr/sbin/gdm
```

---

### Post by waldorf on 2006-06-16
wow awesome response. Thanks everyone.

btw: i installed kubuntu-desktop and left the manager as gdm but wanted to try kdm. and now I know how!

---

