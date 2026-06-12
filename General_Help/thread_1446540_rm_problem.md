---
title: "rm problem"
date: 2010-04-04
forum: General Help
---

### Post by RichardCain on 2010-04-04
I tried to delete a folder from terminal using the command
```
rm barry
```
but it spat back > rm: cannot remove `barry': Is a directory
I thought rm was supposed to delete directories as well as files?
Is there another command that I'm missing?

---

### Post by louieb on 2010-04-04
You need to use the -r option. Strongly suggest you use the -ri option.

See the man page for more information.

```
man rm
```

---

### Post by RichardCain on 2010-04-04
Thanks a lot!

---

