---
title: "look for a text"
date: 2011-04-11
forum: General Help
---

### Post by cucucur on 2011-04-11
hi! I modified a .xml file, but I dont remember wich file was, does it exist some comand similar to "locate" to see it?

Thanks!!!

---

### Post by deathadder on 2011-04-11
If you know what directory it was in (probably not the case here), you can order the ls command to display files based on when they were edited (the newest at the end):
```
ls -lart
```
Alternatively you can use find. If you know it was within your home directory within the last 60 days you could use:
```
find /home/cucucur -iname "*.xml" -mtime -60 -print
```
If you know you edited within the last 10 days you would change that to:
```
find ... -mtime -10 -print
```
Finally, if you know it was edited exactly 6 days ago you could use:
```
find ... -mtime 6 -print
```
[http://www.cyberciti.biz/faq/howto-finding-files-by-date/](http://www.cyberciti.biz/faq/howto-finding-files-by-date/)

Once you've got a list of the XML files edited you'll need to open them up and have a look.

---

### Post by profeta81 on 2011-04-11
if you remember a particular string you added to the file you may use:

```
grep -i "<string>" `find <path> -name "*xml"`
```

the second part of the command search in <path> all the files with xml extension, the first bit of the command search the string <string> in all the files found

cheers ;)

---

### Post by cucucur on 2011-04-12
thanks!!!!!

Solved!!!

---

