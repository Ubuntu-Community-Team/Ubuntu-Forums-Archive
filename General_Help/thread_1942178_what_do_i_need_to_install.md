---
title: "what do i need to install"
date: 2012-03-17
forum: General Help
---

### Post by nataliafoster26 on 2012-03-17
i keep getting this message
rubi1989@rubi1989-laptop:~$ gcc -g -lglut -o addlines addlines.o ast11pr.o
/usr/bin/ld: cannot find -lglut
collect2: ld returned 1 exit status

i have gcc already , why the -lglut

---

### Post by TeoBigusGeekus on 2012-03-17
Well, do you have glut installed?
The -lglut switch tells gcc to include glut while linking your program.

---

