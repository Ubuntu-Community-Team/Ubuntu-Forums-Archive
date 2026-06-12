---
title: "Both Windows managers are running at the same time"
date: 2010-02-02
forum: General Help
---

### Post by leveliv on 2010-02-02
I recently installed KDE, by using kubuntu-desktop and I set my default wm to kdm thinking it would be all fine I logged in and I noticed that my gnome panels were underneath my KDE panels. 

How can I get rid of this, I don't really want to uninstall gnome cause I like all the programs that it uses.

---

### Post by howefield on 2010-02-03
Are you running any gnome applications (deliberately I mean, not the obvious panels ect) ?

---

### Post by leveliv on 2010-02-03
no I can't say that I am, actually now that I think of it Gnome-Do starts up everytime I turn it on, 

But now that I am using KDE how do I get to my start up programs? just to check to see if anything else is running

---

### Post by howefield on 2010-02-04
I have yet to use KDE for more than an hour or so, can't quite decide whether I like it or not. But as far as I know, there should be a startup folder in /home with icons of the programs that start up at boot, eg.

```
/home/username.kde/Autostart
```

The alternative might be to load gnome and see if you can stop gnome-do from loading. Obviously, if this isn't the problem, and you want to use it from KDE, you can reverse anything you do.

---

### Post by rocket16 on 2010-02-04
> **leveliv said:**
> no I can't say that I am, actually now that I think of it Gnome-Do starts up everytime I turn it on, 

But now that I am using KDE how do I get to my start up programs? just to check to see if anything else is running

Hi! One of my friends too does use KDE and GNOME both. You can set up an extra Account for using KDE. Then, you won't even require to select KDE or GNOME everytime from the Login Sreen.

---

### Post by mcduck on 2010-02-04
If you really tried to set KDMa s your window manager, there's the problem. It's not a window manager. :D

KDM is desktop manager, a program that handles your login process, selecting the desktop environment you want to use and language etc. It doesn't manage your windows.. So you could use KDM as replacement for Gnome's desktop amanger, GDM, but definitely you can't use it as your window manager... :D

(KDE's window manager is KWin.)

---

