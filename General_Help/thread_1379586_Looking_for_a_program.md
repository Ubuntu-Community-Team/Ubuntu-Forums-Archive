---
title: "Looking for a program"
date: 2010-01-12
forum: General Help
---

### Post by Marvin666 on 2010-01-12
Anybody know of a "lottery" program. I was needing something that if I enter a list of names, and how many "tickets" they have, then it would randomly pick a name. I could just use a scheme with a random number generator, but if the program applied weighting for me, it would be a lot easier.

---

### Post by gsmanners on 2010-01-12
I don't think there's an app with that specific function, but this is a good chance to practice scripting. Here's a Python script that does what you're talking about:

```
import random

# name, number of tickets
list = [ ['Jack',10], ['Jill',20] ]

# get the total number of tickets
total = 0
for i,v in list:
    total += v

# get a random value
x = random.randint(1, total)
print x, total

# determine winner
for i,v in list:
    if x <= v:
        print 'Winner is:', i
        break
    else:
        x -= v
```

---

### Post by Marvin666 on 2010-01-12
So, I would just save this as something like random.py on my desktop, and double click to run it?

---

### Post by gsmanners on 2010-01-13
Or you could pull up a terminal and type:

python random.py

Just make sure the list contains the names and values you want.

---

### Post by Marvin666 on 2010-01-14
Okay got the file made, but python is spitting this into my terminal: ```

marvin@Local-Machine:~$ python random.py
Traceback (most recent call last):
  File "random.py", line 1, in <module>
    &#65279;import random
  File "/home/marvin/random.py", line 12, in <module>
    x = random.randint(1, total)
AttributeError: 'module' object has no attribute 'randint'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.6/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "/home/marvin/random.py", line 12, in <module>
    x = random.randint(1, total)
AttributeError: 'module' object has no attribute 'randint'

Original exception was:
Traceback (most recent call last):
  File "random.py", line 1, in <module>
    &#65279;import random
  File "/home/marvin/random.py", line 12, in <module>
    x = random.randint(1, total)
AttributeError: 'module' object has no attribute 'randint'
marvin@Local-Machine:~$ 

```
Is it python, or am I causing some sort of buffer overflow? It is almost 10,000 total tickets, at least 50 names, with tickets per person ranging from 3850 to 1. Yes it took forever to format the list properly...

---

### Post by lykwydchykyn on 2010-01-14
Rename the file to something else.  The problem is that if you have a file called random.py and try to import "random", python is going to assume you mean "random.py" rather than the built-in library.  So you're importing your own script which hasn't implemented the "randint" function.

Just call it "lottery.py" or something and then it should work.

---

### Post by Marvin666 on 2010-01-14
Thanks, it works now.

---

