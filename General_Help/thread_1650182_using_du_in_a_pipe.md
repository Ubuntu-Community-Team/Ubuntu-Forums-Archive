---
title: "using du in a pipe"
date: 2010-12-21
forum: General Help
---

### Post by Eraemaajaervi on 2010-12-21
hi,
i'd like to know the total filesize of all files found with the find command, so

```
find -iname '*.mpg' | xargs -I {} du -sh {}
```
but this gives me the filesize of each file, since each line is passed to "du".

how can I pass the whole list through the pipe?

thanks

---

### Post by psusi on 2010-12-21
Rather than pipe to xargs, just use the -exec switch to find.

---

### Post by Eraemaajaervi on 2011-01-01
i tried ```
find -iname '*.pdf' -exec du -sh '{}' \;
``` but this still doesn't give me the summarized filesize of all files found by $find

---

### Post by sisco311 on 2011-01-01
Try:
```
find path/to/dir -iname '*.avi' -exec du -**c**sh '{}' **+**
```

If you want to list only the total, pipe it to tail:
```
find path/to/dir -iname '*.avi' -exec du -**c**sh '{}' **+** | tail -1
```

EDIT: the same with find & xargs:
```
find path/to/dir -iname '*.avi' -print0 | xargs -0 du -csh '{}'
```

---

### Post by Eraemaajaervi on 2011-01-01
thanks, that did it!

edit: just a question: what does the + do?

---

### Post by AlphaLexman on 2011-01-01
This is Sisco311's exact words from another post:
> -exec command {} \; runs the command once on each matched file.

command file1
command file2
command file3
...

-exec command {} + runs the command on the selected files, but the command line is built by appending each selected file name at the end.

command file1 file2 file3

---

### Post by Eraemaajaervi on 2011-01-02
thanks. all clear now.

---

