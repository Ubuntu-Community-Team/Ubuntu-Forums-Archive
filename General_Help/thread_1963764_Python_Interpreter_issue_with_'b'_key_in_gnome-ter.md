---
title: "Python Interpreter issue with 'b' key in gnome-terminal"
date: 2012-04-22
forum: General Help
---

### Post by heathdbrown on 2012-04-22
When I go into a python interpreter shell in gnome-terminal I can not use the lower case 'b' key anymore.  I can ctrl + 'b', shfit + 'b'.  If I turn caps lock on and try shift + 'b' this fails as well.

If I copy and paste code into interpreter that has a lower case 'b' it removes the 'b'.

When I exit python interpreter I do not have any issues.

**Example of me trying to type 'Bob':**
Python 2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.

>>> Bo

**Example of copy and pasting AttributeError**:
Python 2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.

>>> AttriuteError

**Example of copy and pasting out of Python shell:**
Python 2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.

>>> None.some_method
**Traceback** (most recent call last):
  File "<console>", line 1, in <module>
**AttributeError**: 'NoneType' **object** has no **attribute** 'some_method'


**Versions and system info**
-----------------------------
GNOME terminal 3.0.1
python 2.7.2+
GCC 4.6.1
Ubuntu 11.10

---

### Post by papibe on 2012-04-22
Hi heathdbrown. Welcome to the forums!

That's a very odd problem. Does it work if 'b' is used on a script? For instance:
```
python -c 'print "Bob"'
```
Also, do you have a ~/.pythonrc.py file? If so, what's there?

Regards.

---

### Post by heathdbrown on 2012-04-23
Looks like the script works:

```
$  python -c 'print "Bob"'
Bob
```Attached is my ~/.pythonrc file

---

### Post by papibe on 2012-04-23
Thanks.

The problem lies on a bug on the file ~/.pythonrc.py

Specifically the line:
```
readline.parse_and_bind("bind ^I rl_complete")
```
(read about it [here]("http://stackoverflow.com/questions/7124035/in-python-shell-b-letter-does-not-work-what-the")).

The odd behaviour could be avoided by renaming the file:
```
mv ~/.pythonrc.py ~/.pythonrc.py.old
```
However, note that although that file it is not installed in a standard installation, some how you installed another python module, or package that installed the file on your home.

At this moment I don't understand its fully function, so I don't know if it would stop the extra functionality from working properly (I mean the one from the extra module or package you installed).

It would require a little more research to understand the complete purpose of that file, and if there is a fix around.

Regards.

---

### Post by heathdbrown on 2012-04-23
papibe, thanks for the article.  I use the same dot files from github as that user does.

I need to work on my Google fu.

Thanks so much for the help.

Now, how do I mark this guy as [Solved]? is that just updating the Title?

---

### Post by heathdbrown on 2012-04-23
I found the button for solving.

Thanks for your help.

---

### Post by heathdbrown on 2012-04-23
FYI...I moved the the ~/.pythonrc.py to ~/pythonrc.py.old.

Now when I go into the python shell I can type the 'b'.

It complains about missing the pythonrc.py file and it could not start 'PYTHONSTARTUP'

```
$  python
Python 2.7.2+ (default, Oct  4 2011, 20:06:09)
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
Could not open PYTHONSTARTUP
IOError: [Errno 2] No such file or directory: '/home/heathdbrown/.pythonrc.py'
>>> Bob
```I will do some more research on the actual cause with link provided and if I get it fixed will make sure to post the answer back.

---

