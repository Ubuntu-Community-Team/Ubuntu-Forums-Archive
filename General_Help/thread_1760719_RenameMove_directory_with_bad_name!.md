---
title: "Rename/Move directory with bad name?!"
date: 2011-05-17
forum: General Help
---

### Post by Parsa86 on 2011-05-17
I have a directory which was downloaded and has a silly name like "-=Directory=-" on my headless (no GUI) linux box and when I try to deal with this directory using "mv" in order to rename it or move it somewhere, it simply does not work. Terminal instead says:

```
mv: invalid option -- '='

```


Any ideas of how I can rename or move it?!

Cheers!

---

### Post by sisco311 on 2011-05-17
```
mv -- -=Directory=- Directory
```

---

### Post by nothingspecial on 2011-05-17
```
mv -- "-=directory=-" sensible_name
```

-- tells bash to not interpret the next - as an argument to the proceeding command.

---

### Post by nothingspecial on 2011-05-17
](*,)](*,)](*,)](*,)](*,)](*,)

every time ......... :D

---

### Post by dargaud on 2011-05-17
There are plenty of ways to remove files with bad names. The "mv -- -file" given above works in your case but more generic options are:[LIST]
[*]Use autocompletion: mv startofbadname[tab] newname
[*]Move everything else out of the way, then: mv * newname
[*]"ls -i" to find the inode number, then "find -inum inodenumber -delete"
[*]Use convmv when there are encoding problems
[*]...
[/LIST]

---

### Post by Parsa86 on 2011-05-17
You guys are gods among men :D

---

### Post by sisco311 on 2011-05-17
Don't forget to mark this thread as solved.

> **nothingspecial said:**
> ](*,)](*,)](*,)](*,)](*,)](*,)

every time ......... :D

:P

---

