---
title: "Bad Blocks Found In Maintenance Mode. False Positive?"
date: 2012-08-15
forum: General Help
---

### Post by whitecat23 on 2012-08-15
Hello all. First off, I'm using the 64-bits edition of Ubuntu 12.04 (updated enough so that uname shows it to be 12.04.1 as of today). I booted into maintenance mode and chose fsck from the menu. It ran fsck on my volumes (mounting the filesystems in read/write mode by default) and said there were bad blocks detected and that the filesystem had changed (I'm assuming it did some "corrections"). The thing is, I ran a full disk check using smartmon-tools and examined the output afterwards: The SMART tables show a pristine disk with no re-allocated sectors! I then ran the badblocks utility from within my desktop session on all volumes and no errors were detected then, either.
Has anyone had a similar experience? I'm not sure what this means, so can someone please clarify what I saw?
Thanks.

---

