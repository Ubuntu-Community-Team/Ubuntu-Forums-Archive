---
title: "bash - putting string in file (file is variable)"
date: 2011-05-28
forum: General Help
---

### Post by kamaji792 on 2011-05-28
OK I have a simple script that does:
```
# Create temporary file:
pwFile="~/Tmp/temp.cnf"
echo "$password" > "$pwFile"
```

But I get an error message:
```
~/Tmp/temp.cnf: No such file or directory
```

What am I doing wrong?

---

### Post by kamaji792 on 2011-05-28
OK I worked out what the problem was.  It did not like the tilde character in the file name.

So this worked:

```
pwFile="/home/kamaji/Tmp/temp.cnf"
echo "$password" > "$pwFile"
```

---

### Post by AlphaLexman on 2011-05-28
For an explanation, see [tilde expansion]("http://wiki.bash-hackers.org/syntax/expansion/tilde").

---

### Post by Jose Catre-Vandis on 2011-05-28
You can also use **$HOME** instead of **~**

---

