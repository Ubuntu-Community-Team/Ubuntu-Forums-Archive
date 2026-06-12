---
title: "synaptic/updatemanager don't find apt/wx modules"
date: 2009-11-02
forum: General Help
---

### Post by flatulusrex on 2009-11-02
I'm not exactly green but definitely no geek -- interested in java/python/blender and try to avoid os issues -- so that's my caveat and here's the problem:

Running 9.04 on a typical pc. Needed to run winpdb with python and blender, but got wx module not found, so trolled forums and tried many variations including updating wx using apt-get and compiling python from source (am now at 2.6.3).  Deduced from discussions that wxPython is binding to 2.5 instead of 2.6, so removed python 2.5 which I now understand was a disastrous thing to do.

synaptic now can't find the apt module, and update-manager can't find module pygtk, even after reinstalling python 2.5, reinstalling wx (apt-get install --reinstall python-wxgtk2.8 python-wxtools wx2.8-i18n) and reinstalling update-manager using synaptic (or seeming to).

following are the output from executing python, update-manager, and synaptic (synaptic does run despite the complaint).

steve:~$ python
Python 2.6.3 (r263:75183, Oct 22 2009, 21:47:23) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import wxversion
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named wxversion
>>> import wx
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named wx

steve:~$ sudo update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk

steve:~$ sudo synaptic
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 484, in <module>
    import apt
ImportError: No module named apt

Would *really* like to get update-manager working so that a network upgrade to 9.10 is possible, hopefully finessing my current problem.  I have in fact attempted such an upgrade with the alternate cd, but this became a semi-disaster as I  booted from the cd and so got an install not an upgrade (a forced-march of an install, as the 'guided' partitioning option dangles 'cancel' and 'go back' options in front of you, but ignores them and presses on without really telling you what it's up to, just displaying 'reformatting partition' with a progress bar seemingly stuck at 0%, but in the background you hear the ominous tick tick of your harddrive -- really the perfect activity  for Halloween) therefore have cleaved my ubuntu partition into two pieces: 9.04 with all my data and apps, 9.10 brand-spanking-clean.  Subsequent attempts to upgrade from the alternate cd (without booting from it) die silently.

Any help, advice?

---

### Post by liquidbee on 2009-11-02
```
sudo apt-get install python-wxgtk2.6 python-wxversion python-gtk2 python-apt

```

---

### Post by flatulusrex on 2009-11-02
Tried the above. No change in symptoms.  Then tried reinstalling update-manager via synaptic -- still no change.

---

### Post by flatulusrex on 2009-11-04
Okay, moved all my stuff onto the accidentally installed 9.10.  Problem solved.

---

