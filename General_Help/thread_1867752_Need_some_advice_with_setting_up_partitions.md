---
title: "Need some advice with setting up partitions"
date: 2011-10-23
forum: General Help
---

### Post by Jiggle156 on 2011-10-23
Hi,  I'm getting a 120GB SSD soon - and I need some help setting it up. I intend to use Ubuntu 11.10 as my primary operating system and windows 7 for gaming (and only gaming - with no file transfers between the two.) How should I partition my SSD? I heard that you need to split your Ubuntu partition into about four or five sections :/   When I get my second SSD, will setting things up in raid 0 be simple?  thanks in advance

---

### Post by dino99 on 2011-10-23
thats my way:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

About winblow i beleive that it need the first partition on the disk, ubuntu can be installed where you want, it doesn't matter.
(note: not fully sure about winblow as i've dropped it since 2005 :))

---

### Post by dFlyer on 2011-10-23
Unless your running a server you only need / (root), /home and swap partitions. A separate /home partition makes it easier when you dist-upgrade or reinstall using a live desktop cd/dvd.

---

### Post by raja.genupula on 2011-10-23
> **dFlyer said:**
> Unless your running a server you only need / (root), /home and swap partitions. A separate /home partition makes it easier when you dist-upgrade or reinstall using a live desktop cd/dvd.

+1 I support this

Install the Ubuntu in the normal procedure , thats gonna make it.No need to all the stuff like creating space for different dir's.

---

