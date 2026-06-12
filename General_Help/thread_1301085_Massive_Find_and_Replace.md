---
title: "Massive Find and Replace"
date: 2009-10-25
forum: General Help
---

### Post by codeking on 2009-10-25
I have a pretty big PHP project I'm doing.  There's a variable that makes an appearance in a large portion of the files, and I have to rename it.  Is there any way I can run a find and replace on every single file in the project's directory? (and it's sub-directories)

---

### Post by sisco311 on 2009-10-25
yep, find and sed should do the trick.

**BACKUP YOUR FILES** :)

```
find /path/to/dir -type f -iname "*.php" -exec sed -i 's/oldvar/newvar/g' '{}' \;
```

try it first on test files.

[uhelp]community/find[/uhelp]
[http://sed.sourceforge.net/sed1line.txt]("http://sed.sourceforge.net/sed1line.txt")

---

