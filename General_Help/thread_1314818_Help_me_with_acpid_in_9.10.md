---
title: "Help me with acpid in 9.10"
date: 2009-11-04
forum: General Help
---

### Post by san_terre on 2009-11-04
I had to assign events for my brightness keys in 9.04 in /etc/acpi/events based on some scripts that I had created.  Now that I updated to 9.10 they don't work anymore.

I used enter this to get them to work by restarting acpid -> /etc/init.d/acpid restart

Now when I try to restart acpid I get this:

```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart acpid
acpid start/running, process 2638
```

No big deal, but when I do a restart acpid my previous scrips no longer function.

Any ideas?

Thanks

---

