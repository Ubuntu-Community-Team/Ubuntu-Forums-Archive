---
title: "how does one discern a physical core from and a logical core?"
date: 2011-01-04
forum: General Help
---

### Post by carolinason on 2011-01-04
how does one discern a physical core from and a logical core? [COLOR="Red"]edit ->[/COLOR] am i to assume the first 0-3 are the physical cores?

```
sam@bogue:~$ cat /proc/cpuinfo | grep 'core id'
core id         : 0
core id         : 1
core id         : 2
core id         : 3
core id         : 0
core id         : 1
core id         : 2
core id         : 3
```

and

```
sam@bogue:~$ cat /proc/cpuinfo | grep 'apicid'
apicid          : 0
initial apicid  : 0
apicid          : 2
initial apicid  : 2
apicid          : 4
initial apicid  : 4
apicid          : 6
initial apicid  : 6
apicid          : 1
initial apicid  : 1
apicid          : 3
initial apicid  : 3
apicid          : 5
initial apicid  : 5
apicid          : 7
initial apicid  : 7

```

---

