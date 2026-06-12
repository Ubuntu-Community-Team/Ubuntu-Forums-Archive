---
title: "Administration -&gt; Hardware Drivers does nothing - can't open it."
date: 2010-03-18
forum: General Help
---

### Post by FunkeyMonk on 2010-03-18
I'm running Ubuntu Karmic 9.10.   

Having trouble getting Compiz to start, and want to check which video driver I'm using. 

However, the "Hardware Drivers" menu item isn't working for me.   When I select it from the Administration menu, I see my HD indicator light blinking, but nothing happens.

Is there a problem with my Ubuntu Installation?  Is there perhaps a way I could reinstall that menu?

---

### Post by howefield on 2010-03-18
> **FunkeyMonk said:**
> However, the "Hardware Drivers" menu item isn't working for me.   When I select it from the Administration menu, I see my HD indicator light blinking, but nothing happens.

Try opening a terminal (Applications > Accessories > Terminal) and type into it

```
jockey-gtk
```

If there is a problem, you should get a clue about what is causing it, which you can either use to work out the problem or paste it here.

---

### Post by FunkeyMonk on 2010-03-18
Thanks for the suggestion -- here's the error I just got after jockey-gtk:
```
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 394, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 417, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 99, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 254, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 741, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 90, in backend
    self._dbus_iface = Backend.create_dbus_client()
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 631, in create_dbus_client
    obj = bus.get_object(DBUS_BUS_NAME, '/DeviceDriver')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1

```

Ideas?

---

### Post by FunkeyMonk on 2010-03-18
OK -- I went to Synaptic Package manager and reinstalled Python 2.6, and the Jockey-GTK packages.

Back in business.

Thanks very much!

(Why the heck is "Hardware Drivers" called Jockey, anyway?)

---

