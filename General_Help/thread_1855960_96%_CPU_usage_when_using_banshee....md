---
title: "96% CPU usage when using banshee..."
date: 2011-10-07
forum: General Help
---

### Post by switch10 on 2011-10-07
I recently switched from Rhythmbox to Banshee, just because it works much better with album art.  I love Rhythmbox otherwise, and I wish I could continue to use it.

When I use the search feature in Banshee, or simply skip a song, the CPU usage jumps to 96+% and there is a huge delay, which makes it practically unusable.  

I've installed sqlite3 and ran the following with little to no change in performance.
```
sqlite3 ~/.config/banshee-1/banshee.db "vacuum; analyze;"
```

I am running a dell mini 9 with 2gb of ram, and an atom processor, on Ubuntu 11.04.

Does anyone have any ideas why Banshee is so sluggish, and what I can do to help/fix the issue?

Thanks,

Dave

---

