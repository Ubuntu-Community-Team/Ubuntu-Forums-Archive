---
title: "xbindkeys - simulate mouse click"
date: 2012-08-15
forum: General Help
---

### Post by Lubos on 2012-08-15
Hi all,

i am trying to simulate left mouseclick with xte and xbindkeys. My .xbindkeysrc for my keyboard looks like this:

```
# bind mouse left mouse click to F1
"xte 'mouseclick 1 &'"
m:0x10 + c:67
```

and it works. When i press F1, it send left mouseclick. But it send it onle one simple click, it doesnt recognise, if i am holding F1 down or not, its like one press. I cant select text with it, i cant drag&drop and most important, i need to press F1 again and again, if i want to fire more than one bullet in Counter Strike ;).

So the answer is, how can i use xte to recognise buttondown for simulating mouse buttons?
Thank yoy!

---

