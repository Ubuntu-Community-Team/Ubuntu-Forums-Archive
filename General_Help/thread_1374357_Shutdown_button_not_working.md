---
title: "Shutdown button not working"
date: 2010-01-06
forum: General Help
---

### Post by jvvg on 2010-01-06
I am running Ubuntu in VirtualBox and when I hit the shutdown button, it just logs me out, and when I click it from the login screen, it does nothing.

---

### Post by warfacegod on 2010-01-06
I assume you're talking about the actual power button.

Go to Preferences> Power Managment> General tab> Drag down menu for: When the power button is pressed> select shut down.

If shut down is already selected, select something else then select shut down again.

I have to do this every other week or so and haven't bothered to find a permanent fix for it yet.

---

### Post by llamabr on 2010-01-06
I've never used virtual box, but fyi, the command line to shut down is:

```
shutdown -h now
```

---

