---
title: "Pyton development package"
date: 2006-06-13
forum: General Help
---

### Post by zugu on 2006-06-13
I'm trying to compile a game from source. However I need some deps. In the readme file of the game I found advice for exactly the problem I have:```
If you get an error like :

[... lots of text here ...]
distutils.errors.DistutilsPlatformError: invalid Python installation:
unable to open /usr/lib/python2.2/config/Makefile (No such file or directory)
Traceback (most recent call last):
  File "./setup.py", line 28, in ?
    do("cd %s; python setup.py %s -f" % (package_dir, " ".join(sys.argv[1:])))
  File "./setup.py", line 12, in do
    raise RuntimeError, command
RuntimeError: cd soya; python setup.py build -f

or something about "python2.X/config/Makefile", you NEED to install
the Python development package for your distribution
(libpython2.X-devel on Mandrake).

```

Is the [python-dev]("http://packages.ubuntu.com/dapper/python/python-dev") package in the repos the Debian/Ubuntu equivalent of Mandrake's libpython2.X-devel ?

---

### Post by scxtt on 2006-06-13
[QUOTE=zugu]Is the [python-dev]("http://packages.ubuntu.com/dapper/python/python-dev") package in the repos the Debian/Ubuntu equivalent of Mandrake's libpython2.X-devel ?[/QUOTE]yup ...
> from synaptic description of python2.4-dev:

**Header files and a static library for Python (v2.4)**
Header files, a static library and [color=red]development[/color] tools for building
Python (v2.4) modules, extending the Python interpreter or embedding
Python (v2.4) in applications.

Maintainers of Python packages should read README.maintainers.just make sure you download the dev. package for the version of python that's currently installed:```
:> python -V
Python 2.4.3
```

---

### Post by zugu on 2006-06-13
Thank you, I managed to compile the game :)

---

