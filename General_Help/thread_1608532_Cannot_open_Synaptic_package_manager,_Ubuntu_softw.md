---
title: "Cannot open Synaptic package manager, Ubuntu software centre etc"
date: 2010-10-29
forum: General Help
---

### Post by gamepoint on 2010-10-29
i tried to install Redshift's PPA then an error occure, ater that , my sotware centre is not working, after i click the ubuntu software centre, nothing's happening..and also i cannot open synaptic package manager.But there is an error coming out

```
E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/jonls-redshift-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

here are the errors i got after tried to open Ubuntu tweak

```
Distribution: Ubuntu 10.10
Application: Ubuntu Tweak 0.5.7
Desktop: gnome

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py", line 102, in list_autoremovable
    for pkg in self.cache.keys():
AttributeError: 'NoneType' object has no attribute 'keys'
```

here's some more

```
Distribution: Ubuntu 10.10
Application: Ubuntu Tweak 0.5.7
Desktop: gnome

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py", line 437, in setup_notebook
    page = module()
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/nautilus.py", line 111, in __init__
    self.nautilus_terminal = AptCheckButton(_('Open folder in terminal'), 'nautilus-open-terminal')
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py", line 314, in __init__
    self.set_active(self.get_state())
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py", line 318, in get_state
    pkg = PACKAGE_WORKER.get_cache()[self.pkgname]
TypeError: 'NoneType' object is unsubscriptable

```

:(

---

### Post by plucky on 2010-10-29
> E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/jonls-redshift-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



Post output from a terminal of ```
cat etc/apt/sources.list.d/jonls-redshift-ppa-maverick.list
```

---

### Post by gamepoint on 2010-10-29
i finally solved it...
run ```
sudo gedit /etc/apt/sources.list

```

n delete the "n"..problems solved:popcorn:
thanx btw my friend

---

### Post by plucky on 2010-10-29
Well Done 

To mark Thread as [SOLVED] use Thread Tools at top of page

---

