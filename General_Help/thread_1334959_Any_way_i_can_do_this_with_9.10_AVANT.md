---
title: "Any way i can do this with 9.10/ AVANT?"
date: 2009-11-23
forum: General Help
---

### Post by JoeyF on 2009-11-23
When i shut the computer down i get a "Screen isn't composited" message.

Avant works fine though.

Any way to disable that?

Thanks,
;)

---

### Post by jocko on 2009-11-23
Either be quick and tick the "don't show this again" box and "ok" when you see it the next time, or open up the gconf-editor:
```
gconf-editor
```
Find "/apps/avant-window-navigator/show_dialog_if_not_composited" and inactivate it.

---

