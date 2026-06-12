---
title: "Problem running meld on server"
date: 2009-10-13
forum: General Help
---

### Post by eshober on 2009-10-13
I'd like to run meld on an Ubuntu server platform (not running X) and use my development desktop (running X) to view the application. Other X applications work fine but when I run meld on my server I get the following message:

Traceback (most recent call last):
  File "/usr/bin/meld", line 109, in <module>
    meldapp.main()
  File "/usr/lib/meld/meldapp.py", line 855, in main
    app = MeldApp()
  File "/usr/lib/meld/meldapp.py", line 528, in __init__
    self.prefs = MeldPreferences()
  File "/usr/lib/meld/meldapp.py", line 465, in __init__
    prefs.Preferences.__init__(self, "/apps/meld", self.defaults)
  File "/usr/lib/meld/prefs.py", line 91, in __init__
    self._gconf.add_dir(rootkey, gconf.CLIENT_PRELOAD_NONE)
glib.GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-zaweY3ixlw: Connection refused)

I don't think I have any stale NFS locks. What do I need to do?

---

