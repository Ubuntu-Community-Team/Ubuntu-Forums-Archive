---
title: "System bus / Message bus daemon fails, can't connect"
date: 2010-11-14
forum: General Help
---

### Post by jverdeyen on 2010-11-14
Hi,

I'm running Ubuntu Hard 8.04.4.

Since yesterday I get the following errors in my syslog. And my avahi server fails to start.
Where should I look for? Any solutions? Google didn't gave me any working answer.

```

Nov 14 19:47:53 kermit avahi-daemon[24630]: Found user 'avahi' (UID 110) and group 'avahi' (GID 120).
Nov 14 19:47:53 kermit avahi-daemon[24630]: Successfully dropped root privileges.
Nov 14 19:47:53 kermit avahi-daemon[24630]: avahi-daemon 0.6.22 starting up.
Nov 14 19:47:53 kermit avahi-daemon[24630]: dbus_bus_get_private(): Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Nov 14 19:47:53 kermit avahi-daemon[24630]: WARNING: Failed to contact D-Bus daemon.
Nov 14 19:47:54 kermit console-kit-daemon[14918]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Nov 14 19:47:55 kermit NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Nov 14 19:47:57 kermit console-kit-daemon[14918]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 

```

Thx!

---

