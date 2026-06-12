---
title: "Error Mounting Filesystem Which Checking During Boot"
date: 2009-12-14
forum: General Help
---

### Post by ArmchairArmada on 2009-12-14
Before upgrading to 9.10 the filesystem check during the boot process worked just fine.  After upgrading it has never worked.  Because the filesystem check keeps failing (and I have to cancel it with escape) it keeps annoying me ever time I turn my computer on.

Several times I would get this error message and be sent out to a console:

```
General Error Mounting Filesystems 80f-433e-8a9c-fbfeaf8f066b
A maintenance shell will now be started.
Control-D will terminate this shell and retry.
```

I press Control-D, the filesystem check tries again, I hit escape and Ubuntu boots up just fine with no further problems.

What can I do to actually make the filesystem check either work correctly or simply skip the checking all together?

---

### Post by ArmchairArmada on 2009-12-14
Bump.

---

### Post by drewtam on 2009-12-14
I got the same thing. I assumed it had to do with improper shutdown of the computer. But maybe I assumed too much.

Logging in root, and running the file system check manually solved it for me.
"fsck"

My thread is here:
[http://ubuntuforums.org/showthread.php?t=1354453](http://ubuntuforums.org/showthread.php?t=1354453)

---

### Post by ArmchairArmada on 2009-12-14
We did have a black-out a little while back.  I didn't really think of that.  I'll try manually running the check.  Thanks.

---

### Post by ArmchairArmada on 2009-12-14
Thanks.  I guess that's all that needed to be done.  It seems to be much better now.

---

