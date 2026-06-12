---
title: "Wubi error Windows 7"
date: 2010-10-23
forum: General Help
---

### Post by taylorc8 on 2010-10-23
> 10-23 13:06 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-23 13:06 DEBUG  TaskList: # Cancelling tasklist
10-23 13:06 DEBUG  TaskList: New task check_iso
10-23 13:06 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-23 13:06 DEBUG  CommonBackend: Searching for local ISO
10-23 13:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-23 13:06 DEBUG  TaskList: New task get_metalink
10-23 13:06 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-23 13:06 DEBUG  TaskList: # Cancelling tasklist
10-23 13:06 DEBUG  TaskList: # Finished tasklist
Gives error message permission denied.

I've seen this in your forums but I still haven't found the fix.  I've tried the latest release Wubi downloader too.

This one is ran from a CD.  Version 10.04

---

### Post by sandyd on 2010-10-23
> **taylorc8 said:**
> Gives error message permission denied.

I've seen this in your forums but I still haven't found the fix.  I've tried the latest release Wubi downloader too.

This one is ran from a CD.  Version 10.04

dont use wubi.
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

---

### Post by taylorc8 on 2010-10-23
If I install Ubuntu 10.04 to a different hard drive than my W7 install, will I have to configure a bootloader?

I would prefer to keep the Windows bootloader around.

What would happen if I used a 10.04 live CD, installed from Live to diff hd?

---

### Post by sandyd on 2010-10-23
> **taylorc8 said:**
> If I install Ubuntu 10.04 to a different hard drive than my W7 install, will I have to configure a bootloader?

I would prefer to keep the Windows bootloader around.

What would happen if I used a 10.04 live CD, installed from Live to diff hd?

that would work as well, as long as you set the ubuntu hard drive as the boot hard drive in your bios

---

