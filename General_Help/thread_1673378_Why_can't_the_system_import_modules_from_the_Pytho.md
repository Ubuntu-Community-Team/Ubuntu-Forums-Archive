---
title: "Why can't the system import modules from the Python Standard Library in Ubuntu?"
date: 2011-01-22
forum: General Help
---

### Post by c00kiemonster on 2011-01-22
Boy have I had a long day today. Like most Linux days it started out fun but then turned funny.

The whole day was more or less spent reinstalling a basic Gnome Ubuntu system. Everything went swimmingly until I started with the XBMC part of the installation. After wrestling with PPAs and apt-get for hours I finally got it installed, but then it all turned awkward in a hurry.

It simply refused to start up. I clicked the icon and nothing happened for a good few seconds. The screen then flickered black for an instant, but after that nothing. I started from a terminal and it showed an error message saying it couldn't import Python's os and shutil modules. I found that mighty strange since both modules are part of the Python Standard Library.

Finally, in a bizarre twist, it turns out this doesn't seem to be a XBMC problem, suddenly apt-get started complaining too.

TL,DR: I (nor the system) can't import any Standard Library modules in Python in Ubuntu! Help!

Is this a path problem? Or have I actually managed to uninstall some vital python packages, if so which ones?

I am running Ubuntu 10.10 by the way.

Here are some dumps to show the error messages: (I forgot to copy the XBMC error message, but it looked exactly the same as these below, i.e., it couldn't import the os module)

First from apt-get:

```
tv@tv:/usr/lib$ sudo apt-get autoremove
[sudo] password for tv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libqt3-mt python-qt3 python-sip
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 19.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 75111 files and directories currently installed.)
Removing python-qt3 ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
ImportError: No module named os
dpkg: error processing python-qt3 (--remove):
 subprocess installed pre-removal script returned error exit status 1
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
ImportError: No module named os
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing python-sip ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
ImportError: No module named os
dpkg: error processing python-sip (--remove):
 subprocess installed pre-removal script returned error exit status 1
Removing libqt3-mt ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python-qt3
 python-sip
E: Sub-process /usr/bin/dpkg returned an error code (1)
tv@tv:/usr/lib$
```

Second from trying to import the os module in a regular python prompt in the terminal:

```
tv@tv:~$ python
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named os
>>> 
```

---

### Post by c00kiemonster on 2011-01-23
Finally figured it out.

[link]("http://superuser.com/questions/236442/why-cant-the-system-import-modules-from-the-python-standard-library-in-ubuntu")

---

