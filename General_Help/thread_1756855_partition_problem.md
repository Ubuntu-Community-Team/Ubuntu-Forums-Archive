---
title: "partition problem"
date: 2011-05-12
forum: General Help
---

### Post by pooper on 2011-05-12
Hi all 
I've partitioned my 1tb hd as follows (attachment) 
Can anyone explain why it is saying 14gb has been used on the last partition when in fact that partition is empty and has never had anything saved on to it. also what are all the unallocated bits about?

thanks

---

### Post by Quackers on 2011-05-12
The 1MB unallocated spaces are just to separate the partitions. This is normal nowadays.
Your BigYellowStorage partition is formatted as ext4. Just formatting a partition uses a percentage of the space. Not sure whether it should take 14GB but as it's a BIG partition it could be right.

---

