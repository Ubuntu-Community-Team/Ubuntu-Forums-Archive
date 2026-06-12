---
title: "python based programs fail to start.."
date: 2010-10-30
forum: General Help
---

### Post by Lyoko on 2010-10-30
I got this problem today, since it started i cannot launch software-center, vlc, emesene... they all stopped working... i checked the logs of synaptic to see if i removed a python package and i didn't. i tried selecting all python packages for reinstall, and it didn't help!
i really don't want to reinstall ubuntu, Please help me.

---

### Post by J V on 2010-10-30
Try starting the programs from a terminal and checking the output... IIRC, vlc isn't a python program...

---

### Post by Lyoko on 2010-10-30
> **J V said:**
> Try starting the programs from a terminal and checking the output... IIRC, vlc isn't a python program...
```
lyoko@lyoko-desktop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 22, in <module>
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
  File "/usr/lib/python2.6/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: No module named pyexpat


```

was the output of software-center..

---

### Post by Lyoko on 2010-10-31
bump..

---

### Post by TeoBigusGeekus on 2010-10-31
Try this
```
gksu python2 /usr/bin/software-center
```

---

### Post by Lyoko on 2010-10-31
> **TeoBigusGeekus said:**
> Try this
```
gksu python2 /usr/bin/software-center
```
nothing... :(

---

### Post by J V on 2010-10-31
pyexpat seems to be a default module in python, if you could show the error from vlc so we know it's really a python problem, open synaptic and do a complete reinstall of the python packages and see what happens...

---

### Post by Lyoko on 2010-10-31
> **J V said:**
> pyexpat seems to be a default module in python, if you could show the error from vlc so we know it's really a python problem, open synaptic and do a complete reinstall of the python packages and see what happens...
I did that before opening the thread... and ofc nothing...


here's vlc output..
```
lyoko@lyoko-desktop:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x805d914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x81010ac] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x81010ac] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x805d914] main libvlc error: interface "default" initialization failed
lyoko@lyoko-desktop:~$ 

```


sorry i can see it has nothing to do with python...

---

### Post by cavalier911 on 2010-10-31
The solution may involve security/permissions with **dbus**:
vlc:```
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
```
software-center:
```
File "/usr/share/software-center/softwarecenter/app.py", line 22, in <module>
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
```

---

### Post by Lyoko on 2010-11-01
Thanks!!! I just reinstalled dbus packages and Vlc works again!  but emesene, update-manager, software-center still don't...

---

