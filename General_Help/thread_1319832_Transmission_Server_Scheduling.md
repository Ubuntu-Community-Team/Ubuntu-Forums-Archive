---
title: "Transmission Server Scheduling"
date: 2009-11-08
forum: General Help
---

### Post by themagicmanfromtrent on 2009-11-08
I'm trying to get the transmission daemon on my server to only download during btween the times of 11pm and 7am, but the code is completely ignoring me.

What am I doing wrong here?

```
    "alt-speed-down": 1,
    "alt-speed-enabled": 1,
    "alt-speed-time-begin": 420,
    "alt-speed-time-enabled": 1,
    "alt-speed-time-end": 1380,
    "alt-speed-up": 1,
```

---

### Post by themagicmanfromtrent on 2009-11-11
I solved this by updating from 1.51 to 1.75.

Either there was a bug, or the scripting changed between the versions.

---

