---
title: "Patching and Diff"
date: 2006-06-23
forum: General Help
---

### Post by Apple 101 on 2006-06-23
Hi all,

How can I apply a diff file to sources?  I can use gedit but it is really slow.

---

### Post by oscar on 2006-06-23
I think the easiest way is to put to .diff file in the same dir as the source file it is patching and go:
```
patch file.diff
```
where file.diff is the name of your patch file. (I haven't checked this, try to look at the man page for patch)

---

### Post by Apple 101 on 2006-06-23
Excellent.  Thanks oscar.

---

### Post by lamego on 2006-06-23
The correct usage is 
```
patch -p0 < file.diff
```
The -p number depends on how the diff file was created, like how many levels of paths it included on the diff file names.

---

