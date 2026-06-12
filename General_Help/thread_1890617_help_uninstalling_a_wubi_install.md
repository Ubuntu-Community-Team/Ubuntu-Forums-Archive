---
title: "help uninstalling a wubi install"
date: 2011-12-03
forum: General Help
---

### Post by paradive on 2011-12-03
it didn't work out. won't even boot (i'd post the log but doubt i'd get any answers).

anyway, running the uninstall program only gets me 

">>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified."

any ideas?
what the deuce is bcdedit?

[EDIT] bcdedit's in there. it must not be finding a file the uninstall program is calling ({a9ad606b-1bb0-11e1-a009-aa4c69b8c636}?)........[/EDIT]

---

### Post by Frogs Hair on 2011-12-03
See the guide and the mega thread .

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Rubi1200 on 2011-12-04
Please post the log so we can get a better idea of what is going on.

It is in your %temp% folder.

Thanks.

---

### Post by paradive on 2011-12-04
> **Rubi1200 said:**
> Please post the log so we can get a better idea of what is going on.

It is in your %temp% folder.

Thanks.

12-03 18:31 INFO   root: === wubi 11.10 rev241 ===
12-03 18:31 DEBUG  root: Logfile is c:\users\owner\appdata\local\temp\wubi-11.10-rev241.log
12-03 18:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-03 18:31 DEBUG  CommonBackend: data_dir=C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\data
12-03 18:31 DEBUG  WindowsBackend: 7z=C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\bin\7z.exe
12-03 18:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-03 18:31 DEBUG  CommonBackend: Fetching basic info...
12-03 18:31 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-03 18:31 DEBUG  CommonBackend: platform=win32
12-03 18:31 DEBUG  CommonBackend: osname=nt
12-03 18:31 DEBUG  CommonBackend: language=en_US
12-03 18:31 DEBUG  CommonBackend: encoding=cp1252
12-03 18:31 DEBUG  WindowsBackend: arch=amd64
12-03 18:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\data\isolist.ini
12-03 18:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-03 18:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-03 18:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-03 18:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-03 18:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-03 18:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-03 18:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-03 18:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-03 18:31 DEBUG  WindowsBackend: Fetching host info...
12-03 18:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-03 18:31 DEBUG  WindowsBackend: windows version=vista
12-03 18:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-03 18:31 DEBUG  WindowsBackend: windows_sp=None
12-03 18:31 DEBUG  WindowsBackend: windows_build=7600
12-03 18:31 DEBUG  WindowsBackend: gmt=-8
12-03 18:31 DEBUG  WindowsBackend: country=US
12-03 18:31 DEBUG  WindowsBackend: timezone=America/Los_Angeles
12-03 18:31 DEBUG  WindowsBackend: windows_username=Owner
12-03 18:31 DEBUG  WindowsBackend: user_full_name=Owner
12-03 18:31 DEBUG  WindowsBackend: user_directory=C:\Users\Owner
12-03 18:31 DEBUG  WindowsBackend: windows_language_code=1033
12-03 18:31 DEBUG  WindowsBackend: windows_language=English
12-03 18:31 DEBUG  WindowsBackend: processor_name=AMD A4-3300M APU with Radeon(tm) HD Graphics
12-03 18:31 DEBUG  WindowsBackend: bootloader=vista
12-03 18:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 234674.535156 mb free ntfs)
12-03 18:31 DEBUG  WindowsBackend: drive=Drive(C: hd 234674.535156 mb free ntfs)
12-03 18:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
12-03 18:31 DEBUG  WindowsBackend: drive=Drive(E: hd 69.875 mb free ntfs)
12-03 18:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-03 18:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-03 18:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-03 18:31 DEBUG  WindowsBackend: keyboard_id=67699721
12-03 18:31 DEBUG  WindowsBackend: keyboard_layout=us
12-03 18:31 DEBUG  WindowsBackend: keyboard_variant=
12-03 18:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-03 18:31 DEBUG  CommonBackend: locale=en_US.UTF-8
12-03 18:31 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-03 18:31 DEBUG  CommonBackend: Searching ISOs on USB devices
12-03 18:31 DEBUG  CommonBackend: Searching for local CDs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Ubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Ubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Kubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Kubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Xubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Xubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Mythbuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp is a valid Mythbuntu CD
12-03 18:31 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 18:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:31 INFO   root: Running the uninstaller...
12-03 18:31 INFO   CommonBackend: This is the uninstaller running
12-03 18:31 DEBUG  WindowsFrontend: __init__...
12-03 18:31 DEBUG  WindowsFrontend: on_init...
12-03 18:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\translations, languages=['en_US', 'en']
12-03 18:31 INFO   root: Received settings
12-03 18:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl3226.tmp\translations, languages=['en_US', 'en']
12-03 18:31 DEBUG  TaskList: # Running tasklist...
12-03 18:31 DEBUG  TaskList: ## Running Remove bootloader entry...
12-03 18:31 DEBUG  WindowsBackend: Removing bcd entry {a9ad606b-1bb0-11e1-a009-aa4c69b8c636}
12-03 18:31 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
12-03 18:31 DEBUG  TaskList: # Cancelling tasklist
12-03 18:31 DEBUG  TaskList: # Finished tasklist
12-03 18:31 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
12-03 18:37 INFO   root: === wubi 11.10 rev241 ===
12-03 18:37 DEBUG  root: Logfile is c:\users\owner\appdata\local\temp\wubi-11.10-rev241.log
12-03 18:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-03 18:37 DEBUG  CommonBackend: data_dir=C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\data
12-03 18:37 DEBUG  WindowsBackend: 7z=C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\bin\7z.exe
12-03 18:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-03 18:37 DEBUG  CommonBackend: Fetching basic info...
12-03 18:37 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-03 18:37 DEBUG  CommonBackend: platform=win32
12-03 18:37 DEBUG  CommonBackend: osname=nt
12-03 18:37 DEBUG  CommonBackend: language=en_US
12-03 18:37 DEBUG  CommonBackend: encoding=cp1252
12-03 18:37 DEBUG  WindowsBackend: arch=amd64
12-03 18:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\data\isolist.ini
12-03 18:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-03 18:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-03 18:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-03 18:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-03 18:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-03 18:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-03 18:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-03 18:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-03 18:37 DEBUG  WindowsBackend: Fetching host info...
12-03 18:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-03 18:37 DEBUG  WindowsBackend: windows version=vista
12-03 18:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-03 18:37 DEBUG  WindowsBackend: windows_sp=None
12-03 18:37 DEBUG  WindowsBackend: windows_build=7600
12-03 18:37 DEBUG  WindowsBackend: gmt=-8
12-03 18:37 DEBUG  WindowsBackend: country=US
12-03 18:37 DEBUG  WindowsBackend: timezone=America/Los_Angeles
12-03 18:37 DEBUG  WindowsBackend: windows_username=Owner
12-03 18:37 DEBUG  WindowsBackend: user_full_name=Owner
12-03 18:37 DEBUG  WindowsBackend: user_directory=C:\Users\Owner
12-03 18:37 DEBUG  WindowsBackend: windows_language_code=1033
12-03 18:37 DEBUG  WindowsBackend: windows_language=English
12-03 18:37 DEBUG  WindowsBackend: processor_name=AMD A4-3300M APU with Radeon(tm) HD Graphics
12-03 18:37 DEBUG  WindowsBackend: bootloader=vista
12-03 18:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 234672.078125 mb free ntfs)
12-03 18:37 DEBUG  WindowsBackend: drive=Drive(C: hd 234672.078125 mb free ntfs)
12-03 18:37 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
12-03 18:37 DEBUG  WindowsBackend: drive=Drive(E: hd 69.875 mb free ntfs)
12-03 18:37 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-03 18:37 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-03 18:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-03 18:37 DEBUG  WindowsBackend: keyboard_id=67699721
12-03 18:37 DEBUG  WindowsBackend: keyboard_layout=us
12-03 18:37 DEBUG  WindowsBackend: keyboard_variant=
12-03 18:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-03 18:37 DEBUG  CommonBackend: locale=en_US.UTF-8
12-03 18:37 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-03 18:37 DEBUG  CommonBackend: Searching ISOs on USB devices
12-03 18:37 DEBUG  CommonBackend: Searching for local CDs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Ubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Ubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Kubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Kubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Xubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Xubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Mythbuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylC908.tmp is a valid Mythbuntu CD
12-03 18:37 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 18:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 18:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 18:37 INFO   root: Running the uninstaller...
12-03 18:37 INFO   CommonBackend: This is the uninstaller running
12-03 18:37 DEBUG  WindowsFrontend: __init__...
12-03 18:37 DEBUG  WindowsFrontend: on_init...
12-03 18:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\translations, languages=['en_US', 'en']
12-03 18:37 INFO   root: Received settings
12-03 18:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylC908.tmp\translations, languages=['en_US', 'en']
12-03 18:37 DEBUG  TaskList: # Running tasklist...
12-03 18:37 DEBUG  TaskList: ## Running Remove bootloader entry...
12-03 18:37 DEBUG  WindowsBackend: Removing bcd entry {a9ad606b-1bb0-11e1-a009-aa4c69b8c636}
12-03 18:37 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
12-03 18:37 DEBUG  TaskList: # Cancelling tasklist
12-03 18:37 DEBUG  TaskList: # Finished tasklist
12-03 18:37 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a9ad606b-1bb0-11e1-a009-aa4c69b8c636} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=

---

### Post by Mark Phelps on 2011-12-04
If you can't boot, how can you run the uninstaller?

According to the log, the entry has already been removed.

IF you CAN boot into Windows and the entery is still there, the safest way to remove it is to download and install EasyBCD from NeoSmart Technologies.  That will install a GUI that will allow you to edit the Windows boot list without having to enter commands.

---

### Post by paradive on 2011-12-04
> **Mark Phelps said:**
> If you can't boot, how can you run the uninstaller?

According to the log, the entry has already been removed.

IF you CAN boot into Windows and the entery is still there, the safest way to remove it is to download and install EasyBCD from NeoSmart Technologies.  That will install a GUI that will allow you to edit the Windows boot list without having to enter commands.

i'm confuckled.
yeah, i'm running the wubi uninstaller in windows.

i haven 't changed any entries.
all i've done is changed the default in Grub to windows.

---

### Post by Mark Phelps on 2011-12-05
If Wubi won't remove using Control Panel --> Programs and Features, you can do the following (all in Win7):
1) Follow my directions in the previous post to install EasyBCD, and use it to remove the Boot entry for Ubuntu.
2) Open Windows Explorer and look for a file named root.disk -- that is the Ubuntu filesystem.  Simply delete it.

At this point, most of Wubi is gone -- there may be some registry entries, but it's not worth risking corrupting that to remove them.

---

### Post by paradive on 2011-12-05
> **Mark Phelps said:**
> If Wubi won't remove using Control Panel --> Programs and Features, you can do the following (all in Win7):
1) Follow my directions in the previous post to install EasyBCD, and use it to remove the Boot entry for Ubuntu.
2) Open Windows Explorer and look for a file named root.disk -- that is the Ubuntu filesystem.  Simply delete it.

At this point, most of Wubi is gone -- there may be some registry entries, but it's not worth risking corrupting that to remove them.

well, i used Revo Uninstaller to successfully remove it.

now c:\ubuntu nor any registry entries exist.

problem is... the Grub menu is still there to annoy me at startup.

i noticed wubildr.mbr is still in c:\ but am totally afraid to touch it.
do i really have to do a system restore or reinstall or something to get rid of it?

---

### Post by Mark Phelps on 2011-12-05
You shouldn't have a "GRUB menu" -- as Wubi doesn't use that to boot; it uses the Windows boot loader, instead.  However, if you forced an install of GRUB, then it will still be there -- lurking in the MBR.

To restore the Windows MBR, use the Boot-Repair utility:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by paradive on 2011-12-05
> **Mark Phelps said:**
> You shouldn't have a "GRUB menu" -- as Wubi doesn't use that to boot; it uses the Windows boot loader, instead.  However, if you forced an install of GRUB, then it will still be there -- lurking in the MBR.

To restore the Windows MBR, use the Boot-Repair utility:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

yeah, some other idiot did the install.
and now i have **both **grub **and** the windows boot manager.

now that ubuntu is gone, will this utility get me back to **no **boot managers and just let windows boot straight up or do i have to fdisk the MBR (always a scary situation)?

---

### Post by Mark Phelps on 2011-12-06
> **paradive said:**
> yeah, some other idiot did the install.
and now i have **both **grub **and** the windows boot manager.

now that ubuntu is gone, will this utility get me back to **no **boot managers and just let windows boot straight up or do i have to fdisk the MBR (always a scary situation)?

This utility will restore the Window MBR, thus allowing the machine to boot into Windows by default.

---

