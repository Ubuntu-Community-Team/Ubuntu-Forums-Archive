---
title: "How to reclaim leaked memory"
date: 2010-10-07
forum: General Help
---

### Post by msknight on 2010-10-07
Hi Folks,

I'm using a program somewhere that is leaking memory. I think it is handbrake but I can't be certain. Even after terminating the programs (I have three instances ripping DVD's simultaneously) there is still a lot of memory not accounted for. (memory used is a gig or so more than the total used by the processes listed)

Is there any way I can reclaim that memory please? Some form of memory flushing system? I've searched but I can't find anything.

---

### Post by WorMzy on 2010-10-07
Are you sure that this memory is in use by an application? [It could just be used for caching]("http://www.linuxatemyram.com/").

---

### Post by msknight on 2010-10-07
Loks like this was it. Went from 3792 used to 2818 used, (buffers went from 629 to 9) but quickly started to climb again. After just five minutes, already back to 3769 again with buffers at 767.

This (on the face of it) is appearing to cause a problem with other things having to swap to disk. Any way to put a maximum cap on this?

---

### Post by WorMzy on 2010-10-07
If it is buffers and caching that's eating your ram, then like the article says: you don't need to worry about it. You can clear the buffers and cache if you really want to, but it won't be of any benefit to you, in fact it'll probably make your system more sluggish.

From [this link]("http://www.linuxatemyram.com/play.html"): 

```
For experimentation, it's very convenient to be able to drop the disk cache. For this, we can use the special file /proc/sys/vm/drop_caches. By writing 3 to it, we can clear most of the disk cache:

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1504       1471         33          0         36        801
-/+ buffers/cache:        633        871
Swap:         2047          6       2041

$ echo 3 | sudo tee /proc/sys/vm/drop_caches 
3

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1504        763        741          0          0        134
-/+ buffers/cache:        629        875
Swap:         2047          6       2041


Notice how "buffers" and "cached" went down, free mem went up, and free+buffers/cache stayed the same. 
```

---

### Post by Cope57 on 2010-10-15
To reclaim unused memory, just run this as root.

```
# sync; echo 3 > /proc/sys/vm/drop_caches
```


**Edit:** Err wait, I forgot...

```
$ sudo sync; echo 3 > /proc/sys/vm/drop_caches
```

---

