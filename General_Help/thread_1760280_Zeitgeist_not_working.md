---
title: "Zeitgeist not working?"
date: 2011-05-16
forum: General Help
---

### Post by Quadunit404 on 2011-05-16
Each time I try running an app related to Zeitgeist, I get this error message:

```
ERROR:dbus.proxies:Introspect error on :1.1050:/org/gnome/zeitgeist/log/activity: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/bin/gnome-activity-journal", line 90, in <module>
    CLIENT = ZeitgeistClient()
  File "/usr/lib/pymodules/python2.7/zeitgeist/client.py", line 361, in __init__
    self._iface = ZeitgeistDBusInterface()
  File "/usr/lib/pymodules/python2.7/zeitgeist/client.py", line 235, in __init__
    self.INTERFACE_NAME, self.OBJECT_PATH)
  File "/usr/lib/pymodules/python2.7/zeitgeist/client.py", line 149, in __init__
    self.__methods, self.__signals = self.get_members(proxy.Introspect())
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.1050 was not provided by any .service files

```

or something similar to that. Regardless all say the same basic thing: Message did not receive a reply. This affects Synapse (don't see anything logged in it,) the Unity Files and Folders lens and prevents Zeitgeist Global Privacy and Gnome Activity Journal from running.

I don't want to reinstall so how do I fix this?

---

### Post by Larkspur on 2011-05-16
Try running "zeitgeist-daemon --replace" and then launch Gnome Activity Journal.  What they don't tell you is that for the Journal to work, Zeitgeist has to be stopped so the two can communicate.

---

### Post by Quadunit404 on 2011-05-16
```
tom@tom-laptop-linux:~$ zeitgeist-daemon --replace
[DEBUG - singleton] Checking for another running instance...
[INFO - zeitgeist.sql] Using database: /home/tom/.local/share/zeitgeist/activity.sqlite
Traceback (most recent call last):
  File "/usr/bin/zeitgeist-daemon", line 167, in <module>
    mainloop, interface = setup_interface()
  File "/usr/bin/zeitgeist-daemon", line 103, in setup_interface
    return mainloop, RemoteInterface(mainloop = mainloop)
  File "/usr/share/zeitgeist/_zeitgeist/engine/remote.py", line 71, in __init__
    self._engine = get_engine()
  File "/usr/share/zeitgeist/_zeitgeist/engine/__init__.py", line 42, in get_engine
    _engine = main.ZeitgeistEngine()
  File "/usr/share/zeitgeist/_zeitgeist/engine/main.py", line 104, in __init__
    self._cursor = cursor = get_default_cursor()
  File "/usr/share/zeitgeist/_zeitgeist/engine/sql.py", line 447, in get_default_cursor
    _cursor = create_db(dbfile)
  File "/usr/share/zeitgeist/_zeitgeist/engine/sql.py", line 166, in create_db
    cursor.execute("PRAGMA journal_mode = DELETE")
  File "/usr/share/zeitgeist/_zeitgeist/engine/sql.py", line 74, in execute
    return super(UnicodeCursor, self).execute(statement, parameters)
sqlite3.DatabaseError: database disk image is malformed

```

WOW. Thanks. That helped a LOT. It revealed the problem originated in the database and deleting the database then allowing Zeitgeist to create a new one worked wonders! Again, thank you :D

---

### Post by Larkspur on 2011-05-16
> **Quadunit404 said:**
> WOW. Thanks. That helped a LOT. It revealed the problem originated in the database and deleting the database then allowing Zeitgeist to create a new one worked wonders! Again, thank you :D

Hey, if you want to thank me for forgetting to tell you the important part of solving your problem, I won't stop you.;)

---

