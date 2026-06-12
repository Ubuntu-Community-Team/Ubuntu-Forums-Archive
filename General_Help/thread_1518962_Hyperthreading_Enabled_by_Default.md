---
title: "Hyperthreading Enabled by Default?"
date: 2010-06-27
forum: General Help
---

### Post by njparton on 2010-06-27
I've come across a few old articles on the web that suggest that hyperthreading isn't enabled by default in Ubuntu.  Some of those articles date back to 2006 so can someone clarify this for Lucid please?

I have an i7 system and would like to make sure it's enabled for when I start folding.

---

### Post by gmargo on 2010-06-27
One way to tell: On the command line, run the "top" command.  Now hit the 1 (one) key, which switches top's display from an aggregate cpu state display to a per-cpu state display.  Your quad-core i7 should show up as 8 cpus if hyperthreading is working.  (Adjust accordingly if you have a newer 2- or 6-core cpu.)

---

### Post by njparton on 2010-06-27
Thanks - it shows 8 cores as it should for an i7 920.

I also ran:

```
dmesg | grep Intel
```

which shows 8 cores too - I should have thought about that before!

---

### Post by delatun on 2011-03-03
A bit late but just came across this. First, wow, enjoy that beast i7 hahaha. 

Another option that I like to use:
```
cat /proc/cpuinfo
```

That way you see the logical processors split with the cache and other cool features you have. I don't have to scroll down too much with my two logicals but you'll have a heck of a time with eight =)

---

