---
title: "List folders and subfolders with size"
date: 2010-01-02
forum: General Help
---

### Post by DouglasCaixeta on 2010-01-02
Hi,

I want to list my folders and subfolders (recursive) and also show the size of the files in terminal.

I started using this:

```
ls -h -R > /test.txt
```

I got everything but not the size of the folders.

Then I tried this:

```
du -h --max-depth=1 > test.txt
```

Suppose to show me everything, but I can't see subfolders. And this command do not accept recursive.

How can I show the size of the files and folders like the second command, but including the subfolders?

---

### Post by Barriehie on 2010-01-02
```
du -h -c -b /SomePath
``` Should do the trick.

---

### Post by DouglasCaixeta on 2010-01-03
> **Barriehie said:**
> ```
du -h -c -b /SomePath
``` Should do the trick.

This command does not list the files, only the folders.

---

### Post by Barriehie on 2010-01-03
See if ```
ls -Rs1h
``` does it for you. (that's a numeric 1!)

---

### Post by DouglasCaixeta on 2010-01-03
> **Barriehie said:**
> See if ```
ls -Rs1h
``` does it for you. (that's a numeric 1!)

Yes it does. No the way I wanted, buy it does. Thanks

---

### Post by Barriehie on 2010-01-03
> **DouglasCaixeta said:**
> Yes it does. No the way I wanted, buy it does. Thanks

:) 
 To really slice/dice/mutilate/process the listing you might want to check out gawk, probably already installed on your system and it's not to terribly complicated.

---

