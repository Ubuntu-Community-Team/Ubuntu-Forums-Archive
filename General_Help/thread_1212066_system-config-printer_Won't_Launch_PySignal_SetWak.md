---
title: "system-config-printer Won't Launch: PySignal_SetWakeupFd"
date: 2009-07-13
forum: General Help
---

### Post by dannyman on 2009-07-13
Hello,

I would like to add a new printer to my computer.  Alas, whenever I select System > Administration > Printing nothing happens.

So, I ask the command-line:

```
0-07:52 dannhowa@T60p ~$ **system-config-printer**
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 32, in <module>
    import gtk.glade
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.5/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.5/gtk-2.0/glib/_glib.so: undefined symbol: PySignal_SetWakeupFd
1-07:53 dannhowa@T60p ~$ **sudo system-config-printer**
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 32, in <module>
    import gtk.glade
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.5/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.5/gtk-2.0/glib/_glib.so: undefined symbol: PySignal_SetWakeupFd
1-07:53 dannhowa@T60p ~$ **cat /etc/lsb-release** 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
0-07:53 dannhowa@T60p ~$ **uname -a**
Linux T60p 2.6.27-14-generic #1 SMP Tue Jun 30 19:54:46 UTC 2009 x86_64 GNU/Linux
```

So . . . how can I fix that? :)  Thanks!

Sincerely,
-daniel

---

### Post by dannyman on 2009-07-14
A work-around.

Visit: [http://localhost:631/](http://localhost:631/)

I was able to add a printer via that interface.

---

### Post by dannyman on 2009-07-16
Solution: [http://ubuntuforums.org/showpost.php?p=5784157&postcount=21](http://ubuntuforums.org/showpost.php?p=5784157&postcount=21)

0-11:42 dannhowa@T60p ~$ cd /usr/local/bin
0-11:42 dannhowa@T60p bin$ sudo mv python python-broken

Now things work.

What a crappy bug.

---

