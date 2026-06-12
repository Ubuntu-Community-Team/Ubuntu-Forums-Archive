---
title: "Howto repair broken (pythonpath) zeitgeist ?"
date: 2010-01-28
forum: General Help
---

### Post by qwill on 2010-01-28
I installed manually an old version of zeitgeist (was 0.2 I guess) by using bzr a few monthes ago.
It didn't work (due to a problen with Python Path I guess : 

```
Traceback (most recent call last):
  File "/usr/local/bin/zeitgeist-daemon", line 30, in <module>
    from zeitgeist import _config
ImportError: cannot import name _config

```


When the new version was announced in zeitgeist ppa, I zapped the old version ( in usr/local/*) and installed the new one the "right" way : apt-get install ...

I have the same error when firing zeitgesit-daemon : 
```
Traceback (most recent call last):
  File "/usr/bin/zeitgeist-daemon", line 30, in <module>
    from zeitgeist import _config
ImportError: cannot import name _config

```

I tried to purg/reinstall zeitgeist, python 2.5 python 2.6 python packages ... no success. 
Any hints where's the devil's hidden ??

Thanks a lot,
Qwill.
Whereis the PYTHONPATH set ?

---

### Post by qwill on 2010-01-28
Half-Solved : 
The following command enables zeitgeist-daemon to run :P : 
```

PYTHONPATH=/usr/share/pyshared:/usr/lib/pyshared:/usr/lib/pyshared/python2.5:/usr/lib/pyshared/python2.6:/usr/lib/pyshared/python2.6:/usr/lib/pyshared/python2.6 : export PYTHONPATH

```
Then gnome-activity-journal complains :mad: : 
```
gnome-activity-journal 
Traceback (most recent call last):
  File "/usr/bin/gnome-activity-journal", line 25, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
  File "/usr/share/pyshared/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: No module named _cairo
```

What is the "normal" PYTHONPATH ?
Is there a way to reconfigure Python ? 
(Tried dpkg-reconfigure python) without success...

---

### Post by RainCT on 2010-01-29
I guess you're missing /usr/lib/pymodules/python2.6/gtk-2.0 in there.

---

### Post by qwill on 2010-02-01
Thanks for the hint, I reinstalled the python-cairo and python-gtk2 packages, as suggested by these threads : 
[http://ubuntuforums.org/showthread.php?t=86849](http://ubuntuforums.org/showthread.php?t=86849)
[http://ubuntuforums.org/showthread.php?t=768563](http://ubuntuforums.org/showthread.php?t=768563)

It didn't solve the problem.

To summarize, 2 questions are now to be answered : 
1. Where is the PYTHONPATH set up, and what is the correct content of this variable ?
2. What are the faulty packages, and how force their correct reinstallation... 

* Weird thing is that on my others laptops, (same ubuntu distrib) zeitgeist and gnome-actovity-journal work like a charm...

(to follow...)

---

### Post by warfacegod on 2010-02-01
As for #2 I'd say try using Synaptic> Edit> Fix Broken Packages

---

### Post by qwill on 2010-02-01
Finally, I found the solution by comparing the content of /usr/lib/python2.6 on both laptop.

There was a faulty directory left by previous installation of zeitgeist ( installing the source) : /usr/lib/python2.6/dist-pakages/zeitgeist.

I simply removed it and zeitgeist is now working !!!

Thanks for everyone's help and hints.

By the way, the following thread is usefull if you suspect having a problem with your PYTHONPATH :
[http://ubuntuforums.org/showthread.php?t=916419](http://ubuntuforums.org/showthread.php?t=916419) 

Qwill :p

---

