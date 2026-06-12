---
title: "Error when installing gcc 4.5.0"
date: 2010-04-26
forum: General Help
---

### Post by zainka on 2010-04-26
Hi

When installing gcc 4.5.0 I have the following roblemo


```
configure: error: cannot compute suffix of object files: cannot compile
See `config.log' for more details.
make[1]: *** [configure-target-libgcc] Error 1
```


Config.log shows that there are several paths the compiler do nto find. I have though installed build essentials trying to prevent this. Any sugestions 


[QUOTE="config.log"]hostname = v-ubuntu
uname -m = i686
uname -r = 2.6.31-20-generic
uname -s = Linux
uname -v = #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin[/QUOTE]

---

