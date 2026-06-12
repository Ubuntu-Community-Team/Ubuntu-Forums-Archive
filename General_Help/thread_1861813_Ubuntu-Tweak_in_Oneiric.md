---
title: "Ubuntu-Tweak in Oneiric"
date: 2011-10-16
forum: General Help
---

### Post by Shibblet on 2011-10-16
After I loaded Natty, I downloaded Ubuntu-Tweak, which was a great way to make some little adjustments to the Unity interface.  Namely making windows pop up "centered" and moving the "close, minimize, and maximize" buttons to the right hand side of windows.  

But, Ubuntu-Tweak isn't out for Oneric.  Is there anyway to accomplish these tasks without screwing up Compiz?

---

### Post by JRV on 2011-10-16
You can download the latest ubuntu-tweak version for oneiric.

```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

It is not very functional yet.

---

### Post by mtguy on 2011-10-17
Upgraded to oneiric and installed latest Ubuntu-tweak.  It won't start.  Here's the output from terminal:

> ERROR:root:Could not find any typelib for Notify
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 34, in <module>
    from ubuntutweak.common.consts import VERSION, IS_INSTALLED, IS_TESTING
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/common/consts.py", line 14, in <module>
    from gi.repository import GLib, Notify
ImportError: cannot import name Notify

---

### Post by JRV on 2011-10-18
The code above worked to install it for me.  (32 bit)

---

