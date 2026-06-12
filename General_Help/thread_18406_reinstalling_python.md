---
title: "reinstalling python"
date: 2005-03-06
forum: General Help
---

### Post by trash on 2005-03-06
I've accidentally(and stupidly) deleted python and python2.4 while trying to change the link from python -> python2.4 to python -> python2.3.
I've apt the packages but where do I go from here with the configuring of python 2.4 since to install python it requires 2.4.

Or maybe this is an easier route? I have heard there is a way to recover deleted files would this work on python and python2.4 files?

thanks

---

### Post by trash on 2005-03-06
k, I'm pretty sure I just hosed my system lol...
I tried synaptic to reinstall python and python2.4 but there were dependency issues, so of course I tried a more drastic measure... remove python and python2.4 which removed a lot of stuff.
Now I get the same dependency issues trying to install the packages again...
Python depends on python2.4 but
package python2.4 is not configured yet.
Is this something I need to do by hand?

thanks

---

### Post by trash on 2005-03-07
nobody can help me reinstall python or maybe this should be moved to Hoary dev. list?
this is the apt-get output:

Setting up python2.4 (2.4dfsg-1ubuntu3) ...
Compiling python modules in /usr/lib/python2.4 ...
/var/lib/dpkg/info/python2.4.postinst: line 20: /usr/bin/python2.4: No such file or directory
dpkg: error processing python2.4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python:
 python depends on python2.4 (>= 2.4-2); however:
  Package python2.4 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 python2.4
 python
E: Sub-process /usr/bin/dpkg returned an error code 1

---

### Post by trash on 2005-03-09
No progress here, I still have pyhthon2.3 (which python dependecies lists as a conflict?)

I've tried --force-overwrite and a bunch of other things including installing from src to no avail. I've installed all listed dependencies for both python and python2.4... last resort now seems to be removing python2.3, good idea/bad idea, i don't know?

last output now makes refrences to python2.5... is there such a thing??

Setting up python2.4 (2.4dfsg-1ubuntu3) ...
Compiling python modules in /usr/lib/python2.4 ...
/var/lib/dpkg/info/python2.4.postinst: line 20: /usr/bin/python2.4: No such file or directory
dpkg: error processing python2.4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python:
 python depends on python2.4 (>= 2.4-2); however:
  Package python2.4 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-roman:
 python-roman depends on python (>= 2.1); however:
  Package python is not configured yet.
dpkg: error processing python-roman (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-docutils:
 python-docutils depends on python (>= 2.3); however:
  Package python is not configured yet.
 python-docutils depends on python (<< 2.5); however:
  Package python is not configured yet.
dpkg: error processing python-docutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-docutils:
 python2.4-docutils depends on python2.4; however:
  Package python2.4 is not configured yet.
 python2.4-docutils depends on python-docutils; however:
  Package python-docutils is not configured yet.
 python2.4-docutils depends on python-roman; however:
  Package python-roman is not configured yet.
dpkg: error processing python2.4-docutils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4
 python
 python-roman
 python-docutils
 python2.4-docutils
E: Sub-process /usr/bin/dpkg returned an error code (1)

So besides my first grand mistake, wtf am I doing wrong here? anybody?

---

