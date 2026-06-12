---
title: "rm problem"
date: 2010-06-03
forum: General Help
---

### Post by lyovushka on 2010-06-03
Hi guys,

I have a dual boot setup with Ubuntu 10.04 and Windows. I was cleaning up my ntfs partition the other day. I removed 1.3G file from command line, but according to df -h the size of partition didn't change. Now neither Ubuntu nor Windows can see the file, but the memory is not freed. Any ideas?

---

### Post by ajgreeny on 2010-06-03
I presume you mean the free space did not change; the partition size will not change just because you removed 1.3GB of files from it.

---

### Post by pricetech on 2010-06-03
You're also not freeing memory, just hard drive space.

---

### Post by lyovushka on 2010-06-03
Yes, you are right. I mean free space didn't change.

---

### Post by lyovushka on 2010-06-03
Solved! After running all partition tools I know (ntfsfix, testdisk from Linux, chkdsk from Windows) n times, I found found.000 directory with some file of approximately 1.3G. I presume that is the file I am looking for

---

