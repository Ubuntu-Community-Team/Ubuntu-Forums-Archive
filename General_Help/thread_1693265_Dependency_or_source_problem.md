---
title: "Dependency or source problem?"
date: 2011-02-22
forum: General Help
---

### Post by layers on 2011-02-22
Hey, I was trying to compile a program taken from a debian machine, and I get "error: glib.h: No such file or directory" , so I tried installing libglib2.0-dev from Synaptic, but all I get is "libglib2.0-dev:
  Depends: libglib2.0-0 (=2.24.0-0ubuntu4) but 2.24.1-0ubuntu1 is to be installed". When I search for 2.24.0, the screen is empty. Am I missing something?

---

### Post by layers on 2011-02-22
Alright I managed to install libglib2.0-dev, but when I'm compiling the program with CodeBlocks, it still says libg.h not found. In terminal, it works. Why is there a difference, and how do I make CodeBlocks work?

---

### Post by TeoBigusGeekus on 2011-02-22
I think there is an option in Codeblocks to include any extra headers when compiling.
Find the header with
```
find / -name glib.h 2>/dev/null
```
and add it to codeblocks compiling preferences.

---

### Post by layers on 2011-02-22
> **TeoBigusGeekus said:**
> I think there is an option in Codeblocks to include any extra headers when compiling.
Find the header with
```
find / -name glib.h 2>/dev/null
```and add it to codeblocks compiling preferences.
Thanks a lot. Now glib is not the problem.

---

