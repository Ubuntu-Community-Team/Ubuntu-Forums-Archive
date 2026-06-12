---
title: "Update manager not working"
date: 2010-04-11
forum: General Help
---

### Post by blairm on 2010-04-11
Hi,

I'm unable to run the update manager; when I try to start it through system-admin-update manager nothing happens. When I try from the terminal I get the following:


```
blairm@medusa:~$ update-manager

(process:15133): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 107, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 119, in __init__
    logging.exception("setlocale failed")
NameError: global name 'logging' is not defined
```

Is anyone else having this issue? And any idea how I can fix it?

Cheers,

Blair

---

