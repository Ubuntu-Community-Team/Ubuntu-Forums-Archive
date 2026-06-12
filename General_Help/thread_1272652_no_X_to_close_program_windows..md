---
title: "no X to close program windows."
date: 2009-09-22
forum: General Help
---

### Post by dluzius on 2009-09-22
I've done it again. I messed around, I think with changing <THEMES>, and now when I open a program, it doesn't show the 3 little boxes in the upper right hand corner. This makes it hard to close some programs. And opened programs don't appear to be displayed all the way to the top of the monitor. Please help me undo the damage I have caused.
   Dave

---

### Post by P4man on 2009-09-22
do they have border with the window title in it ? Same border that should have those buttons?

If not, then you don't have a window decorator. A quick fix is probably:

alt+F2
```
metacity --replace
```

If you're using compiz for desktop effects, let me know.

If you do have that border, then simply pick another theme

---

### Post by dluzius on 2009-09-22
yes, I am using compiz.

---

### Post by P4man on 2009-09-22
Do you have windows borders (titlebar) ?
Im guessing you dont, so  if you are using compiz, open up compiz config setting manager, make sure "enable window decoration" plugin is checked. If that doesn't help, then look in the settings of that plugin in the "command" box, make sure there is "/usr/bin/compiz-decorator" (or click the broom to the right to restore that default value)

---

### Post by blur xc on 2009-09-22
Not a fix to your problem, but you can alt-right click anywhere inside the window to pull up a windows control menu.

BM

---

### Post by dluzius on 2009-09-22
Tks P4Man, that solved the problem.

---

