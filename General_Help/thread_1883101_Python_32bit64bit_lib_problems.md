---
title: "Python 32bit/64bit lib problems"
date: 2011-11-18
forum: General Help
---

### Post by jmb52695 on 2011-11-18
I am trying to run a 32 bit python script on my Ubuntu 11.10. However, when it tries to load the random and math libraries it tries to load the 64 bit ones as those are the ones in /usr/local/lib/ How do i get the 32 bit python 2.7 libs (to get this script to work as much as it is i had to install python 2.7 from source, it would not run at all with the python installed via the package manager) and how to i get the py script to load the 32 bit ones? I have ia32-libs installed, but that does not seem to do it. Any help?

Here are the errors i get when i try to run it:

Traceback (most recent call last):
  File "/home/jared/X-Plane 9/Resources/plugins/PythonScripts/PI_GroundServices.py", line 34, in <module>
    from random import randint
  File "/usr/local/lib/python2.7/random.py", line 45, in <module>
    from math import log as _log, exp as _exp, pi as _pi, e as _e, ceil as _ceil
ImportError: /usr/local/lib/python2.7/lib-dynload/math.so: wrong ELF class: ELFCLASS64
'PI_GroundServices' failed to load

Thanks in advance!

---

### Post by jmb52695 on 2011-11-18
Well, after a bit more research, i have to have the 32 bit version of python. So how can i build the 32 bit version of python and install it on my Ubuntu without compromising the 64 bit one? and then how do i make the py script use the 32 bit libraries from that one?

---

