---
title: "what does this do?"
date: 2009-08-19
forum: General Help
---

### Post by BufordPants on 2009-08-19
What does this do to textFile.txt?

sed -i 's/bb+/b/g' textFile.txt

---

### Post by DaithiF on 2009-08-19
Hi,
it replaces occurrences of 'bb+' with 'b' throughout the file.
why thats useful, i'm not sure :)

---

### Post by Bachstelze on 2009-08-19
> **DaithiF said:**
> Hi,
it replaces occurrences of 'bb+' with 'b' throughout the file.
why thats useful, i'm not sure :)

Wrong. It replaces all strings of two consecutive b's or more by a single b.

*EDIT: actually, it depends on your version of sed. GNU sed does indeed behave as DaithiF said (unless the -r flag is used).*

---

### Post by DaithiF on 2009-08-19
not for me it doesn't.  If you escape the + character as \+ then yes, but otherwise + matches literal +

```
dave@hadrian:~/tmp$ cat testfile
bbbline1bb+
line2bbbbb
libne3b
dave@hadrian:~/tmp$ sed 's/bb+/b/g' testfile
bbbline1b
line2bbbbb
libne3b
dave@hadrian:~/tmp$ sed 's/bb\+/b/g' testfile
bline1b+
line2b
libne3b
```

---

