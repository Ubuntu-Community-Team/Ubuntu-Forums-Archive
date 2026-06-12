---
title: "hwo do I permenentally &quot;export SHELL=/bin/bash&quot;"
date: 2009-12-11
forum: General Help
---

### Post by ant2ne on 2009-12-11
```
ant2ne@lenobuntu:~$ env | grep SHELL
SHELL=/bin/sh
ant2ne@lenobuntu:~$ export SHELL=/bin/bash

```but the next time I load a terminal it is back to /bin/sh. How do I set this permanently?

```
ant2ne@lenobuntu:~$ ls -la ~/.profile
ls: cannot access /home/ant2ne/.profile: No such file or directory

```

---

### Post by falconindy on 2009-12-11
exporting your shell doesn't change it. You need to use:
```
chsh -s /bin/bash
```

---

### Post by ant2ne on 2009-12-11
> **falconindy said:**
> exporting your shell doesn't change it. You need to use:
```
chsh -s /bin/bash
```that didn't work either ;-(

---

### Post by bodhi.zazen on 2009-12-11
> **ant2ne said:**
> that didn't work either ;-(

chsh does not take effect until you start a new shell (log off and back in or open a new terminal).

---

