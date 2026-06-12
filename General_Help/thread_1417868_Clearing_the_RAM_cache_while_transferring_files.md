---
title: "Clearing the RAM cache while transferring files"
date: 2010-02-27
forum: General Help
---

### Post by blueshiftoverwatch on 2010-02-27
Just out of curiosity. What would happen if I [cleared]("http://www.scottklarr.com/topic/134/linux-how-to-clear-the-cache-from-memory/") the RAM cache while in the middle of copying a large file from an internal to an external hard drive?

Would the transfer process get buggered up because chunks of the file that were next in line to get transferred would no longer be stored in the RAM? Or would Linux be smart enough (since Ext4 is a journaled file system) to just re-copy the missing chunks that were next in line from the HD to the RAM where they would await transfer to the other hard drive as they were before, as if nothing had happened?

---

### Post by johngreth on 2010-02-27
There is one way to find out...

---

### Post by blueshiftoverwatch on 2010-02-27
> **johngreth said:**
> There is one way to find out...
I was going to attempt it if nobody responded. The only reason I didn't was because I'm currently transferring about 500GB worth of files from one drive to another and didn't want the 2.5 hours I have left to find out.

Edit: After re-reading that I've come to the conclusion that the information age has made us more impatient than ever before.

---

### Post by dcstar on 2010-02-27
> **blueshiftoverwatch said:**
> Just out of curiosity. What would happen if I [cleared]("http://www.scottklarr.com/topic/134/linux-how-to-clear-the-cache-from-memory/") the RAM cache while in the middle of copying a large file from an internal to an external hard drive?
........

You would force copying the same data that was already cached again from the source hard drive - thus wasting more time for a process bound by the write speed of the destination drive.

You may get the illusion that the copy process has speeded up - probably because some indicator now shows the cache filling up again quite quickly - but this is just an illusion because once the cache fills again the rate will drop to the exact rate that the cache empties.

People complain that "my system runs slow when I am copying lots of data", well Der Fred, of course it will.

When all the RAM is fully committed to running apps and is already caching masses of data for copying, then there won't be any more room in RAM until another process is swapped out OR some of the cache clears by being written to the destination disk - both things require disk writes and take time, but will eventually happen.

Perhaps the kernel should automatically trash part of the cache to allow RAM for loading apps, but that can be tricky to work out as an app can start using a lot more RAM as it loads and runs and that may result in continual sacrifice of cache which the kernel has to decide what can actually be discarded and what must be kept - all in real time.

---

### Post by blueshiftoverwatch on 2010-03-07
Thanks for that detailed explanation.

---

