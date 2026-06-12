---
title: "eclipse compiling problem"
date: 2011-08-09
forum: General Help
---

### Post by xoron on 2011-08-09
hi im new to programming on ubuntu but not to programming in general.

im trying to compile a openGL program with eclipse but then i try to run the project it says:

"launch failed. binary not found."

a did a brief google search and found this may be because of a missing G++ compiler but when i checked, this was already installed so i dont know why it is not compiling.

im sure it something simple but i cant figure out what :P

thanks in advanced.

---

### Post by avihebbar on 2011-08-09
First of all make sure Glut is installed on your system.
Then
select the project containing opengl code.Right click->Properties->C/C++ Build
There under the tool settings tab,
GCC C linker->libraries
Add the glut library there.This must help.I too had the same problem.

---

