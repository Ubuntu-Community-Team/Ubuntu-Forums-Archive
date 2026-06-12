---
title: "kernel scheduler adjustment??"
date: 2009-12-24
forum: General Help
---

### Post by turbozmike on 2009-12-24
Im using 9.10 and having all sorts of issues now, I miss 9.04.
Anyways I play WoW and have some new issues.

I found a wiki that says if you adjust the scheduler with
> echo 21 > /proc/sys/kernel/sched_features
echo 25000000 > /proc/sys/kernel/sched_batch_wakeup_granularity_ns
echo 4000000 > /proc/sys/kernel/sched_min_granularity_ns
that it may help with some of what Im experiancing.
Ive no idea how to do this and the wiki does not specify.
Can I do this in the sysctl.conf?

Ive had nothing but problems with this release.

---

