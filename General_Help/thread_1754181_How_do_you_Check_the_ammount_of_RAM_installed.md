---
title: "How do you Check the ammount of RAM installed?"
date: 2011-05-09
forum: General Help
---

### Post by princerameses on 2011-05-09
I upgraded from 96 MB to 256 MB and I'm not seeing an increase in speed. I'm using Debian. Thanks.

---

### Post by wilee-nilee on 2011-05-09
> **princerameses said:**
> I upgraded from 96 MB to 256 MB and I'm not seeing an increase in speed. I'm using Debian. Thanks.

In the terminal
free

---

### Post by denver on 2011-05-09
Try the following command in a terminal:

```
free -m
```

---

### Post by K_45 on 2011-05-09
```
sudo lshw -html > results.html && firefox results.html &
```

You may need to:

```
sudo apt-get install lshw
```

---

### Post by cymbaline42 on 2011-05-09
Applications - System Tools - System Profiler and Benchmark.  On the left tab, click Summary and it'll show you how much RAM you have installed.  

If you don't see the System Profiler and Benchmark, you can install it from the Software Center.

---

