---
title: "tkinter in python3.x , unable to install"
date: 2010-10-21
forum: General Help
---

### Post by dave WB3DWE on 2010-10-21
[SIZE=3]Installed python 3.1.2 in Ubuntu 10.4 using Synaptic.
GUI tkinter won't load. Error message "No module named tkinter
(or _tkinter)" "Please install the python-tk package."
Synaptic has no tk package for python 3.1 in any repository.
~$ aptitude search python-tk   ->  information given is for
ver 2.6.3 ; says needs python < 2.7
Googled with no clear answer. A few say use ActiveState Python,
which is not what I have.
Strangely my /usr/lib/python3.1/ has a dir tkinter containing many files.
[/SIZE]

---

### Post by dave WB3DWE on 2010-10-22
[SIZE=3][FONT=Lucida Sans Unicode]Solved.  In "Universe" repository I found python3-tk
and python3-tk-debug. I was reluctant to install these
because :
1. All python docs say tkinter is included.
2. After clicking on them Synaptic said that Python3
    must also be installed.  I already had 3.1.2 installed
    and working and did not want to overwrite it.

Took a chance and let Synaptic install them.  Now tkinter
can be imported and python 3.1.2 is working as before.
[/FONT][/SIZE]

---

### Post by Amndeep7 on 2012-09-09
Just wanted to say that this has worked for me (Ubuntu 12.04).  It didn't tell me to reinstall python3 though.

---

