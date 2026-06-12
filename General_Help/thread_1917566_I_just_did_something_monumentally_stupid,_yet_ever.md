---
title: "I just did something monumentally stupid, yet everything appears to be still working"
date: 2012-01-30
forum: General Help
---

### Post by jgcsd on 2012-01-30
So, I just accidentally deleted /usr/lib64

About 0.5 seconds after I hit enter, I realised what I'd done. I expected Ubuntu to come to a grinding halt. Surprisingly it didn't.

Even more surprisingly, it still worked even when I rebooted. And /usr/lib64 is back!

So have I actually done any damage here? Or am I fine to continue?

---

### Post by Wayne_V on 2012-01-30
do "dpkg --search /usr/lib64" to see which packages install files there directly.

then "dpkg --listfiles <packagename> | grep lib64" to see which files they are.

if you are up and running you are probably OK.   If you find something that doesn't run due to a missing library you can just reinstall that package.

---

### Post by WorMzy on 2012-01-30
/urs/lib64 should just be a symlink to /usr/lib. You should be fine.

---

### Post by hwttdz on 2012-01-30
Can verify, lib64 is a symlink.  So if the system linked it again, you're fine.

---

