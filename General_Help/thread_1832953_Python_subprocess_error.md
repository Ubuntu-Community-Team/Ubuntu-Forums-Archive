---
title: "Python subprocess error"
date: 2011-08-25
forum: General Help
---

### Post by maziar_mirzazad on 2011-08-25
Hello,
I am trying to install n4c on ubuntu.
when I run the program I get the following error related to python.

Traceback (most recent call last):
  File "./base.py", line 26, in <module>
    if len(re.findall('(lxc)',(subprocess.Popen(shlex.split('rpm -qa'), stdout=subprocess.PIPE).communicate()[0]))):
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

can any body help me?

BRGDs,

Maziar

---

