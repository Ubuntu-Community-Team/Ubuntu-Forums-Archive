---
title: "[64 bit] Upgrade 9.10 -&gt; 10.04, desktop effects freezes, if disable comes snow."
date: 2010-05-07
forum: General Help
---

### Post by isia on 2010-05-07
Hello,
have upgraded my kubuntu, after what desktop at random time from login freezes, some times completely, some times for few seconds, after what composing automatically disables.

When i disable desktop effects or when it stops automatically, screen begin randomly fill with pixels... 
Screenshot: [http://isia.kiev.ua/uploads/snapshot2.png](http://isia.kiev.ua/uploads/snapshot2.png)

GeForce GT 220, T ~39-45C
Linux isia-pc 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

Tried to reinstall original nVidia drives, didn't helped. 
Also tried gnome desktop, snow begins after login.

In vesa mode working fine 800x600, and I don't think that is related to video card, it should be big coincidence.

---

### Post by dino99 on 2010-05-07
you should have an app or service with too high activity (see with htop)

sudo dpkg --configure -a

---

### Post by isia on 2010-05-07
Only when effects enabled, and it freezes completely, by sshing on box i so /usr/bin/X was eating 100% of cpu core.

>sudo dpkg --configure -a
No output.

---

