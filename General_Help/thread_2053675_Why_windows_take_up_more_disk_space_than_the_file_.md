---
title: "Why windows take up more disk space than the file size? because of Linux?"
date: 2012-09-05
forum: General Help
---

### Post by northfly on 2012-09-05
I used linux partitioner to creat a disk of 72G for windows.

And then I installed windows 7 on that disk, I formatted that partiton again when installing.

But, after installed, the computer icon disk bar shows that the windows 7 system alone took up 39G disk space. I didn't believe it, and so I go into C: and select all files and right click properties, and found the actual size is 12G.

I believe 12G is the correct one, but why the little bar shows 39G?

Is it because I partitioned the disk from Linux? or else?

Thanks!

---

### Post by HermanAB on 2012-09-05
Deleted files, CD/DVD image files, Swap file, File system journal, System logs...

You could run the Windows cleanup utility to get some space back.

---

### Post by mastablasta on 2012-09-06
are you sure you are looking at Gigabytes in bot GUI? or are one of them maybe Gibibits?
 
[http://en.wikipedia.org/wiki/Gibibit](http://en.wikipedia.org/wiki/Gibibit)

---

### Post by mcduck on 2012-09-06
Difference between GB and GiB wouldn't be that large.

Anyway, Windows directory hierarchy contains plenty of hidden stuff that you can't count in simply by selecting all visible files/directories and looking at their sizes. While 39GB sounds too much for a fresh Windows install, it's more likely to be the correct value for used disk space than the 12GB is. Check for any backups, system restore points, cache files etc. that might be using the space...

(and no, creating the partition in Linux would have no effect on this. Especially since you created the actual filesystem with the Windows installer.)

---

### Post by LewisTM on 2012-09-06
+1
NTFS also reserves space for its Master File Table. The swap file and hibernation file are also sizable hidden system files.

---

### Post by Jerry N on 2012-09-06
> **mcduck said:**
> ....While 39GB sounds too much for a fresh Windows install, it's more likely to be the correct value for used disk space than the 12GB is. ....

Just for information, the "Windows" folder (Win 7)on my primary computer is 12.2 GB but the other files in the partition ("Program Files", "Program Data", "Users", etc) bring the total use of the partition up to 30.1 GB. 

Jerry

---

