---
title: "Can't disable Hibernate option in Ubuntu 9.10"
date: 2009-12-02
forum: General Help
---

### Post by ShiftyEyes on 2009-12-02
I removed the hibernate option from the menus in 9.04 using gconf-editor, but now that I've installed 9.10 that method doesn't seem to work anymore.

gconf-editor: apps --> gnome-power-manager --> general 'can_hibernate' is unchecked (even when doing sudo gconf-editor)

But hibernate still appears in indicator-applet-session, and I also tried setting the key to mandatory. I had originally just upgraded from 9.04 using the update manager, but that resulted in an essentially unusable system so I did a completely new install. That fixed a lot of the issues, but not this one. I haven't been able to find anyone else talking about this issue, but I don't know why I'd be the only one with the problem. My system is pretty standard, except that it's 64 bit.

Any advice?

---

### Post by carnagex420x on 2009-12-27
same problem, eetz been driving me nutz!

edit: BUG! [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/432598](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/432598)

---

