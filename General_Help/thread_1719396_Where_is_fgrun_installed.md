---
title: "Where is fgrun installed?"
date: 2011-04-01
forum: General Help
---

### Post by rva1945 on 2011-04-01
I followed these guidelines

[http://www.flightgear.org/forums/viewtopic.php?f=35&p=111549](http://www.flightgear.org/forums/viewtopic.php?f=35&p=111549)

Downloaded and ran the script

[http://ubudog.homelinux.net/scripts/downloadinstallfgrun.sh](http://ubudog.homelinux.net/scripts/downloadinstallfgrun.sh)

now I want to run fgrun but

No command 'fgrun' found, did you mean:
 Command 'fbrun' from package 'fluxbox' (universe)
 Command 'grun' from package 'grun' (universe)
fgrun: command not found

In case it is installed, how do I look for that executable file in Ubuntu (10.10)?

---

### Post by seawolf167 on 2011-04-01
If it installed to a location in your $PATH variable, you can find it with

```
which *programname*
```

If that doesn't find it, you can use the *find *command

---

