---
title: "Delete certain files"
date: 2010-04-11
forum: General Help
---

### Post by codeking on 2010-04-11
I have an old project I'm digging up and want to add it to version control.  However, it's full of all these junk files.  I want to delete the following files within the project directory and it's subdirectories:

[LIST]
[*]All .DS_Store files and directories
[*]All files starting with "._"
[*]All files ending with ~
[/LIST]

I know regexes, so a single example of one of those would probably be sufficient, and I'll figure out the rest on my own.

---

### Post by falconindy on 2010-04-11
Globbing is sufficient here.

```
rm -r .DS_Store ._* *~
```

---

### Post by codeking on 2010-04-11
That only works within the root directory.  The matching files within subdirectories aren't delete.

---

### Post by falconindy on 2010-04-11
use find, then.

```
find . \( -name '.DS_Store' -o -name '._*' -o -name '*~' \) -delete
```

---

### Post by kgarbutt on 2010-04-11
Hey fal, I'm impressed with your terminal skills, Good job. Ken

---

### Post by codeking on 2010-04-12
Thanks!  With a little tweaking, that did exactly what I wanted to do!

---

