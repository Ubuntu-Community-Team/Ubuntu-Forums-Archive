---
title: "Flexget install help?"
date: 2009-11-17
forum: General Help
---

### Post by Hackit on 2009-11-17
Hi all,

I need some assistance, has anyone installed flexget?

I keep getting errors when I follow the steps on the wiki for flex get.
[http://flexget.com/wiki/InstallEgg](http://flexget.com/wiki/InstallEgg)

ex:
*******@********:~$ sudo easy_install FlexGet-1.0r869-py2.6.egg
Searching for FlexGet-1.0r869-py2.6.egg
Reading [http://pypi.python.org/simple/FlexGet-1.0r869-py2.6.egg/](http://pypi.python.org/simple/FlexGet-1.0r869-py2.6.egg/)
Couldn't find index page for 'FlexGet-1.0r869-py2.6.egg' (maybe misspelled?)
Scanning index of all packages (this may take a while)
Reading [http://pypi.python.org/simple/](http://pypi.python.org/simple/)
No local packages or download links found for FlexGet-1.0r869-py2.6.egg
error: Could not find suitable distribution for Requirement.parse('FlexGet-1.0r869-py2.6.egg')

I was not sure where to post, hope this is the wright place.

---

### Post by Hackit on 2009-11-18
Has anyone tried to install this?

---

### Post by Hackit on 2009-11-18
Ok I have sorted it out, after python is installed I ran this command,

easy_install [http://download.flexget.com/unstable/FlexGet-1.0r947-py2.6.egg](http://download.flexget.com/unstable/FlexGet-1.0r947-py2.6.egg)

It's working now just need to configure.

hope this helps someone else.

---

### Post by qbase on 2009-12-05
> **Hackit said:**
> 

hope this helps someone else.


It helped me, was able to install flexget on my QNAP 239 Pro thanks to your post :D

---

