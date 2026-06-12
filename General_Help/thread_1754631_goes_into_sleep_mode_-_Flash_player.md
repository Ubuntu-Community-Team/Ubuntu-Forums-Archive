---
title: "goes into sleep mode - Flash player"
date: 2011-05-10
forum: General Help
---

### Post by kirill578 on 2011-05-10
My Ubuntu goes into sleep mode while I'm watching video on fullscreen, is there any solution for it?

---

### Post by Frogs Hair on 2011-05-10
Preferences > Screen Saver > Power Management , adjust screen saver and sleep times from there. There are also other threads , so use the forum search.

---

### Post by kirill578 on 2011-05-10
yes, i know that i can change the sleep time, but it's not a real solution.

---

### Post by lovinglinux on 2011-05-10
This is what I use before playing flash in fullscreen:

```
xset -dpms
```

This was the only way I could prevent the sleep mode while running flash in fullscreen.

You can revert the changes with:

```
xset +dpms
```

From xset man pages:

> 
The -dpms option disables DPMS (Energy Star) features.

The +dpms option enables DPMS (Energy Star) features.


---

