---
title: "I want to make sure I have a /swap partition"
date: 2009-07-22
forum: General Help
---

### Post by JP1989 on 2009-07-22
When I installed Ubuntu 9.04, I decided to go with manual partitioning and do 3 of them, / - /home and /swap . But when I was done, it was saying there wasn't any swap partition detected.  Is there a way to check if the one I created is being used and ok?

Thank you.

---

### Post by ibutho on 2009-07-22
You can check whether you have swap by running "free -m". I get
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2004        584       1419          0         21        306
-/+ buffers/cache:        256       1747
Swap:          509          0        509

```
The output shows I have 509MB of swap which is unused. I wonder whether you created a directory called /swap instead of swap space. You can check this by running
```
ls /
```

---

### Post by Cheesemill on 2009-07-22
It sounds like you've created an ext3 partition and mounted it as /swap. This isn't what a swap partition is.

The partition needs to be formatted as type swap not as type ext3. Also a mount point isn't needed (in fact you cannot assign one).

---

### Post by jmszr on 2009-07-22
JP1989,

I did the same thing (/swap); this thread may be of help: [http://ubuntuforums.org/showthread.php?t=1146548](http://ubuntuforums.org/showthread.php?t=1146548) .

---

### Post by JP1989 on 2009-07-22
Thank you, that's exactly what I needed to know and all of you three where useful. Now I have a swap and its a lot better. :)

---

