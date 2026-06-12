---
title: "ls - list only folders"
date: 2010-01-06
forum: General Help
---

### Post by gabe17 on 2010-01-06
Hi! I want to ask whether it is possible to list only folder with the ls command. I haven't found it in the man.

---

### Post by mcduck on 2010-01-06
```
ls -d */
```
(note that if there are no directories inside the dir where you run this command you get an error message instead of no output at all)

---

### Post by gabe17 on 2010-01-06
Thanks.

---

### Post by theDaveTheRave on 2010-01-06
Another option is to use 

```

du

```

this will give the size of the directories also.

However using
```

du --max-depth=N

```
will show the subdirectories to a depth of 'N'

so in your subfolder /Documents/

if you have a bunch of sub folders they will show up in the tree.

Note it will also show the "hidden" directories (ie those starting with '.')

David

---

