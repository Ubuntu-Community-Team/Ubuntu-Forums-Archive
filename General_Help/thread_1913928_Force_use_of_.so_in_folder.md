---
title: "Force use of .so in folder"
date: 2012-01-23
forum: General Help
---

### Post by IReadTheManual on 2012-01-23
How do I force the use of the lib if it is already in the folder? 

My program requires a shared library which I have put in the same folder as my program. In this situation, showing my game to a professor, I cannot install the lib on his machine. I have put the library in the same folder and have a Bashscript that runs the program. In Windows, I can just have the .DLL there, but this apparently is not the case in Ubuntu so I am confused.

Thanks!

---

### Post by gsgleason on 2012-01-23
What it you update the environment variable LD_LIBRARY_PATH to include the current directory before launching the app?

LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH command

---

