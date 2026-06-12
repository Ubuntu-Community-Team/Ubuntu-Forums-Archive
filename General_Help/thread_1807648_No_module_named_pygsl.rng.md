---
title: "No module named pygsl.rng"
date: 2011-07-19
forum: General Help
---

### Post by jstevens199 on 2011-07-19
Hello,

I'm trying to run a python based (I'm running 2.7 on Natty) program, but I'm having problems with the pyGSL. I have installed the latest version of the gsl and pygsl. Whenever I run the program I get the following: 

```
josh@heng-scope:~/Downloads/pGQL$ python pGQL.py
Traceback (most recent call last):
  File "pGQL.py", line 44, in <module>
    import GQL
  File "/home/josh/Downloads/pGQL/GQL.py", line 57, in <module>
    from GQLQueryEditor import *
  File "/home/josh/Downloads/pGQL/GQLQueryEditor.py", line 39, in <module>
    import pygsl.rng
ImportError: No module named pygsl.rng
```

I have looked throughout my filesystem and cannot find the location of pygsl.rng. Has anyone else had a similar problem? Any ideas where that file may be, or if maybe I'm lacking software?

Thanks for your help,
Josh

---

### Post by raja.genupula on 2011-07-19
[http://sourceforge.net/tracker/?func=detail&aid=810861&group_id=34743&atid=412366](http://sourceforge.net/tracker/?func=detail&aid=810861&group_id=34743&atid=412366)

---

### Post by jstevens199 on 2011-07-19
I saw that page, but it seems that it is not the same problem that I am having. That bug was fixed over 7 years ago. That said, I cannot find the file which they are referring to, "pygsl.testing.rng". It seems not to be included.

I found a file for what appears to be a random number generator (rng.py), but simply changing out the code in question 
```
from Tkinter import *
#from ProbEditorContinuous import gauss_function # Also imports PyGSL!
from GQLQuery import GQLQuery
import pygsl.rng
import math
import colorsys
```

to ```
from Tkinter import *
#from ProbEditorContinuous import gauss_function # Also imports PyGSL!
from GQLQuery import GQLQuery
import rng.py
import math
import colorsys
```
probably unsurprisingly doesn't work.

Forgive me if it seems as if I am at least slightly retarded, Linux and Python are completely new to me

---

