---
title: "Nasty memory leak in natty"
date: 2011-10-13
forum: General Help
---

### Post by dining_philosopher on 2011-10-13
Hello!

I have 8gb ram and 16 gb swap (on ssd). After some weeks of uptime this memory gets almost entirely fulfilled (mostly by chrome). But when i close all programs i started, almost half of memory remains filled. For instance, in this case there are 3.5 gb of ram and 6.3 gb of swap (almost 10 gb total):

```
wormball@wormball-desktop:~$ uptime 
 19:32:09 up 42 days, 16 min,  2 users,  load average: 0.00, 0.11, 0.45

wormball@wormball-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       8189276    3510356    4678920          0      62776     478768
-/+ buffers/cache:    2968812    5220464
Swap:     16775164    6303128   10472036

```

However, ksysguard tells me that there are no running programs with comparable memory consumption.

Can i set this memory free? Without rebooting or restarting programs.

Thanks in advance.

---

### Post by elvetemedve on 2011-12-11
I have the same experiance with Natty.
I sum the memory usage reported by System Monitor for all processes. It was 1551 MB, but **free -m** reports 3510 MB as used.

Maybe others are also affected:
[http://askubuntu.com/questions/49608/system-monitor-and-top-reporting-wildly-different-memory-usage](http://askubuntu.com/questions/49608/system-monitor-and-top-reporting-wildly-different-memory-usage)

---

### Post by Bobhuber on 2011-12-11
System Monitor does not include cache and buffered memory and is VERY deceiving as to actual memory available.

This needs to be run as root and won't hurt anything.
Heres the simple batch file that I run to clear cache memory.

clearmem.sh

```
#!/bin/bash
sync &
echo 3 > /proc/sys/vm/drop_caches &
exit 0
```

---

### Post by gennatolls on 2011-12-11
I had similar experiences with natty as well. I have 8gb ram and 8gb swap. A couple times both were completely filled minus 100 mb or so of swap. It occured when using chrome and converting movies in Handbrake. I haven't encountered the issue in 11.10

---

