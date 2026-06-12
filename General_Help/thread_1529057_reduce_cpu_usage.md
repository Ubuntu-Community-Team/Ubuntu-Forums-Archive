---
title: "reduce cpu usage"
date: 2010-07-11
forum: General Help
---

### Post by Nonno Bassotto on 2010-07-11
I need to rip my DVDs, an operation which is heavy on the CPU, on my laptop. This makes the temperature rise very quickly, even if the process has very high nice value, and my laptop was already shut off automatically once. Probably there is some bug, since the temperature if often hotter than optimal, but this is really too much (plus these days my room is hot too).

I don't want to ruin anything, so I'd like to put some kind of limit on the CPU usage. Say I don't want any of the two CPUs to go over 70% (a moment ago they were both at 100%, I have paused the process). Is there a way ti d0 this?

---

### Post by TonyFordz on 2010-07-11
I would also like an answer on this question.

Thanks,
Tony

---

### Post by Nonno Bassotto on 2010-07-11
By adding your very useful comment you have actually reduced the odds that someone knowleadgeable will answer, since now the question does not appear amymore in the Unanswered section.

---

### Post by mörgæs on 2010-07-11
This is just guessing, since I have not encountered this problem myself: Can you lower the clock frequency in BIOS? 

Vacuum cleaning the fan and heat-sink might also help.

---

### Post by Nonno Bassotto on 2010-07-11
I'd rather not tinker with the BIOS, unless it is the only viable way.

On the other hand, I just found one can use different governors (usually "performance", "conservative", "ondemand" and "powersave") to choose the policy for the CPU. The available governors can be checked with
```

cat /sys/devices/system/cpu/cpuX/cpufreq/scaling_available_governors

```
and your current governor can be seen with
```

cat /sys/devices/system/cpu/cpuX/cpufreq/scaling_governor

```

**In both cases change X for the number of the desired cpu (0, 1 and so on).**

To set a governor "whatever" for cpu X one can use
```

sudo cpufreq-selector -c X -g whatever

```

I tried this and I set both my cpus to use governor "powersave", but this is maybe too drastic. Now I don't have any overheating anymore, but the video encoding has really slowed down: from ~1hr to ~4hr. There must be something intermediate... On the other hand no noticeable slowing happens for other processes.

Note that the system monitor will still report CPU usage up to 100%; this does not mean it is really used as much as before. I don't know how to measure how much I have actually decreased my CPU usage.

---

### Post by Nonno Bassotto on 2010-07-11
Better yet: all these setting are available in one of the standard gnome applets...

---

### Post by mörgæs on 2010-07-12
Good. Would you tell us which applet...?

---

### Post by Nonno Bassotto on 2010-07-12
I'd be glad, but my interface is localized in italian. Anyway, it is something quite obvious when you browse them. A literal translation would be "Variation of CPU frequency"

---

### Post by mörgæs on 2010-07-12
Thanks. I guess that I found it in my Danish Ubuntu.

---

