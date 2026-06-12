---
title: "Firefox locking up"
date: 2010-02-19
forum: General Help
---

### Post by Silvernail on 2010-02-19
After some use, firefox will not restart from the panel or a terminal. Looking in '.mozilla/firefox' I find:
> 
lrwxrwxrwx 1 dave dave       15 2010-02-19 20:55 lock -> 127.0.1.1:+2189

The number at the end changes everytime I remove it.
Is this something trying to get in or something trying to get out? Or what?
This has been going on for a while.

Any ideas, comments? This problem has been addressed in a bunch of thread but no solutions.

Dave

---

### Post by lovinglinux on 2010-02-20
Open System Monitor and kill firefox-bin process if it is running,, before starting Firefox again. If not, then try this command:

```
firefox -P
```

---

