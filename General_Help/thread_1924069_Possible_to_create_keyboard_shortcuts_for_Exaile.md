---
title: "Possible to create keyboard shortcuts for Exaile?"
date: 2012-02-11
forum: General Help
---

### Post by nrundy on 2012-02-11
Using 11.10, I tried going to "keyboard" and changing the "sound and media" section so that Ctrl+P would work pause/play. The shortcut "took" and displays as being set. but it never works in Exaile. Is there something else I can try? Is this a bug?

---

### Post by Vishnu V on 2012-02-12
Try to create a custom shortcut with command exaile -t then assign Ctrl+P to it ,

---

### Post by nrundy on 2012-02-13
> **Vishnu V said:**
> Try to create a custom shortcut with command exaile -t then assign Ctrl+P to it ,

Thanks!

Do you know other shortcuts? What are the shortcuts for Stop, Next, & Previous. I'd like to set the following Exaile shortcuts:

Play/Pause = exaile -t
Stop =
Next =
Previous =

---

### Post by Vishnu V on 2012-02-13
stop = exaile -s
Next = exaile -n
Previous = exaile -p

For more info use
```

man exaile

```

---

### Post by nrundy on 2012-02-13
Thanks a lot guys!

---

