---
title: "Time command"
date: 2010-06-16
forum: General Help
---

### Post by ryansteele on 2010-06-16
Hi, folks - 

Saw an old (locked) thread on this topic, but it doesn't look like things were ever resolved.  ([http://ubuntuforums.org/showthread.php?t=733458](http://ubuntuforums.org/showthread.php?t=733458))

In short, the "time" command doesn't appear to work in any shell other than dash.  The link above discusses its failures in bash; I've confirmed this behavior in tcsh, as well.  

Does anyone know of a fix for this problem or an alternative to "time"?  I'm perfectly happy using the dash-ified version, but users, in general, shouldn't have to come here to find this out.

Thanks!
Ryan

---

### Post by bodhi.zazen on 2010-06-16
use the full path =)

time is a bash builtin

```
~# which time
/usr/bin/time

# using the time "builtin"
~# time -o log ls
bash: -o: command not found

real    0m0.002s
user    0m0.000s
sys     0m0.004s

# time --output=log ls
bash: --output=log: command not found

real    0m0.002s
user    0m0.000s
sys     0m0.000s 

[COLOR=darkred][B]# use the full path

# /usr/bin/time -o log ls

banshee:~# cat ./log
0.00user 0.00system 0:00.00elapsed 200%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+274minor)pagefaults 0swaps[/B][/COLOR]
```

Note: the documentation on this is very obscure, you will need to dig to find it

[http://tldp.org/LDP/abs/html/timedate.html](http://tldp.org/LDP/abs/html/timedate.html)

[http://www.unixguide.net/unix/bash/G4.shtml](http://www.unixguide.net/unix/bash/G4.shtml)

---

