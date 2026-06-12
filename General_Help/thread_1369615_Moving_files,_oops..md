---
title: "Moving files, oops."
date: 2010-01-01
forum: General Help
---

### Post by User0123 on 2010-01-01
I ran nautilus with "sudo nautilus" so I could cut some files from out of my home directory to another location.

These were movies in AVI format, I forgot that when using sudo nautilus if you close the window it halts the transfer. So I have ended up with one of the movies split across two locations. Is there any way to repair this and merge the files back together?

---

### Post by warfacegod on 2010-01-01
Avidemux might work. I've read that it sometimes encodes audio and video out of sync but that shouldn't be a problem for you if you're just sticking two together. Read up on it first though.

---

### Post by Leppie on 2010-01-01
try using cat:
```
cat file1 file2 > outputfile
```

---

### Post by SuperSonic4 on 2010-01-01
Can't you copy the rest of the file over?

I shan't even go into why you were running nautilus as root simply to move a film

---

### Post by User0123 on 2010-01-01
> **SuperSonic4 said:**
> Can't you copy the rest of the file over?

I shan't even go into why you were running nautilus as root simply to move a film


I was copying it to a location which requires root privileges maybe?

---

