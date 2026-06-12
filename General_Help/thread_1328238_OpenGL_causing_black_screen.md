---
title: "OpenGL causing black screen"
date: 2009-11-16
forum: General Help
---

### Post by g9k on 2009-11-16
Hi there.. Ive been searching around for someone with the same problem as me, but havent had any luck with it, so i thought id try asking myself:

Whenever i try to open an application wich is OpenGL accelerated, all i get is a black screen.. This happens both when trying to run programs in wine, but also when trying to run things like java3d applications.

The programs dont freeze as i get a working cursor, and i can hear sound when i mouse over certain buttons and such..

My computer is a thinkpad x61s, with a x3100 intel graphics accelerator.

When i run :~$ glxinfo | grep rendering
it says: direct rendering: Yes

Im running Ubuntu 9.10

Any help would be appriciated very much :)

---

### Post by ArcaVex on 2009-11-16
Are you trying to run the application using OpenGL or not?

If not try adding  "-openGL" to the end of the launcher link of the program.  or try via a terminal

---

### Post by g9k on 2009-11-16
Guess I should have clarified that ^^

It is only when i run the program in openGL mode that the black screen ocurs... I can run them in glfx mode, but its just reallu really choppy/buggy, since wine doesn't support that so well afaik...

Im fairly certain that java3d runs in openGL as well.

---

