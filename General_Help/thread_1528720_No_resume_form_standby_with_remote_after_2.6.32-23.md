---
title: "No resume form standby with remote after 2.6.32-23 #37 Kernel version"
date: 2010-07-11
forum: General Help
---

### Post by alanwww1 on 2010-07-11
With latest Ubuntu kernel upgrade (2.6.32-23 #37) i lost the ability to resume the computer from standby WITH the Vista Remote. With the power button it resumes perfectly. It seems that somehow the receiver does not get enough power to receive the signals.

Reverting back to kernel 2.6.32-22 immediately solves the problem.

I tried it with two different hardware and two different installations with the SAME results. 

Has anyone experienced this ? Is it the same situation with other remotes ?
Has anyone having resume with remote with 2.6.32-23 #37 kernel version.

You can check the kernel version with 

```
uname -r -v
```

Please give me some feedback to confirm this problem so that i can start an Ubuntu BUG report.

Cheers, Alan

---

