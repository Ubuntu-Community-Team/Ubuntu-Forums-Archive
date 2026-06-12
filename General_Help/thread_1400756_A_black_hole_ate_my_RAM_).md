---
title: "A black hole ate my RAM :)"
date: 2010-02-07
forum: General Help
---

### Post by yeeeev on 2010-02-07
Hi,

I'm seeing something very weird on my current system. the free util reports that I have 1.8G of memory used by programs. when I sum up the memory using "ps avx" or "ps -eF", I get to ~0.7G occupied by processes.
I checked for zombie processes, but found none...

What am I missing?

Thanks in advance!

---

### Post by OrangeCrate on 2010-02-07
This may help...

**Linux Memory Management**

[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

---

### Post by yeeeev on 2010-02-07
It is not an issue related to cache vs. buffer memory.
Here's some output of commands I ran:
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3961       3391        570          0        927        637
-/+ buffers/cache:       1826       2134
Swap:         6565          0       6565
$ ps -eF | grep -v COMMAND | awk '{vsum +=$5;rsum+=$6}END{print vsum,rsum}'
2958183 753164
$ ps avx | grep -v COMMAND | awk '{sum +=$9}END{print sum}'
13.4

```

Thanks in advance!

---

### Post by llawwehttam on 2010-02-07
Have you got an integrated graphics card? It may be eating your ram.

---

### Post by yeeeev on 2010-02-07
Got an external nVidia GeForce 8600M GT

---

### Post by yeeeev on 2010-02-07
Any ideas would be appreciated...:)

---

### Post by yeeeev on 2010-02-08
anyone???

---

