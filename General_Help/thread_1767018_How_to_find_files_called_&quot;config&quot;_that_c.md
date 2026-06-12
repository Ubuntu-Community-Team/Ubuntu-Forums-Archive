---
title: "How to find files called &quot;config&quot; that contain some specific text?"
date: 2011-05-25
forum: General Help
---

### Post by oopsie on 2011-05-25
Question is in the title.

---

### Post by ignacio69 on 2011-05-25
Dear oopsie,
in graphic mode, you can use search files
in terminal mode, you can use command ```
find
```, you can combined it also with ```
grep
```.
you can find more information if you type ```
man -k find 
```in the terminal
For instance
```
find -i config* | grep "thetextIamlookingfor"
```I.

---

