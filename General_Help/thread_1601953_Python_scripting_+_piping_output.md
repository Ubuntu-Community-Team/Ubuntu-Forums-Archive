---
title: "Python scripting + piping output"
date: 2010-10-20
forum: General Help
---

### Post by mglyons on 2010-10-20
I have written this simple script in python:



------------------------
a=2
b=3
a=2*a
b=3*b
c=a+b


print c


import os
os.system("./python_test.py > test.txt")
-------------------------





When I go to the terminal and type this:  python python_test.py, which is what the script is saved as, it gives me this error:





-------------------------
brittany@macdaddy-pro:~/FreedroidTesting$ python python_test.py 
13
sh: ./python_test.py: Permission denied
-------------------------





As you can see, it outputs the correct answer of 13 into the terminal but in my script I am trying to redirect the output into a text file.  You see my error that I get and I just want to know why it keeps saying 'Permission denied.'

---

### Post by mglyons on 2010-10-20
I don't know if bumping is aloud since I am new to these forums but I didn't get a response so I am going to bump this.

---

### Post by DaithiF on 2010-10-21
> **mglyons said:**
> I just want to know why it keeps saying 'Permission denied.'

because the script is not executable.  

```
chmod +x python_test.py
```
to make it executable, and make sure you have a **#!/usr/bin/python** as the first line so the shell knows what command to execute it with.

as you can see its not quite the same thing to do:
```
python script.py
```
and
```
./script.py
```
in the first case the script.py only needs to be readable, it need not be executable.  In the second case the script needs to be both readable and executable.

---

