---
title: "Ubuntu bootup error messages"
date: 2011-02-03
forum: General Help
---

### Post by LanguidLegend on 2011-02-03
So everytime I resume Ubuntu from hibernation, it remains black for a time then 2 messages on the screen appear for about 10 seconds before I can log-in:
```
[ 0.556247] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[ 0.556320] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
```
Does anyone know what these mean and how to fix it?

---

### Post by Habitual on 2011-02-03
[http://kerneltrap.org/mailarchive/linux-kernel/2010/12/5/4655062](http://kerneltrap.org/mailarchive/linux-kernel/2010/12/5/4655062)

I'd try another kernel. ;)

---

### Post by LanguidLegend on 2011-02-24
**[bump]**

Still having this issue, has anyone else found a cause or fix for it?

---

### Post by thefasterblueone on 2011-02-24
Seems to be a known bug.

[http://www.google.com/search?client=ubuntu&channel=fs&q=render+ring+head+not+reset+to+zero+ctl&ie=utf-8&oe=utf-8]("http://www.google.com/search?client=ubuntu&channel=fs&q=render+ring+head+not+reset+to+zero+ctl&ie=utf-8&oe=utf-8")

---

