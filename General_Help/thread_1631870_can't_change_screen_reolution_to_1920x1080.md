---
title: "can't change screen reolution to 1920x1080"
date: 2010-11-27
forum: General Help
---

### Post by iShurtugal on 2010-11-27
I got a TV I'm using as a monitor, and it has support for 1080p (1920x1080 resolution), but I can't change it to that. I've tried using the graphical monitor preferences and adding to to xrandr manually and trying to change it, but it doesn't work.

The computer I'm using has a (crappy) intel g31 graphics chipset, could this be why?  I looked it up and it says it should support it.  It also says that it needs a special fix/driver because they had problems, but I can't/don't know how to get the driver on ubuntu.

---

### Post by dandnsmith on 2010-11-27
Have a look at [this page](http://intellinuxgraphics.org/documentation.html) which says the driver for g31/g33 chipset is G33, and offers mor documentation, tips ...

I haven't tried this, but lsmod in a terminal window (as root) might show which driver is currently in use - sounds like it could be a default (like *vesa*).

---

