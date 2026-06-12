---
title: "Load averages on a single core with HT"
date: 2011-06-07
forum: General Help
---

### Post by airspoon on 2011-06-07
Hello, I'm new to Ubuntu, having recently installed 11.04. I have a question about load averages and how they pertain to Intel's "Hyper-Threading" technology.

My Ubuntu is running on an older machine with a single core P4 w/ HT. It appears as if Ubuntu is treating this processor as a dual core processor, at least according to the "System Monitor". It shows:
```

Processor0: Intel(R) Pentium(R) 4 CPU 3.00GHz
Processor1: Intel(R) Pentium(R) 4 CPU 3.00GHz

```
 I'm not sure what the "(R)" stands for, anyone? Is that the "step"?

Anyway, I'm sure that applications capable of taking advantage of multi-core CPUs aren't able to squeeze the same performance out of my CPU as they would from a dual-core processor, but it appears as if the system is registering it as a dual-core, which brings me to my question regarding the load averages.

Since the "System Monitor" seems to be reading this processor as a dual-core, could this also be the case for whatever is calculating the load averages?

I'm getting constant load averages around 1.00 and sometimes as high as 2.5. I'm not sure if I should be alarmed, as I'm not sure if < 1.00 is ideal or if it should be < 2.00. How exactly should I interpret the load averages, relative to a single or dual core processor?

Also, am I right to assume that the System Monitor is reading my P4 w/HT as a dual-core, since it is showing both Processor0,1, or is that just a default for 11.04, being that most computers are now multi-core? Am I taking full advantage of the Hyper-Threading and if so, how should I interpret the load averages, as a single-core or as a dual-core?

Thanks.

---

### Post by jramshu on 2011-06-07
Pretty sure the "R" means registered trademark.

I have a p4 ht on my desktop with xp, when I enabled it it showed "new hardware detected" so in short, yes it will show it as a dual core.

---

### Post by airspoon on 2011-06-07
Thanks, but does it just show it as a dual-core or does it also treat it as a dual-core and if it does treat it as a dual core (maybe even if it doesn't), should I interpret the load averages from a single or dual core perspective? 

In other words, if my load averages go above 1.00, should that be okay since I have processor with HT?

Thanks.

---

### Post by jramshu on 2011-06-07
From what I understand it treats it as a dual core and the load averages should be from dual core. Load average should be ok so long as it doesn't consistently run over 2 in the 5 and 15 min intervals. I am pretty sure I'm ok on this. 

I'll have to go back and make sure I am right on this, or maybe a guru can correct me.

---

### Post by airspoon on 2011-06-07
Cool, thanks. That's a pretty good deal then if Ubuntu is treating the HT as an additional core. Do you know of any other way to get a more detailed view of the load averages and how they affect the system?

---

### Post by jramshu on 2011-06-07
You could set up conky to watch each core, cpu averaging, well with it you could watch pretty much anything you want. 
Lots of screen shots showing conky and config files. It really helps looking at them to get some ideas on how to get the look you like.

WARNING: It tends to be addictive!!! LOL!!!

There is also "top" in the terminal. It gives good info also.

---

