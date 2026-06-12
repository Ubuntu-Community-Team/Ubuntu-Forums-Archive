---
title: "Benchmark software"
date: 2006-05-16
forum: General Help
---

### Post by GoodPanos on 2006-05-16
Is there a software/utility that I could benchmark (i.e. PerformanceTest) Ubuntu installs and in general Linux distros?

---

### Post by az on 2006-05-16
[QUOTE=GoodPanos]Is there a software/utility that I could benchmark (i.e. PerformanceTest) Ubuntu installs and in general Linux distros?[/QUOTE]
The gold standard is to time the compilation of  the same source code with the same compiler on different machines.  That gives you cpu powere and disk i/o in a real-world usage case.

There is other software to simulate disk i/o bottlenecks and so forth, but I forget the name...

---

### Post by grimdestripador on 2007-07-10
I googled here looking for ubuntu benchmarks, and still no answer. The ones I found in synaptic are pretty lame, but for comparing multi-threaded harddrive IO, "tiobench" gives out some serious data. 
```
sudo apt-get install tiobench
```

I'm still searching for a good multithreaded battery benchmark. Like the windows's "Sandra". 
I want to compare a 64 bit 2.4 GHz with a 32 bit 2.8. Using 32 bit threaded apps. Hell, I want it to compare everything, but still havent found the software. Did i mention i want this on a live cd, or atleast installable from a live cd via apt-get.

---

### Post by cmcginty on 2007-08-04
Here are some good CPU benchmark programs in linux for those who are interested.

```

sudo apt-get install crafty
crafty
bench

```

```

sudo apt-get install john
john -test

```

```

openssl speed

```

---

