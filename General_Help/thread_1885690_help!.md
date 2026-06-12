---
title: "help!?"
date: 2011-11-23
forum: General Help
---

### Post by celeste068809 on 2011-11-23
i had ubuntu on my laptop during a class but then my computer crashed and it went back to factory settings i dont remember which version i had so i went to the ubuntu website to download it and install it alongside my windows operating system but when its almost done it comes up with an error that says permission denied? it said to look in the temp file for more info but i dont understand why its not working or how to fix it hers what the temp file says

11-23 13:15 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
11-23 13:15 DEBUG  TaskList: # Cancelling tasklist
11-23 13:15 DEBUG  TaskList: # Finished tasklist
11-23 13:15 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'

---

### Post by Paddy Landau on 2011-11-29
It looks as though you are installing WUBI. (WUBI is totally different in how it installs from standard Ubuntu. You don't install WUBI *alongside* Windows; you install it *inside* Windows. Standard Ubuntu installs alongside Windows.)

Please first check if WUBI is already installed, and if so, uninstall it. Then try again to install.

---

