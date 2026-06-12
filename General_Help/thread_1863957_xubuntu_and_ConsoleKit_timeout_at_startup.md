---
title: "xubuntu and ConsoleKit timeout at startup"
date: 2011-10-18
forum: General Help
---

### Post by Tares on 2011-10-18
hello,

I've noticed that my boot times are little high and I've started investigating. I've found that durning boot I loose 10+ seconds on a timeout. Here a part from my syslog:
```
Oct 17 06:45:34 tengoku dbus[849]: [system] Failed to activate service 'org.freedesktop.ConsoleKit': timed out
Oct 17 04:45:34 tengoku rtkit-daemon[1133]: Warning: PolicyKit call failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Oct 17 06:45:34 tengoku accounts-daemon[1277]: started daemon version 0.6.14
Oct 17 06:45:34 tengoku pulseaudio[1131]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Oct 17 06:45:34 tengoku pulseaudio[1128]: [pulseaudio] main.c: Daemon startup failed.

```

Anyone has an idea what to do?

---

### Post by Tares on 2011-10-18
Help?

---

