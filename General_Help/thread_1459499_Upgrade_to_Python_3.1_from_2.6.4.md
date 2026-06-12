---
title: "Upgrade to Python 3.1 from 2.6.4"
date: 2010-04-21
forum: General Help
---

### Post by iEthan on 2010-04-21
I'm trying to upgrade my Python installation from 2.6.4 to 3.1. I have the 3.1 packages install:

```

~$ apt-cache search python3.1
python3-all - Package depending on all supported Python runtime versions
python3-all-dbg - Package depending on all supported Python debugging packages
python3-all-dev - Package depending on all supported Python development packages
python3-dbg - Debug Build of the Python Interpreter (version 3.1)
python3-gdbm - GNU dbm database support for Python 3.x
python3-tk - Tkinter - Writing Tk applications with Python 3.x
idle-python3.1 - An IDE for Python (v3.1) using Tkinter
libpython3.1 - Shared Python runtime library (version 3.1)
python3.1 - An interactive high-level object-oriented language (version 3.1)
python3.1-dbg - Debug Build of the Python Interpreter (version 3.1)
python3.1-dev - Header files and a static library for Python (v3.1)
python3.1-doc - Documentation for the high-level object-oriented language Python (v3.1)
python3.1-examples - Examples for the Python language (v3.1)
python3.1-minimal - A minimal subset of the Python language (version 3.1)

```
```

~$ apt-cache search python | grep -E "31|3\.1"
python3-dbg - Debug Build of the Python Interpreter (version 3.1)
idle-python3.1 - An IDE for Python (v3.1) using Tkinter
libpython3.1 - Shared Python runtime library (version 3.1)
python3.1 - An interactive high-level object-oriented language (version 3.1)
python3.1-dbg - Debug Build of the Python Interpreter (version 3.1)
python3.1-dev - Header files and a static library for Python (v3.1)
python3.1-doc - Documentation for the high-level object-oriented language Python (v3.1)
python3.1-examples - Examples for the Python language (v3.1)
python3.1-minimal - A minimal subset of the Python language (version 3.1)

```

I have all the packages installed. But when I do this:
```

~$ python -V
Python 2.6.4

```

What is going wrong here?

---

### Post by linuxnovice. on 2010-05-10
Same here please help I tried installing from the source (tar.bz2) and ended up screwing ubuntu with a lot of ruined packages, then I installed from synaptic 
I install python 3
but when I type python in the terminal this appears 


> Python 2.6.5rc2 (r265rc2:78822, Mar 11 2010, 13:01:50) 
[GCC 4.4.3] on linux2


so please help I really need python 3 for my computer lesson

---

### Post by nikhilbhardwaj on 2010-05-10
try
```

python3 -v

```
or
python3.1 -v
if that works

then change the symlink /usr/bin/python

---

