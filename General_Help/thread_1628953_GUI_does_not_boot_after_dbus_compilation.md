---
title: "GUI does not boot after dbus compilation"
date: 2010-11-23
forum: General Help
---

### Post by ameeck on 2010-11-23
Hi guys,

Yesterday I wanted to install PBC (software for printing board circuits). While running configure, it said something about dbus missing, so I downloaded the latest from here :[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus) (running the standard configure, make, make install)

Now everything went fine and I managed to install PBC. However when I tried to boot up the system in the morning. I got an error message that my screen, display nad input devices could not be detected and that ubuntu had to run in low-graphics mode. When I clicked, ok use low-graphics, it looked like it's started, but just hangs with the default image background i see before seeing the system boot into windows mode.

in recovery mode, i can login to console and type startx to run the system. however things like network-admin fails to start giving this error:

```
Libooobs-WARNING **: Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: Connection refused

Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

WARNING **: Error connecting to bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: Connection refused

process 1503: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5980
This is normally a bug in some application using the D-Bus library.
 D-bus not build with -rdynamic so uanble to print a backtrace
```It might not at all be connected to dbus, but it's the only thing I changed.

---

