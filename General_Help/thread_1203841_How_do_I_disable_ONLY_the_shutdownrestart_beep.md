---
title: "How do I disable ONLY the shutdown/restart beep"
date: 2009-07-03
forum: General Help
---

### Post by jenkinbr on 2009-07-03
In Ubuntu 9.04 Jaunty, the shutdown and restart options both emit a series of beeps when shutting down.  I find this very irritating, especially with late-night shutdowns.  What I want to do is disable this, but ONLY for the shutdown sequence.

I have seen many many many threads regarding this, most of which suggest adding the line ```
blacklist pcspkr
``` to my '/etc/modprobe.d/blacklist.conf' file.  I do not want to do this, as I prefer to keep the system beep turned on.

I have also seen several other suggestions that involve turning the system bell off in various other ways - bot only for specific apps like vim or gnome-terminal. Others show turning the bell off for all X apps, also not what I want.

Is there any way to disable the system bell for ONLY the shutdown/restart functions accessed through Fast-user-switcher?

---

### Post by jenkinbr on 2009-07-09
bump

---

### Post by CatKiller on 2009-07-09
Does unchecking System -> Preferences -> Power Management -> General -> Use sound to notify in event of an error help?

---

### Post by jenkinbr on 2009-07-09
Nope - it's already unchecked, but still beeps every time I shutdown or restart using the fast-user-switch applet.

---

