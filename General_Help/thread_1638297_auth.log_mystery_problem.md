---
title: "auth.log mystery problem"
date: 2010-12-05
forum: General Help
---

### Post by reddae on 2010-12-05
Dec  5 12:12:31 Toshiba-LPTP dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.197" (uid=1000 pid=7622 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1077 comm="/usr/sbin/console-kit-daemon))

I noticed the above error in my auth.log and checked on OSSEC which displays it as:

**2010 Dec 05 12:12:32**             Rule Id: [1002]("http://www.ossec.net/wiki/index.php/Rule:1002")             level: 2
            **Location:** Toshiba-LPTP->/var/log/auth.log 
                         **Unknown problem somewhere in the system.**                              Dec  5 12:12:31 Toshiba-LPTP dbus-daemon: [system]  Rejected send message, 2 matched rules; type="method_call",  sender=":1.197" (uid=1000 pid=7622 comm="nautilus)  interface="org.freedesktop.DBus.Properties" member="GetAll" error  name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1077  comm="/usr/sbin/console-kit-daemon))

Is there a way to isolate this and figure out what the problem is?

---

### Post by smeggs on 2010-12-05
> **reddae said:**
> Dec  5 12:12:31 Toshiba-LPTP dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.197" (uid=1000 pid=7622 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1077 comm="/usr/sbin/console-kit-daemon))

I noticed the above error in my auth.log and checked on OSSEC which displays it as:

**2010 Dec 05 12:12:32**             Rule Id: [1002]("http://www.ossec.net/wiki/index.php/Rule:1002")             level: 2
            **Location:** Toshiba-LPTP->/var/log/auth.log 
                         **Unknown problem somewhere in the system.**                              Dec  5 12:12:31 Toshiba-LPTP dbus-daemon: [system]  Rejected send message, 2 matched rules; type="method_call",  sender=":1.197" (uid=1000 pid=7622 comm="nautilus)  interface="org.freedesktop.DBus.Properties" member="GetAll" error  name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1077  comm="/usr/sbin/console-kit-daemon))

Is there a way to isolate this and figure out what the problem is?


I've noticed this in my auth.log as well. I haven't been able to find anything about it, though I haven't really searched very hard. It's not a recurring problem and I don't notice any problems with any functionality anywhere.

---

