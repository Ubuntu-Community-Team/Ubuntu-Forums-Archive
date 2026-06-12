---
title: "Partitioner cant see free"
date: 2010-05-01
forum: General Help
---

### Post by Satchmo2 on 2010-05-01
Gparted, windows disk management and other partitioners simply will not see the free space I have on C: and thus will not let me resize it. They say 0 kb free, which isn't true as win explorer shows nearly 100 gigs. Also,chkdisk wont run on boot(I've told it too in cmd prmt but it just won't for some reason). Help appreciated.

---

### Post by Satchmo2 on 2010-05-01
bump

---

### Post by krismatth3 on 2010-05-01
That windows shows you free space does not mean the disk can be resized. The partitioning tool need a single block of free space, not many small blocks. Can you try defragging your windows partition? (within windows, run "dfrg.msc" or search for "defrag")

---

### Post by ankspo71 on 2010-05-01
I don't exactly know how to help so I'll post some links.

The chkdsk command parameters available when you are using the Recovery Console:
[http://technet.microsoft.com/en-us/library/bb491051.aspx](http://technet.microsoft.com/en-us/library/bb491051.aspx)

From inside a running windows OS (XP), I think the command parameters would be.
chkdsk -f 
chkdsk -r
chkdsk -x
Edit: I found them here:
[http://technet.microsoft.com/en-us/library/bb490876.aspx](http://technet.microsoft.com/en-us/library/bb490876.aspx)

chkntfs might also help schedule a chkdsk.
[http://technet.microsoft.com/en-us/library/bb490877.aspx](http://technet.microsoft.com/en-us/library/bb490877.aspx)

The only other partitioner that I liked using was:
EASEUS Partition Master  (Freeware for Windows)
[http://www.snapfiles.com/get/easeuspartitionman.html](http://www.snapfiles.com/get/easeuspartitionman.html)
I have successfully used this before, back when I was a windows user and wanted a separate partition for file storage. Make sure there are no errors before using it though.

---

