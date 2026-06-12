---
title: "how to ignore the session cache?"
date: 2009-08-19
forum: General Help
---

### Post by silverrope on 2009-08-19
Several times a bad session got stored in cache in which the login was incomplete. I would either get a frozen blue screen before the desktop starts or the desktop login stops just before displaying the panels. To fix this, I had to login under failsafe and delete the files in the .cache/session directory.

In order to avoid this in the future, I would like to start with a completely fresh session every time I login, essentially ignoring the cache. Is there a way in xfce to make that as a default every time I login?

---

### Post by Brandon Williams on 2009-08-20
Open the 'Session and Startup' settings dialog and uncheck the 'Automatically Save Session on Logout' setting.

---

### Post by silverrope on 2009-08-21
> **Brandon Williams said:**
> Open the 'Session and Startup' settings dialog and uncheck the 'Automatically Save Session on Logout' setting.

I did that and I also realised that I should uncheck the "Save session" checkbox on the "Quit" screen. Xfce will still read the session cache on each login but I assume, in principle, the cache will remain empty (is this true?). Anyway, will test this and if so, it should be ok as workaround.

---

