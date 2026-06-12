---
title: "thread-safe version of libsqlite3"
date: 2010-12-02
forum: General Help
---

### Post by wworld on 2010-12-02
Hello everybody.

(For svn) I need a threadsafe version of the SQLite3 shared library. The one contained in the libsqlite3-0 package isn't thread-safe obviously. So I got a threadsafe build from the sqlite homepage and placed it in /usr/local/lib/.
But when I adjust the corresponding symlink (/usr/local/lib/libsqlite3.so.0), this gets undone nearly every time I run apt-get upgrade.
What would be the proper solution?

---

### Post by searchfgold6789 on 2010-12-02
I thought the entirety of SQlite was threadsafe by default. But I guess it is now not.
Try 3.2

---

### Post by wworld on 2010-12-02
The only packages I can find in the repository are *libsqlite3-0* and *libsqlite0*. Both are installed and svnadmin complains "SQLite is required to be compiled and run in thread-safe mode".
When I replace the library manually with v3.7.3 from the sqlite homepage it works, but gets reverted by apt-get upgrade.

---

### Post by wworld on 2010-12-10
Can really nobody tell me, how I am supposed to do changes in usr/local/lib without them being reverted on *apt-get upgrade?*

---

