---
title: "Emacs color themes"
date: 2010-01-27
forum: General Help
---

### Post by mringer on 2010-01-27
X-ub 8.04, GNU Emacs 22.1-0ubuntu10.1
as downloaded by package manager.

Are these emacs color themes documented anywhere? I cannot find
anything in the manual.

---

### Post by jpkotta on 2010-01-31
Color themes are in the emacs-goodies-el package.  M-x color-theme-select should bring up a list of all the themes.  Note that not all color themes define all colors, so you could get different results by selecting them in a different order.  I don't think there's any official documentation other than what's on the website and the normal source documentation.  To read that, do M-x find-library RET color-theme RET.

---

### Post by miguelastico on 2010-02-12
Is there anybody that knows how to modify a theme, or introduce a new one?
I used the command M-x color-theme-print after modifying a theme in the way I wanted, but now I am stuck with a .el file and I don't know what to do with it.
I put the color theme specifications in the color-theme.el file, put a reference in the list, but still I cannot access/see my theme.
The instructions in color-theme.el stop at the "print" command.
Any suggestions?

EDIT: obviously, the very first attempt done after this post gave me the solution.
I modified the color-theme.el file but it didn't work; I looked at the messages and it said "source file <FILEPATH> newer than the compiled one"
Looking for that on bing(let's change this google at least once) led me to the reference manual, section "byte compilation". Well, actually the wiki had the correct solution: from emacs, M-x byte-compile-file
then you choose the file and everything goes smoothly. I had to start emacs as root though.

---

