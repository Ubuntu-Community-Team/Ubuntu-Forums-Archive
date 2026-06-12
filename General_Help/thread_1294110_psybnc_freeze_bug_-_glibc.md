---
title: "psybnc freeze bug - glibc"
date: 2009-10-17
forum: General Help
---

### Post by sk0t1337 on 2009-10-17
Psybnc is an irc bouncer the only one i know of that supports multi-network-per-single-user-and-single-irc-client-connection, because of that even tho is is VERY out of date is is still very much used now days.

But it has a "freeze bug" this bug happens when the irc has been running for a perord of 12-24 hrs and depending on your server this time span can be longer... it will stop accepting client connections.

And become useless that that point the only fix is to kill -9 the bnc and start it backup

But i have found a way of fixing this bug, more or less a work around.

If someone was to compile psybnc on an older glibc lib the warnings should stop and the freeze bug should go away.

I myself am not as well skilled with Ubuntu as others so i was wondering if someone here could show me how to compile psybnc with older glibc libs, so i can fix this bug...

Bug report: [http://sourceforge.net/apps/trac/psybnc/ticket/1](http://sourceforge.net/apps/trac/psybnc/ticket/1)
Anothers post about the same bug: [http://ubuntuforums.org/showthread.php?t=471811](http://ubuntuforums.org/showthread.php?t=471811)

Thanks sk0t.

---

