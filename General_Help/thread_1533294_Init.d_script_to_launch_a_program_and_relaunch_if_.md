---
title: "Init.d script to launch a program and relaunch if it crashes"
date: 2010-07-17
forum: General Help
---

### Post by Barry Cent on 2010-07-17
Hi,

I'm trying to setup an init script that will launch a program (on boot) and then relaunch it if the program crashes.

I understand that restarting a crashed program is quite easily achievable using:

```
while true; do <app>; done
```

However I'm not able to work out how I can incorporate this into my init script (modified skeleton script).

I know that this is quite a common question and a simple concept, but I'm not that experienced with scripts, and I haven't been able to find anything on joining the init script and "while true; do" together.

Would someone be able to tell me where I could fit in the "while true; do" idea into a skeleton init script please?

I appreciate everyone's time for looking at this thread.

Thanks,

Joe

---

