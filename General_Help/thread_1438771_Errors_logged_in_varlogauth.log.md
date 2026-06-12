---
title: "Errors logged in /var/log/auth.log"
date: 2010-03-25
forum: General Help
---

### Post by Rubi1200 on 2010-03-25
I have noticed the following errors (?) showing up on a fairly regular basis in /var/log/auth.log:

dbus-daemon: Rejected send message, 3 matched rules; type="method_call", sender=":1.50" (uid=1000 pid=1583 comm="/usr/lib/indicator-messages/indicator-messages-ser") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.8" (uid=0 pid=882 comm="/sbin/wpa_supplicant))

Does anyone know what this means and should I be concerned?

Thanks in advance.

---

### Post by Rubi1200 on 2010-03-25
I think I may have solved this one on my own: it seems the errors could be related to a bug in the way the wpa_supplicant handles internet connections. The error always shows up after I start the computer and Network Manager connects to the wireless router.
Other than that, not sure what to say, but I hope someone can correct me if what I wrote is incorrect.
:)

---

