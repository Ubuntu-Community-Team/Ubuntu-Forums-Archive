---
title: "Unable to contact DBUS system bus"
date: 2009-08-31
forum: General Help
---

### Post by paul99 on 2009-08-31
Hi,

I'm running Ubuntu 9.04.

I tried to start F-Spot Photo Manager from the menu and got an error about not being able to find the DBus session bus.  I see these errors in syslog:
[FONT="Courier New"]
Aug 31 13:33:18 x2100-1 pulseaudio[9409]: module-hal-detect.c: Unable to contact DBUS system bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Aug 31 13:33:18 x2100-1 pulseaudio[9409]: module.c: Failed to load  module "module-hal-detect" (argument: "tsched=0"): initialization failed.
Aug 31 13:33:18 x2100-1 pulseaudio[9409]: main.c: Module load failed.
Aug 31 13:33:18 x2100-1 pulseaudio[9409]: main.c: Failed to initialize daemon.
Aug 31 13:33:18 x2100-1 pulseaudio[9407]: main.c: Daemon startup failed.[/FONT]

Any ideas what's going on?

Thanks,

Paul

---

