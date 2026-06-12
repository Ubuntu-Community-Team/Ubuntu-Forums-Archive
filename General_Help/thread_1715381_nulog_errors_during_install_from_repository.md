---
title: "nulog errors during install from repository"
date: 2011-03-26
forum: General Help
---

### Post by c0mputerking on 2011-03-26
Hello all I am having issues getting nulog to work properly on Ubuntu 10.04 LTS. I can get to the nulog webinterface and it does seem to have 3536 entries in ulog HOWEVER 

I get the following errors/warning during install 

Setting up nulog (2.0.dfsg.1-1) ...
Starting nulog: /usr/lib/python2.6/dist-packages/formless/annotate.py:730: DeprecationWarning: object.__new__() takes no parameters
  rv = cls = InterfaceClass.__new__(cls, name, bases, dct)
/usr/lib/python2.6/dist-packages/nevow/testutil.py:7: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  from popen2 import Popen3
/usr/lib/python2.6/dist-packages/nevow/guard.py:15: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/usr/lib/python2.6/dist-packages/twisted/enterprise/util.py:19: DeprecationWarning: twisted.enterprise.util is deprecated since Twisted 8.0.0.
  category=DeprecationWarning)
DB: SELECT COUNT(*) FROM conntrack_ulog;
DB: SELECT MIN(timestamp), MAX(timestamp) FROM ulog_1;
nulog.

Also while running the triggers.py script I get the error below i did see in the docs that it may have to do with my version of mysql, and that i should remove line 69 however looking at the triggers.py file line 69 does not seem right

cat triggers.py | mysql -uuser -ppass nulog
ERROR 1064 (42000) at line 4: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '"""
Copyright(C) 2007 INL
Written by Romain Bignon <romain AT inl.fr>

This prog' at line 1

---

