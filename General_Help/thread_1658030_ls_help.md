---
title: "ls help"
date: 2011-01-02
forum: General Help
---

### Post by GuiGuy on 2011-01-02
If I run

ls -R1 

I get a recursive listing of all files under the current directory.

However, if I do

ls -R1 *.avi 

, ie I want to search only for files with the file descriptor .avi, I get an error

> ls: cannot access *.avi: No such file or directory

So it seems I am using ls incorrectly. What's the correct way to use wild card pattern matching when using the -R switch? Or maybe that isn't possible?

TIA

---

### Post by dcstar on 2011-01-02
> **GuiGuy said:**
> 
.........
So it seems I am using ls incorrectly. What's the correct way to use wild card pattern matching when using the -R switch? Or maybe that isn't possible?

TIA

```
ls -R1 | grep .avi
```or
```
man find
```

---

### Post by GuiGuy on 2011-01-02
> **dcstar said:**
> ```
ls -R1 | grep .avi
```or
```
man find
```

Many thanks. I should have known | grep :redface:

---

