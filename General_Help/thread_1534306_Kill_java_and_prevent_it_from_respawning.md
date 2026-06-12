---
title: "Kill java and prevent it from respawning?"
date: 2010-07-19
forum: General Help
---

### Post by Krovas on 2010-07-19
I run Freenet occasionally, but not all the time. Freenet doesn't run unless told to, but Java loads on every boot and sits there and hogs resources for no reason whatsoever. What's worse, as soon as I kill it with fire (sudo kill -9 "PID"), it respawns within seconds.

How do I make Java not load unless required? And die and stay dead when I want it dead?

---

### Post by Krovas on 2010-07-19
Okay, never mind. I have a 95% answer now. I should have just checked the Freenet wiki in the first place.

In case it's of interest to somebody here in the future, running:

```
/freenet/bin/remove_cronjob.sh
```

...will stop Java from loading automatically during boot.


EDIT: Actually...

> /freenet/run.sh stop

...shuts everything down nicely too :rolleyes:

---

