---
title: "Missing menubar in some programs, gwibber not starting"
date: 2010-06-23
forum: General Help
---

### Post by Ekeluo on 2010-06-23
I have a couple of issues on an otherwise problem-free lucid install on my laptop: 

1) The menubar is invisible (as in completely missing, the space isn't even there, almost as if it was set to hidden) in some programs, so far Gauyadeque music player and xiphos. I have a lot a lot of gtk themes installed however all other programs function correctly with menubar and all.

2) Gwibber won't start properly, no gui shows though several processes run when I start it via any method (Indicator Applet Session, icon in menu, terminal). This is the only terminal output

```
ekeluo@Kels-A935:~$ gwibber

** (gwibber:23707): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:23707): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:23707): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/23813
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/23813/fd'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID23813 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.

```

Seriously, time to relax? Actually quite funny,... or not.

Another minor thing, the tab autocomplete in terminal isn't comprehensive, am I missing something (sorry kinda used to konsole, haven't download it yet). E.g it should complete apt-get instructions like **install**, **remove** etc and also package names but it doesn't do this.

---

### Post by Ekeluo on 2010-06-23
Found the solution for the missing menubars, partly my fault, installed globalmenu but wasn't using it. Did a complete purge and all menubars are back.

---

