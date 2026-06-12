---
title: "Run a command or script every time a file gets modified"
date: 2010-06-14
forum: General Help
---

### Post by bruno9779 on 2010-06-14
Every time /var/log/auth.log gets modified I need a command to be run.

Any suggestions?

---

### Post by DaithiF on 2010-06-14
Hi,
inotify is probably what you want -- its the kernel system for monitoring changes to files.  Most languages have libraries which wrap the inotify system calls -- eg. pyinotify for python ([http://trac.dbzteam.org/pyinotify](http://trac.dbzteam.org/pyinotify))

---

