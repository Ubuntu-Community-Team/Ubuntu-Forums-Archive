---
title: "Lucid returns to log-in screen randomly"
date: 2010-05-07
forum: General Help
---

### Post by chandearriba on 2010-05-07
My desktop computer (Lucid) crashes randomly and returns to the log-in screen. It does so when when there is no activity and the screen-saver is on.

I get messages like this:
> May  7 14:27:36 xxx-sobremesa pulseaudio[14267]: pid.c: Stale PID file, overwriting.
May  7 14:27:36 xxx-sobremesa pulseaudio[14267]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-VvkOwqlRyF: Conexión rechazada
May  7 14:27:41 xxx-sobremesa bonobo-activation-server (alex-14326): could not associate with desktop session: Failed to connect to socket /tmp/dbus-VvkOwqlRyF: Conexión rechazadaAny kind and patient soul out there to offer me some fix?

---

### Post by bredman on 2010-05-07
I'm sure I saw this on the Absolute Beginner Talk yesterday, but I can't find it now.

The solution was to use Synaptic Package Manager to remove screensaver.

This is a bit extreme because you lose your screensaver but at least you are not logged out.

---

### Post by chandearriba on 2010-05-10
Thanks bredman. I've removed gnome-screensaver and even other secreensaver-related packages, but the problem terribly persists. Actually, it makes the OS nearly unusable. From what  I get from aforementioned messages, somehow the issue has to do with pulseaudio, but I'm blind beyond that. I know there have been similar problems reported as bugs over in launchpad (like [this one]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540626")), but I can't see any solution. 

I've even reinstalled the whole 10.04 thing (out of not knowing what else to do, I guess). To no avail. After some time of no activity, X hangs, all processes are killed, and the login screen takes over. The only thing I can think of is trying the 64 bit version, just to see if somehow the issue doesn't recur there... Lucid is giving me a hard time.

---

