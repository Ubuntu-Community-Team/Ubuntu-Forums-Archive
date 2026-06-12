---
title: "ls -l Numbers?"
date: 2009-09-02
forum: General Help
---

### Post by wizardfait on 2009-09-02
When using ls -l, it outputs something like:
drwxr-xr-x 2 brandon brandon      4096 2009-09-02 08:22 Desktop
Which is all good and fine, but what does the 2 just after permissions, but before the username?

---

### Post by sisco311 on 2009-09-02
The number of [hard links]("http://en.wikipedia.org/wiki/Hard_link") to the file.

---

### Post by abhilashm86 on 2009-09-02
> **wizardfait said:**
> When using ls -l, it outputs something like:
drwxr-xr-x 2 brandon brandon      4096 2009-09-02 08:22 Desktop
Which is all good and fine, but what does the 2 just after permissions, but before the username?

the number is the hard link count of the specified file...... in this case its 2

---

### Post by wizardfait on 2009-09-02
Ah! Thank you all so very much! :)

---

### Post by Bachstelze on 2009-09-02
For files, it is the number of hard links to the file (including the file itself since it is also technically a hard link). For directories, it's a bit more complicated but basically, it's the number of direct subdirectories plus two (by "direct subdirectories", I mean only subdirectories of the given directory, not sub-subdirectories).

---

### Post by sisco311 on 2009-09-02
> **HymnToLife said:**
> For directories, it's a bit more complicated but basically, it's the number of direct subdirectories plus two (by "direct subdirectories", I mean only subdirectories of the given directory, not sub-subdirectories).

It's not so complicated.
 
Every directory contains two hard links.
. is a hard  link to the current directory and
.. is a hard link to the parent directory.

---

### Post by wizardfait on 2009-09-02
Nvm, Sisco Answered it already. :)

---

