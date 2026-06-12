---
title: "Delete duplicate files command line"
date: 2010-04-14
forum: General Help
---

### Post by wattaman on 2010-04-14
Is there a way to remove duplicate files from a specific folder through SSH? I've uploaded a lot of flash games on my server and I can see in the Webmin's file manager that I have many duplicates. Their names are different, of course.
Thanks!

---

### Post by ibuclaw on 2010-04-14
There is a program called fdupes - that can be used to locate duplicate files.

```
fdupes /path
```

You can tell fdupes to delete dupes (via prompting you to select which one):
```
fdupes -d /path
```
However, care should be taken to avoid accidentally loss of data.

Regards
Iain

---

### Post by wattaman on 2010-04-14
Wow, my eyes burn... I feel like I was welding without glasses :)
I've just checked more the 600 groups of duplicates. From almost 3000 files now I have 1600.
Fdupes helped a lot. Thanks for the suggestion!

I'll mark this solved to end it.

---

