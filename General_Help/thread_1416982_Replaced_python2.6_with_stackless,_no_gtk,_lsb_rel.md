---
title: "Replaced python2.6 with stackless, no gtk, lsb_release, pygobject"
date: 2010-02-26
forum: General Help
---

### Post by bobobo1618 on 2010-02-26
Hello various wise ones,

I have, in my infinite wisdom, gone and replaced the official python2.6 from ubuntu with my stackless 2.6.2 3.1b3. Now whenever I attempt to launch Terminator, Rhythmbox, or any other python based gtk software I get something like this:

```
ImportError: No module named gobject

** (rhythmbox:12253): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:12253): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:12253): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
```

I have tried to reinstall python, that didn't fix it. I downloaded the source code of the python gtk bindings but when I try to compile I get this:

```
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers
```

That's just the end of the output from the configure script.

Any ideas?

I had the idea that maybe I could completely remove python and reinstall it. Would that work?

---

