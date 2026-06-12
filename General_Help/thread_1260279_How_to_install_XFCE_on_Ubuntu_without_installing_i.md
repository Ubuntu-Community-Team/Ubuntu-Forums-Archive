---
title: "How to install XFCE on Ubuntu without installing it's default set of apps ?"
date: 2009-09-07
forum: General Help
---

### Post by credobyte on 2009-09-07
Ok, here's what I need - Ubuntu with all it's Gnome applications, but, XFCE desktop environment. I mean, I still need my gedit, and all the other basic stuff from Gnome & installing them on Xubuntu would be .. time consuming.

Is there a way to install XFCE desktop environment without installing mousepad, abiword, etc. ?

---

### Post by Brandon Williams on 2009-09-07
```
sudo aptitude -R install xubuntu-desktop
```

That command line will install the xubuntu-desktop, but without automatically installing all of recommended packages (like abiword and mousepad). I recommend going this route (rather than trying to install the absolute minimum XFCE environment) because you'll get a desktop that's better integrated with ubuntu.

---

### Post by budhajeewa on 2010-09-07
Thanks, this helped!

---

