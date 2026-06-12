---
title: "running my hello word python script"
date: 2010-08-28
forum: General Help
---

### Post by netboom on 2010-08-28
hey guys some i'm messing around with some python.

im reading a book that says i need to put 

#!/usr/bin/env python
print "Hello, world!"

at the start of my script(the path bit) and then i can just type the name of my script from the terminal and it should run(instead of typing python hello.py) 

when i do which python i get 

darren@darren-laptop:~$ which python
/usr/bin/python

How do i change the first line of the script to make it work? i've tried putting what i though but it doesnt work. i just get

darren@darren-laptop:~$ hello.py
hello.py: command not found

Hope that made sense, TY

---

### Post by guandalino on 2010-08-28
Hello, try to add +x execution flag and call your script with ./hello.py

---

### Post by Dayofswords on 2010-08-28
darren@darren-laptop:~$ [SIZE="3"]**./**[/SIZE]hello.py

EDIT: what dude above means is do
```
chmod +x hello.py
```
this added(+) the execution flag(x) to the file so it can be ran

---

### Post by netboom on 2010-08-28
what does the ./ do? if im in the cwd?

---

### Post by guandalino on 2010-08-28
AFAIK linux doesn't add the current working directory to path for security reasons, so you have to specify it explicitly.

---

### Post by WorMzy on 2010-08-28
The cwd isn't in the PATH variable, so you can't call files within it with just their names. You have to tell the shell to look for the file in the cwd with ./

---

