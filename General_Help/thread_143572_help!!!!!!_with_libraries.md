---
title: "help!!!!!! with libraries"
date: 2006-03-12
forum: General Help
---

### Post by tomach on 2006-03-12
So i have install python and omniORB but i have problem now...cos whenever i try to import omniORB it writes that:

ImportError: /usr/local/src/omniORB4/lib/python2.3/site-packages/_omnipymodule.so: cannot open shared object file: No such file or directory

but the whole point is that i have this library there !!!!! so why it writes taht there is no file even it is!!

help me people!!!

---

### Post by taurus on 2006-03-12
Maybe you want to add this line "usr/local/src/omniORB4/lib/python2.3/site-packages" to your /etc/ld.so.conf using any one of text editors.  Then at the prompt, run
```

ldconfig

```
Now, try to run your program again to see if it can find the library in the right place!!!

---

### Post by tomach on 2006-03-13
Thanks but i added this , and run ldconfig but it doesnt help :(

after i run Python and try to import omniORB this kind of lines appear:

```

>>> import omniORB
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/usr/local/src/omniORB4/lib/python2.3/site-packages/omniORB/__init__.py", line 194, in ?
    import _omnipy
ImportError: /usr/local/src/omniORB4/lib/python2.3/site-packages/_omnipymodule.so: cannot open shared object file: No such file or directory
>>>

```

and this is what i have in :
```

root@tomek:/usr/local/src/omniORB4/lib/python2.3/site-packages# ls
CORBA.py                _omnicodesetsmodule.so.2    _omnipymodule.so
CORBA.pyc               _omnicodesetsmodule.so.2.0  _omnipymodule.so.2
CosNaming               omniidl                     _omnipymodule.so.2.3
CosNaming_idl.py        omniidl_be                  PortableServer__POA.py
CosNaming_idl.pyc       _omniidlmodule.so           PortableServer__POA.pyc
CosNaming__POA          _omniidlmodule.so.1         PortableServer.py
__init__.py             _omniidlmodule.so.1.0       PortableServer.pyc
__init__.pyc            omniORB
_omnicodesetsmodule.so  omniORB.pth
root@tomek:/usr/local/src/omniORB4/lib/python2.3/site-packages#

```

any ideas???

BR
TOM

---

### Post by tomach on 2006-03-13
hey anybody has any idea????

---

### Post by tomach on 2006-03-15
hehhh i really need this :(
so if i removed file _omnipymodule.so it says:

```

import _omnipy
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named _omnipy

```

if i put it back on the place it says:
```

 import _omnipy
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: /usr/local/src/omniORB4/lib/python2.3/site-packages/_omnipymodule.so: cannot open shared object file: No such file or directory

```

so for me it means that it can see the module and library but cant use it somehow....what can be wrong?? someitng with shared libraries at all in my ubuntu???

---

