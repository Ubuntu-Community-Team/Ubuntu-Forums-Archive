---
title: "No gwibber"
date: 2010-04-30
forum: General Help
---

### Post by noogs on 2010-04-30
I recently updated my Lenovo laptop to Lucid Lynx, and everything works great, however Gwibber will not open. When run from the terminal I get the following errors. Any help is greatly appreciated. Thank you.


** (gwibber:4031): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:4031): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:4031): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 50, in <module>
    from gwibber import client
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 3, in <module>
    import gtk, gobject, gwui, util, resources, actions, json, gconf
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 2, in <module>
    import os, json, urlparse, resources, util
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 2, in <module>
    from microblog.util.couch import RecordMonitor
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 4, in <module>
    import desktopcouch, pycurl, oauth, threading, urllib, re, json
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 20, in <module>
    from desktopcouch.start_local_couchdb import process_is_couchdb, read_pidfile
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 38, in <module>
    from desktopcouch import local_files
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 297, in <module>
    xdg_base_dirs.save_config_path("desktop-couch"))
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 237, in __init__
    self.configuration = _Configuration(self)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 91, in __init__
    {'desktopcouch': 'basic'})
gnomekeyring.IOError

---

### Post by rybajz on 2010-04-30
I have the same problem. I have started gwibber only at first time after installation of 10.04. When I started computer at second time. The gwibber did not run. If I run gwibber in terminal, I have the same warnings.

---

### Post by factory909 on 2010-04-30
its also broken on my machine, same song and dance as you guys.

---

### Post by factory909 on 2010-04-30
you can run gnome-keyring-daemon -f &
then run gwibber, should start

---

### Post by Peter7K on 2010-04-30
> **factory909 said:**
> you can run gnome-keyring-daemon -f &
then run gwibber, should start

$ gnome-keyring-daemon -f &
[1] 2892
$ GNOME_KEYRING_CONTROL=/tmp/keyring-AsrgJd
SSH_AUTH_SOCK=/tmp/keyring-AsrgJd/ssh
GNOME_KEYRING_PID=2892
** Message: another secret service is running

I receive that error when I attempt to run gnome-keyring-daemon -f &

And of course Gwibber still does not function (gets the same error as those above me have)

---

### Post by noogs on 2010-04-30
This worked perfectly for me after running command gwibber started right up thank you for your help.

---

### Post by Danbo19 on 2010-05-20
I have the same problem, running gwibber in a terminal produces:

```
danny@danny-laptop:~$ gwibber

** (gwibber:2697): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:2697): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:2697): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
No dbus monitor yet
Updating...
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 58, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 144, in setup_ui
    self.stream_view.set_state(self.model.settings["streams"] or DEFAULT_SETTINGS["streams"])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 438, in set_state
    self.update()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 426, in update
    self.message_view.render([self.navigation.selected_stream["view"]])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 706, in render
    message = item['doc']
KeyError: 'doc'

```

Running gnome-keyring-daemon -f results in:

```
danny@danny-laptop:~$ gnome-keyring-daemon -f
GNOME_KEYRING_CONTROL=/tmp/keyring-Jslggk
SSH_AUTH_SOCK=/tmp/keyring-Jslggk/ssh
GNOME_KEYRING_PID=2676
** Message: another secret service is running

```

Gwibber still won't start any other suggestions?

---

