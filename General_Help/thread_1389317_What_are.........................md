---
title: "What are........................"
date: 2010-01-24
forum: General Help
---

### Post by squid69 on 2010-01-24
The letters in brackets in bookmarks in Opera ??
and how can i delete them because they are not visible in manage bookmarks ???


Also how can i get rid of the "Shut-down in 60 secs" message when i shut it down ???

Or at least can i alter the time till shutdown ?

Ubuntu 9.10 64 bit by the way

---

### Post by howefield on 2010-01-24
> **squid69 said:**
> The letters in brackets in bookmarks in Opera ??
and how can i delete them because they are not visible in manage bookmarks ???

Can you post a screenshot ?


> Also how can i get rid of the "Shut-down in 60 secs" message when i shut it down ???

Press alt + F2 keys together and in the run box, type

```
gconf-editor
```

Navigate to apps > indicator-session and check the box beside suppress_logout_restart_shutdown.

Then close the gconf-editor window

---

### Post by squid69 on 2010-01-24
Screenshot Attached

the Ubuntu folder was made after the install of 9.10 the rest came over from windoze and a few folders have them but not all

---

### Post by Saiko Berry on 2010-01-24
Theyre hotkeys for quick access through keyboard controls. Remove them by editing the hotkey out through manage bookmarks of disabling the hotkey plugin.

---

