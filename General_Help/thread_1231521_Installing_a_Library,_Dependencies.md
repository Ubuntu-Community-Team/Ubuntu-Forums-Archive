---
title: "Installing a Library, Dependencies"
date: 2009-08-04
forum: General Help
---

### Post by captcadaver on 2009-08-04
Hi,

I'm pretty horrible at trying to install stuff in Ubuntu. Installing packages is pretty easy, but installing this library isn't going so well.

I want to install:

[http://code.google.com/p/python-twitter/](http://code.google.com/p/python-twitter/)

So, I go to this site to take care of the dependencies:

[http://pypi.python.org/pypi/simplejson/](http://pypi.python.org/pypi/simplejson/)

I ran "python ez_setup.py" and it said that setuptools had been installed. I don't know anything about this, but I've been reading:

[http://peak.telecommunity.com/DevCenter/EasyInstall#using-easy-install](http://peak.telecommunity.com/DevCenter/EasyInstall#using-easy-install)

I don't see any .egg files, so that seems to be a dead end.

I tried "python setup.py build" and all I got were many errors about functions being undeclared, probably because I don't have that .egg file anywhere to be installed.

Suggestions?

---

### Post by llamabr on 2009-08-04
Why bother fighting with egg files?

```
brock@hops:~$ apt-cache search python twitter
python-twitter - Twitter API wrapper for Python
python-twyt - An interface to Twitter API functions for Python
brock@hops:~$ 

```

---

