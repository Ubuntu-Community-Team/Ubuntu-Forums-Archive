---
title: "How do I update Empathy on Natty?"
date: 2011-05-16
forum: General Help
---

### Post by xxhopingtearsxx on 2011-05-16
How do I update Empathy on Natty to it's latest version? I've been having trouble to figure it out.. The version that comes on Ubuntu 11.04 doesn't even have an icon that tells me which contacts are on mobile.

---

### Post by xxhopingtearsxx on 2011-05-16
Bamp.

---

### Post by tmette on 2011-05-16
You could try checking the repositories and see if the PPA is listed, not sure if it is or not by default since I don't use Empathy.  I believe this is the PPA:

ppa:telepathy/ppa

---

### Post by xxhopingtearsxx on 2011-05-16
When I installed Empathy 3.1.1, it looked like a program from a previous Ubuntu version.. like it's unaware I'm on Ubuntu 11.04 with Unity..

Is the latest not even available for use on Ubuntu 11.04? Because that's kind of ridiculous.

---

### Post by xxhopingtearsxx on 2011-05-19
bump

---

### Post by nutznboltz on 2011-05-21
Related thread (but no solution)

[http://ubuntuforums.org/showthread.php?t=1719814](http://ubuntuforums.org/showthread.php?t=1719814)

---

### Post by Frogs Hair on 2011-05-21
From what I can find , it looks like the latest version of Empathy uses Gnome 3 and 11.04 uses Gnome 2.xx . It possible to install via PPA if you install Gnome 3 first , but then you would be stuck with Gnome 3 and would not be able to revert to Gnome 2.xx .

---

### Post by nutznboltz on 2011-05-22
Natty comes with Empathy 2.34.

There is a 2.91.* series in git

```
$ git tag | grep 2.91 | tail -2
EMPATHY_2_91_92
EMPATHY_2_91_93

```

and tarball release
[http://ftp.acc.umu.se/pub/GNOME/sources/empathy/2.91/](http://ftp.acc.umu.se/pub/GNOME/sources/empathy/2.91/)

I will see if that is suitable.

---

### Post by nutznboltz on 2011-05-22
No, 2.91 is not suitable.

> NEW in 2.91.0 (04/10/2010)
=============

This is the first release in the new 2.91 development branch.
Empathy now depends on GTK+3 and can't build with GTK+2 anymore.
As a consequence, dependencies linking on GTK+ itself have been bumped to
depend on the GTK+3 version of those libs.


---

