---
title: "compiling dbus"
date: 2009-08-26
forum: General Help
---

### Post by kruschev on 2009-08-26
Dear Gurus,

I'm trying to get a firewire sound card working on my laptop. For this, I compiled and installed the latest dbus for my machine (Linux machine 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux). To do this I downloaded the latest beta from here:

[http://dbus.freedesktop.org/releases/dbus/dbus-1.3.0.tar.gz]("http://dbus.freedesktop.org/releases/dbus/dbus-1.3.0.tar.gz")

then I unzipped it and did a 

```
configure --prefix=/usr
make
sudo make install
```

but this broke da' bus, now if I try to start nautilus I have problems:

```
dude@ross:matlab$ nautilus

(nautilus:21952): nautilus-extension-gnome-mount-WARNING **: Cannot connect to system bus: org.freedesktop.DBus.Error.FileNotFound : Failed to connect to socket /usr/var/run/dbus/system_bus_socket: No such file or directory

(nautilus:21952): nautilus-extension-gnome-mount-WARNING **: Could not initialize hal context


** (nautilus:21952): WARNING **: Cannot connect to DBus Failed to connect to socket /usr/var/run/dbus/system_bus_socket: No such file or directory

process 21952: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3436.
This is normally a bug in some application using the D-Bus library.
  D-Bus not built with -rdynamic so unable to print a backtrace
Aborted
```

can anyone help me to fix it, I can't seem to figure it out. I tried a sudo make uninstall, as well as reinstalling dbus with aptitude, but it doesn't help. 

In general, how should one go about compiling and installing bleeding edge versions? What about aptitude and it's knowledge of what's installed? Should/can aptitude somehow be notified that a different version has been installed over the top of what it put there itself?

---

