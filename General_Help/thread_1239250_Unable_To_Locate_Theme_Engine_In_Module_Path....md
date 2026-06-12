---
title: "Unable To Locate Theme Engine In Module Path..."
date: 2009-08-13
forum: General Help
---

### Post by dharvell on 2009-08-13
While attempting to open RAWstudio, the window opens, then closes.  To see if I could get some feedback as to why this is happening, I attempted to open RAWstudio from the console.  When I did, I received the following message:

> (rawstudio:6069): Gtk-WARNING **: Unable to locate theme engine in module_path:
"clearlooks",
Segmentation fault

Any ideas to help me get through this would be very much appreciated!

---

### Post by dharvell on 2009-08-13
Unfortunately, I had to get the answer from a photography forum, but the here's the solution:

```
apt-get install gtk2-engines
```

Hope this can help somebody else down the road... :guitar:

---

