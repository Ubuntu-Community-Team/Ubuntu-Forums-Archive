---
title: "update-alternatives and python and apt"
date: 2010-06-07
forum: General Help
---

### Post by Cowloon on 2010-06-07
I installed python 2.5 from deadsnakes and registered it with update-alternatives. Now, with:

/etc/alternatives/python -> /usr/bin/python2.6
/usr/bin/python -> /etc/alternatives/python

apt complains:

/usr/bin/python does not match the python default version.

If I then:

ln -sf /usr/bin/python2.6 -> /usr/bin/python

The error messages goes away.

In this case, it's less work to use ln -sf to switch between python versions. But, is there a way to get update-alternatives to work with python and apt?

---

### Post by kesten on 2011-12-27
This is still a "Not my bug" as of Oncelot 11.10.

Somebody at update-alternatives needs to talk to somebody at ubuntu and make this stop happening.
If update-alternatives is potentially going to screw up future upgrades they need to warn about this upon install or get pyversion to handle a double sym link case.

I just got roughly the same error trying to upgrade VirtualBox

ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7

However,

/usr/bin$ ls -al | grep python

lrwxrwxrwx 1 root root 24 2011-12-04 16:16 python -> /etc/alternatives/python

/etc/alternatives$ ls -al | grep python

lrwxrwxrwx 1 root root 18 2011-12-04 16:16 python -> /usr/bin/python2.7

so /usr/bin/python is sym linked to /etc/alternatives/python and this is sym-linked to /usr/bin/python2.7

$ python

Python 2.7.2+ (default, Oct 4 2011, 20:06:09)

[GCC 4.6.1] on linux2

...

>>>

That is, /usr/bin/python points to the correct (default debian 2.7) python, but it does so through 2 symlinks.  The extra indirection is messing things up.  The bug lies either with the post-installation script (owned by VirtualBox) requesting the version in a way that doesn't support update-alternatives, or with update-alternatives for not conforming to some expected interface requirements.  Submitting a bug report to both.

kesten

---

