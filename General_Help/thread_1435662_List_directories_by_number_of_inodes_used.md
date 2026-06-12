---
title: "List directories by number of inodes used"
date: 2010-03-21
forum: General Help
---

### Post by mrmoney on 2010-03-21
Hi,

I recently used up all my free inodes on my server. I had a bunch of mail messages that were sitting there using up a bunch, so I cleared the postfix queue. That gave me some room.

What I'd like to do, is get a listing of the directories using the most inodes (or containing the most number of files), so that I can find the other culprits.

Basically I want the output of "df -i" but to be able to do it recursively on a specific directory.

Can anyone help a poor sucker out?

Thanks in advance

---

### Post by blueridgedog on 2010-03-21
You could run ```
find /usr/share | wc -l
``` on each directory in / then narrow the search down a bit.

---

