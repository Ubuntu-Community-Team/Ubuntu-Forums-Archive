---
title: "ubuntu-tweak will NOT start"
date: 2011-10-17
forum: General Help
---

### Post by mtguy on 2011-10-17
I have the latest version...I've upgraded it twice today, but it still won't start.  Here's the output from a terminal:
> ERROR:root:Could not find any typelib for Notify
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 34, in <module>
    from ubuntutweak.common.consts import VERSION, IS_INSTALLED, IS_TESTING
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/common/consts.py", line 14, in <module>
    from gi.repository import GLib, Notify
ImportError: cannot import name Notify 			 		

---

### Post by finomeno on 2011-10-18
Same error here. Any tips extremely welcome.

---

### Post by crdlb on 2011-10-18
You need the [gir1.2-notify-0.7](apt:gir1.2-notify-0.7) package. If you installed it from a package, that package is apparently missing a dependency.

---

### Post by Bobhuber on 2011-10-18
+1    Web - Upd8 now has Tweak and all of the tweak extras in there PPA

[http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) oneiric

---

