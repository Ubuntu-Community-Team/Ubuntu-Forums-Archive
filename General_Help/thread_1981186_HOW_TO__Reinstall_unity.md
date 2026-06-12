---
title: "HOW TO : Reinstall unity?"
date: 2012-05-16
forum: General Help
---

### Post by bpb101 on 2012-05-16
how do i fully unistall unity and then reinstall it

---

### Post by jerome1232 on 2012-05-16
There may be an easier solution, depending on what your actual problem is.


This resets all of compiz to default, and Unity to default settings.
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
unity --reset
unity --reset-icons
```

---

### Post by cortman on 2012-05-16
Info [here]("http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity").

---

### Post by bpb101 on 2012-05-16
this is the problem 
i tryed the ask ubuntu link and it didnt work , but it did get me the video lenes but my scrolling problem has go worst
[http://www.youtube.com/watch?v=aGOnUa0o40o](http://www.youtube.com/watch?v=aGOnUa0o40o)

---

