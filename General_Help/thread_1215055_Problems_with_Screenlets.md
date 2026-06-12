---
title: "Problems with Screenlets"
date: 2009-07-16
forum: General Help
---

### Post by ZettaGeek on 2009-07-16
Howdy All!

I am trying to install desktop screenlets, but when I run them, I get this error:

[joshua@localhost ~]$ screenlets
cat: /etc/screenlets/prefix: No such file or directory
Traceback (most recent call last):
File "/usr/share/screenlets-manager/screenlets-manager.py", line 25, in <module>
import pygtk
ImportError: No module named pygtk
[joshua@localhost ~]$

What is causing this problem? I install "pygtk" and it still gives me this error.

~ ZettaGeek

EDIT: [

[root@localhost joshua]# urpmi pygtk
Package python-gtk-0.6.11-13mdv2007.1.i586 is already installed
[root@localhost joshua]#

PyGTK is installed, so why I get this error, I have no clue.

]

---

### Post by ZettaGeek on 2009-07-16
Bump!

---

### Post by ZettaGeek on 2009-07-16
BUMP!
BUMP!
BUMP!
BUMP!
BUMP!

Ok, enough bumping. Anyone? I tried uninstalling/reinstall Python, I tried install pygtk, then installing screenlets, I tried a fresh formatted system.. Nothing seems to help.

~ ZettaGeek

---

### Post by ZettaGeek on 2009-07-17
Bbbbuuuummmmpppp!

---

