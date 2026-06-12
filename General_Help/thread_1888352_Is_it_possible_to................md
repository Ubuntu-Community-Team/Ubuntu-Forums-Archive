---
title: "Is it possible to..............."
date: 2011-11-29
forum: General Help
---

### Post by Herbon on 2011-11-29
Is it possible to take the contents of a text file ie { ls *avi > file_list.txt } and create folders with the name of the avi files. :confused:

---

### Post by nothingspecial on 2011-11-29
You just do this

```
for f in *.avi; do mkdir "${f/.avi/}"; mv "$f" "${f/.avi/}";done

```

That will create a folder for each avi file but without the .avi extension, then move the avi file into it's corresponding folder.

---

### Post by nothingspecial on 2011-11-29
Moved to General Help.

---

### Post by Herbon on 2011-11-29
Cool it worked!!!

Thanks!:P

---

### Post by nothingspecial on 2011-11-29
No problem :)

---

### Post by Herbon on 2011-11-29
> **nothingspecial said:**
> No problem :)

Ok so that worked perfectly, so what do I use (code or program) to get the movie poster jpeg from a website in the same folder? Is that grep?

---

