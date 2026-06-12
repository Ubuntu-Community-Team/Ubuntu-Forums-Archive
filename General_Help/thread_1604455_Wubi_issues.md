---
title: "Wubi issues"
date: 2010-10-24
forum: General Help
---

### Post by boburob on 2010-10-24
Trying to install ubuntu on a crappy £100 netbook i bought.

The torrent runs fine(but INCREDIBLY slowly) and then once the download finishes I get this error:

```
in task download
10-23 23:23 DEBUG  TaskList: ### Finished download
10-23 23:23 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
10-23 23:23 DEBUG  TaskList: # Cancelling tasklist
10-23 23:23 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
10-23 23:23 DEBUG  TaskList: # Finished tasklist

```

Im running XP and its a system admin account so I cant understand why im getting permissions issues....

Any help would be great!

EDIT: Should probably mention I was trying to install using wubi!

---

### Post by bcbc on 2010-10-24
You didn't include the whole wubi log file. Can you look and tell me if wubi is at release 10.04.1? If it is, then it won't work with netbook edition.

The reason is that wubi.exe is release specific and for some reason, it was made to run at 10.04.1 and yet there was no netbook released at this version. So, it just won't work.

You can either find the 10.04 wubi.exe, or use the 10.10 wubi.exe to install.

For 10.10
1. Download wubi.exe from here [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/) or another mirror
2. Download the netbook edition 10.10 .iso yourself using bittorrent (it's much faster as you've figured out)
3. Place the two downloads in the same folder, and run wubi.exe, selecting netbook edition.

For 10.04 you'll need a wubi.exe from here: [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/) (you need the wubi-r189.exe as it is at 10.04, r190 is 10.04.1)

---

