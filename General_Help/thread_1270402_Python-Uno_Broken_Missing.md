---
title: "Python-Uno Broken? Missing?"
date: 2009-09-19
forum: General Help
---

### Post by krgp on 2009-09-19
I upgraded to OOo 3.1 and Python's most recent 3.1.1 (i think that's it). I keep getting errors that python-uno can't be found when I try to install the Mendeley plugin to cite-while-write.

Here's the error:
```
The OpenOffice unopkg utility gave the following output:
ERROR: python object raised an unknown exception ('No module named uno', traceback follows
<NULL>
unopkg failed.
```

So I tried installing python-uno:

```

----:~$ sudo apt-get install python-uno
[sudo] password for krgp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-uno is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
  linux-backports-modules-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So I tried to uninstall/reinstall it:

```

----:~$ sudo apt-get remove python-uno
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
  linux-backports-modules-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openoffice.org-emailmerge python-uno
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 618kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 211045 files and directories currently installed.)
Removing openoffice.org-emailmerge ...

ERROR: There is no such extension deployed: org.openoffice.legacy.mailmerge.py

unopkg failed.
Removing extension org.openoffice.legacy.mailmerge.py...
ERROR: There is no such extension deployed: org.openoffice.legacy.mailmerge.py

unopkg failed.
 done.
Removing python-uno ...
INFO: using unknown version '/usr/bin/python3.0' (debian_defaults not up-to-date?)
krgp@bluebell:~$ 
```

I'm quite noob, so any help needs to give detailed commands. I really appreciate it.

---

### Post by krgp on 2009-09-28
By the way, this problem arose because I'm trying to install a bibliographic plug-in for EITHER Mendeley or Zotero--both generate the same error ("no module named uno") and so I'm figuring this is an openoffice.org / uno problem.

---

