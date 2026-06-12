---
title: "Can't finish installation with WUBI--E:\\ problem"
date: 2012-03-11
forum: General Help
---

### Post by drh1 on 2012-03-11
hi ubuntuniks,

i've just tried installing 11.10 with WUBI.  my system: 64-bit, 12 GB, 900 GB HD (RAID), windows 7.  the installation seemed to go smoothly until nearly the very end, when i got the following [i've deleted the preceding parts of the boot log;  note that volume E:\\ is just a removable hard drive, i.e. USB port] :

.....
03-11 12:38 DEBUG  TaskList: ### Finished download
03-11 12:38 DEBUG  downloader: download finished (read 507143012 bytes)
03-11 12:38 DEBUG  TaskList: ## Finished get_diskimage
03-11 12:38 DEBUG  TaskList: ## Running extract_diskimage...
03-11 12:39 DEBUG  TaskList: ## Finished extract_diskimage
03-11 12:39 DEBUG  TaskList: ## Running choose_disk_sizes...
03-11 12:39 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
03-11 12:39 DEBUG  TaskList: ## Finished choose_disk_sizes
03-11 12:39 DEBUG  TaskList: ## Running expand_diskimage...
03-11 12:41 DEBUG  TaskList: ## Finished expand_diskimage
03-11 12:41 DEBUG  TaskList: ## Running create_swap_diskimage...
03-11 12:41 DEBUG  TaskList: ## Finished create_swap_diskimage
03-11 12:41 DEBUG  TaskList: ## Running modify_bootloader...
03-11 12:41 DEBUG  TaskList: New task modify_bcd
03-11 12:41 DEBUG  TaskList: ### Running modify_bcd...
03-11 12:41 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 726408.558594 mb free ntfs)
03-11 12:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {ab3e92c3-bc7a-11df-add4-f83c34313b68}
03-11 12:41 DEBUG  TaskList: ### Finished modify_bcd
03-11 12:41 DEBUG  TaskList: New task modify_bcd
03-11 12:41 DEBUG  TaskList: ### Running modify_bcd...
03-11 12:41 DEBUG  WindowsBackend: modify_bcd Drive(E: removable 0.0 mb free )
03-11 12:41 DEBUG  WindowsBackend: BCD has already been modified
03-11 12:41 DEBUG  TaskList: ### Finished modify_bcd
03-11 12:41 DEBUG  TaskList: New task modify_bcd
03-11 12:41 DEBUG  TaskList: ### Running modify_bcd...
03-11 12:41 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
03-11 12:41 DEBUG  WindowsBackend: BCD has already been modified
03-11 12:41 DEBUG  TaskList: ### Finished modify_bcd
03-11 12:41 DEBUG  TaskList: ## Finished modify_bootloader
03-11 12:41 DEBUG  TaskList: ## Running diskimage_bootloader...
03-11 12:41 DEBUG  WindowsBackend: Copying C:\Users\david\AppData\Local\Temp\pyl583D.tmp\winboot -> C:\ubuntu\winboot
03-11 12:41 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
03-11 12:41 DEBUG  TaskList: # Cancelling tasklist
03-11 12:41 DEBUG  TaskList: # Finished tasklist
03-11 12:41 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'

Please advise -- thanks in advance.

-drh1

---

### Post by bcbc on 2012-03-11
That's bug [lpbug]862003[/lpbug]. You can ignore the error as the installation was actually successful.

---

