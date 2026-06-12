---
title: "Running GUI from terminal while SU'd"
date: 2010-08-25
forum: General Help
---

### Post by mastermindg on 2010-08-25
I'm trying to run a script that launches a GUI using DirectFB while su'd as a different user. I probably have to add environmental variables but I'm not sure exactly what to do to get this working.

Here's the error I'm getting:

```
(*) DirectFB/Core: Single Application Core. (2009-06-02 06:26) 
(*) Direct/Memcpy: Using libc memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
```

I'm not getting any errors when launching under my own session.

Any ideas?

---

### Post by LowSky on 2010-08-25
It looks like the other user account need access to /dev/fb0, which it doesn't have.

---

### Post by mastermindg on 2010-08-25
There is no /dev/fb0 device but this doesn't prevent me from logging in under my own session.

---

