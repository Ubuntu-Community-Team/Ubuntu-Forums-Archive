---
title: "Ktorrent fails after update"
date: 2011-06-24
forum: General Help
---

### Post by kaizo2560 on 2011-06-24
Hi my Ktorrent suddenly started showing a blank window after an update a few days ago.

I tried reinstalling and rebooting a number of times with no progress.

The client is utterly redundant. Does anybody else have the same problem?

Thanks in advance.

---

### Post by TeoBigusGeekus on 2011-06-24
Launch it from a terminal
```
ktorrent
```
and post us any error messages.

---

### Post by kaizo2560 on 2011-06-24
I've got:

a@b:~$ ktorrent
Warning: Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Warning: Calling appendChild() on a null node does nothing.
a@b:~$ <unknown program name>(9405)/ main: 2 - parseCommandLine
<unknown program name>(9405)/ main: 3 - create KApplication
nspluginviewer(9405)/nspluginviewer (Qt/Xt) main: 4 - create XtEvents and GlibEvents
nspluginviewer(9405)/nspluginviewer (Qt/Xt) main: 5 - dbus requestName
nspluginviewer(9405)/nspluginviewer (Qt/Xt) main: 6 - new NSPluginViewer
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
nspluginviewer(9405)/nspluginviewer (Qt/Xt) main: 7 - app.exec()
nspluginviewer(9405)/nspluginviewer (Qt/Xt) GlibEvents::process: Qt already providing Glib integration, dropping ours

---

### Post by kaizo2560 on 2011-06-26
bump

---

