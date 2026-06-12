---
title: "cant find dir"
date: 2011-02-11
forum: General Help
---

### Post by debd on 2011-02-11
recently I've been facing a problem....that's whenevr I try to cd into any dir that has a <space> in its name , it fails to change the dir. 
the shell takes only the 1st word as the dir name !
like
```
cd /media/new installtions here/Dev-Cpp/include
bash: cd: /media/new: No such file or directory

```

what to do to avoid this problem?
although folders can be renamed , I cant rename volumes from nautilus..
it says 

```
Sorry, could not rename "500 GB Hard Disk: new installtions here" to "500 GB Hard Disk: new_installtions here": Operation not supported by backend
```

now ..what to do? :|

---

### Post by Jonnox on 2011-02-11
use the escape ('\') character for spaces.

example: Dir "my spaced dir"

use 

```
cd my\ spaced\ dir
```

---

### Post by debd on 2011-02-11
ow..thanks. worked. :)

---

### Post by jim_deadlock on 2011-02-11
You can also use quotes:

```
cd "my directory"
```

---

### Post by hakermania on 2011-02-11
My own suggestion is:
1) If there is only one director in /media/ you can give cd *
2) You can always use the magic [TAB] cd 50[TAB] should work

---

### Post by debd on 2011-02-11
> You can always use the magic [TAB] cd 50[TAB] should work

didn't undrstand this one..

e.g. pls?

---

### Post by Vaphell on 2011-02-11
tab key is for autocompletion
**cd /me[tab]** autocompletes to **cd /media** (if there is no other object matching given characters). Usually you need to put max 3 chars to get what you want, unless you have tons of objects with very similar names.
very useful for very long, typo prone names like your 'new installations here'

**cd /me[tab]/new[tab]/D[tab]/inc[tab]** will produce the valid full path **/media/new installtions here/Dev-Cpp/include**, automatically hardened against spaces with \

in case of multiple matches tab shows all options so you can give additional chars to narrow down

---

### Post by debd on 2011-02-11
ya...got it.
very helpfull.
thanks Vaphell & others.

---

