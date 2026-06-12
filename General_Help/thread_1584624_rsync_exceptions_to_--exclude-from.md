---
title: "rsync: exceptions to --exclude-from"
date: 2010-09-29
forum: General Help
---

### Post by loedu on 2010-09-29
Hi.

I have a cron job that backs up some files over to an external disk.

It ignores the hidden folders in my home dir, by using the --exclude-from option.

However, there is one specific hidden dir that I do want to back up.

Is there some way to add an exception to the list of exclusions?

Many thanks.

-- 
 Eduard Capell

---

### Post by DaithiF on 2010-09-29
Hi,
```
--include=.somedir --exclude-from=filewithpatterns 
```

the order is important, excluding first, then including won't work.

---

### Post by pbrane on 2010-09-29
you can also create an exclude file. Whatever file types, files, or directories you place in that file will be excluded.

for instance you create a file called **rsync_excludes**:
```

.somedir
.gvfs
*.o
somedir/subdir

```

usage:
**rsync --exclude-from=rsync_excludes**

---

