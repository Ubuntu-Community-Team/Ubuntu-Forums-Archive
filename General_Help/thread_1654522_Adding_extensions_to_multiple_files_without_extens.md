---
title: "Adding extensions to multiple files without extensions"
date: 2010-12-28
forum: General Help
---

### Post by Fuith on 2010-12-28
I have a directory of a load of files without extensions. I know what the filetype should be, so is there any way of batch renaming the files to append a given extension onto it. i.e. text would be renamed as text.txt? 

Many Thanks.

---

### Post by corncob on 2010-12-28
> **Fuith said:**
> I have a directory of a load of files without extensions. I know what the filetype should be, so is there any way of batch renaming the files to append a given extension onto it. i.e. text would be renamed as text.txt? 

Many Thanks.

You're right!  The rename option is ghosted out when I select multiple files:D  If I wanted to add, for example, the .txt extension to all the files in a directory, I'd cd to that directory in the Terminal and enter
```
mv * *.txt
```

---

### Post by gmargo on 2010-12-28
Use the **rename** command:
```

rename "s/$/.txt/"  file1 file2 file3 ...

```Filling out your "text -> text.txt" example:
```

$ touch text
$ ls -lgG text*
-rw-r--r-- 1 0 Dec 28 12:03 text
$ rename "s/$/.txt/" text
$ ls -lgG text*
-rw-r--r-- 1 0 Dec 28 12:03 text.txt

```

---

### Post by Fuith on 2010-12-28
> **gmargo said:**
> Use the **rename** command:
```

rename "s/$/.txt/"  file1 file2 file3 ...

```Filling out your "text -> text.txt" example:

Worked great, thanks!

---

