---
title: "Ps and grep"
date: 2012-01-16
forum: General Help
---

### Post by Joundill on 2012-01-16
Hi all,

I was just trying to grep the output of ps,
```
ps aux | grep public@10.129.128.1
```
retrieved two processes,
mrtg and grep.

Now, I don't want to have grep showing up as a process, so I've changed my command to be
```
ps aux | grep -v grep | grep public@10.129.128.1
```

Is there a better way to do this?

Cheers,

Joundill

---

### Post by Vaphell on 2012-01-16
try pgrep
[http://linux.about.com/library/cmd/blcmdl1_pgrep.htm](http://linux.about.com/library/cmd/blcmdl1_pgrep.htm)

---

### Post by Joundill on 2012-01-16
Neat, cheers.

---

