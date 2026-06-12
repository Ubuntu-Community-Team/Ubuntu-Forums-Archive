---
title: "Installed ncurses but mysql still complains it cant find ncurses"
date: 2010-06-27
forum: General Help
---

### Post by foolfoolz on 2010-06-27
I installed ncurses with:

sudo apt-get install libncurses5-dev

and it installed.

then when i try mysql i get:

$ mysql
mysql: error while loading shared libraries: libncursesw.so.5: cannot open shared object file: No such file or directory

Is there something for my path i need to change to make this work?

---

### Post by happyhamster on 2010-06-27
Try installing libncursesw5-dev. Good luck.

---

### Post by Helios747 on 2010-06-27
ncurses-dev is not ncurses. That's just the header files.

Make sure you have ncurses5 and possibly ncursesw5 runtines installed. You don't need the dev packages unless you're compiling.

---

