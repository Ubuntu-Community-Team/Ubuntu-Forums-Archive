---
title: "can' open printing options"
date: 2011-10-02
forum: General Help
---

### Post by JCM_Pico on 2011-10-02
Hi there,

when I go to System > Administration > Printing nothing appens.

I tryed to run it in command line and I got this

system-config-printer

```
File "/usr/share/system-config-printer/system-config-printer.py", line 31, in <module>
    from timedops import *
  File "/usr/share/system-config-printer/timedops.py", line 20, in <module>
    import gobject
ImportError: No module named gobject

```

Any guess in how to solve this?

---

### Post by Toz on 2011-10-08
Have you been doing anything with python? Installing extra/other versions?

Try this:
```
$ which python
/usr/bin/python

$ python --version
Python 2.7.2+

head -1 /usr/share/system-config-printer/system-config-printer.py
#!/usr/bin/python

```

---

