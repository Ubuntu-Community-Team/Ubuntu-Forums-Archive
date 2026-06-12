---
title: "one question about rm command"
date: 2010-03-11
forum: General Help
---

### Post by pooya_mr2009 on 2010-03-11
hi
i'm in the folder and i can delete it's file with rm * command(i don't want to delete folder)
if i'm not in the folder and i want to delete it's file(don't want to delete folder) how can i do it?
thank's a lot

---

### Post by jocko on 2010-03-11
```
rm [COLOR=Red]/path/to/folder/[/COLOR]*
```

---

### Post by pooya_mr2009 on 2010-03-11
thank's a lot
but i have one problem:
i want to delete files and folders in that folder but with command only files will be delete
but i want to delete files and folders together
can you say me a new command?
thank's a lot

---

### Post by pooya_mr2009 on 2010-03-11
i have this problem again

---

### Post by bodhi.zazen on 2010-03-11
To remove directories ("folders") use the -r flag

rm [COLOR=Black]-rf /path/to/folder/*[/COLOR]

---

### Post by jocko on 2010-03-11
```
rm -r [COLOR=Red]/path/to/folder/[/COLOR]*
```
The '-r' (recursive) option allows removal of folders.
To learn more:```

man rm
```

---

### Post by lisati on 2010-03-11
If the folder is empty you can use rmdir.

---

