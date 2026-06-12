---
title: "Bluepath and ganycontrol"
date: 2009-07-23
forum: General Help
---

### Post by jossaq on 2009-07-23
Hi there

I'm trying to use my bluetooth cell phone to control presentations etc. I downloaded bluepad and ganycontrol. Actually I'm using Jaunty - Gnome

But I wasn't able to install them.
The reason: They depend in some packages I'm not able to install.

Bluepad: python2.4-gtk2 I have python-gtk2
gAnyControl: bluez-dev.... Didn't find it.

Any help

What can I do to install them? ... al teast one.


Thanks a lot

---

### Post by dox_drum on 2009-12-31
> **jossaq said:**
> Hi there

I'm trying to use my bluetooth cell phone to control presentations etc. I downloaded bluepad and ganycontrol. Actually I'm using Jaunty - Gnome

But I wasn't able to install them.
The reason: They depend in some packages I'm not able to install.

Bluepad: python2.4-gtk2 I have python-gtk2
gAnyControl: bluez-dev.... Didn't find it.

Any help

What can I do to install them? ... al teast one.


Thanks a lot

Hi Joosaq,
   I used bluepad in Jaunty and it works just fine. Try installing the following.
```
sudo apt-get install python2.6-gtk2 python2.6-glade2 python-bluez python-notify
```

By the way, after installing Karmic it doesn't work anymore. Does anyone knows why?

Bye

---

