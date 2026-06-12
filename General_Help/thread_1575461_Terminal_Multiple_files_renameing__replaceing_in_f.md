---
title: "Terminal: Multiple files renameing / replaceing in filename"
date: 2010-09-15
forum: General Help
---

### Post by JaizEdelmann on 2010-09-15
Hey guys, im having a little issue with using the rename function in ubuntu, i've been trying to google abit about how the file rename function works however i havent found the help i need'd :( so i hope someone can help me out here (i dont mind if its python)

Anyway to the point.

I need to rename all files recursively under a specific folder.

example file
```
stupid_info_Dummy_Artist-Dummy_track_something.mp3
```

example endresult
```
Dummy_Artist-Dummy_track_something.mp3
```

---

### Post by ks07 on 2010-09-15
Depending on how varied these filenames are- you could try using pyrenamer and the delete from option. It's available in the repos. ([apt://pyrenamer)]("apt://pyrenamer")

---

### Post by JaizEdelmann on 2010-09-15
> **ks07 said:**
> Depending on how varied these filenames are- you could try using pyrenamer and the delete from option. It's available in the repos. ([apt://pyrenamer)]("apt://pyrenamer")

its the same thing that should be removed from each file , also i do not run with gnome so i cant use graphical interfaced applications (i dont know if pyrenamer works with commandlines?)

Here's what i came up with so far

```
for f in *.mp3*;do mv $f ${f/remove/};done
```

remove is what you want to remove , however this doesent work recursivly

---

### Post by gmargo on 2010-09-15
Relatively easy to do it with **find** and **rename**.
```

find . -type f -name '*.mp3*' -print0 | \
xargs -0 rename 's/^(.*)\/stupid_info_([^\/]+\.mp3.*)$/$1\/$2/'

```

---

### Post by Nythain on 2010-09-15
ubuntu comes with a nifty command line tool called "rename"... does exactly what you want, with one fun command and a relatively simple regex

---

### Post by JaizEdelmann on 2010-09-16
Thanks for the help guys!

---

