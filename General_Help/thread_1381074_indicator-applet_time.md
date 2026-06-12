---
title: "indicator-applet time"
date: 2010-01-14
forum: General Help
---

### Post by linuxhippy on 2010-01-14
I have installed the ubuntu netbook remix and like it a lot.  I'm trying to customize some things, though.  When I shut down with the indicator-applet it starts a 60 second countdown.  I don't want this-how do I remove the coutdown or set it to 0?

---

### Post by sisco311 on 2010-01-17
> **linuxhippy said:**
> I have installed the ubuntu netbook remix and like it a lot.  I'm trying to customize some things, though.  When I shut down with the indicator-applet it starts a 60 second countdown.  I don't want this-how do I remove the coutdown or set it to 0?

Press Alt+F2 and run:
```
gconf-editor
```

go to apps/indicator-session and select the suppress_logout_restart_shotdown checkbox.

---

