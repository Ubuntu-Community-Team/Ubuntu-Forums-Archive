---
title: "nano question"
date: 2010-02-02
forum: General Help
---

### Post by ziekfiguur on 2010-02-02
Hello people,

I'm trying to get rnano (or nano -R) to write to a named pipe, but if I run `$rnano fifo' nano stops responding because it tries to read from the pipe.
Is there any way to start rnano without it trying to read the file?
I know there is a read-only mode, but I'm looking for a write-only mode :p

In the nano documentation I found this:
> For version 2.2:
...
- Allow nano to work like a pager (read from stdin) [DONE]
in the TODO list, i think this might be what i need but i could not find anything else about it (not even how to use it)

---

