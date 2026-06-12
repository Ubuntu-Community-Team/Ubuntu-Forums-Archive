---
title: "Partition will not defrag"
date: 2009-08-10
forum: General Help
---

### Post by mdharp on 2009-08-10
I have WinXP (audio production) Hardy (audio in wine) & Jaunty partitons installed on one physical hard drive. There is a large NTFS (Not Too F%$#ng Sure) partition for storage & swapping project files between Ubuntu & PC projects. It has become fragmented to the point where JKDefrag & Windows defrag, CHKDSK etc cannot clean it up. See following report from WinXP;

Disk Defragmenter
Volume Projects - D:
Volume size = 97.81 GB
Cluster size = 4 KB
Used space = 42.86 GB
Free space = 54.95 GB
Percent free space = 56 %
Volume fragmentation
Total fragmentation = 17 %
File fragmentation = 34 %
Free space fragmentation = 0 %
File fragmentation
Total files = 38,803
Average file size = 1 MB
Total fragmented files = 115
Total excess fragments = 721
Average fragments per file = 1.01
Pagefile fragmentation
Pagefile size = 0 bytes
Total fragments = 0
Folder fragmentation
Total folders = 6,298
Fragmented folders = 1
Excess folder fragments = 0
Master File Table (MFT) fragmentation
Total MFT size = 49 MB
MFT record count = 46,614
Percent MFT in use = 92 %
Total MFT fragments = 8
--------------------------------------------------------------------------------
Fragments File Size Files that cannot be defragmented
None
N.B. these stats are after a few attempts at CHKDSK, defrags & defrag & optimize attempts.
 
I'm suspicious that loading this volume in Ubuntu & moving & deleting project files may be a crime against Microsoft, punishable by the above mentioned problems. 
Can anyone help out with a fix here.
Any help appreciated & needed.

---

### Post by mikewhatever on 2009-08-10
Why have you decided it can't be defragmented?

According to the report:

Total fragmentation = 17 %

Fragments File Size Files that cannot be defragmented
None

---

