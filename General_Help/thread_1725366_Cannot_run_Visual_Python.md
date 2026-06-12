---
title: "Cannot run Visual Python"
date: 2011-04-09
forum: General Help
---

### Post by vamc on 2011-04-09
I installed vpyhton package from Synaptic in Ubuntu 10.10. When I tried to run an example, this is the output I got:


```
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from visual import *
>>> sphere()

(<unknown>:1977): GdkGLExt-WARNING **: Cannot open `"`
L.so

(<unknown>:1977): GdkGLExt-WARNING **: Cannot open `"`
L.so

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: Unable to get extension function: glCreateProgramObjectARB even though the extension is advertised.

aborting...
Aborted
```


Am I missing something?

Thanks in advance.

---

### Post by wojox on 2011-04-09
sphere() is only an empty object. Try setting some attributes and values.

---

