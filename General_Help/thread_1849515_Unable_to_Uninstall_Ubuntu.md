---
title: "Unable to Uninstall Ubuntu"
date: 2011-09-24
forum: General Help
---

### Post by H3boy on 2011-09-24
I receive an error when attempting to uninstall ubuntu. The error is shown below.

[IMG]https://lh3.googleusercontent.com/-Op4koyAb2MQ/Tn44jLaoaaI/AAAAAAAAAZc/m2Jo4mWwT_Q/ubuntu.PNG[/IMG]

---

### Post by Blasphemist on 2011-09-24
I can't see the image of the error you tried to include. You should be able to add it as an attachment or a link using the toolbar of the post.

---

### Post by H3boy on 2011-09-24
The image should now be visible.

---

### Post by Blasphemist on 2011-09-24
Ah, I don't have any experience with wubi. But I can offer these two things. One, what does the log referred to say? You could post it or the end of it at least withing code tags here for us to read. Two, see if this guide shows anything being done differently than you have done. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by H3boy on 2011-09-24
This is the Log-File the error referred to.  
```
09-24 14:48 INFO   root: === wubi 11.04 rev211 ===
09-24 14:48 DEBUG  root: Logfile is c:\users\jd\appdata\local\temp\wubi-11.04-rev211.log
09-24 14:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
09-24 14:48 DEBUG  CommonBackend: data_dir=C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\data
09-24 14:48 DEBUG  WindowsBackend: 7z=C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\bin\7z.exe
09-24 14:48 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-24 14:48 DEBUG  CommonBackend: Fetching basic info...
09-24 14:48 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
09-24 14:48 DEBUG  CommonBackend: platform=win32
09-24 14:48 DEBUG  CommonBackend: osname=nt
09-24 14:48 DEBUG  CommonBackend: language=en_US
09-24 14:48 DEBUG  CommonBackend: encoding=cp1252
09-24 14:48 DEBUG  WindowsBackend: arch=amd64
09-24 14:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\data\isolist.ini
09-24 14:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 14:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 14:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 14:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 14:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 14:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 14:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 14:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 14:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-24 14:48 DEBUG  WindowsBackend: Fetching host info...
09-24 14:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 14:48 DEBUG  WindowsBackend: windows version=vista
09-24 14:48 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
09-24 14:48 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-24 14:48 DEBUG  WindowsBackend: windows_build=6001
09-24 14:48 DEBUG  WindowsBackend: gmt=-5
09-24 14:48 DEBUG  WindowsBackend: country=US
09-24 14:48 DEBUG  WindowsBackend: timezone=America/New_York
09-24 14:48 DEBUG  WindowsBackend: windows_username=JD
09-24 14:48 DEBUG  WindowsBackend: user_full_name=JD
09-24 14:48 DEBUG  WindowsBackend: user_directory=C:\Users\JD
09-24 14:48 DEBUG  WindowsBackend: windows_language_code=1033
09-24 14:48 DEBUG  WindowsBackend: windows_language=English
09-24 14:48 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
09-24 14:48 DEBUG  WindowsBackend: bootloader=vista
09-24 14:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 131190.417969 mb free ntfs)
09-24 14:48 DEBUG  WindowsBackend: drive=Drive(C: hd 131190.417969 mb free ntfs)
09-24 14:48 DEBUG  WindowsBackend: drive=Drive(D: hd 1660.609375 mb free ntfs)
09-24 14:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-24 14:48 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-24 14:48 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
09-24 14:48 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
09-24 14:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-24 14:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-24 14:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-24 14:48 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 14:48 DEBUG  WindowsBackend: keyboard_layout=us
09-24 14:48 DEBUG  WindowsBackend: keyboard_variant=
09-24 14:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-24 14:48 DEBUG  CommonBackend: locale=en_US.UTF-8
09-24 14:48 DEBUG  WindowsBackend: total_memory_mb=2046.703125
09-24 14:48 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 14:48 DEBUG  CommonBackend: Searching for local CDs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Ubuntu Netbook CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 14:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 14:48 INFO   root: Running the uninstaller...
09-24 14:48 INFO   CommonBackend: This is the uninstaller running
09-24 14:48 DEBUG  WindowsFrontend: __init__...
09-24 14:48 DEBUG  WindowsFrontend: on_init...
09-24 14:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\translations, languages=['en_US', 'en']
09-24 14:48 INFO   root: Received settings
09-24 14:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl82D6.tmp\translations, languages=['en_US', 'en']
09-24 14:48 DEBUG  TaskList: # Running tasklist...
09-24 14:48 DEBUG  TaskList: ## Running Backup ISO...
09-24 14:48 DEBUG  TaskList: ## Finished Backup ISO
09-24 14:48 DEBUG  TaskList: ## Running Remove bootloader entry...
09-24 14:48 DEBUG  WindowsBackend: Removing bcd entry {cd37fb40-d363-11e0-9468-001e3707894e}
09-24 14:48 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
09-24 14:48 DEBUG  TaskList: # Cancelling tasklist
09-24 14:48 DEBUG  TaskList: # Finished tasklist
09-24 14:48 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
09-24 14:57 INFO   root: === wubi 11.04 rev211 ===
09-24 14:57 DEBUG  root: Logfile is c:\users\jd\appdata\local\temp\wubi-11.04-rev211.log
09-24 14:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
09-24 14:57 DEBUG  CommonBackend: data_dir=C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\data
09-24 14:57 DEBUG  WindowsBackend: 7z=C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\bin\7z.exe
09-24 14:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-24 14:57 DEBUG  CommonBackend: Fetching basic info...
09-24 14:57 DEBUG  CommonBackend: original_exe=H:\wubi.exe
09-24 14:57 DEBUG  CommonBackend: platform=win32
09-24 14:57 DEBUG  CommonBackend: osname=nt
09-24 14:57 DEBUG  CommonBackend: language=en_US
09-24 14:57 DEBUG  CommonBackend: encoding=cp1252
09-24 14:57 DEBUG  WindowsBackend: arch=amd64
09-24 14:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\data\isolist.ini
09-24 14:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 14:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 14:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 14:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 14:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 14:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 14:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 14:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 14:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-24 14:57 DEBUG  WindowsBackend: Fetching host info...
09-24 14:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 14:57 DEBUG  WindowsBackend: windows version=vista
09-24 14:57 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
09-24 14:57 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-24 14:57 DEBUG  WindowsBackend: windows_build=6001
09-24 14:57 DEBUG  WindowsBackend: gmt=-5
09-24 14:57 DEBUG  WindowsBackend: country=US
09-24 14:57 DEBUG  WindowsBackend: timezone=America/New_York
09-24 14:57 DEBUG  WindowsBackend: windows_username=JD
09-24 14:57 DEBUG  WindowsBackend: user_full_name=JD
09-24 14:57 DEBUG  WindowsBackend: user_directory=C:\Users\JD
09-24 14:57 DEBUG  WindowsBackend: windows_language_code=1033
09-24 14:57 DEBUG  WindowsBackend: windows_language=English
09-24 14:57 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
09-24 14:57 DEBUG  WindowsBackend: bootloader=vista
09-24 14:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 130472.351563 mb free ntfs)
09-24 14:57 DEBUG  WindowsBackend: drive=Drive(C: hd 130472.351563 mb free ntfs)
09-24 14:57 DEBUG  WindowsBackend: drive=Drive(D: hd 1660.609375 mb free ntfs)
09-24 14:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-24 14:57 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-24 14:57 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
09-24 14:57 DEBUG  WindowsBackend: drive=Drive(H: removable 13635.40625 mb free fat32)
09-24 14:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-24 14:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-24 14:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-24 14:57 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 14:57 DEBUG  WindowsBackend: keyboard_layout=us
09-24 14:57 DEBUG  WindowsBackend: keyboard_variant=
09-24 14:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-24 14:57 DEBUG  CommonBackend: locale=en_US.UTF-8
09-24 14:57 DEBUG  WindowsBackend: total_memory_mb=2046.703125
09-24 14:57 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 14:57 DEBUG  CommonBackend: Searching for local CDs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Ubuntu Netbook CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl1739.tmp is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 14:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 14:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 14:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-24 14:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
09-24 14:57 INFO   Distro: Found a valid CD for Ubuntu: H:\
09-24 14:57 INFO   root: Running the CD menu...
09-24 14:57 DEBUG  WindowsFrontend: __init__...
09-24 14:57 DEBUG  WindowsFrontend: on_init...
09-24 14:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\translations, languages=['en_US', 'en']
09-24 14:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\translations, languages=['en_US', 'en']
09-24 14:58 INFO   root: CD menu finished
09-24 14:58 INFO   root: Already installed, running the uninstaller...
09-24 14:58 INFO   root: Running the uninstaller...
09-24 14:58 INFO   CommonBackend: This is the uninstaller running
09-24 14:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl1739.tmp\translations, languages=['en_US', 'en']
09-24 14:58 INFO   WindowsFrontend: Operation cancelled
09-24 14:58 DEBUG  WindowsFrontend: frontend.quit
09-24 14:58 DEBUG  WindowsFrontend: frontend.on_quit
09-24 14:58 DEBUG  root: application.on_quit
09-24 14:58 INFO   root: sys.exit
09-24 15:28 INFO   root: === wubi 11.04 rev211 ===
09-24 15:28 DEBUG  root: Logfile is c:\users\jd\appdata\local\temp\wubi-11.04-rev211.log
09-24 15:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
09-24 15:28 DEBUG  CommonBackend: data_dir=C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\data
09-24 15:28 DEBUG  WindowsBackend: 7z=C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\bin\7z.exe
09-24 15:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-24 15:28 DEBUG  CommonBackend: Fetching basic info...
09-24 15:28 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
09-24 15:28 DEBUG  CommonBackend: platform=win32
09-24 15:28 DEBUG  CommonBackend: osname=nt
09-24 15:28 DEBUG  CommonBackend: language=en_US
09-24 15:28 DEBUG  CommonBackend: encoding=cp1252
09-24 15:28 DEBUG  WindowsBackend: arch=amd64
09-24 15:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\data\isolist.ini
09-24 15:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 15:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 15:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 15:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 15:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 15:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 15:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 15:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 15:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-24 15:28 DEBUG  WindowsBackend: Fetching host info...
09-24 15:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 15:28 DEBUG  WindowsBackend: windows version=vista
09-24 15:28 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
09-24 15:28 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-24 15:28 DEBUG  WindowsBackend: windows_build=6001
09-24 15:28 DEBUG  WindowsBackend: gmt=-5
09-24 15:28 DEBUG  WindowsBackend: country=US
09-24 15:28 DEBUG  WindowsBackend: timezone=America/New_York
09-24 15:28 DEBUG  WindowsBackend: windows_username=JD
09-24 15:28 DEBUG  WindowsBackend: user_full_name=JD
09-24 15:28 DEBUG  WindowsBackend: user_directory=C:\Users\JD
09-24 15:28 DEBUG  WindowsBackend: windows_language_code=1033
09-24 15:28 DEBUG  WindowsBackend: windows_language=English
09-24 15:28 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
09-24 15:28 DEBUG  WindowsBackend: bootloader=vista
09-24 15:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 130267.5625 mb free ntfs)
09-24 15:28 DEBUG  WindowsBackend: drive=Drive(C: hd 130267.5625 mb free ntfs)
09-24 15:28 DEBUG  WindowsBackend: drive=Drive(D: hd 1660.609375 mb free ntfs)
09-24 15:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-24 15:28 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-24 15:28 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
09-24 15:28 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
09-24 15:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-24 15:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-24 15:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-24 15:28 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 15:28 DEBUG  WindowsBackend: keyboard_layout=us
09-24 15:28 DEBUG  WindowsBackend: keyboard_variant=
09-24 15:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-24 15:28 DEBUG  CommonBackend: locale=en_US.UTF-8
09-24 15:28 DEBUG  WindowsBackend: total_memory_mb=2046.703125
09-24 15:28 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 15:28 DEBUG  CommonBackend: Searching for local CDs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Ubuntu Netbook CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl4807.tmp is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 15:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:28 INFO   root: Running the uninstaller...
09-24 15:28 INFO   CommonBackend: This is the uninstaller running
09-24 15:28 DEBUG  WindowsFrontend: __init__...
09-24 15:28 DEBUG  WindowsFrontend: on_init...
09-24 15:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\translations, languages=['en_US', 'en']
09-24 15:28 INFO   root: Received settings
09-24 15:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl4807.tmp\translations, languages=['en_US', 'en']
09-24 15:28 DEBUG  TaskList: # Running tasklist...
09-24 15:28 DEBUG  TaskList: ## Running Backup ISO...
09-24 15:28 DEBUG  TaskList: ## Finished Backup ISO
09-24 15:28 DEBUG  TaskList: ## Running Remove bootloader entry...
09-24 15:28 DEBUG  WindowsBackend: Removing bcd entry {cd37fb40-d363-11e0-9468-001e3707894e}
09-24 15:28 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
09-24 15:28 DEBUG  TaskList: # Cancelling tasklist
09-24 15:28 DEBUG  TaskList: # Finished tasklist
09-24 15:28 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
09-24 15:53 INFO   root: === wubi 11.04 rev211 ===
09-24 15:53 DEBUG  root: Logfile is c:\users\jd\appdata\local\temp\wubi-11.04-rev211.log
09-24 15:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
09-24 15:53 DEBUG  CommonBackend: data_dir=C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\data
09-24 15:53 DEBUG  WindowsBackend: 7z=C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\bin\7z.exe
09-24 15:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-24 15:53 DEBUG  CommonBackend: Fetching basic info...
09-24 15:53 DEBUG  CommonBackend: original_exe=I:\wubi.exe
09-24 15:53 DEBUG  CommonBackend: platform=win32
09-24 15:53 DEBUG  CommonBackend: osname=nt
09-24 15:53 DEBUG  CommonBackend: language=en_US
09-24 15:53 DEBUG  CommonBackend: encoding=cp1252
09-24 15:53 DEBUG  WindowsBackend: arch=amd64
09-24 15:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\data\isolist.ini
09-24 15:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 15:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 15:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 15:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 15:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 15:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 15:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 15:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 15:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-24 15:53 DEBUG  WindowsBackend: Fetching host info...
09-24 15:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 15:53 DEBUG  WindowsBackend: windows version=vista
09-24 15:53 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
09-24 15:53 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-24 15:53 DEBUG  WindowsBackend: windows_build=6001
09-24 15:53 DEBUG  WindowsBackend: gmt=-5
09-24 15:53 DEBUG  WindowsBackend: country=US
09-24 15:53 DEBUG  WindowsBackend: timezone=America/New_York
09-24 15:53 DEBUG  WindowsBackend: windows_username=JD
09-24 15:53 DEBUG  WindowsBackend: user_full_name=JD
09-24 15:53 DEBUG  WindowsBackend: user_directory=C:\Users\JD
09-24 15:53 DEBUG  WindowsBackend: windows_language_code=1033
09-24 15:53 DEBUG  WindowsBackend: windows_language=English
09-24 15:53 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
09-24 15:53 DEBUG  WindowsBackend: bootloader=vista
09-24 15:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 130587.660156 mb free ntfs)
09-24 15:53 DEBUG  WindowsBackend: drive=Drive(C: hd 130587.660156 mb free ntfs)
09-24 15:53 DEBUG  WindowsBackend: drive=Drive(D: hd 1660.609375 mb free ntfs)
09-24 15:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-24 15:54 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-24 15:54 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
09-24 15:54 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
09-24 15:54 DEBUG  WindowsBackend: drive=Drive(I: removable 6936.8046875 mb free fat32)
09-24 15:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-24 15:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-24 15:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-24 15:54 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 15:54 DEBUG  WindowsBackend: keyboard_layout=us
09-24 15:54 DEBUG  WindowsBackend: keyboard_variant=
09-24 15:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-24 15:54 DEBUG  CommonBackend: locale=en_US.UTF-8
09-24 15:54 DEBUG  WindowsBackend: total_memory_mb=2046.703125
09-24 15:54 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 15:54 DEBUG  CommonBackend: Searching for local CDs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu Netbook CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 15:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-24 15:54 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-24 15:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
09-24 15:54 INFO   Distro: Found a valid CD for Ubuntu: I:\
09-24 15:54 INFO   root: Running the CD menu...
09-24 15:54 DEBUG  WindowsFrontend: __init__...
09-24 15:54 DEBUG  WindowsFrontend: on_init...
09-24 15:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\translations, languages=['en_US', 'en']
09-24 15:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\translations, languages=['en_US', 'en']
09-24 15:54 INFO   root: CD menu finished
09-24 15:54 INFO   root: Already installed, running the uninstaller...
09-24 15:54 INFO   root: Running the uninstaller...
09-24 15:54 INFO   CommonBackend: This is the uninstaller running
09-24 15:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\translations, languages=['en_US', 'en']
09-24 15:54 INFO   root: Received settings
09-24 15:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl70BC.tmp\translations, languages=['en_US', 'en']
09-24 15:54 DEBUG  TaskList: # Running tasklist...
09-24 15:54 DEBUG  TaskList: ## Running Backup ISO...
09-24 15:54 DEBUG  TaskList: ## Finished Backup ISO
09-24 15:54 DEBUG  TaskList: ## Running Remove bootloader entry...
09-24 15:54 DEBUG  WindowsBackend: Removing bcd entry {cd37fb40-d363-11e0-9468-001e3707894e}
09-24 15:54 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
09-24 15:54 DEBUG  TaskList: # Cancelling tasklist
09-24 15:54 DEBUG  TaskList: # Finished tasklist
09-24 15:54 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
09-24 15:55 INFO   root: === wubi 11.04 rev211 ===
09-24 15:55 DEBUG  root: Logfile is c:\users\jd\appdata\local\temp\wubi-11.04-rev211.log
09-24 15:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
09-24 15:55 DEBUG  CommonBackend: data_dir=C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\data
09-24 15:55 DEBUG  WindowsBackend: 7z=C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\bin\7z.exe
09-24 15:55 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-24 15:55 DEBUG  CommonBackend: Fetching basic info...
09-24 15:55 DEBUG  CommonBackend: original_exe=I:\wubi.exe
09-24 15:55 DEBUG  CommonBackend: platform=win32
09-24 15:55 DEBUG  CommonBackend: osname=nt
09-24 15:55 DEBUG  CommonBackend: language=en_US
09-24 15:55 DEBUG  CommonBackend: encoding=cp1252
09-24 15:55 DEBUG  WindowsBackend: arch=amd64
09-24 15:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\data\isolist.ini
09-24 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 15:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-24 15:55 DEBUG  WindowsBackend: Fetching host info...
09-24 15:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 15:55 DEBUG  WindowsBackend: windows version=vista
09-24 15:55 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
09-24 15:55 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-24 15:55 DEBUG  WindowsBackend: windows_build=6001
09-24 15:55 DEBUG  WindowsBackend: gmt=-5
09-24 15:55 DEBUG  WindowsBackend: country=US
09-24 15:55 DEBUG  WindowsBackend: timezone=America/New_York
09-24 15:55 DEBUG  WindowsBackend: windows_username=JD
09-24 15:55 DEBUG  WindowsBackend: user_full_name=JD
09-24 15:55 DEBUG  WindowsBackend: user_directory=C:\Users\JD
09-24 15:55 DEBUG  WindowsBackend: windows_language_code=1033
09-24 15:55 DEBUG  WindowsBackend: windows_language=English
09-24 15:55 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
09-24 15:55 DEBUG  WindowsBackend: bootloader=vista
09-24 15:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 130587.191406 mb free ntfs)
09-24 15:55 DEBUG  WindowsBackend: drive=Drive(C: hd 130587.191406 mb free ntfs)
09-24 15:55 DEBUG  WindowsBackend: drive=Drive(D: hd 1660.609375 mb free ntfs)
09-24 15:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
09-24 15:55 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-24 15:55 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
09-24 15:55 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
09-24 15:55 DEBUG  WindowsBackend: drive=Drive(I: removable 6936.8046875 mb free fat32)
09-24 15:55 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-24 15:55 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-24 15:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-24 15:55 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 15:55 DEBUG  WindowsBackend: keyboard_layout=us
09-24 15:55 DEBUG  WindowsBackend: keyboard_variant=
09-24 15:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-24 15:55 DEBUG  CommonBackend: locale=en_US.UTF-8
09-24 15:55 DEBUG  WindowsBackend: total_memory_mb=2046.703125
09-24 15:55 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 15:55 DEBUG  CommonBackend: Searching for local CDs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Ubuntu Netbook CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-24 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-24 15:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-24 15:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-24 15:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-24 15:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-24 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
09-24 15:56 INFO   Distro: Found a valid CD for Ubuntu: I:\
09-24 15:56 INFO   root: Running the CD menu...
09-24 15:56 DEBUG  WindowsFrontend: __init__...
09-24 15:56 DEBUG  WindowsFrontend: on_init...
09-24 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\translations, languages=['en_US', 'en']
09-24 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\translations, languages=['en_US', 'en']
09-24 15:56 INFO   root: CD menu finished
09-24 15:56 INFO   root: Already installed, running the uninstaller...
09-24 15:56 INFO   root: Running the uninstaller...
09-24 15:56 INFO   CommonBackend: This is the uninstaller running
09-24 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\translations, languages=['en_US', 'en']
09-24 15:56 INFO   root: Received settings
09-24 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JD\AppData\Local\Temp\pyl2CE9.tmp\translations, languages=['en_US', 'en']
09-24 15:56 DEBUG  TaskList: # Running tasklist...
09-24 15:56 DEBUG  TaskList: ## Running Backup ISO...
09-24 15:56 DEBUG  TaskList: ## Finished Backup ISO
09-24 15:56 DEBUG  TaskList: ## Running Remove bootloader entry...
09-24 15:56 DEBUG  WindowsBackend: Removing bcd entry {cd37fb40-d363-11e0-9468-001e3707894e}
09-24 15:56 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
09-24 15:56 DEBUG  TaskList: # Cancelling tasklist
09-24 15:56 DEBUG  TaskList: # Finished tasklist
09-24 15:56 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {cd37fb40-d363-11e0-9468-001e3707894e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.The system cannot find the file specified.
>>stdout=
```

---

