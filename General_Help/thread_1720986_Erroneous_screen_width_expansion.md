---
title: "Erroneous screen width expansion"
date: 2011-04-03
forum: General Help
---

### Post by Thrasyllus on 2011-04-03
At random moments - about once a month - I boot up and find that everything on screen is expanded along the horizontal axis. For example, the little circle with a whirly pattern (the signal that tells me to wait while something loads) becomes an ellipse elongated horizontally. This has happened again tonight; I rebooted several times and the screen remains expanded the same way. The last time this happened everything returnd to normal after a few reboots, but again it was a random event. What can I do to correct this?

---

### Post by matt_symes on 2011-04-03
Hi

Start by making a copy of your (case sensitive)

```
/var/log/Xorg.0.log
```

file when it happens. Compare and contrast it against a successful bootup log file and look for differences. 

Try to eliminate the monitor as the culprit by using another for a couple of months if possible.

That would be my starting point.

It's hard to know how to fix it until you know what causes it. It's quite possible that someone here will have seen it before and offer you a solution.

Kind regards

---

### Post by Thrasyllus on 2011-04-03
Thank you Matt.

---

