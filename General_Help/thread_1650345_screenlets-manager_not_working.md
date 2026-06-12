---
title: "screenlets-manager not working"
date: 2010-12-21
forum: General Help
---

### Post by karthick87 on 2010-12-21
Screenlets-manager is not working in ubuntu 10.10,These are the outputs when i run it from terminal,

```
karthick@linux:~$ screenlets-manager
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 28, in <module>
    import screenlets
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 51, in <module>
    from options import *
  File "/usr/lib/pymodules/python2.6/screenlets/options.py", line 30, in <module>
    import utils
  File "/usr/lib/pymodules/python2.6/screenlets/utils.py", line 16, in <module>
    import dbus
  File "/usr/lib/pymodules/python2.6/dbus/__init__.py", line 100, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/pymodules/python2.6/dbus/_dbus.py", line 46, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 46, in <module>
    from dbus.connection import Connection
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 42, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 35, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/pymodules/python2.6/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ExpatError, ParserCreate
ImportError: No module named parsers.expat

```

---

### Post by karthick87 on 2010-12-22
Bump....!

---

