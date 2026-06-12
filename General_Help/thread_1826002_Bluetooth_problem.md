---
title: "Bluetooth problem"
date: 2011-08-16
forum: General Help
---

### Post by onako on 2011-08-16
After disabling bluetooth and restarting the machine, I do not get the option for bluetooth file transfer. Namely, after clicking on the bluetooth icon in the upper right corner, I get the options: bluetooth: off (shaded), turn off bluetooth, preferences.
Last time I had the option to select and send the file, but now, even in the Preferences, after selecting Bluetooth on, nothing happens.
What might be the problem? Perhaps a recent update had changed something?
 I'm using Ubuntu 10.04 LTS - the Lucid Lynx.

Thanks

---

### Post by onako on 2011-08-16
The following commands have been tried:
```

sudo apt-get install bluez python-gobject python-dbus

``````

Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez is already the newest version.
python-gobject is already the newest version.
python-dbus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```then
```
[FONT=monospace]
[/FONT]cd  /usr/share/doc/bluez/examples/[FONT=monospace]
[/FONT]hcitool dev

``````

Devices:
    hci0    90:4C:E5:F3:22:65

```and 
```

sudo ./simple-agent hci0 90:4C:E5:F3:22:65

```with the output
```

Traceback (most recent call last):
  File "./simple-agent", line 84, in <module>
    manager = dbus.Interface(bus.get_object("org.bluez", "/"),
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
dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.ServiceUnknown: The name org.bluez was not  provided by any .service files

```Any thoughts?

---

