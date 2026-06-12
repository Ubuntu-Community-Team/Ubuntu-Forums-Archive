---
title: "Ubuntu 11.10 Crazy Slow - Decent Computer - WTH!"
date: 2011-11-08
forum: General Help
---

### Post by KneeDragr on 2011-11-08
System is as follows.
Intel i5 Q2Quad 2.6Ghz
4GB Ram
1TB 7200 RPM Drive
GTX460 Core 216 graphics

Ubuntu 11.10 is ridiculously slow for some tasks. For instance downloading a file brings the whole system down so its virtually unresponsive. Same thing with uncompressing a file - windows grey out, cursor freezes. It took 15 minutes to uncompress a 400mb archive that takes about 20 seconds if I boot into Win7. 

I cant for the life of me figure out WTH is going on. I had Fedora on it before and it ran like butter. 

Help me fix it before I wipe the partition clean and go back!

---

### Post by efflandt on 2011-11-08
Are you running it on its own partition(s) or using Wubi on a Windows partition?

Watch the **Resources** graphs on **System Monitor** and see if they show anything unusual when that happens, like a race condition at 100% or memory leak.

Or make a **bin** directory in your /home/username directory (log out and back in so that ends up in your $PATH) and execute a script from it with the following to see if it is working hard enough to get your cores up to speed (or if they are max'ing out frequently). Ctrl-C to stop it.

```
#!/bin/sh
while [ 1 ]; do
    grep MHz /proc/cpuinfo
    echo
    sleep 1
done
```I have somewhat similar hardware with more RAM, but lower end graphics, and my cores are just idling (mostly 1200 MHz each for 3.2 GHz cpu).

---

