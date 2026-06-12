---
title: "Software Centre doesn't let me download anything"
date: 2010-03-12
forum: General Help
---

### Post by coldfusion92 on 2010-03-12
Every time i try to get anything from the software centre i get this message:
The action would require the installation of packages from not authenticated sources.

It was working fine, but i updated ubuntu, using the update manager and since then the software centre has stopped working.

There are a few suggestions around but none of them seem to work for me.

Please help me.
Thanks in advance.

---

### Post by plucky on 2010-03-12
> **coldfusion92 said:**
> Every time i try to get anything from the software centre i get this message:
The action would require the installation of packages from not authenticated sources.

It was working fine, but i updated ubuntu, using the update manager and since then the software centre has stopped working.

There are a few suggestions around but none of them seem to work for me.

Please help me.
Thanks in advance.

From a terminal ```
sudo apt-get update
sudo apt-get upgrade
``` 

and if that doesn't work,post the output to the forums of ```
cat /etc/apt/sources.list
```

Good Luck

---

