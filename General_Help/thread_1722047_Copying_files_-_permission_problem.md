---
title: "Copying files - permission problem"
date: 2011-04-05
forum: General Help
---

### Post by JohnBUK on 2011-04-05
Main system Ubuntu 10.10, dual boot with Windows Vista.

My earlier post today explained I had toasted my Ubuntu system and so now before I reformat etc I am trying to copy folders and files from the partition to a external HDD using an Ubuntu Live CD. In particular I ran a website with Net Objects Fusion on Virtualbox in Ubuntu 10.10 and am hoping to copy the whole folder.
The problem is I'm getting refused on some random files and folders because I do not have permission as I'm not the "owner".
Any thoughts on how to get round this please.
JB

---

### Post by jamesisin on 2011-04-05
Use root-level permissions and rsync:

```
sudo rsync -ailS --progress /path/for/from/directory path/of/to/directory
```

---

### Post by JohnBUK on 2011-04-05
> **jamesisin said:**
> Use root-level permissions and rsync:

```
sudo rsync -ailS --progress /path/for/from/directory path/of/to/directory
```
OK, thanks for that, in the end I had to chmod the files as it seemed the system didn't like the two-named "New Volume" the ext HDD was called.

---

### Post by jamesisin on 2011-04-05
```
sudo rsync -ailS --progress /path/for/from/directory "path/of/to/New Volume"
```

---

### Post by JohnBUK on 2011-04-05
> **jamesisin said:**
> ```
sudo rsync -ailS --progress /path/for/from/directory "path/of/to/New Volume"
```
For some reason it wasn't happy with "New Volume". When I used the TAB to complete the path it showed "/New(3backslash) Volume" and then didn't find the Dir when run!!

Thanks for your help.
John

---

### Post by jamesisin on 2011-04-05
I have seen that on occasion where tab completion and execution seem to be at odds.  I have found that exiting from the terminal and reopening it will sometimes reset wheat ever is mixed up there.  The quotes might also be the route to take.  Did it give you an error when you tried to run rsync?

---

