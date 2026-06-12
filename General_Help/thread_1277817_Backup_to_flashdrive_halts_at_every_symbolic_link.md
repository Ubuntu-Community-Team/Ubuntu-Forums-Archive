---
title: "Backup to flashdrive halts at every symbolic link"
date: 2009-09-28
forum: General Help
---

### Post by triplemaya on 2009-09-28
I use a large flash drive to back up my current work. The drive is formatted to fat32 so I can read it on all kinds of computer.
The copying stops again and again because it gets to a symbolic link - as in about a hundred times, it's really not workable.
I've looked all through the man page for cp to try to find a way to get the copy command to simply ignore symbolic links, but there's no such option, which I find extraordinary!? I've also googled, and searched the forums, and found nothing. Other people must be having this problem, so I presume I'm searching for the wrong thing. (I've tried searching for 'ubuntu how can I copy to flash drive without symbolic links stopping copy' and all kinds of variations on these words. And I can't find anything on the forums under flash drive, fat32 and symbolic links either)
 Please could someone let me know how to do this.
Thanks

---

### Post by falconindy on 2009-09-28
You can use cpio, in this fashion:
```
find <source> -depth -print0 | cpio --null --sparse -pvd <destination>
```

---

### Post by triplemaya on 2009-09-29
Thanks falconidy

---

