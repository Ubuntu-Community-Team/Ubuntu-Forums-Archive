---
title: "gdebi gone very wrong..."
date: 2010-08-23
forum: General Help
---

### Post by shantiq on 2010-08-23
tried to use gdebi and i am getting this

this is on a fairly recent clean install tried rmove purge reinstall and still the same

```
shantiq@shantiq-desktop:~$ gdebi
Traceback (most recent call last):
  File "/usr/bin/gdebi", line 35, in <module>
    from GDebi.GDebiCli import GDebiCli
  File "/usr/lib/python2.6/dist-packages/GDebi/GDebiCli.py", line 35, in <module>
    from DebPackage import DebPackage, Cache
  File "/usr/lib/python2.6/dist-packages/GDebi/DebPackage.py", line 26, in <module>
    import apt_inst, apt_pkg
ImportError: /usr/lib/libapt-inst-libc6.10-6.so.1.1: undefined symbol: ctTar4DoneEb
shantiq@shantiq-desktop:~$ 

```


it does not start when i double-click on a deb

any ideas about what the terminal says here i am puzzled

---

