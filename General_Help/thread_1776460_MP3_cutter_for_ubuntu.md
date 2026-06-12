---
title: "MP3 cutter for ubuntu"
date: 2011-06-06
forum: General Help
---

### Post by kanishkdudeja on 2011-06-06
is there any application by which i cut mp3 files in ubuntu?
so that i give the start and the end time and my mp3 gets cut.

---

### Post by nothingspecial on 2011-06-06
audacity will do that with a gui.

Perhaps simpler is sox

```
sox song.mp3 split.mp3 trim 30 120
```

That will take the mp3 file song.mp3 and create a new file called split.mp3 that starts 30 seconds through song.mp3 and ends 120 seconds later.

That can catch you out, the second number is not the end time, it is how many seconds after the start time you want it to end.

---

### Post by kanishkdudeja on 2011-06-06
thanks a lot mate..:)

---

### Post by FerroPower on 2011-07-28
Thanks sox is superb !! it also can trim fraction of second.

---

