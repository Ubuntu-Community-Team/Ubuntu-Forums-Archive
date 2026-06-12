---
title: "Shebang line, python, ubuntu"
date: 2011-06-18
forum: General Help
---

### Post by Demo58 on 2011-06-18
How come when I run python programs from terminal, I have to write "python file.py" or "python3.2 file.py" ? If I'm including a shebang line specifying that the program should be opened with python 3.2 interpreter, shouldn't it automatically open with python3.2 w/o specifying "python3.2 file.py". Shouldn't I just only have to specify the file name, "file.py"?

---

### Post by gmargo on 2011-06-18
Your file will need to be executable ("chmod +x file.py").  Then a "./file.py" will refer to the she-bang line to find the interpreter.

---

