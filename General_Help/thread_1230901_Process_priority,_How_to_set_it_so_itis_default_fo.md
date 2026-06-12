---
title: "Process priority, How to set it so itis default for the process"
date: 2009-08-03
forum: General Help
---

### Post by rodh on 2009-08-03
I would like to find a way to Set process priority for a program that tries to hog the cpu time.  If I set it to 3 everything seems to work just fine. but if I leave it at zero sound is spotty at best, and the program runs very slow.  Like maybe a system process that it depends on can't get the cpu time it requires.  Is there anyway to set the priority so that it stays as the default for that program or process.

---

### Post by dcstar on 2009-08-05
> **rodh said:**
> I would like to find a way to Set process priority for a program that tries to hog the cpu time.  If I set it to 3 everything seems to work just fine. but if I leave it at zero sound is spotty at best, and the program runs very slow.  Like maybe a system process that it depends on can't get the cpu time it requires.  Is there anyway to set the priority so that it stays as the default for that program or process.

```
man nice
```

---

### Post by XCan on 2009-08-05
You could create/change a script that starts it with nice, for example,

```
 nice -n3 yourprogram 
```

---

### Post by rodh on 2009-08-05
Thanks,  appreciate

---

