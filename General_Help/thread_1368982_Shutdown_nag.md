---
title: "Shutdown nag"
date: 2009-12-31
forum: General Help
---

### Post by lewmur on 2009-12-31
I don't know about others, but the "nag" box that appears whenever I click to shutdown or restart irritates me.  How can I set the delay time in those boxes to zero?

---

### Post by StuartN on 2009-12-31
> **lewmur said:**
> I don't know about others, but the "nag" box that appears whenever I click to shutdown or restart irritates me.  How can I set the delay time in those boxes to zero?

I do not know if the graphical system configuration editor has caught up with reality yet, but this terminal command should work:

```
gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
```

---

