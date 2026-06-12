---
title: "Compiz stops working"
date: 2009-08-03
forum: General Help
---

### Post by chmacka on 2009-08-03
Compiz just stops working (like if somebody suddenly switched visual effects to none).

I can't determine if it's something that I do that triggers this. When I log out and log in again, everything is O. K. Compiz is working again and I see all effects.

---

### Post by CatKiller on 2009-08-03
It is possible that something you do is triggering a Compiz crash, which launches the fallback window manager. Obviously, this is not desirable.

Pressing Alt-F2 and running ```
compiz --replace
``` will restart Compiz without you having to log out.

---

### Post by chmacka on 2009-08-03
I'll try compiz --replace next time it crashes.

---

