---
title: "waking from Sleep mode Ubuntu becomes non-functional"
date: 2012-04-18
forum: General Help
---

### Post by kkruecke on 2012-04-18
I use 11.04. I've been using Ubuntu for several years. Now, today, after a recent "aptitude full-upgrade" my system isn't really usable if I go into Sleep mode. When it wakes up, its sluggish, non-responsive, the video "tears" in spots. Strange. 

Any ideas?
```
kurt@kurt-natty:~$ uname -a

Linux kurt-natty 2.6.38-14-generic-pae #58-Ubuntu SMP Tue Mar 27 19:06:30 UTC 2012 i686 i686 i386 GNU/Linux

```

---

### Post by MonkeyPaw on 2012-04-18
Were you using the proprietary AMD/ATI drivers by chance? If so, you might need to uninstall and reinstall them. Not long ago a group of updates blank screened me at boot, and reinstalling those drivers fixed it.

If not that, more detail on your hardware and what version of Ubuntu you are running would help.

---

### Post by kkruecke on 2012-04-18
I've been using the same HP pc for the last four years. It never happened before this week.

---

### Post by kkruecke on 2012-04-22
Solution: After resuming from Suspend, do Alt+F2, then "unity --reset"

---

