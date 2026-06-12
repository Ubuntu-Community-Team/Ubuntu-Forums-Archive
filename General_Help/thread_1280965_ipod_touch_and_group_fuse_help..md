---
title: "ipod touch and group fuse help."
date: 2009-10-02
forum: General Help
---

### Post by BraedenNaylor on 2009-10-02
[SOLVED]

I'm trying to wirelessly sync my itouch with my computer. Its telling me that I need to add myself to fuse group then logout and back in. However under manage groups, there is only 2. root, and myself. Can someone please help me.

Karmic Koala Beta.


Edit:

```

sudo adduser username fuse

```
Produces:
"The user `username' is already a member of `fuse'."


but:

```

sudo ipod-touch-mount

```
Produces:
Please add yourself to the fuse group, logout/in and try again.



For some reason rebooting worked....But logging out and back in didnt.

---

