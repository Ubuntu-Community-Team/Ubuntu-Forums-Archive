---
title: "Firefox - Window not responding"
date: 2010-07-17
forum: General Help
---

### Post by pickarooney on 2010-07-17
Every time I click on the button to close Firefox I get a warning message saying the window is busy and not responding and asking if I want to shut the application.It disappears after about three seconds.

This happens even in safe-mode with one tab open.It's version 3.0.19 on Jaunty.

---

### Post by lovinglinux on 2010-07-17
Your Firefox could be trying to perform heavy functions on shutdown. Do you have any extensions installed?

---

### Post by pickarooney on 2010-07-18
I hve a few normally, but it also happens in safe-mode with everything disabled.

---

### Post by lovinglinux on 2010-07-18
Try to create a new FF profile and see if the problem persists.

Start Firefox the profile manager:

```
firefox -P
```

If the new profile works fine, then see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

