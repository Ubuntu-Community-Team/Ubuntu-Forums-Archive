---
title: "What does virtual size mean when there is no swap?"
date: 2011-05-23
forum: General Help
---

### Post by whoisit on 2011-05-23
I have an 80GB solid state drive and 6GB of RAM so I decided not to use a swap partition for desktop use.

As far as I know, all swap is disabled. How, then, can virtual size not equal resident size in the 'top' command?

In summary:

There is no swap partition and fstab reflects this
/proc/swaps is empty
free -m shows no swap
top shows no swap
top shows virtual images that are larger than resident images.

Why? How? Is swap really off?


$ cat /proc/swaps 
Filename				Type		Size	Used	Priority


$ free -m
             total       used       free     shared    buffers     cached
Mem:          5974       4669       1304          0        183       3115
-/+ buffers/cache:       1370       4603
Swap:            0          0          0


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                
 4786 root      20   0  214m  83m  31m S    2  1.4   7:50.64 Xorg                                   
 4938 meme      20   0  913m 137m  18m S    2  2.3   7:49.63 compiz

---

