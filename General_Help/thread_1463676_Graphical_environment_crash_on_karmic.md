---
title: "Graphical environment crash on karmic"
date: 2010-04-27
forum: General Help
---

### Post by rgeddes on 2010-04-27
ubuntu 9.10, 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

This morning my graphical environment disappeared, when I was editing a keepass file... the system took me back to the login screen.

Found these entries in /var/log/messages:
Apr 27 09:08:36 kimberton pulseaudio[15947]: pid.c: Stale PID file, overwriting.
Apr 27 09:08:38 kimberton pulseaudio[15947]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-ysHbDRF0MT: Connection refused
Apr 27 09:08:40 kimberton bonobo-activation-server (rgeddes-15959): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ysHbDRF0MT: Connection refused


Anyone seen this before?

Does this look pulseaudio related?

R

---

