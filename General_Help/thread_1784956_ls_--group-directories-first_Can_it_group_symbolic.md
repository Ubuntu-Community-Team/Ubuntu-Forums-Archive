---
title: "ls --group-directories-first: Can it group symbolic links to directories too?"
date: 2011-06-17
forum: General Help
---

### Post by vergenzt on 2011-06-17
My home folder contains a mixture of files, directories, and symbolic links to directories (e.g. Documents, Downloads--they're in a different location).  Can the functionality of "ls --group-directories-first" be achieved such that it groups symbolic links at the top, too?

---

### Post by bab1 on 2011-06-17
> **vergenzt said:**
> My home folder contains a mixture of files, directories, and symbolic links to directories (e.g. Documents, Downloads--they're in a different location).  Can the functionality of "ls --group-directories-first" be achieved such that it groups symbolic links at the top, too?

Sure, just add the [COLOR="Purple"]**-L**[/COLOR] Like this ```
ls -l **[COLOR="Purple"]-L[/COLOR]** --group-directories-first
```

From the *ls man pages*```
      [COLOR="Purple"]**-L**[/COLOR], --dereference
              when showing file information for a symbolic link, show informa&#8208;
              tion  for  the file **[COLOR="Purple"][or directory][/COLOR]** the link references rather than for the link
              itself

```

In this case a directory is a type of file.

---

### Post by vergenzt on 2011-06-18
Ahh, thank you very much, good sir.  I was perusing the man page but somehow I missed that.  You are a gentleman and a scholar.

---

