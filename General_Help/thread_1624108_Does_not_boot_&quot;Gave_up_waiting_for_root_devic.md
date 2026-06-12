---
title: "Does not boot &quot;Gave up waiting for root device&quot;"
date: 2010-11-17
forum: General Help
---

### Post by papermoon on 2010-11-17
I installed ubuntu netbook 10.10 on my acer aspire one with the "install inside windows" option. The first time it booted into ubuntu properly and completed the installation, then it automatically restarted and now when I try to boot ubuntu, I get the following error message:

```
Gave up waiting for root device. Common problems:
- Boot args (cat/proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules(cat/proc/modules; ls/dev)
Alert! /dev/sbd2 does not exist. Dropping to a shell!
```

---

### Post by papermoon on 2010-11-17
bump

---

### Post by drs305 on 2010-11-17
If you can boot a LiveCD and then run the boot info script from the following site we may be able to see what the problem is. 

After running the script, post the contents of RESULTS.txt in a new post, between 'code' tags. Generate the tags by pressing the post menubar's # icon.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Mark Phelps on 2010-11-17
Know this is going to sound silly ... but have you tried again?

I encountered this for the first time recently, since I installed 10.10.  After searching through solutions (many of which said -- try again), I tried again.  And, it booted OK this time.

---

