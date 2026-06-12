---
title: "Software Centre wont load"
date: 2011-04-05
forum: General Help
---

### Post by shaydn on 2011-04-05
hi
any ideas on why my software centre wont run?

this is the software-centre.log

2011-04-06 00:32:02,693 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2011-04-06 00:32:02,693 - root - WARNING - failed to add sca db Couldn't detect type of database
2011-04-06 00:32:11,314 - softwarecenter.app - INFO - software-center-agent finished with status 0
2011-04-06 00:32:12,631 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-04-06 00:32:12,631 - dbus.proxies - ERROR - Introspect error on :1.57:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.54" (uid=999 pid=4596 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.57" (uid=0 pid=4633 comm="/usr/bin/python))
2011-04-06 00:32:19,957 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-04-06 00:32:19,957 - dbus.proxies - ERROR - Introspect error on :1.57:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.54" (uid=999 pid=4596 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.57" (uid=0 pid=4633 comm="/usr/bin/python))
2011-04-06 00:34:47,858 - softwarecenter.app - INFO - software-center-agent finished with status 1
2011-04-06 00:35:36,585 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-04-06 00:35:36,584 - dbus.proxies - ERROR - Introspect error on :1.57:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.58" (uid=999 pid=4733 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.57" (uid=0 pid=4633 comm="/usr/bin/python))

---

