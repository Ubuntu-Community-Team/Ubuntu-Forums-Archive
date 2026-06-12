---
title: "man error"
date: 2009-10-05
forum: General Help
---

### Post by PANNY on 2009-10-05
Whenever I try to open a **man** page I get the following error:

```
man: can't execute /usr/bin/most: No such file or directory
man: command exited with status 255: /usr/bin/most -s
```

Any ideas...?

---

### Post by sisco311 on 2009-10-05
*most* is (probably) not installed,
try:
```
sudo apt-get install most
```

But, the default pager in Ubuntu is less.

to select the pager, type:
```
sudo update-alternatives --config pager
```

---

### Post by PANNY on 2009-10-05
Yes, that was the problem. I reinstalled Ubuntu and I forgot I've changed the pager in my old .bashrc. ](*,)

---

