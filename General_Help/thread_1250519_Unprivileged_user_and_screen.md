---
title: "Unprivileged user and screen"
date: 2009-08-26
forum: General Help
---

### Post by supradave on 2009-08-26
I'm trying to set up an unprivileged user that has access to screen.

So I run screen as my unprivileged user:

```
user@mach:~$ screen
Cannot open your terminal '/dev/pts/13' - please check.
```

Which then led me to:
```
ls -l /dev/pts
total 0
crw--w---- 1 usr1 tty 136,  0 2009-08-24 10:29 0
crw--w---- 1 usr1 tty 136,  1 2009-08-24 07:52 1
crw--w---- 1 usr1 tty 136, 10 2009-08-26 12:04 10
crw--w---- 1 usr1 tty 136, 11 2009-08-26 12:22 11
crw--w---- 1 usr1 tty 136, 12 2009-08-26 12:33 12
crw------- 1 usr1 tty 136, 13 2009-08-26 14:10 13
crw--w---- 1 usr1 tty 136,  2 2009-08-24 10:29 2
crw--w---- 1 usr1 tty 136,  3 2009-08-24 12:05 3
crw--w---- 1 usr1 tty 136,  4 2009-08-24 10:29 4
crw--w---- 1 usr1 tty 136,  6 2009-08-26 13:59 6
crw--w---- 1 usr1 tty 136,  7 2009-08-26 14:10 7
crw--w---- 1 usr1 tty 136,  8 2009-08-26 11:24 8
crw--w---- 1 usr1 tty 136,  9 2009-08-26 11:46 9
```

and I can see that /dev/pts/13 doesn't have write permissions.

How do I give my unprivileged user that perm?  (Yes, I know I could just chmod it, but that's not permanent.)

Thanks,
Dave

---

### Post by supradave on 2009-08-26
Nevermind.  Jumped the shark.

---

