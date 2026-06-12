---
title: "cpu throttling 'on demand' threshold?"
date: 2009-06-30
forum: General Help
---

### Post by uschxc on 2009-06-30
I've been trying to figure out why my machine suffers to play flash animations until I realized that the processor cores (2) were getting taxed 25-45% while the cpu scaling was set to on demand but dropped to 5-10 percent when set to performance.  

I've started to notice in other instances throughthe CPU Frequency Scaling Monitor that while in on demande mode, the cpu frequency only goes from 800 mhz to 2.4ghz when both cores are maybe 50%, but definitely 75%+.

is there any way to set what cpu/core usage percentage triggers the on demand mode to scale the cpus to max?

edit:
or, is it possible to make either the on demand or conservative profiles switch both cpus instead of them both independently

---

### Post by t4thfavor on 2009-06-30
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/107545](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/107545)

Check this out, I believe this is your answer.

---

### Post by uschxc on 2009-06-30
thanks i should be able to do the opposite and make mine more aggressive.  i want virtually all my cpu power when anything is going on but while idle or lightweight processing i'd like a lower core speed for heat reasons alone.

---

