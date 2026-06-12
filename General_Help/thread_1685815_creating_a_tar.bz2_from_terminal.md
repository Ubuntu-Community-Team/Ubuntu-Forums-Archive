---
title: "creating a tar.bz2 from terminal"
date: 2011-02-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-11
I was making a download option in a script but i cant seem to get the command right
```
tar cjf /tmp/file.tar.bz2 --exclude=\"config\" ./
```my archive ends up with a file-1.tar in it

---

### Post by anglican on 2011-02-11
> **pqwoerituytrueiwoq said:**
> I was making a download option in a script but i cant seem to get the command right
```
tar cjf /tmp/file.tar.bz2 --exclude=\"config\" ./
```my archive ends up with a file-1.tar in itPerhaps you could explain in a bit more detail what you're trying to achieve - it isn't clear to me from this message.

H

---

### Post by pqwoerituytrueiwoq on 2011-02-11
i was/am working on a php script i was making a download a copy script
i wanted to add a link to download the files in the folder i figured i would make a .tar.bz2 with
```
shell_exec("tar cjf /tmp/file.tar.bz2 --exclude=\"config\" ./");
```
every time i open it i get a file-[int].tar in it instead of the files  (the tar contains the files in the tar.bz2) i want them in the top level archive not in a sub archive

---

### Post by pqwoerituytrueiwoq on 2011-02-12
bump

---

