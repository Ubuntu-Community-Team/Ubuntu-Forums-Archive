---
title: "Rhythmbox kills keyboard"
date: 2009-12-10
forum: General Help
---

### Post by h_howee on 2009-12-10
My keyboard stops working whenever I start Rhythmbox. If I run it by clicking the icon in the menu, closing it doesn't fix it, but if I run it through the terminal and close the terminal, the keyboard starts working again.
Why is this happening and how do I fix it?

I don't know how much of this is relevant; I included the terminal output, and changes in the log when Rhythmbox was run.

Console output when running Rhythmbox
```
** (rhythmbox:3599): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3599): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Rhythmbox: could not open config files /home/howard/.lircrc and /etc/lirc//lirc/lircrc
Rhythmbox: No such file or directory
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
```

When opening Rhythmbox (syslog and daemon.log)
```
Dec 10 18:40:32 howard-laptop lircd-0.8.6[771]: accepted new client on /var/run/lirc/lircd
Dec 10 18:40:32 howard-laptop lircd-0.8.6[771]: initializing '/dev/input/event5
```

closing Rhythmbox (syslog and daemon.log)
```
Dec 10 18:41:35 howard-laptop lircd-0.8.6[771]: removed client
Dec 10 18:41:35 howard-laptop lircd-0.8.6[771]: closing '/dev/input/event5'
```

[edit]
Turns out it's a problem with the LIRC plugin. Removing that fixed it.
I don't see what that had to do with the keyboard though...

---

### Post by Ninja Tux on 2009-12-10
I had the very same problem as you. Rythmbox also uses a lot of my memory. So instead, why not use amarok? It is free, and comes with most ubuntu systems. It is very light-weight and has many more features than rythmbox. If it is not already installed, use add/remove programs.

---

