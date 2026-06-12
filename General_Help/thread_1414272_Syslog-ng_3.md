---
title: "Syslog-ng 3"
date: 2010-02-23
forum: General Help
---

### Post by letharion on 2010-02-23
I would like to send the logs of a specific server to a remote system, and I'm recommended to use syslog-ng 3 for this.
AFAICT syslog-ng 3 isn't in Ubuntus repos?
I tried installed both a .deb archive, and compiling the source myself, but failed.

The primary question:
Has anyone else used syslog-ng 3 on a server and would like to direct me to instructions?

Second:
If installing from the .deb archive, how do I restart the process?

Third:
Last option, if I need to compile myself, what do I need to install to resolve:
checking for GLIB - version >= 2.10.1... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: Cannot find GLIB version >= 2.10.1: is pkg-config in path?
91891-configure:7059: checking for GLIB - version >= 2.10.1
91945-configure:7192: result: no
91972-configure:7220: gcc -o conftest -g -O2 -Wall    conftest.c   >&5
92037:conftest.c:42:18: error: glib.h: No such file or directory
92096-conftest.c: In function 'main':
92128:conftest.c:48: error: 'glib_major_version' undeclared (first use in this function)
92211-conftest.c:48: error: (Each undeclared identifier is reported only once
92283-conftest.c:48: error: for each function it appears in.)
92339:conftest.c:48: error: 'glib_minor_version' undeclared (first use in this function)
92422:conftest.c:48: error: 'glib_micro_version' undeclared (first use in this function)

---

