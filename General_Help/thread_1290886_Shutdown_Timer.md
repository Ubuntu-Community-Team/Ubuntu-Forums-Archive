---
title: "Shutdown Timer"
date: 2009-10-14
forum: General Help
---

### Post by slip5789 on 2009-10-14
When I click "Shut Down" the dialogue comes up with "The computer will shut down in 60 seconds" and counts down.  Is there an easy way to edit the timer so it counts down from 20 or 30 instead of 60, and if so, how?

---

### Post by justleen on 2009-10-14
I think its hard coded.. You can disable it by right clicking the power button, and select prefs.
If you need a timer, you could use the shutdown command
```
 sudo shutdown +5 -h 
``` will shutdown after five minutes...
if you need seconds, you could use it with sleep
```
 sleep 30 && sudo shutdown now -h 
```

---

