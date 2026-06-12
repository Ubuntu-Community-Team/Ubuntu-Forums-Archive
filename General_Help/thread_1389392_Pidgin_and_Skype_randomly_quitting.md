---
title: "Pidgin and Skype randomly quitting"
date: 2010-01-24
forum: General Help
---

### Post by blueshiftoverwatch on 2010-01-24
I'm using Pidgin, Skype, and the Skype4Pidgin plugin that allows me to IM people on Skype through Pidgin. Because I prefer to have 1 IM window for every conversation, not many.

The only problem is that Pidgin and Skype are constantly quitting. At least once a day one of the IM clients will randomly just stop working. Sometimes it's when I come back to my computer after several hours of being away. Other times I'll be in the middle of typing a message when the process will suddenly drop off the face of the Earth.

Does anyone else have this problem?

EDIT: Options #2 and #3 are the same thing.

---

### Post by LoloftheRings on 2010-01-24
You could run pidgin and skype from terminal to maybe get some error message that might help you along figuring out what the problem might be.

---

### Post by blueshiftoverwatch on 2010-01-24
> **LoloftheRings said:**
> You could run pidgin and skype from terminal to maybe get some error message that might help you along figuring out what the problem might be.
I got this when Skype quit:
```
skype: ../../src/xcb_io.c:176: process_responses: Assertion `!(req && current_request && !(((long) (req->sequence) - (long) (current_request)) <= 0))' failed.
Aborted
```

---

### Post by blueshiftoverwatch on 2010-01-27
I didn't get anything in the CLI when Pidgin quit.

---

### Post by NMFTM on 2010-07-03
I'm getting the same problems when running Skype4Pidgin. I'm also using the OTR plugin, but I don't think that has anything to do with it.

---

### Post by enetic on 2011-01-21
i also have this problem, but i have noticed that its more stable if i run it through terminal. But anyways, its still not a permanent solution... 

please post any progress you have.. 

enetic

---

### Post by enetic on 2011-01-22
As far as I can see now, this is an X error. I just got this error after several hours running in terminal: X Error, request 3, minor 0, error code 3 BadWindow (invalid Window parameter) 

I still dont know how to fix it though.. but im sure its a bug in X.

keep us updated..
enetic

---

