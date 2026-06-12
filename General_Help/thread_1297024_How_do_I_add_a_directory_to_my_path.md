---
title: "How do I add a directory to my path?"
date: 2009-10-21
forum: General Help
---

### Post by mazz0 on 2009-10-21
How do I add a directory to my path?  You know, so I can run commands without having to type the full path to the executable.  And is there some reason I shouldn't do this, and should do something else instead, like creating shortcuts in a directory that's already in the path, or something?

---

### Post by JKyleOKC on 2009-10-21
If the directory you want to add is "bin" inside your home directory, this line will do it:
```
PATH="$PATH:$HOME/bin"
```
Actually, I copied the line from the hidden ".profile" file in my home directory; it executes automatically if the "bin" subdirectory exists.

---

