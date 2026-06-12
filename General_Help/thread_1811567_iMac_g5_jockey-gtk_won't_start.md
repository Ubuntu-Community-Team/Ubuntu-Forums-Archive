---
title: "iMac g5 jockey-gtk won't start"
date: 2011-07-25
forum: General Help
---

### Post by fundash on 2011-07-25
Hello!

I installed the ppc version of ubuntu 10.10 on my moms iMac g5 and cannot open additional drivers aka jockey-gtk.  I simply see the "searching for additional drivers" window appear for just a sec, than nothing else.

in terminal I get a list of stuff i'm assuming are errors.  So far none of the other solutions on the forum have worked that have solved it for other people.
here is what it gives me when I try to run in terminal:
```
leslie@leslie-desktop:~$ jockey-gtk
Exception in thread thread_call_progress_dialog:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 484, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Python.IOError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 173, in detect
    self.hardware = detection.get_hardware()
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 850, in get_hardware
    result = _get_modaliases()
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 592, in _get_modaliases
    modalias = open(os.path.join(path, 'modalias')).read().strip()
IOError: [Errno 19] No such device


Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 420, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 448, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 101, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 277, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 793, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 212, in available
    return self.handlers.keys()
AttributeError: 'Backend' object has no attribute 'handlers'

leslie@leslie-desktop:~$ 

```

---

### Post by fundash on 2011-07-25
bump I really need help with this!

---

### Post by fundash on 2011-07-25
Seriously? nobody yet? someone has to know how to fix this...

---

### Post by schoelje on 2012-08-10
It's been reported here:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/946973](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/946973)

I'm sorry to say that there is no solution or workaround available yet.

---

