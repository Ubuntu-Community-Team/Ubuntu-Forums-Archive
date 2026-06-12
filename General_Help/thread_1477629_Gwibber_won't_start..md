---
title: "Gwibber won't start."
date: 2010-05-08
forum: General Help
---

### Post by toejamfootball on 2010-05-08
When I click on "Broadcast Accounts" in the drop down menu nothing happens, same for the mail icon menu item "Broadcast".

Clicking Gwibber Social Client in the Applications Menu also does nothing. Typing gwibber in terminal give this result:

```
james@james-ubuntu-desktop:~$ gwibber

** (gwibber:3165): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3165): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3165): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
No dbus monitor yet
Updating...
ERROR:dbus.proxies:Introspect error on com.Gwibber.Service:/com/gwibber/Service: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 29, in __init__
    self.model = gwui.Model()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 43, in __init__
    self.services = json.loads(self.daemon.GetServices())
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```

It was working when I first installed 10.04, since then I have installed Mac4Lin theme, could this have affected gwibber? 

Any ideas? Thanks!

---

### Post by internalkernel on 2010-06-23
I don't have any answers, but I thought I'd chime in... Since I'm getting the exact same error this morning. 

I thought maybe deleting the config files in my ~/ would help, but I can't seem to find them... anywhere.

After digging a bit more, I found this bug report: 

[https://bugs.launchpad.net/gwibber/+bug/515012](https://bugs.launchpad.net/gwibber/+bug/515012)

there's a work around in there.

---

