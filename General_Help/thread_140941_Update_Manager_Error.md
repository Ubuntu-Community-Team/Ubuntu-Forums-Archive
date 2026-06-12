---
title: "Update Manager Error"
date: 2006-03-07
forum: General Help
---

### Post by teataster on 2006-03-07
Update Manager and Add Applications not working, but Synaptic and apt-get seem to be fine.

I had a look at some posts and have tried apt-get update, 
-f install and dist-upgrade.

I then ran Update Manager from the command line with the following results-

daniel@ubuntu:~$ gksudo /usr/bin/update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 27, in ?
    import gtk
  File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?
    import gobject as _gobject
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode

Any suggestions would be very welcome!

---

### Post by teataster on 2006-03-14
Have now fixed this following detective work done [here](http://www.ubuntuforums.org/showthread.php?t=136863&page=2&highlight=python+install) by wile_e8 - thank you!

This was caused by new versions of Python and pygtk being compiled and installed to  different directories following an install of gDesklets using the instructions [here](http://www.ubuntuforums.org/showthread.php?p=692118#post692118) which caused a clash with the versions already installed with Ubuntu.

I can't tell you exactly what fixed the problem as I also reinstalled Python and pygtk from the repositories as well as deleting the new duplicate Python and pygtk directories but I now have Update Manager back.   gDesklets is back to version 35.2 which works with the desklets I am using at the moment.

I wonder if this fix will work for similar problems reported on Dapper Drake?

---

