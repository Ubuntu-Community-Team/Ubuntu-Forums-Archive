---
title: "Help on find comand"
date: 2011-11-30
forum: General Help
---

### Post by smasher40 on 2011-11-30
Hi, i'm starting with linux scripting and i'm having the normal doubts of this process, right now can someone tell me what this exactly command does??


find . -name "rede.?" -print


thanks 

:confused::confused:

---

### Post by New00Folder on 2011-11-30
Give the command "man find" for a detailed manual of the "find" command.
Press "q" to quit viewing manual.

---

### Post by aromo on 2011-11-30
> **New00Folder said:**
> Give the command "man find" for a detailed manual of the "find" command.
Press "q" to quit viewing manual.

That's right, man is your best source of info if you want to learn scripting.

That command searches recursively from the current directory all files named rede.? (where ? is any one character) and prints its name including the path.

Good luck!

---

### Post by smasher40 on 2011-11-30
> **aromo said:**
> That's right, man is your best source of info if you want to learn scripting.

That command searches recursively from the current directory all files named rede.? (where ? is any one character) and prints its name including the path.

Good luck!


Many thanks, because i was trying the command with and without the -print, and the result was always the same, glad for the tip

---

### Post by vangop on 2011-11-30
Man might be not the best friend for a beginner.
I suggest this [guide]("http://www.ipp.mpg.de/~dpc/gnu/findutils-4.1/html_chapter/find_toc.html").

---

### Post by smasher40 on 2011-11-30
> **vangop said:**
> Man might be not the best friend for a beginner.
I suggest this [guide]("http://www.ipp.mpg.de/~dpc/gnu/findutils-4.1/html_chapter/find_toc.html").

pretty cool thanks a lot, i have an essay to do and this will help a lot :)

---

