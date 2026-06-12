---
title: "Weird error message every 10 seconds in auth.log"
date: 2011-02-20
forum: General Help
---

### Post by mokachoka on 2011-02-20
Feb 20 15:19:53 ss4200 getty[14907]: /dev/tty: cannot open as standard input: No such device or address

Please help! I have no idea what it means.

---

### Post by Habitual on 2011-02-20
In a terminal please:
```
ls -ld /dev/tty
```

paste output here.

---

### Post by mokachoka on 2011-02-20
> **Habitual said:**
> In a terminal please:
```
ls -ld /dev/tty
```paste output here.

crw-rw-rw- 1 root tty 5, 0 2011-02-15 21:50 /dev/tty


If it makes a difference, it is on a headless server.

---

### Post by mokachoka on 2011-02-25
anyone :confused:

---

### Post by mokachoka on 2011-03-01
I really don't mean to keep bumping this but i feel this is the best place to ask... Any thoughts?

---

