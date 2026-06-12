---
title: "SysRq+REISUB hangs at &quot;resetting&quot; (without actually resetting/restarting) in Maverick"
date: 2011-03-19
forum: General Help
---

### Post by andrei_1 on 2011-03-19
I'm trying ALT+SysRq+REISUB to see how it would be used to restart my system safely in case of emergency.

However, I find that ALT+SysRq+REISUB hangs at "resetting" (without actually resetting/restarting) in Maverick.

All other SysRq combinations appear to work correctly (i.e. ALT+SysRq+REISU).

cat /proc/sys/kernel/sysrq returns 0. But I'm not sure it's relevant because ALT+SysRq certainly works.

What can I do to have "B" actually restart the system?

Thanks!

---

### Post by ajgreeny on 2011-03-19
I had the same problem and I found by trial and error that REISUO seems to work.  I have no idea what is going on, but give it a try and let us know.

By the way, I assume you mean **AltGr+SysRq+REISUB** (or O), not just SysRq

---

### Post by andrei_1 on 2011-03-19
> **ajgreeny said:**
> I had the same problem and I found by trial and error that REISUO seems to work.  I have no idea what is going on, but give it a try and let us know.

By the way, I assume you mean **AltGr+SysRq+REISUB** (or O), not just SysRq

Thanks for pointing out the missing ALT, I have now corrected my initial post.

O does not shut down my system. Anyway, it would not make a difference to my current situation (where I shut down the system manually when at "resetting" - and I assume it's safe anyway to shut it down at this stage). I just wanted to avoid shutting down the system.

---

### Post by Hakunka-Matata on 2011-08-14
> **andrei_1 said:**
> I'm trying ALT+SysRq+REISUB to see how it would be used to restart my system safely in case of emergency.

However, I find that ALT+SysRq+REISUB hangs at "resetting" (without actually resetting/restarting) in Maverick.

All other SysRq combinations appear to work correctly (i.e. ALT+SysRq+REISU).

cat /proc/sys/kernel/sysrq returns 0. But I'm not sure it's relevant because ALT+SysRq certainly works.

What can I do to have "B" actually restart the system?

Thanks!


[http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf](http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf)

---

