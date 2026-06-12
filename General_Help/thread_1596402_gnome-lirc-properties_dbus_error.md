---
title: "gnome-lirc-properties dbus error"
date: 2010-10-14
forum: General Help
---

### Post by Gorlist on 2010-10-14
Hi, ive installed lirc, and then gnome-lirc-properties to allow setup.  Though ive manually configured my lircrc file ive noticed when I try and run the gnome-lirc-properties program im getting the following error:

```
Traceback (most recent call last):
  File "/usr/bin/gnome-lirc-properties", line 31, in <module>
    gnome_lirc_properties.run(sys.argv[1:], datadir)
  File "/usr/lib/pymodules/python2.6/gnome_lirc_properties/__init__.py", line 59, in run
    return ui.RemoteControlProperties(builder, datadir).run()
  File "/usr/lib/pymodules/python2.6/gnome_lirc_properties/ui/RemoteControlProperties.py", line 53, in __init__
    self.__setup_models()
  File "/usr/lib/pymodules/python2.6/gnome_lirc_properties/ui/RemoteControlProperties.py", line 80, in __setup_models
    self.__hardware_manager = hardware.HardwareManager(receivers_db)
  File "/usr/lib/pymodules/python2.6/gnome_lirc_properties/hardware.py", line 255, in __init__
    self.__hal = self.__bus.get_object(HAL_SERVICE, HAL_MANAGER_PATH)
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
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files

```

Any suggestions?

Also is it possible to function ubuntu itself with the remote, specifically global volume and suspend more?


Thanks.

---

### Post by fedleo on 2010-10-24
Same here, but with my HP MCE usb receiver and my Logitech Harmony remote config. Work fine on 10.04 and XBMC but now in 10.10 it's totally broken. 
I'll try again today, then I fill a bug in launchpad later.

---

### Post by fedleo on 2010-10-24
I Opened a bug just now on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-lirc-properties/+bug/665906").

---

