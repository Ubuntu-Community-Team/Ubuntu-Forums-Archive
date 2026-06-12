---
title: "autorun program"
date: 2012-05-04
forum: General Help
---

### Post by williammartindale on 2012-05-04
Ive looked and asked around but can find anything that works... Im trying to get conky to start as any user logs on to the system.

---

### Post by williammartindale on 2012-05-04
I found it... I had to write a script 

```
#!/bin/bash
sleep 5 && conky &
```the sleep 5 is to delay conky from starting always on top of all windows.

I named it conky_start.sh and placed it in /etc/profile.d

---

