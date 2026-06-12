---
title: "Can not start Software Center, or install updates"
date: 2011-05-07
forum: General Help
---

### Post by 8_Bit on 2011-05-07
I am using Natty 11.04, clean install, with Unity enabled.

Today I turned my PC on and found that I suddenly can no longer start the _Software Center_.

I am able to start the _Update Manager_ but when I press "*Install Updates*" the program hangs.

I tried starting _Software Center_ through terminal to see what was going on and I see these messages:

> Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 47, in <module>
    from softwarecenter.backend.aptd import TransactionFinishedResult
  File "/usr/share/software-center/softwarecenter/backend/__init__.py", line 19, in <module>
    from aptd import AptdaemonBackend
  File "/usr/share/software-center/softwarecenter/backend/aptd.py", line 30, in <module>
    from aptdaemon import client
**ImportError: No module named aptdaemon**

I also tried running _update-manager_ from terminal and get this error:

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 474, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1580, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1654, in get_aptdaemon
    False),
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 474, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1580, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1654, in get_aptdaemon
    False),
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 472, in _inline_callbacks
    result = gen.throw(result.type, result.value, result.traceback)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 50, in commit
    downgrade, defer=True)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
^CTraceback (most recent call last):
  File "/usr/bin/update-manager", line 108, in <module>
    app.main(options)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 1192, in main
    gtk.main()

The only modifications I made to my system before this started to occur were the ones on this page
[http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html)

I tried undoing the changes and that did not help, so I do not think that was what caused it.
_The Software Center_ still won't start, update manager won't install updates. Synaptic won't start either.

And of course I can't even file this as a bug in launchpad because the program does not even start, and "ubuntu-bug" needs the culprit to be running in order to obtain data to report. :/

Thank you for reading and I appreciate all responses.

P.s. Yes I have restarted my computer several times. Doesn't help. :(

---

### Post by andrewthomas on 2011-05-07
sudo apt-get update && sudo apt-get upgrade

In terminal

---

### Post by 8_Bit on 2011-05-07
Update worked but upgrade did not. I got the following error at the end:

Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

But thankfully, this did bring up a "Report a bug?" window, so I was able to formally file a bug on Launchpad.

EDIT: I have solved it all on my own. Apparently this was caused by my  installing python2.6, The Software Center apparently absolutely requires  2.7, and will not start with 2.6. To fix this, I just had to remove the  /usr/bin/python symlink and recreate a new one pointing to python2.7  instead of python2.6.

---

### Post by 71GA on 2012-11-21
> **8_Bit said:**
> To fix this, I just had to remove the  /usr/bin/python symlink and recreate a new one pointing to python2.7  instead of python2.6.

Could you tell a bit more specific how you did this. I have same problem.

---

