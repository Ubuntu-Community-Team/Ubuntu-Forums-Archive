---
title: "Can't use metacity and compiz effects together."
date: 2010-02-27
forum: General Help
---

### Post by gymophett on 2010-02-27
Okay. I'm on a Sabayon Linux install, and the Sabayon forums and stuff have NO idea what I'm talking about and keep giving me "facepalms" (thanks Sabayon community). 

So in Ubuntu I could enable desktop effects and simply use my metacity themes.

In Sabayon, when I enable Compiz, it changes my window theme manager to Emerald.
I want to use metacity, not Emerald.
They kept telling me it wasn't possible when I used Compiz effects and Metacity together all the time.

---

### Post by darolu on 2010-02-27
I a terminal (should work with Alt+F2 [if using gnome]):
```
$ metacity --replace &
```

---

