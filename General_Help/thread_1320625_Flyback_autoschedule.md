---
title: "Flyback autoschedule"
date: 2009-11-09
forum: General Help
---

### Post by jumpa72 on 2009-11-09
Hi,
I've installed flyback v.0.4.0. I've edited preferences and added the folders I need to backup. If I manually run the backups, it works fine. If I actvate the automatic schedule, it doesn't works.
If I run the cron job I get this message:

/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/@warp/programmi/flyback/flyback.py", line 101, in <module>
    client = config_backend.GConfConfig()
  File "/@warp/programmi/flyback/config_backend.py", line 75, in __init__
    self.client.add_dir ("/apps/flyback", gconf.CLIENT_PRELOAD_NONE)
glib.GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Not running within active session)

Could anyone help me?
tnx

---

