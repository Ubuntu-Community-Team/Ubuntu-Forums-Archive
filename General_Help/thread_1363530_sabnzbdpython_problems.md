---
title: "sabnzbd/python problems"
date: 2009-12-24
forum: General Help
---

### Post by ptviperz on 2009-12-24
I had to reinstall Karmic last night and now my formerly wonderfully working sabnzbd spits out these errors when I try to start it

```
brent@brent-desktop:~$ sudo /etc/init.d/sabnzbdplus start
 * Starting SABnzbd+ binary newsgrabber                                                                                             Traceback (most recent call last):
  File "/usr/bin/sabnzbdplus", line 45, in <module>
    import sabnzbd
  File "/usr/share/sabnzbdplus/sabnzbd/__init__.py", line 51, in <module>
    from sabnzbd.assembler import Assembler
  File "/usr/share/sabnzbdplus/sabnzbd/assembler.py", line 33, in <module>
    from sabnzbd.interface import CheckFreeSpace
  File "/usr/share/sabnzbdplus/sabnzbd/interface.py", line 44, in <module>
    from configobj import ConfigObj
  File "/usr/lib/pymodules/python2.5/configobj.py", line 788
    elif isinstance(this_entry, list):                # create a copy rather than a reference
                                      ^
SyntaxError: invalid syntax

```

I have no idea what's going on or how to fix other than a reinstall....anyone have any ideas on how to fix?

I've tried apt-get remove --purge of sab and then reinstalled, I've deleted the .sab dir and started over, etc. etc. but it seems like maybe a python problem.

---

### Post by gsmanners on 2009-12-24
Try reinstalling the "python-configobj" package. That seems to be where you're getting the error from.

---

### Post by ptviperz on 2009-12-24
Thanks for the response but it was no joy, I reinstalled and sab is working again.

---

