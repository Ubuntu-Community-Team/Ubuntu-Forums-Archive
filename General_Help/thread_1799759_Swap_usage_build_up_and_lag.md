---
title: "Swap usage build up and lag"
date: 2011-07-08
forum: General Help
---

### Post by The__Doctor on 2011-07-08
When I use Ubuntu for a long time, I start to build up swap usage, and then Ubuntu starts to lag and freeze a lot. This is only really a problem with Firefox 5, which is the highest memory user out of all my running programs. When programs start to use lots of swap, and keep writing to it or reading, the computer starts to lag, I think because the hard disk is too slow to respond to all the read/write requests or something like that. I'm no expert. Anyway, the computer starts to lag and freeze up, but when I close firefox (save and quit) then start it up again, the lag and freezing stops and Ubuntu runs smoothly. Also, my swap usage would've reduced greatly compared to before, e.g. I was using 60% of swap before, then after I closed and reponed Firefox, the swap usage went down to 30%. 

Additional Info: I had a fresh Install from 9.10, then upgraded to Lucid. The problem only started occurring when I upgraded to Maverick, but it wasn't as prominent. Now it's gotten a lot worse. Also, I am using kernel 2.6.32. Any kernel above that (has a higher version number) starts to lag heaps, because of swap usage (I'm pretty sure).

What is the reason for the increase in swap usage and why does the computer lag when swap usage is high?
Also, why are the new kernels more laggy than 2.6.32?

---

### Post by dcstar on 2011-07-08
> **The__Doctor said:**
> 
.......
What is the reason for the increase in swap usage and why does the computer lag when swap usage is high?

[LIST=1]
[*]Probably because a program/process has a memory leak - use the System Monitor to find it.
[*]Because Swap is slow virtual memory.
[/LIST]

---

### Post by The__Doctor on 2011-07-08
> **dcstar said:**
> 
[LIST=1]
[*]Probably because a program/process has a memory leak - use the System Monitor to find it.
[*]Because Swap is slow virtual memory.
[/LIST]

Well how can you tell if there is a memory leak? Also what's the difference between virtual memory, redient memory, writeable memory, shared memory and X-server memory? For Firefox, System Monitor says it's using 700MB of virtual memory, but only 122MB of resident memory and only 97MB of writeable memory. And how do you fix a memory leak?

---

### Post by SeijiSensei on 2011-07-08
How much physical memory does this computer have?

---

### Post by The__Doctor on 2011-07-09
500MB of RAM, 468MB of SWAP. However, my RAM is never used at more than 350MB, and my swappiness is set at 1.

---

### Post by The__Doctor on 2011-07-14
Bump?

---

