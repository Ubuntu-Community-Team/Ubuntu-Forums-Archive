---
title: "grr wubi"
date: 2009-11-30
forum: General Help
---

### Post by themuddaload on 2009-11-30
I was attempting to do a wubi install on my laptop. (I had ubuntu installed previously but I messed some stuff up stumbling along with some code)

It was going along fine, then pooped out, says "umm u has error, we r die nows, go here for log '...'   kthxbai"
 
heres the last chunk with the error. 

```
 11-30 21:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHILIP~1\AppData\Local\Temp\pylAE29.tmp\translations, languages=['en_US', 'en']
11-30 21:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHILIP~1\AppData\Local\Temp\pylAE29.tmp\translations, languages=['en_US', 'en']
11-30 21:26 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=philiplichte
11-30 21:26 INFO   root: Received settings
11-30 21:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHILIP~1\AppData\Local\Temp\pylAE29.tmp\translations, languages=['en_US', 'en']
11-30 21:26 DEBUG  TaskList: # Running tasklist...
11-30 21:26 DEBUG  TaskList: ## Running select_target_dir...
11-30 21:26 INFO   WindowsBackend: Installing into D:\ubuntu
11-30 21:26 DEBUG  TaskList: ## Finished select_target_dir
11-30 21:26 DEBUG  TaskList: ## Running create_dir_structure...
11-30 21:26 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-30 21:26 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-30 21:26 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-30 21:26 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-30 21:26 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-30 21:26 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-30 21:26 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-30 21:26 DEBUG  TaskList: ## Finished create_dir_structure
11-30 21:26 DEBUG  TaskList: ## Running uncompress_target_dir...
11-30 21:26 DEBUG  TaskList: ## Finished uncompress_target_dir
11-30 21:26 DEBUG  TaskList: ## Running create_uninstaller...
11-30 21:26 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-30 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-30 21:26 DEBUG  TaskList: ## Finished create_uninstaller
11-30 21:26 DEBUG  TaskList: ## Running copy_installation_files...
11-30 21:26 DEBUG  WindowsBackend: Copying C:\Users\PHILIP~1\AppData\Local\Temp\pylAE29.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-30 21:26 DEBUG  WindowsBackend: Copying C:\Users\PHILIP~1\AppData\Local\Temp\pylAE29.tmp\winboot -> D:\ubuntu\winboot
11-30 21:26 DEBUG  WindowsBackend: Copying C:\Users\PHILIP~1\AppData\Local\Temp\pylAE29.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-30 21:26 DEBUG  TaskList: ## Finished copy_installation_files
11-30 21:26 DEBUG  TaskList: ## Running get_iso...
11-30 21:26 DEBUG  TaskList: New task copy_file
11-30 21:26 DEBUG  TaskList: ### Running copy_file...
11-30 21:31 DEBUG  TaskList: ### Finished copy_file
11-30 21:31 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-30 21:31 DEBUG  TaskList: # Cancelling tasklist
11-30 21:31 DEBUG  TaskList: New task check_iso
11-30 21:31 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-30 21:31 DEBUG  CommonBackend: Searching for local ISO
11-30 21:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-30 21:31 DEBUG  TaskList: New task get_metalink
11-30 21:31 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-30 21:31 DEBUG  TaskList: # Cancelling tasklist
11-30 21:31 DEBUG  TaskList: # Finished tasklist

```

(the md5sum on the iso was good)

halp

---

### Post by themuddaload on 2009-12-01
um, bump

---

### Post by themuddaload on 2009-12-02
> **themuddaload said:**
> um, bump

+1

cmon guys ='(

---

### Post by ManiacDan on 2009-12-02
> (the md5sum on the iso was good)How would you know that?  It never downloaded.

Unless you already have an iso, in which case it's in the wrong directory.  The error clearly shows that it looked for an iso, failed to find one, attempted to download one from the Internet, and failed to do that as well.

-Dan

---

### Post by cole01 on 2009-12-02
Download wubi again and do another clean install

---

### Post by themuddaload on 2009-12-02
> **ManiacDan said:**
> How would you know that?  It never downloaded.

Unless you already have an iso, in which case it's in the wrong directory.  The error clearly shows that it looked for an iso, failed to find one, attempted to download one from the Internet, and failed to do that as well.

-Dan

where does it want me to put it??

i have an iso already downloaded

---

### Post by ManiacDan on 2009-12-02
> where does it want me to put it??I'm sure it's in the documentation somewhere.  The error message is pretty clear, I assume the documentation is just as clear.  Try putting the iso in the same directory as the installer, though you may need to name it something special.

-Dan

---

### Post by themuddaload on 2009-12-02
> **ManiacDan said:**
> I'm sure it's in the documentation somewhere.  The error message is pretty clear, I assume the documentation is just as clear.  Try putting the iso in the same directory as the installer, though you may need to name it something special.

-Dan

but... they are both on the same cd... cant put them in a closer location...

---

### Post by themuddaload on 2009-12-02
eh, got it working, for some reason it wasnt working on the cd...

---

