---
title: "Python Running in Terminal Help"
date: 2009-12-29
forum: General Help
---

### Post by BambooSauce on 2009-12-29
I am brand new to ubuntu, and have created a .py file that is on my desktop. In terminal, i type the following and get the following results when i try to run the file:

joe@joe-desktop:~$ python hello.py
python: can't open file 'hello.py': [Errno 2] No such file or directory
joe@joe-desktop:~$ ^C
joe@joe-desktop:~$ 


The file was made in IDLE, and i am using python 3.1, but a bunch of other pythons were default installed on the system, and are still there. I am running Ubuntu 9.10, The Koala one. Shows how nubbish i am. Any halp would be appriciated

---

### Post by x33a on 2009-12-29
try
```
python ./hello.py 
```

also, post the contents of your file here.

---

### Post by astoltz on 2009-12-29
Try: ```
cd Desktop
python hello.py
```
(remember that file and directory names are case sensitive - capital D)

---

### Post by BambooSauce on 2009-12-29
Contents of file (im brand new, and im just testing a hello world):

[B][COLOR=black]Python 3.1.1+ (r311:74480, Nov  2 2009, 14:49:22) 
[GCC 4.4.1] on linux2
Type "copyright", "credits" or "license()" for more information.
==== No Subprocess ====
>>> print("hello, world")[/COLOR][/B]

This was made in the 3.1 IDLE, then saved to home then moved to desktop for convenience. This is what happens in terminal:

[B]joe@joe-desktop:~$ python ./hello.py
python: can't open file './hello.py': [Errno 2] No such file or directory
joe@joe-desktop:~$ [/B]

Thanks for the help.

Weird....it says invalid syntax now......so i guess the file is TRYING to run. Maybe there is something wrong with the code. Did i forget like a required header for linux? I started today on windows, which i guess doesn't require something that Linux does. Please check my code. Thanks.

This is what terminal says now:

[B]
joe@joe-desktop:~/Desktop$ python hello.py
  File "hello.py", line 1
    Python 3.1.1+ (r311:74480, Nov  2 2009, 14:49:22) 
             ^
SyntaxError: invalid syntax[/B]


Again, please check my code. Am i missing something i need for linux python programming?

---

### Post by astoltz on 2009-12-29
You've got to get rid of everything except the ```
print("hello world")
```I guess you could comment out (by adding the # character as the first thing on the line) the other lines but they don't really do anything and they are not valid python commands.

Your file should look like:
```
# Python 3.1.1+ (r311:74480, Nov 2 2009, 14:49:22)
# [GCC 4.4.1] on linux2
# Type "copyright", "credits" or "license()" for more information.
# ==== No Subprocess ====
print("hello, world")
```

---

