---
title: "Listing the total amount of data in a partition or folder"
date: 2010-03-06
forum: General Help
---

### Post by Chirola on 2010-03-06
Hello


I'm trying to list the total amount of Data in my Windows XP partition.

I've only 330MB free in my windows partition in a total of 12,2G.

I think that is why i can't boot windows.

When i open a console, and type:

```
ls -ash /media/sda1
```

It appears to me the complete list with all files and folders and the respective size.

But the total size is only 777MB .

I've noticed that all folders appear with the size of 16K , but when i list those folders they have files a lot larger then that.

Any explanation to that?

---

### Post by Eraemaajaervi on 2010-03-06
use
```

du -sh /media/sda1

```

to get the total amount of data in this folder.
could take a long time depending on the size

do
```

du -sh /media/sda1/*

```
to see all summarized sizes of the folders

also 
```
df -h
``` gives you an overview of your disk spaces

---

### Post by Chirola on 2010-03-06
> **Eraemaajaervi said:**
> use
```

du -sh /media/sda1

```to get the total amount of data in this folder.
could take a long time depending on the size

also 
```
df -h
``` gives you an overview of your disk spaces

Is it possible to list all files and folders in sda1, and to show the size of the folders?

With 

```
 ls -ash /path 
``` 

I can obtain the list and size of all files, but not from the folders. Can you help me with that ?

---

### Post by Chirola on 2010-03-06
> **Eraemaajaervi said:**
> use
```

du -sh /media/sda1

```to get the total amount of data in this folder.
could take a long time depending on the size

do
```

**du -sh /media/sda1/***

```to see all summarized sizes of the folders

also 
```
df -h
``` gives you an overview of your disk spaces


Thank you very much!;)

---

