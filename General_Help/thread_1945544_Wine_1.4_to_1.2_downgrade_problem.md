---
title: "Wine 1.4 to 1.2 downgrade problem"
date: 2012-03-23
forum: General Help
---

### Post by NilPointer on 2012-03-23
I've upgraded to wine 1.4, but it seemed a bit slow to me, so I wanted to get 1.2 back.

I removed package wine1.3 (which is actually 1.4), then reinstalled wine1.2, but... Apparently, something went wrong. Main problem is that all applications start extremely slowly (winecfg appears after few minutes from launch). On drives tab it says it can't connect to mount manager. In processes, there's wineboot.exe which wasn't there before, as I understand, it shouldn't run constantly (it should prepare environment at wine start?), but it doesn't seem it's going to exit.

Is there any way to downgrade? I thought to completely remove (purge) wine and installing it again, but I'm afraid it will kill registry and other settings.

---

### Post by zombifier25 on 2012-03-23
Upgrading/downgrading between Wine version will cause problem (personal experience at least). (IMHO Wine 1.4 works better than 1.2, so I see no reason to downgrade) Try renaming/removing the .wine folder and start winecfg and see if that solves the problem.

---

### Post by NilPointer on 2012-03-23
Well, that solved problem. Thanks...

---

