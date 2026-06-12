---
title: "python-scipy installed, but won't load"
date: 2011-07-27
forum: General Help
---

### Post by Lyuokdea on 2011-07-27
```

t@xx:~$ python
Python 2.6.5 (r265:79063, May 12 2011, 21:34:16) 
[GCC 4.1.2 20080704 (Red Hat 4.1.2-50)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
>>> import scipy
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named scipy
>>> from scipy import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named scipy

```

However, I've run sudo apt-get install python-scipy and the package appears to be correctly installed. I've removed scipy and reinstalled it (in case there was some error with the installation), and that also didn't fix any problems. 

Is there anything else I should check?

Thanks,

~Lyuokdea

---

### Post by Lyuokdea on 2011-07-28
any ideas on how to fix that? I've tried installing the enthought tools, but they don't seem to work either.

Thanks,

~Lyuokdea

---

### Post by NERDMAN! on 2011-07-28
so you've installed it by commandline? interesting, i installed the scipy and numpy packages through ubuntu software center and it worked just fine, i never even had to manually import them via commandline.
perhaps it might be wise to uninstall scipy via commandline, then use the onboard package manager of your distro to reinstall it.

otherwise i wish i could help. all i can say is mine worked out of the box and i wish you the best of luck working with python. :D

---

### Post by Lyuokdea on 2011-07-28
I don't have access to the computer (it's remote) - so I can't install via GUI - but I'm not sure if that will make a difference, so long as I am using the aptitude installer?

Thanks,

~Lyuokdea

---

