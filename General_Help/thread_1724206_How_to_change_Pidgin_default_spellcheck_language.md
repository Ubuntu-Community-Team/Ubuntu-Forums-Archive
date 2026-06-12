---
title: "How to change Pidgin default spellcheck language?"
date: 2011-04-08
forum: General Help
---

### Post by InnerBushman on 2011-04-08
Hi. I use Pidgin for Gadu-Gadu protocol. I use it almost entirely to communicate with polish people. Each time I open new tab i need to manually change to "polish" from the context menu.

Is there a way to change the default spell check language without changing the environment language? I don't mind if it is some dirty hack or requires recompiling but since I'm not the only one trying to do that some simple tweak solution would be nice.

Bushman

---

### Post by virx on 2011-06-17
I have the same problem ... did you find a solution for it? It must be something similar, when you want to make the first day of week to be Monday. Too bad that Ubuntu does not make those settings by Location...

---

### Post by virx on 2012-03-13
Just in case somebody finds himself with the same problem, then solution was (on estonian) example:
```
update-locale LANG=et_EE.UTF-8 LC_MESSAGES=POSIX
```
You want also to install spelling package...

---

