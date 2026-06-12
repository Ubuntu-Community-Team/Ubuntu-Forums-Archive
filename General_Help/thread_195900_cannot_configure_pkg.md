---
title: "cannot configure pkg"
date: 2006-06-13
forum: General Help
---

### Post by metricben on 2006-06-13
i have installed the "setiathome" package, but while configuring it tries to access  a server that is not running.
since this server does not exist anymore, it cannot configure(although it tried for about an hour)
if i try to reconfigure packages i get this:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
ben@benspc:~$ sudo dpkg --configure -a
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--18:20:32--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
           => `/tmp/fileQJppZs'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... dpkg: error processing

```

please help: i want 2 install more packages!!!

thx ben

---

### Post by metricben on 2006-06-13
fixed it

wow the world of a linux n00b

---

