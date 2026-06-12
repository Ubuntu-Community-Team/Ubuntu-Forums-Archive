---
title: "Ubuntu 10.10 - Python 2.7 lsb_release"
date: 2010-11-03
forum: General Help
---

### Post by martinh78 on 2010-11-03
I installed Python (IDLE) 2.7 from the Ubuntu Software Centre. All good. I them deleted the symlink /usr/bin/python and recreated it to point at /usr/bin/python2.7

Now if I ctrl-alt-F1 to a virtual terminal, a python error comes up "no module named lsb_release". I checked the /usr/lib/python2.7/dist-packages directory, and sure enough there isn't anything called lsb_release, whereas there are for python2.6

Do I need this package in Python 2.7, and if so, how do I go about getting it?

Thanks,

Martin.

---

### Post by oldfred on 2010-11-03
Welcome to the forum.

I think you have it backwards. Big parts of Ubuntu run on python 2.6 and you should not change that. 

If you want to run 2.7 for anything you can just specify that at run time.

---

### Post by taleia on 2011-02-17
> **oldfred said:**
> If you want to run 2.7 for anything you can just specify that at run time.

Is that something that's easy to do?  I'm running Ubuntu 10.10 and want to install a package that requires python 2.7, but I don't want to mess up my system doing an upgrade.

I'm a complete noob to linux so any help would be greatly appreciated.

---

