---
title: "graphical interface problems"
date: 2012-03-24
forum: General Help
---

### Post by Meijuh on 2012-03-24
For a while ago I installed gnome (apt-get install gnome).

Now the graphical interface uses very weird icons etc.

See: [http://postimage.org/image/vinhqqpv9/](http://postimage.org/image/vinhqqpv9/) how for example nautilus looks like.

It seems to me that all (gtk) icons are replaced kde icons. But I could be wrong. 

I guess this all happened when I did a "apt-get autoremove mono-*". Maybe this was stupid, but I am unsure. 

Also when the login screen pops up for lightdm I cannot boot in unity anymore, i.e. it only shows gnome and gnome-classic where previously I could also choose unity etc.

Any ideas how I can get my old system back?

apt-get install --fix-missing has no effect.

---

### Post by clikus on 2012-03-24
To change style of icon you can use [**UbuntuTweak**]("http://ubuntu-tweak.com/"). 
If you want restore Unity and Unity2D just install [**ubuntu-desktop**]("apt://ubuntu-desktop").

---

### Post by Meijuh on 2012-03-24
Simply installing ubuntu-desktop fixed my problems. Thanks.

---

