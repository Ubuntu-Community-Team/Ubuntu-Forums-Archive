---
title: "executing without ./filename"
date: 2009-10-24
forum: General Help
---

### Post by deep_flame on 2009-10-24
hello ! 
after writing a simple "hello world" program in c,
and compiling without warning with - ' gcc -Wall hello.c -o hello'
i can run the program only with ' ./hello ',
what do i need to do in order to run it simply with 'hello'?

an ubuntu beginner question...
thanks,
Shahar

---

### Post by hambone79 on 2009-10-24
You need to add the directory that the hello program is in to your path.

---

### Post by amauk on 2009-10-24
move compiled programs to a directory called "bin" in your home directory

Debian based distros automatically add ~/bin (if it exists) to the path variable

---

