---
title: "Gwibber crashes on startup"
date: 2010-05-01
forum: General Help
---

### Post by DaftPyramid on 2010-05-01
I tried installing Gwibber on Ubuntu 9.10, but when I start the program, it just goes grey and requires a force-quit.

Running it in the terminal produced the following errors.

```
/usr/lib/python2.6/dist-packages/gwibber/microblog/support/facelib.py:47: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
ERROR:dbus.proxies:Introspect error on :1.76:/net/launchpad/gwibber/Interface: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
console message: undefined @1: ReferenceError: Can't find variable: addMessages
console message: undefined @22: ReferenceError: Can't find variable: setGtkConfig
console message: undefined @1: ReferenceError: Can't find variable: setAccountConfig
console message: undefined @1: ReferenceError: Can't find variable: addMessages
console message: undefined @22: ReferenceError: Can't find variable: setGtkConfig
console message: undefined @1: ReferenceError: Can't find variable: setAccountConfig
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 477, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 991, in process
    self.manage_indicator_items(view.message_store, tab_num=self.tabs.page_num(tab))
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 948, in manage_indicator_items
    if not self.is_gwibber_active():
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 945, in is_gwibber_active
    return self.window.xid == screen.get_active_window().get_xid()
AttributeError: 'NoneType' object has no attribute 'get_xid'
```

Any help would be greatly appreciated, thanks in advance.

---

### Post by DaftPyramid on 2010-05-01
Bump

---

