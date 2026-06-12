---
title: "Wallbox won't start"
date: 2010-01-29
forum: General Help
---

### Post by dmillerw on 2010-01-29
I'm attempting to run Wallbox, a Facebook notifier for Ubuntu, but keep getting this error

> dylan@Zeus:~$ wallbox
Traceback (most recent call last):
  File "/usr/bin/wallbox", line 5, in <module>
    from pkg_resources import load_entry_point
ImportError: No module named pkg_resources


---

### Post by yurenju on 2010-02-04
please install python-setuptools, we will fix dependency on next version

---

### Post by afri.ca on 2011-04-03
hi all!

my problem is a little different: when i first try to activate wallbox with the "first run wizard" i get an error message from the facebook page, that there is a problem and i should try again later. 

according to the net this seems to be a common problem. isn't there any sollution for that?

---

