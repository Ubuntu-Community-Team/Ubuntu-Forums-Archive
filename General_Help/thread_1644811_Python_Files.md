---
title: "Python Files"
date: 2010-12-13
forum: General Help
---

### Post by Ntwiles on 2010-12-13
Hey guys. I'm not sure that this is strictly an Ubuntu question but it is a question that should be right up your guys' alleys. 

I'm trying to start working with Python. I'm used to compiled languages like C++ and Java so I'm having trouble opening Python files. I've got Python running in the terminal and I'm trying things like:

```
>>> python bottles.py
  File "<stdin>", line 1
    python bottles.py
                 ^
SyntaxError: invalid syntax

```

and

```
>>> bottles.py
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'bottles' is not defined

```

I'm guessing this is because I need to change the folder Python is searching for the files? Is that right? If so where could I change that? Thanks (:

---

### Post by cgroza on 2010-12-13
You must cd to the script directory and then run the "python script.py" directly from the bash shell. What you are doing now is run it from a python shell. 

Or, you can just mark your file as executable, double click it and select run in terminal.

---

### Post by Ntwiles on 2010-12-13
Gotcha. But that would start the Python shell and I would have to close it each time to reopen the file, wouldn't I?

Is there any way to open it right from the Python shell? Or even open an updated version of a file that's already opened?

When I open it just by double clicking it, the file opens in the terminal then closes immediately. I added the line:

```
raw_input('Press Enter to exit')
```

To wait for input but it still closed immediately.

---

### Post by Vaphell on 2010-12-13
that line should certainly work

why do you use the python shell exactly? it's cool to test some stuff in it but when you write a program it's actually easier to use gedit or any other text editor and after each save (ctrl+s) rerun **python file.py** in terminal (up arrow to get the last command, enter). With the embedded terminal plugin for gedit, single gedit window is all you need. Doubleclicking is a waste of time, trust me. You can also use some IDE supporting python (ie Geany) - it will do all the 'legwork' for you.

[http://ubuntuforums.org/showthread.php?t=1199414](http://ubuntuforums.org/showthread.php?t=1199414)

---

