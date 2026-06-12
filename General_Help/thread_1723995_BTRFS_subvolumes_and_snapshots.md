---
title: "BTRFS subvolumes and snapshots"
date: 2011-04-07
forum: General Help
---

### Post by The Cog on 2011-04-07
I decided to try playing with btrfs. I think you could do lots of fancy things with that. One thing puzzles me though - I can make a snapshot or a subvolume the default volume to mount (using btrfs set-default , but how do I then remove that subvolume default so that the base filesystem is the default mount again.

---

### Post by The Cog on 2011-04-07
Oops, never mind. I found out by trial and error.
Given this:```
# btrfs sub list /media/disk/
ID 256 top level 5 path snap1
ID 257 top level 5 path snap2
ID 258 top level 5 path sub1
```
I found that **btrfs sub set 5 /media/disk/** set the default back to the top level.

---

