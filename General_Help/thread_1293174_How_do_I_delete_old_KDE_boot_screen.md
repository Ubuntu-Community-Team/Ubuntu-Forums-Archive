---
title: "How do I delete old KDE boot screen?"
date: 2009-10-16
forum: General Help
---

### Post by YumaJim on 2009-10-16
In the past I had both KDE and Gnome desktop managers on my laptop. I removed KDE some time ago as I finally settled on Gnome. Now when the machine boots I still see the old Kde screen that says "Kubuntu" and has a status line under the "Kubuntu". Next the screen gos black with the cursor "circle" and then the normal Gnome login screen appears.

My question is, how do I remove the first old KDE screen from appearing during the boot process.

thanks,
YumaJim

---

### Post by wojox on 2009-10-16
Type:

```
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu.so /etc/alternatives/usplash-artwork.so
```

---

### Post by YumaJim on 2009-10-20
I tried the ln code but I have the very same boot sequence as before.
The same old Kubuntu screen is still there.

YumaJim

---

### Post by mocoloco on 2009-10-20
Sounds like you're booting to KDM instead of GMD, which are the respective login screens (display managers) for KDE and Gnome.  I would recommend just using [this handy guide]("http://psychocats.net/ubuntu/puregnome") to removing all the KDE stuff.  Note the version at the top of the page and make sure it's your same Ubuntu version.

---

### Post by P4man on 2009-10-20
```
sudo dpkg-reconfigure usplash-theme-ubuntu
```

---

### Post by YumaJim on 2009-10-21
Fixed - I installed 'startup-manager' and it's usage fixed my problem.
It as some additional features such as cleaning up, deleting, old kernals and removing same from the grub menue.lst.

Thanks for all the help.
YumaJim :P

---

