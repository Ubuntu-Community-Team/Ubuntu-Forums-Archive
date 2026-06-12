---
title: "Problem with blueman"
date: 2011-06-09
forum: General Help
---

### Post by manoharagent13 on 2011-06-09
Hi..
I am using ubuntu 10.10 and i have a nokia 5130XM phone which i use as a modem.
Whenever i pair the phone with blueman and connect to network access point, it gives me following error:

```
Connection Failed: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "<string>", line 2, in ServiceProxy
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/DBusService.py", line 119, in ServiceProxy
    self.Applet.Plugins.RunEx("service_connect_handler", cb, interface, object_path, _method, args, ok, err)
  File "/usr/bin/blueman-applet", line 278, in RunEx
    ret = getattr(inst, function)(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 322, in service_connect_handler
    conn = self.find_active_connection(d.Address, "panu")
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 279, in find_active_connection
    nma_connection = self.find_connection(address, type)
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 267, in find_connection
    conns = self.nma.ListConnections()
AttributeError: 'NoneType' object has no attribute 'ListConnections'

```

I have no idea how to solve this one..any help here?

---

