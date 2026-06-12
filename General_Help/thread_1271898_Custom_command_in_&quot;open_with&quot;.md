---
title: "Custom command in &quot;open with&quot;"
date: 2009-09-21
forum: General Help
---

### Post by DnjS on 2009-09-21
I have a number of file-types that I'd like to assign a standard program that will open it when clicking it. The problem is that the programs I'd like to use doesn't show up in the list over available programs. For instance I'd like vim to open any "*.java" file I double click and Zsnes for any "*.smc" file.

How can you write a custom command that will make this happen? :KS

---

### Post by sisco311 on 2009-09-21
Right Click on a .java file -> Properties -> Open with tab -> Add button -> Use a custom command -> ```
gnome-terminal -x vim
```

Is zsnes a GUI or CLI application?


EDIT:
If it has a GUI, then
```
zsnes
```

If you have to run it in a terminal:
```
gnome-terminal -x zsnes
```

---

### Post by DnjS on 2009-09-21
Thank you very much, that solved everything! Much appreciated! :KS

---

### Post by sisco311 on 2009-09-21
Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

