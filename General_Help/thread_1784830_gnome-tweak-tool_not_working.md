---
title: "gnome-tweak-tool not working"
date: 2011-06-17
forum: General Help
---

### Post by BSpider on 2011-06-17
Hi guys 

I have ubuntu 11.04 installed with gnome3. Some days ago (after a regular update) I notice some applications not running. Here is an example of the error message:
```
~$ gnome-tweak-tool 
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 21, in <module>
    gi.require_version("Gtk", "3.0")
AttributeError: 'module' object has no attribute 'require_version'
```

I think it's a python problem but I don't know how to fix it :(
Please help.

Thanks

---

### Post by BSpider on 2011-06-18
Found that it works after removing gedit it works :confused:

---

