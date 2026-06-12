---
title: "Unexplained memory useage"
date: 2010-05-12
forum: General Help
---

### Post by Cavs23 on 2010-05-12
I have been having a problem with the 64bit 10.04. I boot up and am using over 900MB of memory in programs that don't even show on the process list. I first edited my services a week or so ago and it dropped down to 300-400 after boot. But recently it has spiked to 900MB RIGHT after boot. And now I use on average of 1.1-1.3GB whereas before the spike I was using 600-800MB on average. 

How might I solve this?

---

### Post by frostschutz on 2010-05-12
can you post the output of free -m? chances are it's just cache / buffers... which is a good thing (tm)

---

### Post by CharlesA on 2010-05-12
More then likely, it's cached memory, as frostschutz stated.

---

### Post by Cavs23 on 2010-05-12
```


total       used       free     shared    buffers     cached
Mem:          8003       1779       6223          0         74        474
-/+ buffers/cache:       1230       6772
Swap:         6234          0       6234

```

---

### Post by r m h on 2010-05-12
Modern operating systems will try to utilize 100% of your memory with pre-fetching and caching so using 100% of your memory may not mean that you are memory constrained.

Your use of pagefile and/or swap space *may* be a better indicator of your memory constraints but there are waay too many variables to say this with a broad paint brush.

Think about this for a bit.  If your operating system were always using 100% of your RAM by pre-fetching and caching pages that were most likely to be used, your disk i/o would smooth out and you would see a gain in throughput for your system.  On the other hand, if you had lots of free memory your throughput may suffer greatly and you wouldn't be utilizing your system's resources to their optimal capacity.  Remember that disk i/o is thousands of times slower than RAM i/o....

---

