---
title: "weird error while trying to upgrade"
date: 2006-03-27
forum: General Help
---

### Post by bionnaki on 2006-03-27
after running sudo apt-get update and sudo apt-get upgrade, I receive the following errors:

> eg@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python2.4-gnome2-extras (2.12.0-0ubuntu1.1) ...
Compiling /usr/lib/python2.4/site-packages/museek/messages.py ...
  File "/usr/lib/python2.4/site-packages/museek/messages.py", line 603
    def __init__(self, upload = None, user = None, path = None)
                                                               ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-gnome2-extras (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on python2.4-gnome2-extras; however:
  Package python2.4-gnome2-extras is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
Setting up python2.4-ctypes (0.9.6+cvs20050712-1ubuntu2) ...
Compiling /usr/lib/python2.4/site-packages/museek/messages.py ...
  File "/usr/lib/python2.4/site-packages/museek/messages.py", line 603
    def __init__(self, upload = None, user = None, path = None)
                                                               ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-ctypes (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python2.4-pysqlite2 (2.0.3-1) ...
Compiling /usr/lib/python2.4/site-packages/museek/messages.py ...
  File "/usr/lib/python2.4/site-packages/museek/messages.py", line 603
    def __init__(self, upload = None, user = None, path = None)
                                                               ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-pysqlite2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of serpentine:
 serpentine depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing serpentine (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-gnome2-extras
 python-gnome2-extras
 python2.4-ctypes
 python2.4-pysqlite2
 serpentine
E: Sub-process /usr/bin/dpkg returned an error code (1)
ge@ubuntu:~$


how can I fix this?
thanks

---

### Post by bionnaki on 2006-03-27
bump

---

### Post by open_sauce on 2006-03-28
Hi, Looks like nobody is answering, so...

This looks like it is trying to install python-related stuff and getting a syntax error on a def __ini__ line. I think it is probably not a syntax error but rather missing or old python.

Try opening synaptic and de-selecting some of the 'yet to be upgraded' items in favour of python updates.

One of the problems with python is that new versions tend to break old code more than other languages.

Specifically, open synaptic and de-select serpentine (you can search for it) and re-run apt-get update and apt-get upgrade.

Hope this helps...

---

### Post by bionnaki on 2006-03-28
thanks for responding

I opened synaptic and did not see "yet to be upgraded" entries...or even a section like that. I did completely remove serpentine.

after apt-get update/upgrade I am still getting the error:

> @ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python2.4-gnome2-extras (2.12.0-0ubuntu1.1) ...
Compiling /usr/lib/python2.4/site-packages/museek/messages.py ...
  File "/usr/lib/python2.4/site-packages/museek/messages.py", line 603
    def __init__(self, upload = None, user = None, path = None)
                                                               ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-gnome2-extras (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on python2.4-gnome2-extras; however:
  Package python2.4-gnome2-extras is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
Setting up python2.4-sip4-qt3 (4.2.1-1ubuntu4) ...
Compiling /usr/lib/python2.4/site-packages/museek/messages.py ...
  File "/usr/lib/python2.4/site-packages/museek/messages.py", line 603
    def __init__(self, upload = None, user = None, path = None)
                                                               ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-sip4-qt3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4-qt3:
 python2.4-qt3 depends on python2.4-sip4-qt3 (>= 4.2); however:
  Package python2.4-sip4-qt3 is not configured yet.
 python2.4-qt3 depends on python2.4-sip4-qt3 (<< 4.3); however:
  Package python2.4-sip4-qt3 is not configured yet.
dpkg: error processing python2.4-qt3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-qt3:
 python-qt3 depends on python2.4-qt3; however:
  Package python2.4-qt3 is not configured yet.
dpkg: error processing python-qt3 (--configure):
 dependency problems - leaving unconfigured
Setting up python2.4-ctypes (0.9.6+cvs20050712-1ubuntu2) ...
Compiling /usr/lib/python2.4/site-packages/museek/messages.py ...
  File "/usr/lib/python2.4/site-packages/museek/messages.py", line 603
    def __init__(self, upload = None, user = None, path = None)
                                                               ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-ctypes (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python2.4-pysqlite2 (2.0.3-1) ...
Compiling /usr/lib/python2.4/site-packages/museek/messages.py ...
  File "/usr/lib/python2.4/site-packages/museek/messages.py", line 603
    def __init__(self, upload = None, user = None, path = None)
                                                               ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-pysqlite2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.4-gnome2-extras
 python-gnome2-extras
 python2.4-sip4-qt3
 python2.4-qt3
 python-qt3
 python2.4-ctypes
 python2.4-pysqlite2
E: Sub-process /usr/bin/dpkg returned an error code (1)

...which I suppose is the same error. any ideas?

---

### Post by bionnaki on 2006-03-28
well, figured it out. I simply

> sudo dpkg -P python2.4-ctypes python2.4-gnome2-extras python-gnome2-extras python2.4-sip4-qt3 python2.4-qt3 python-qt3 python2.4-pysqlite2

sudo apt-get update/upgrade
works now.

---

