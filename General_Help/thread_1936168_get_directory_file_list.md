---
title: "get directory file list"
date: 2012-03-05
forum: General Help
---

### Post by Philip Marlowe on 2012-03-05
how can i get the file list of a directory? i want files in subdirectory as well and i want to import this list to a openoffice calc spreadsheet. i tried with the ls command but not seem to be the proper solution. thanks to anybody who can help

---

### Post by spiky001 on 2012-03-05
Hi

How about "du /path/to/directory"

---

### Post by MG&amp;TL on 2012-03-05
Change directory to where you want to be:

```
cd ~/Documents
```  (for instance)

"find" everything ( the full stop is important!).
```
find .
```

OR:

```
find ~/Documents
```


EDIT: As you can see, there's lots of different ways of doing the same thing. ;)

---

