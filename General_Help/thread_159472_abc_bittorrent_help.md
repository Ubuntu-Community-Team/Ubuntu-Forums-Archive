---
title: "abc bittorrent help"
date: 2006-04-12
forum: General Help
---

### Post by egghead3 on 2006-04-12
Im trying to get the abc bittorrent client to work in breezy, and having some trouble. I downloaded the python source and have python2.4 and python-wxgtk2.6 installed via synaptic. Attempting to run the command python abc.py yields the following errors.

```

Traceback (most recent call last):
  File "abc.py", line 967, in ?
    run([""], abcpath)
  File "abc.py", line 959, in run
    app = ABCApp(0, params, single_instance_checker, abcpath)
  File "abc.py", line 928, in __init__
    wxApp.__init__(self, x)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "abc.py", line 932, in OnInit
    self.params, self.abcpath)
  File "abc.py", line 697, in __init__
    if (sys.platform == 'win32'):
NameError: global name 'sys' is not defined

```

If anyone has abc working please let me know how. I'm sure im missing something silly...

---

