---
title: "Screenlets and CompizConfig Settings Manager will not start"
date: 2011-04-10
forum: General Help
---

### Post by mistu on 2011-04-10
Hi, I'm kind of new to Ubuntu so there's probably just something simple I'm overlooking, but any help would be appreciated.

When I try to run Screenlets from Applications > Accessories > Screenlets, it says "Starting Screenlets" for a few seconds, and then nothing happens. 'screenlets-manager' from the terminal produces the following
```
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 28, in <module>
    import screenlets
  File "/usr/local/lib/python2.6/dist-packages/screenlets/__init__.py", line 36, in <module>
    import rsvg
ImportError: No module named rsvg
```I have checked to make sure python-rsvg is installed.

Upon looking for a solution, I read somewhere that it might have something to do with Compiz. I installed the Compiz settings manager, but when I run it from System > Preferences > CompizConfig Settings Manager, it does the exact same thing Screenlets does ("Starting CompizConfig Settings Manager", then nothing).

ccsm from the terminal produces the following
```
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: No module named compizconfig
```Are the issues related? How can I solve this?

Thanks in advance.

---

### Post by mistu on 2011-04-14
Bump? :(

---

