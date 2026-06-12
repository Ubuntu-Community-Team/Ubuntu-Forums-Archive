---
title: "How to interpret filefrag results?"
date: 2010-07-17
forum: General Help
---

### Post by sulekha on 2010-07-17
Hi all,

 I executed the filefrag command as follows to get the following results 

filefrag -v g*.html

Filesystem type is: ef53
Filesystem cylinder groups is approximately 448
File size of geomat24-hw.html is 53262 (14 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0  1580089              12 merged
   1      12  1580102  1580100      2 merged,eof
geomat24-hw.html: 2 extents found, perfection would be 1 extent


now what is meant by this extent ?

does it mean that file is stored as 2 fragments ?

---

