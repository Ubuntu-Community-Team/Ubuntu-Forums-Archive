---
title: "kswapd0 maxing CPU"
date: 2009-11-05
forum: General Help
---

### Post by Mazin on 2009-11-05
Since I upgraded to karmic, I've found that kswapd0 likes to constantly take up 100% (out of 400%) CPU.  Needless to say, this shouldn't be happening even when I'm doing nothing, and I can't figure out how to fix it besides rebooting.  I think it might appear only after I've suspended my computer.

Anybody else having the same problem??

```
Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```

---

### Post by daemacles on 2009-11-17
Yes, I'm having the exact same problem.  Very frustrating to have to reboot just to get rid of it when working on many different things.  This happened once before, a year or two ago, but an updated kernel fixed things.  Looks like there is a regression.

Linux raes 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

---

### Post by HuckleSmothered on 2009-11-18
I'm having what appears to be the same problem.
I, also, have no swap space.
Just started happening today but have been using Karmic for over 2 weeks.


Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by guaka on 2009-12-02
[https://bugs.launchpad.net/ubuntu/+bug/484045](https://bugs.launchpad.net/ubuntu/+bug/484045)

---

