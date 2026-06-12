---
title: "Removing duplicates and consolidating many directories"
date: 2012-10-13
forum: General Help
---

### Post by jfl on 2012-10-13
[SIZE="3"][FONT="Arial"]Hi,
Not really an pure Ubuntu question, but members here are so knowledgeable.
I am running 12.04 precise

I have approximately 3-4000 photos spread over 30-40 directories with no particular logic.  There are many duplicates; cameras were saved by different users.

99% of the files are named P10d0000ddd (d is any digit)

I would like:

1- to remove duplicates

2- to create a "master file" to have all the photos in

I tried "meld" which I used in the past; it is great to synchronize 2 (3) directories but I don't see that it could help me here.

Many years ago, I would have written a few lines of perl code ...:confused:

I have a feeling "grep" could help by copying all the files matching the regex to a single file, then duplicates would show an error.

What do you think ?[/FONT][/SIZE]

---

### Post by Girya on 2012-10-13
try fdupes

---

### Post by jfl on 2012-10-14
> **Girya said:**
> try fdupes

[FONT="Comic Sans MS"][SIZE="3"]Looks like it would do part 1. Thanks !

Still need a way to pick files in many different directories and copy them to a single directory.
[/SIZE][/FONT]

---

### Post by BrandonIngalls on 2012-10-14
If you want to move all the files into one directory you could use find...
```
find -iname "*.jpg" -exec mv {} /path/to/new/folder/ \;
```

---

### Post by jfl on 2012-10-14
> **BrandonIngalls said:**
> If you want to move all the files into one directory you could use find...
```
find -iname "*.jpg" -exec mv {} /path/to/new/folder/ \;
```

[FONT="Comic Sans MS"][SIZE="3"]**THANKS !!!**  That's exactly what I want to do.  I need to get more familiar with "find"; the man page scared me ;-)[/SIZE][/FONT]

---

