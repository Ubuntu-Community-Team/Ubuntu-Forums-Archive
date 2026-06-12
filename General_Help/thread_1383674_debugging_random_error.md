---
title: "debugging random error"
date: 2010-01-17
forum: General Help
---

### Post by hwttdz on 2010-01-17
So my machine crashed and as far as I can tell it wasn't associated with any particular program.  Is there some log I can investigate to see if I can determine what caused the crash?

---

### Post by cariboo on 2010-01-17
Have a look at syslog, daemon and messages in /var/log.

---

### Post by hwttdz on 2010-01-19
Ok, I've had it happen again now, but the logs are so large that I'm having some trouble figuring out what it might be.  I've started a "watch "date > time_of_crash.txt"", so after it happens again I should be able to tell exactly when it happened.  This is new hardware so I'm worried it's a problem with that.  The hard disks are old, so I don't suspect it's a problem there.  I ran the memory test, which came back clean so I also don't suspect that, so I suppose it might be a motherboard or cpu problem?

---

