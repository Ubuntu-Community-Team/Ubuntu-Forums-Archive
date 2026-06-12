---
title: "Why Can't I Run  kill  from  .logout ?"
date: 2010-06-23
forum: General Help
---

### Post by Ubuntist on 2010-06-23
Since the OpenOffice quickstarter effectively disables the shutdown and hibernate buttons under Lucid, I put a command into my .logout to kill the quickstarter:```
kill `ps aux | awk '/soffice\.bin/ && (/quickstart/ || /splash-pipe/) {print $2}'`
```

This works fine if I execute it manually, but in the .logout file it seems to have no effect.  What's going wrong?

---

### Post by Paddy Landau on 2010-06-29
I don't think that the .logout file is valid for a GUI context.

I haven't tried this, but have a look at:
[http://www.math.udel.edu/teaching/manual/node34.html#SessionExit](http://www.math.udel.edu/teaching/manual/node34.html#SessionExit)

---

### Post by Paddy Landau on 2010-06-29
I found this, and it works.

[http://ubuntuforums.org/showthread.php?p=1475597#post1475597](http://ubuntuforums.org/showthread.php?p=1475597#post1475597)

---

