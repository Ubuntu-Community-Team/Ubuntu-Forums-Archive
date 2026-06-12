---
title: "Reporting CPU Speed"
date: 2012-02-28
forum: General Help
---

### Post by d4m on 2012-02-28
This is going to sound strange, but is there a way that when a program checks the CPU specs of the machine that those specs can be purposefully reported with the wrong values?

i.e. could I set some global var to say the processor is 5ghz when its only 3ghz and when a program goes to get the cpu speed, it sees the 5ghz?

---

### Post by jacob.david on 2012-02-28
The simple answer is, no, it is not possible.
This information is stored in /proc/cpuinfo. And the /proc file system istelf is a virtual file system. So you can't change it even as a root.

---

### Post by Gremlinzzz on 2012-02-28
Are you saying your processor is speeding:popcorn:

---

### Post by efflandt on 2012-02-28
As mentioned /proc/cpuinfo is a virtual file, but it is also dynamic to reflect automatically changing cpu speed (for each virtual core) at the moment (ie, with 2 cores and hyperthreading it shows 4 speeds).  So even if you could change it manually, it would soon be overwritten.  To change that (with some multiplier) you would need to hack and compile your own kernel.  Not sure what effect false speed would have on operation (timing errors?) if threads took longer than expected.

If you are curious of how cpu speed varies under different loads, run this script.

```
#!/bin/sh
while [ 1 ]; do
    grep MHz /proc/cpuinfo
    sleep 1
    echo
done
```

---

### Post by fragos on 2012-02-29
My favorite source of detailed info on the processors I'm using comes from the cpufrequtils package install-able with the Software Center. Run cpufreq-info to see what MHz your processors are running at. It also tells what the available frequency steps are and what % of the time it's running at each of those steps. It also tells you governor policy is in use.

dmidecode is also interesting. It provides full system hardware information. It reported CPU frequency at it's highest value but also offered a number for maximum. Fox example my Athlon II 245 X2 is 2.9MHz but the reported max was 3.2MHz. Not sure why. Perhaps it's the theoretical max or represents overclocking potential.

---

### Post by d4m on 2012-03-01
The purpose is to fool a piece of server software which has a throttle down feature in it which requires basically certain base speed * # of player slots = min cpu speed for server software to run.

Putting the server at 8 players reports that you need a 6ghz machine, which is insane.  It probably means that a dual 3ghz is workable but the way the server source is coded it was obviously lacking in some forethought in this department.

Its not looking at the current load reported through top, the software is looking at the specs of the cpu which I figured was stored in some register which could be overwritten or spoofed in some way.

---

