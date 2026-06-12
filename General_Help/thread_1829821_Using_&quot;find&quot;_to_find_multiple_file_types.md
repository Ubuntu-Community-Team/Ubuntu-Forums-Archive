---
title: "Using &quot;find&quot; to find multiple file types"
date: 2011-08-20
forum: General Help
---

### Post by Kissell on 2011-08-20
I keep writing scripts with something like this:
> 
find /path/to/files |grep .doc > /tmp/found.txt
find /path/to/files |grep .xls >> /tmp/found.txt
find /path/to/files |grep .ppt >> /tmp/found.txt
file=/tmp/found.txt


It works, but not very pretty or efficient.  Is there a way I can do that find all in one line of code?

---

### Post by papibe on 2011-08-20
```
find /path/to/files -type f -iname '*.doc' -or -iname '*.xls' -or -iname '*.ppt' > /tmp/found.txt

```
-type f will match regular files
-iname will match the regular expression (case insensitive).
-or  will let you add several conditions.

Regards.

---

