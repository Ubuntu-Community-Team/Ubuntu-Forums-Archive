---
title: "python not importing file in terminal."
date: 2011-09-22
forum: General Help
---

### Post by upupz on 2011-09-22
I am trying to use the import command as such:

```
import hello world

```this is the output, plus an ls to show the file is in the directory.


```
upupz@upupz-laptop:~/Documents/Python/Basics$ ls
bbb.txt  hello world.py  input output.py
upupz@upupz-laptop:~/Documents/Python/Basics$ python3.1
Python 3.1.2 (r312:79147, Sep 27 2010, 09:45:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import hello world
  File "<stdin>", line 1
    import hello world
                     ^
```
I am sure this some silly error on my part but for the life of me I can't find it. this is the text in the file.


```
"""
coder : upupz
aim : text output
user base : upupz
"""



print("hello world!")
```

Thanks

---

### Post by patryk77 on 2011-09-22
Again, python will consider this as being 2 arguments when it is expecting one.

It probably also needs to be escaped or enclosed in strings. Never coded in python, so don't ask me, though google might tell you :)

Also, as this is Programming and not an Ubuntu-specific question, you should post it in the Programming Talk forums:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by ofnuts on 2011-09-22
> **upupz said:**
> I am trying to use the import command as such:

```
import hello world

```import sees two tokens: "hello" and "world".

I don't know if there is a syntax that supports spaces in modules names. From [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/) :

[B][I]Modules should have short, all-lowercase names.  Underscores can be used
in the module name if it improves readability.  Python packages should
also have short, all-lowercase names, although the use of underscores is
discouraged.[/I][/B]

---

### Post by upupz on 2011-09-22
Thanks guys, none of this has worked, which is a shame, however I am sure I will figure it out in the end, again most likely me missing something obvious, I am very new to ubuntu.

As to the fact it should have been posted in programming, sorry, I wasn't sure whether or not it was a terminal problem or a python one. I will remember for next time, thanks :)

---

