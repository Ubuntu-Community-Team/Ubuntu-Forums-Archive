---
title: "Adobe Air on 64 Bit Meerkat"
date: 2010-11-28
forum: General Help
---

### Post by vissud on 2010-11-28
I've tried every guide out there to install Adobe Air to no avail.  Where I am at now is, all the 32 bit dependencies one can think of are installed.

When I run ./AdobeAIRInstaller it hangs. Doing an strace I find it spawns a "setup" program out of a tmp directory created each time the installer runs.  Running strace on this process, just finds it spinning with this message:


```
gettimeofday({1290967033, 342669}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0 (Timeout)
gettimeofday({1290967033, 342724}, NULL) = 0
gettimeofday({1290967033, 342748}, NULL) = 0
gettimeofday({1290967033, 342773}, NULL) = 0
read(3, 0x9113d98, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1290967033, 342826}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 49) = 0 (Timeout)
gettimeofday({1290967033, 391944}, NULL) = 0
read(3, 0x9113d98, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
```


And thats where I am.. Anyone have any ideas?  And thanks!

---

