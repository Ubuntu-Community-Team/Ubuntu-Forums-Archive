---
title: "Copying files from nested folders with bash?"
date: 2012-10-03
forum: General Help
---

### Post by bailout on 2012-10-03
I a folder with sub folders. Each of the sub folders contains further folders that contain files of various types. I want to copy all the files into another single folder.

I suspect this is easy with the appropriate bash command but I not sure of the correct syntax. Can anyone help?

thanks

---

### Post by Lars Noodén on 2012-10-03
You should be able to do it with [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html)  This will find all regular files and move them to a single directory.  It won't do anything with the directories themselves that the files were originally in, just [mv](http://manpages.ubuntu.com/manpages/precise/en/man1/mv.1posix.html) the files.

```

find /some/path -type f -exec mv -it /some/other/dir "{}" \;

```

---

### Post by bailout on 2012-10-04
Many thanks Lars. That worked perfectly.

---

