---
title: "apt-policy cache does not work"
date: 2011-04-03
forum: General Help
---

### Post by robertbub on 2011-04-03
**apt-policy cache** works great on my Debian machines and my Karmic Ubuntu machine, but does not work on my Lucid Lynx machine.  Here is the output:```
$ apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
Pinned packages:
```That's all it outputs.

I'm trying to get more extensive output so I can stick the allowed origins into my *50unattended-upgrades* file.

Anybody have any ideas about this?

---

### Post by robertbub on 2011-04-03
Figured it out.  Feel dumb.

Apparently, with Lucid Lynx, you have to do **sudo apt-cache policy**.  (Don't know why all other machines don't need the *sudo*.)

---

### Post by gmargo on 2011-04-03
> **robertbub said:**
> Don't know why all other machines don't need the *sudo*.

Likely due to permissions on the files/directories under /etc/apt/ or /var/lib/dpkg/.  If you have pinned items, then probably /etc/apt/preferences (or /etc/apt/preferences.d/) is unreadable by a normal user.

---

