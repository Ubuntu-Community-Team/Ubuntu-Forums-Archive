---
title: "Ultra slow dockbars"
date: 2010-09-26
forum: General Help
---

### Post by maghoxfr on 2010-09-26
Hi, I'm having lots of issues with dockbars. I was using Gnome Do, with it's docky skin, but it started to run very slow (when I hover the mouse over an aplet it zooms in very slowly), so I switched to AWN, wich for a while was fine but now it takes 1:30 min to load after starting session. Then it works fine but I have a decent pc that should handle a dockbar. I tried it with gnome and lxde, but it did no difference.

My settings:

AMD 6000+, 2Gb RAM, nvidia 8400 GS.
Ubuntu 10.04 with 2.6.31-10-rt kernel.

Thanks

---

### Post by kerry_s on 2010-09-26
the 1's in the repos are old, grab the versions in ppa, there updated regularly.

[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

[https://launchpad.net/~docky-core/+archive/ppa](https://launchpad.net/~docky-core/+archive/ppa)

rt kernel? why? the standard kernel is more updated, so could provide features your missing.
you should also use 64 bit, if your not already.

---

### Post by maghoxfr on 2010-09-26
> **kerry_s said:**
> rt kernel? why? the standard kernel is more updated, so could provide features your missing.
you should also use 64 bit, if your not already.

That's because I work with audio. Buit the general kernel is no difference to my problem of slow dockbars. I guess I should give 64 bit a try.

I'll try those PPA's and post the result.

[EDIT]: the trunk for AWN didn't make any difference either.

It really bothers me because (1) iti didn't happened before and (2) I'm not running a slow machine, it can handle dockbars so there's something I'm missing for sure.

---

### Post by maghoxfr on 2010-09-27
For some reason I had the 173 nvidia drivers installed. I switched back to the proprietary ones (current) and everything's fine now.

Sorry for this post and thanks for the help.

---

