---
title: "Adjust the size of partition"
date: 2011-05-06
forum: General Help
---

### Post by wweeks on 2011-05-06
Does anyone know of a way I can adjust the size of a partition in KDE down to the exact size of the files on it so there is no blank space?

---

### Post by dino99 on 2011-05-06
you always need some free (unused) space , lets say 10 % of size partition to be able to work with it

Always resize an unmounted partition, and use tool like kparted or partedmagic

---

### Post by wweeks on 2011-05-06
I want to resize the partition and DD it to into an ISO without wasting a bunch of space in the ISO. Anyway within KDE to resize the partition? And if I use Gparted or any partitioner will it damage my files? I.e. Will it let me adjust the partition smaller than the size of the files on the partition?

---

### Post by dino99 on 2011-05-06
the partition is the container for the files inside, so that partition need at least be not smaller than the total files sum size, otherwise file(s) are damaged/destroyed (logical dont you ?)

---

### Post by wweeks on 2011-05-06
Exactly, but what I'm asking is will Gparted recognize I have files when I adjust  (if I accidentally made it to small) or will it just wipe them?

---

