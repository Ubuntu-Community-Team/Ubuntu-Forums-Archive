---
title: "problem with php mod_python and MySQLdb"
date: 2006-04-18
forum: General Help
---

### Post by aero142 on 2006-04-18
I am trying to connect to a database from mod_python and I am getting segmentation faults in the apache log.  I found this in an FAQ which vaguely addresses the problem. 
______________________________________________
mod_python FAQ Entry
2.13. mod_python and MySQLDb won't work together
People have reported a number of problems running MySQLDB under mod_python. MySQL code that works fine from the command line breaks when run under mod_python, with a variety of symptoms:

 - "select *" or "select a, b" fails but "select a" works
 - apache coredumps
 - get bogus error messages about float conversions when no float fields are used

usually in the MySQL cursor.execute() routine.

The solution (from David Geller) is as follows:

In my httpd.conf I was loading two DSO modules: mod_python and php4. It turns out, when I removed the reference to php4, the mod_python worked perfectly. Now, why was this? Well, I went back to the php4 module, and checked out "configure" - if you know anything about php, it was being configured with the "--with-mysql" flag, which tells it to use an "internal" version of mysql libs. Apparently, this is fine - as long as *no other modules use mysql* (the php configure tells you this at the end). If they do, you should specify the actual mysql library directory. Well, mod_python was basically another module using mysql. Duuuuh! (well, not so obvious to me, really). When I specified the actual mysql library to php configure, and recompiled and reinstalled the PHP, I could have LoadModules for both php and mod_python and both appear to work.

Thanks David! 
__________________________________________________________
from [http://www.modpython.org/FAQ/faqw.py?req=show&file=faq02.013.htp]("http://www.modpython.org/FAQ/faqw.py?req=show&file=faq02.013.htp")


How hard is it to reinstall PHP?  Am I just reinstalling PHP or mod_php.  Is there anyway to change the configure options without going back to souce and abandoning the ubuntu packages?  I'm not too excited about rebuilding from source because I just don't know that much about Linux yet.  Any help would be appreciated.

---

