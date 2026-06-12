---
title: "out of memory!"
date: 2011-08-10
forum: General Help
---

### Post by itba on 2011-08-10
hi,
I am trying to run a simple perl program that requires getting stock price data from yahoo for just 1 ticker symbol, and it was running fine till this morning, wherein it froze and displayed the message 
Out of memory!

I cleared my cache by running the following:
```

$sync
$sudo echo 1 |sudo tee /proc/sys/vm/drop_caches
$sudo echo 2 |sudo tee /proc/sys/vm/drop_caches
$sudo echo 3 |sudo tee /proc/sys/vm/drop_caches


```but it hasn't helped.
Even Firefox has been freezing, so I basically cannot do anything on my computer.

can you please let me know how I can fix it? thanks!

---

### Post by Basher101 on 2011-08-10
run your system monitor and look if a proccess is taking up all the memory

---

### Post by itba on 2011-08-10
I just ran that and with everything else closed, the perl program itself takes up 92% of memory...

---

### Post by itba on 2011-08-10
aha, it was a memory leak in the program itself....thanks for the tip :p

---

