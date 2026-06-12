---
title: "Change mouse properties for KDE apps in Ubuntu?"
date: 2009-09-13
forum: General Help
---

### Post by mmcmonster on 2009-09-13
I'm running Ubuntu 9.04, and use a few KDE apps.  In particular, I'm using Digikam.

The default mouse settings on KDE apparently have single click opening an item, instead of selecting it (which is default in Gnome apps).

On previous versions of Ubuntu, I could install kcontrol and change the default action for single click on KDE apps.

What is the equivalent in Ubuntu 9.04 and above?  I assume it changed with the coming of KDE4?

---

### Post by mmcmonster on 2009-09-21
Bump!

Basically, I just want single click to select a image in Digikam, instead of opening it.  How can I do this on Ubuntu?

---

### Post by mmcmonster on 2009-09-24
Bump!

Surely there must be away to change mouse properties for KDE apps in Ubuntu?

---

### Post by mmcmonster on 2009-10-08
Solved:

```

gedit ~/.kde/share/config/kdeglobals

``````

[KDE]
SingleClick=false

```

---

