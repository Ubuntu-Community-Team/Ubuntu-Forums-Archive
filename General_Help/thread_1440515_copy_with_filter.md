---
title: "copy with filter"
date: 2010-03-27
forum: General Help
---

### Post by drorata on 2010-03-27
I thought this would be easy, but it turned into an impossible mission.

Assume that in /path/to/source/ starts a tree structure, which holds many sub-directories, and many different file types. Among them, there are PDFs. I want to copy only the PDFs from the source path to a different path. 

I tried to run the following from /path/to/source/

cp -R *.pdf /path/to/dist/

but it didn't work :)

Any ideas?

---

### Post by jobix on 2010-03-27
Try this:

> find /path/to/source -name "*.pdf" -exec cp {} /path/to/dest \;

---

### Post by drorata on 2010-03-29
I used:

```
find -name \*.pdf -print0 | xargs -0 cp -t target/

```

as suggested by a friend, and it worked. I didn't test the option proposed by *jobix*.

Thanks any way,
Dror

---

