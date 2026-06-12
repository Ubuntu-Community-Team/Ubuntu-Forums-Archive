---
title: "Quick GRUB Question"
date: 2006-02-28
forum: General Help
---

### Post by Greeface on 2006-02-28
If I want it to show the full GRUB menu on every startup, do I just comment out the 'hiddenmenu' part?
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

I don't want to screw anything up.  Also, will it count down and then load the default option if I have it display this, or will I have to select it every time?

Thanks

---

### Post by Iandefor on 2006-02-28
Looks like it. There's a separate timeout option, so I think it'll show the menu only so long as the timeout as set for. Try it and see.

---

### Post by K.Mandla on 2006-02-28
I tried this once a long time ago and I think (I didn't keep it long) that's the way it worked. Either way, uncommenting that one line shouldn't screw things up so badly that you can't put it back the old way.

---

### Post by heimo on 2006-02-28
Yes. And if you have *timeout* set, *default *entry will be selected after x seconds.

---

### Post by Greeface on 2006-02-28
Okay, thanks guys, I'll try it out and see how it works.

---

### Post by Greeface on 2006-03-06
Ah, yes, It worked like a charm.  Thanks again

---

