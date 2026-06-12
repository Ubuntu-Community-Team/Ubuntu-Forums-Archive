---
title: "Can't install Python-Qwt package"
date: 2009-09-06
forum: General Help
---

### Post by prasadbrg on 2009-09-06
Hello everyone,
  I'm running Xubuntu Jaunty 9.04. I need to install the package python-qwt5-qt3 (alernatively python-qwt4). Here's the problem (which is the same for both packages):```
$ sudo apt-get install python-qwt4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-qwt4: Depends: python (< 2.6) but 2.6.2-0ubuntu1 is to be installed
E: Broken packages

```
I would appreciate any help/pointers in this regard.
Thanks in advance!
Cheers,
Guru

---

### Post by Liolikas on 2009-09-06
looks like bug report to Ubuntu bugzilla. I think rep has to add new version of python-qwt4, because this one do not work with new python.

---

### Post by prasadbrg on 2009-09-06
Thanks for the reply, Liolikas.
I noticed that a [bug report]("https://bugs.launchpad.net/ubuntu/+source/pyqwt/+bug/397468") has just been submitted. I hope this gets resolved soon!
Cheers,
Guru

---

### Post by DRNewcomb on 2009-09-16
Good, I'm glad it wasn't just me.

---

### Post by bhanuchandu on 2009-11-18
we r also facing d same problem.
is it necessary to install python-qwt4?
and what happens if it is not installed?

---

