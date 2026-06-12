---
title: "NameError: global name 'os' is not defined"
date: 2010-09-14
forum: General Help
---

### Post by Yrrepperry on 2010-09-14
I am trying to use Google App Engine on Ubuntu, but get this error:
NameError: global name 'os' is not defined

I tried to follow the advice from another thread (below)
(I could not reply to that thread for some reason)
but I don't see this path in python 2.5.2 (which is what Google App Engine recommends).

(Beginner Ubuntu question: I assume I do "gksudo..."in the terminal, but then search through the python directories to open that file. I can't find that file when I search)

(Python 2.6 has 2 files with similar names but that version is not recommended by Google App Engine)



----advice from another thread:
, do the following:

1.  gksudo gedit usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py
2.  Enter password.
3.  Below the # symbols, but above everything else, add the following:

import os
import dbus

4.  Close out of gEdit.
5.  Try upgrading the distro again: gksu "update-manager -c" (you need  the quote marks - usually, quote marks aren't added, but you need them  here).

You don't have to know what the # symbols are used for (if you're curious, they are comment symbols in the programming world).

---

