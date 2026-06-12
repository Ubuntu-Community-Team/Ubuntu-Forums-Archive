---
title: "recently created folders 'corrupt'"
date: 2006-03-23
forum: General Help
---

### Post by Burke on 2006-03-23
Hi, I'm running Ubuntu 5.10, and as of today, Windows XP.

I installed the ext2 driver for windows, and it seems to think that every directory I've created in the last month or so is corrupt, and won't open. My mp3 player agrees, as well. Last week I transferred a bunch of music to it, and anything newer than about a month gives me a playback error.

Ubuntu, however, seems to think nothing at all is wrong, and will even open these supposedly corrupt directories. This is the oddest thing that has ever happened to me :-k 

Any idea what could be wrong?

---

### Post by trent dillman on 2006-03-24
Is your Ubuntu install on an ext2 partition or ext3?

---

### Post by Burke on 2006-03-26
Ah, I forgot I posted this. 

I fixed the problem, all I had to do was run fsck manally. It was something about multiply used inodes or something.

---

