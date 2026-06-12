---
title: "How to check if window is maximized?"
date: 2010-08-02
forum: General Help
---

### Post by drewsus on 2010-08-02
Hello all, 
I was just curious if there was an easy way to check if a window is maximized in terminal (preferably with wmctrl and not by checking the x,y dimensions of said window)?

Thanks,
Drew

---

### Post by kalos on 2010-09-06
I never got the impression that wmctrl was mostly write-only.

What are you trying to do?

To make it maximized, you could do this:
```
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

```

You can use remove or toggle instead of add.

---

