---
title: "Make unison to ignore deleted files"
date: 2011-01-01
forum: General Help
---

### Post by geo909 on 2011-01-01
Hello all,

Does anybody knows if there is a way to make unison
ignore any deleted files from a root?

I demonstrate this question with an example:

I have 2 folders, "folder1" and "folder2". They both
contain the files "file1" "file2". I synchronize 
these folders with unison (they are the roots).

If I add a "file3" in "folder1", I would like unison
to behave normally and copy "file3" to "folder2".

However, if I delete "folder1/file1", I would like 
unison to ignore this deletion and do *not* delete
"folder2/file1".

Would that be possible?

Many thanks in advance

EDIT: The reason I'm not using something like 
> rsync -av folder1/ folder2 is that it
seems that rsync compares the contents of these 
folders *every* time it runs and it can take ages if 
the contents are very large files.

---

### Post by dcstar on 2011-01-02
> **geo909 said:**
> Hello all,

Does anybody knows if there is a way to make unison
ignore any deleted files from a root?

I demonstrate this question with an example:

I have 2 folders, "folder1" and "folder2". They both
contain the files "file1" "file2". I synchronize 
these folders with unison (they are the roots).

If I add a "file3" in "folder1", I would like unison
to behave normally and copy "file3" to "folder2".

However, if I delete "folder1/file1", I would like 
unison to ignore this deletion and do *not* delete
"folder2/file1".

Would that be possible?


Then you do not want to "syncronize", you want to use the "**merge**" function in Unison.

---

### Post by geo909 on 2011-01-02
> **dcstar said:**
> Then you do not want to "syncronize", you want to use the "**merge**" function in Unison.

Hi,

Thanks for you reply! I actually realized that I can get the desired result by just adding the "-a" flag in rsync, but I'll definitely look at the merge function.

Thanks again.

---

