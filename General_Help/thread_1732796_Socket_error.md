---
title: "Socket error"
date: 2011-04-18
forum: General Help
---

### Post by iscalunga on 2011-04-18
Hi everybody,

i got the following error while trying to install ubuntu through wubi on windows 7 64bit. 

from the log file:
[..]
04-18 21:25 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-18 21:25 DEBUG  TaskList: # Cancelling tasklist
04-18 21:25 DEBUG  TaskList: # Finished tasklist
04-18 21:25 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files


Any help? 

Thanks a lot

Domenico

---

### Post by bcbc on 2011-04-18
Someone has put the wrong wubi.exe on [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

See here for the right wubi.exe:
[http://ubuntuforums.org/showpost.php?p=10684050&postcount=365](http://ubuntuforums.org/showpost.php?p=10684050&postcount=365)

---

