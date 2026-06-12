---
title: "MP3 player &quot;read only&quot; file system?"
date: 2009-07-03
forum: General Help
---

### Post by carl99fan on 2009-07-03
have a cheap little element mp3 player that has worked fine till I used it on this fresh install of 9.04.
Tried changing the properties using sudo nautilus and still nothing.
any ideas?
It mounts just fine and just Monday I put these songs on it but that was before I bought new hdd and did fresh install.

---

### Post by dcstar on 2009-07-03
> **carl99fan said:**
> have a cheap little element mp3 player that has worked fine till I used it on this fresh install of 9.04.
Tried changing the properties using sudo nautilus and still nothing.
any ideas?
It mounts just fine and just Monday I put these songs on it but that was before I bought new hdd and did fresh install.

File systems with errors usually mount RO, unmount and do a fsck on it (or use the Partition Editor to Check it - same result anyway).

---

