---
title: "Memory usage information"
date: 2011-06-25
forum: General Help
---

### Post by 0x80 on 2011-06-25
Hi , when i recently installed a SysPeek indicator on my Ubuntu 11.04
it tells me that i have 3.2 GiB of ram and 1 GiB is used . 

System monitor tells me the same , but when i use "free" command in terminal
i get different info about memory usage  , it tells me that only 56mb of my ram is currently free .


$ free -m
                 total       used       free     shared    buffers     cached
Mem:          3270       3213         56          0        666       1495
-/+ buffers/cache:       1052       2218
Swap:         3325          0       3325


which one of the above is true ? the System monitor or the "free" output ?? ](*,)

---

### Post by mc4man on 2011-06-25
the 2nd line of free is what you'd look at - the red is used, the blue is available mem
-/+ buffers/cache: [COLOR="Red"]1052[/COLOR] [COLOR="Blue"]2218[/COLOR]

---

### Post by mcduck on 2011-06-25
...and for a bit more detailed explanation, the Linux kernel uses all RAM not used by the OS or running applications to store recently used data in memory, in case it's used again soon (unused RAM is not going to benefit you in any way, so it's better to actually use it for something). The part of the RAM used as cache still counts as free from any program's point of view, as any cached data can simply be dropped if some program needs more memory.

Like mc4man said above, the second line is what you should be reading at when using *free*. The first line includes buffers and cache in used RAM, so after the system has been running for a while it should show pretty much all of your memory being in some use. The second line is what tells the amount of RAM used by your programs, and how much is still available for them.

(so both free and the System Monitor are right, it's just that free is giving you a more detailed view of how the RAM is being used.)

---

