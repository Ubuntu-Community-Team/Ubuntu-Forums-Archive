---
title: "Gwibber, CouchDB wont start"
date: 2010-07-12
forum: General Help
---

### Post by Wiebert on 2010-07-12
Gwibber wont start anymore for some reason..

Output from gwibber:
```

** (gwibber:24585): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:24585): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:24585): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/24800
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/24800/fd'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID24800 exited.  Permissions?
Removing stale, deceptive pid file.

```

Output from couchdb:
```

Apache CouchDB 0.10.0 (LogLevel=info) is starting.
{"init terminating in do_boot",{{badmatch,{error,shutdown}},[{couch_server_sup,start_server,1},{erl_eval,do_apply,5},{erl_eval,exprs,5},{init,start_it,1},{init,start_em,1}]}}

```

Cant seem to find anything about this, someone knows how to fix this ?
Thanks in advance :)

---

### Post by davidmohammed on 2010-07-12
are you using the standard lucid kernel or have you "upgraded" to .34 or a .35 kernel?

---

### Post by Wiebert on 2010-07-12
```
2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010
```

The standard kernel version yes.

---

### Post by mbuotidem on 2010-07-15
Yeah, i have the same problem. I wonder what is wrong. I removed my couchdb and reinstalled it and when i run it from the terminal i got this message: 

```
mbuotidem@NET-SERVER-PC:~$ couchdb
Apache CouchDB 0.10.0 (LogLevel=info) is starting.
{"init terminating in do_boot",{{badmatch,{error,shutdown}},[{couch_server_sup,start_server,1},{erl_eval,do_apply,5},{erl_eval,exprs,5},{init,start_it,1},{init,start_em,1}]}}

Crash dump was written to: erl_crash.dump
init terminating in do_boot ()

```


what could be wrong? :confused:

im missing my gwibber!

---

### Post by Wiebert on 2010-07-15
Gwibber works again for me, i have no idea why / how it works again but it does.
Try installing the latest updates and reboot your computer, thats all i did in the last 3 days..

---

### Post by mbuotidem on 2010-07-16
that's nice to hear, well i installed TweetDeck in the interim and i think it's a great software. so for now i'll stick with it but  will still check Gwibber out later today.

---

