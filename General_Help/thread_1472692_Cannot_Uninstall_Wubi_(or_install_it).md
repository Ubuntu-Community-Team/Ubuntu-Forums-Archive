---
title: "Cannot Uninstall Wubi (or install it)"
date: 2010-05-04
forum: General Help
---

### Post by ljcasey on 2010-05-04
Hi, I cannot uninstall Wubi. I will attach the log file. Please let me know if you require me to add any additional information. 

Other Notes:
Win7 64bit
Ubuntu/Wubi 9.10

```

05-04 19:31 INFO   root: === wubi 9.10ubuntu1 rev160 ===
05-04 19:31 DEBUG  root: Logfile is c:\users\ljcasey\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
05-04 19:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-04 19:31 DEBUG  CommonBackend: data_dir=C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\data
05-04 19:31 DEBUG  WindowsBackend: 7z=C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\bin\7z.exe
05-04 19:31 DEBUG  CommonBackend: Fetching basic info...
05-04 19:31 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-04 19:31 DEBUG  CommonBackend: platform=win32
05-04 19:31 DEBUG  CommonBackend: osname=nt
05-04 19:31 DEBUG  CommonBackend: language=en_GB
05-04 19:31 DEBUG  CommonBackend: encoding=cp1252
05-04 19:31 DEBUG  WindowsBackend: arch=amd64
05-04 19:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\data\isolist.ini
05-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
05-04 19:31 DEBUG  WindowsBackend: Fetching host info...
05-04 19:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-04 19:31 DEBUG  WindowsBackend: windows version=vista
05-04 19:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-04 19:31 DEBUG  WindowsBackend: windows_sp=None
05-04 19:31 DEBUG  WindowsBackend: windows_build=7600
05-04 19:31 DEBUG  WindowsBackend: gmt=0
05-04 19:31 DEBUG  WindowsBackend: country=GB
05-04 19:31 DEBUG  WindowsBackend: timezone=Europe/London
05-04 19:31 DEBUG  WindowsBackend: windows_username=ljcasey
05-04 19:31 DEBUG  WindowsBackend: user_full_name=ljcasey
05-04 19:31 DEBUG  WindowsBackend: user_directory=C:\Users\ljcasey
05-04 19:31 DEBUG  WindowsBackend: windows_language_code=1033
05-04 19:31 DEBUG  WindowsBackend: windows_language=English
05-04 19:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
05-04 19:31 DEBUG  WindowsBackend: bootloader=vista
05-04 19:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 293844.902344 mb free ntfs)
05-04 19:31 DEBUG  WindowsBackend: drive=Drive(C: hd 293844.902344 mb free ntfs)
05-04 19:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-04 19:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-04 19:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-04 19:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-04 19:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-04 19:31 DEBUG  WindowsBackend: keyboard_id=134809609
05-04 19:31 DEBUG  WindowsBackend: keyboard_layout=gb
05-04 19:31 DEBUG  WindowsBackend: keyboard_variant=
05-04 19:31 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-04 19:31 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-04 19:31 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
05-04 19:31 DEBUG  CommonBackend: Searching ISOs on USB devices
05-04 19:31 DEBUG  CommonBackend: Searching for local CDs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Ubuntu Netbook Remix CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Kubuntu Netbook CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 INFO   root: Running the uninstaller...
05-04 19:31 INFO   CommonBackend: This is the uninstaller running
05-04 19:31 DEBUG  WindowsFrontend: __init__...
05-04 19:31 DEBUG  WindowsFrontend: on_init...
05-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\translations, languages=['en_GB', 'en']
05-04 19:31 INFO   root: Received settings
05-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ljcasey\AppData\Local\Temp\pyl228E.tmp\translations, languages=['en_GB', 'en']
05-04 19:31 DEBUG  TaskList: # Running tasklist...
05-04 19:31 DEBUG  TaskList: ## Running Backup ISO...
05-04 19:31 DEBUG  TaskList: ## Finished Backup ISO
05-04 19:31 DEBUG  TaskList: ## Running Remove bootloader entry...
05-04 19:31 DEBUG  WindowsBackend: Removing bcd entry {f421f28a-dc38-11dd-85ee-00508dbf8163}
05-04 19:31 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-04 19:31 DEBUG  TaskList: # Cancelling tasklist
05-04 19:31 DEBUG  TaskList: # Finished tasklist
05-04 19:31 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-04 19:31 INFO   root: === wubi 9.10ubuntu1 rev160 ===
05-04 19:31 DEBUG  root: Logfile is c:\users\ljcasey\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
05-04 19:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-04 19:31 DEBUG  CommonBackend: data_dir=C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\data
05-04 19:31 DEBUG  WindowsBackend: 7z=C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\bin\7z.exe
05-04 19:31 DEBUG  CommonBackend: Fetching basic info...
05-04 19:31 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-04 19:31 DEBUG  CommonBackend: platform=win32
05-04 19:31 DEBUG  CommonBackend: osname=nt
05-04 19:31 DEBUG  CommonBackend: language=en_GB
05-04 19:31 DEBUG  CommonBackend: encoding=cp1252
05-04 19:31 DEBUG  WindowsBackend: arch=amd64
05-04 19:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\data\isolist.ini
05-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-04 19:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
05-04 19:31 DEBUG  WindowsBackend: Fetching host info...
05-04 19:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-04 19:31 DEBUG  WindowsBackend: windows version=vista
05-04 19:31 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-04 19:31 DEBUG  WindowsBackend: windows_sp=None
05-04 19:31 DEBUG  WindowsBackend: windows_build=6000
05-04 19:31 DEBUG  WindowsBackend: gmt=0
05-04 19:31 DEBUG  WindowsBackend: country=GB
05-04 19:31 DEBUG  WindowsBackend: timezone=Europe/London
05-04 19:31 DEBUG  WindowsBackend: windows_username=ljcasey
05-04 19:31 DEBUG  WindowsBackend: user_full_name=ljcasey
05-04 19:31 DEBUG  WindowsBackend: user_directory=C:\Users\ljcasey
05-04 19:31 DEBUG  WindowsBackend: windows_language_code=1033
05-04 19:31 DEBUG  WindowsBackend: windows_language=English
05-04 19:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
05-04 19:31 DEBUG  WindowsBackend: bootloader=vista
05-04 19:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 293833.554688 mb free ntfs)
05-04 19:31 DEBUG  WindowsBackend: drive=Drive(C: hd 293833.554688 mb free ntfs)
05-04 19:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-04 19:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-04 19:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-04 19:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-04 19:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-04 19:31 DEBUG  WindowsBackend: keyboard_id=134809609
05-04 19:31 DEBUG  WindowsBackend: keyboard_layout=gb
05-04 19:31 DEBUG  WindowsBackend: keyboard_variant=
05-04 19:31 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-04 19:31 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-04 19:31 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
05-04 19:31 DEBUG  CommonBackend: Searching ISOs on USB devices
05-04 19:31 DEBUG  CommonBackend: Searching for local CDs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Ubuntu Netbook Remix CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Kubuntu Netbook CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:31 INFO   root: Running the uninstaller...
05-04 19:31 INFO   CommonBackend: This is the uninstaller running
05-04 19:31 DEBUG  WindowsFrontend: __init__...
05-04 19:31 DEBUG  WindowsFrontend: on_init...
05-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\translations, languages=['en_GB', 'en']
05-04 19:31 INFO   root: Received settings
05-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ljcasey\AppData\Local\Temp\pyl954D.tmp\translations, languages=['en_GB', 'en']
05-04 19:31 DEBUG  TaskList: # Running tasklist...
05-04 19:31 DEBUG  TaskList: ## Running Backup ISO...
05-04 19:31 DEBUG  TaskList: ## Finished Backup ISO
05-04 19:31 DEBUG  TaskList: ## Running Remove bootloader entry...
05-04 19:31 DEBUG  WindowsBackend: Removing bcd entry {f421f28a-dc38-11dd-85ee-00508dbf8163}
05-04 19:31 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-04 19:31 DEBUG  TaskList: # Cancelling tasklist
05-04 19:31 DEBUG  TaskList: # Finished tasklist
05-04 19:31 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-04 19:32 INFO   root: === wubi 9.10ubuntu1 rev160 ===
05-04 19:32 DEBUG  root: Logfile is c:\users\ljcasey\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
05-04 19:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-04 19:32 DEBUG  CommonBackend: data_dir=C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\data
05-04 19:32 DEBUG  WindowsBackend: 7z=C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\bin\7z.exe
05-04 19:32 DEBUG  CommonBackend: Fetching basic info...
05-04 19:32 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-04 19:32 DEBUG  CommonBackend: platform=win32
05-04 19:32 DEBUG  CommonBackend: osname=nt
05-04 19:32 DEBUG  CommonBackend: language=en_GB
05-04 19:32 DEBUG  CommonBackend: encoding=cp1252
05-04 19:32 DEBUG  WindowsBackend: arch=amd64
05-04 19:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\data\isolist.ini
05-04 19:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-04 19:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-04 19:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-04 19:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-04 19:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-04 19:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-04 19:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-04 19:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-04 19:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-04 19:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
05-04 19:32 DEBUG  WindowsBackend: Fetching host info...
05-04 19:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-04 19:32 DEBUG  WindowsBackend: windows version=vista
05-04 19:32 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-04 19:32 DEBUG  WindowsBackend: windows_sp=None
05-04 19:32 DEBUG  WindowsBackend: windows_build=6000
05-04 19:32 DEBUG  WindowsBackend: gmt=0
05-04 19:32 DEBUG  WindowsBackend: country=GB
05-04 19:32 DEBUG  WindowsBackend: timezone=Europe/London
05-04 19:32 DEBUG  WindowsBackend: windows_username=ljcasey
05-04 19:32 DEBUG  WindowsBackend: user_full_name=ljcasey
05-04 19:32 DEBUG  WindowsBackend: user_directory=C:\Users\ljcasey
05-04 19:32 DEBUG  WindowsBackend: windows_language_code=1033
05-04 19:32 DEBUG  WindowsBackend: windows_language=English
05-04 19:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
05-04 19:32 DEBUG  WindowsBackend: bootloader=vista
05-04 19:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 293828.5 mb free ntfs)
05-04 19:32 DEBUG  WindowsBackend: drive=Drive(C: hd 293828.5 mb free ntfs)
05-04 19:32 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-04 19:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-04 19:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-04 19:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-04 19:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-04 19:32 DEBUG  WindowsBackend: keyboard_id=134809609
05-04 19:32 DEBUG  WindowsBackend: keyboard_layout=gb
05-04 19:32 DEBUG  WindowsBackend: keyboard_variant=
05-04 19:32 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-04 19:32 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-04 19:32 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
05-04 19:32 DEBUG  CommonBackend: Searching ISOs on USB devices
05-04 19:32 DEBUG  CommonBackend: Searching for local CDs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Ubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Ubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Ubuntu Netbook Remix CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Kubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Kubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Kubuntu Netbook CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Xubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Xubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Mythbuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp is a valid Mythbuntu CD
05-04 19:32 DEBUG  Distro:     does not contain C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 19:32 INFO   root: Running the uninstaller...
05-04 19:32 INFO   CommonBackend: This is the uninstaller running
05-04 19:32 DEBUG  WindowsFrontend: __init__...
05-04 19:32 DEBUG  WindowsFrontend: on_init...
05-04 19:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\translations, languages=['en_GB', 'en']
05-04 19:32 INFO   root: Received settings
05-04 19:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ljcasey\AppData\Local\Temp\pylEF83.tmp\translations, languages=['en_GB', 'en']
05-04 19:32 DEBUG  TaskList: # Running tasklist...
05-04 19:32 DEBUG  TaskList: ## Running Backup ISO...
05-04 19:32 DEBUG  TaskList: ## Finished Backup ISO
05-04 19:32 DEBUG  TaskList: ## Running Remove bootloader entry...
05-04 19:32 DEBUG  WindowsBackend: Removing bcd entry {f421f28a-dc38-11dd-85ee-00508dbf8163}
05-04 19:32 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-04 19:32 DEBUG  TaskList: # Cancelling tasklist
05-04 19:32 DEBUG  TaskList: # Finished tasklist
05-04 19:32 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {f421f28a-dc38-11dd-85ee-00508dbf8163} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=


```

---

### Post by sathpra on 2010-11-01
Buddy!

I had the same problem. Try this first and then uninstall Ubuntu.


From command prompt (Run as admin)

C:\>Diskpart

C:\Diskpart> List volume

C:\Diskpart> Select volume 1 (Considering this is 100 MB system partition)

c:\Diskpart> Online volume

C:\Diskpart> exit

---

### Post by XGaSt on 2010-12-23
Just do manually uninstall..

How do I manually uninstall Wubi?

Remove C:\ubuntu and C:\wubildr* 

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block. 

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

or try to use Find and "wubi" as keyword, press F3 until you find similar registry key as above, maybe it's in different location.

An easy method of removing this registry key is to paste the following text into a plain editor such as Notepad, close and save the file as something like removeWubiKey.reg (you may wish to go to Folder Options > View and disable the "Hide file extensions for known file types" option to check that the .reg extension has been applied correctly). Then you can perform the rest automatically by opening the file in the normal Windows manner, or choosing the "Merge" option from the right click context menu. Note: The formatting is rather strict, so copy the text exactly for best results. You may need to be logged in as the administrator to delete the key, depending on the version of Windows you are using. User Account Control in Vista may also ask for permission, in the typical fashion. 

REGEDIT4

[-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]

After deleting the registry key, Ubuntu may still appear in the program list. If this is the case, you may be asked if you would like to remove the item from the list.



Source: [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I manually uninstall Wubi?

---

### Post by paco42994 on 2011-02-19
I was having trouble with this as well and although this is probably solved, I would like to post this because I came to this post while looking for help.

You can do a lot of things but one of the first things I would try is downloading a separate Ubuntu uninstaller.

You can try it here: [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe")

The Wubi uninstaller tries to uninstall based on what it remembers about what it originally installed, so if something changes for some reason (which was my case), it won't be able to uninstall.  The separate one (link above) doesn't have anything logged, so it LOOKS for where Ubuntu is installed.  I found it under the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide"), the link for the file was RIGHT above where I was directed (how to MANUALLY uninstall it).  I downloaded it, opened it, clicked uninstall, and within seconds it had found all of Ubuntu's stuff and took it out.

---

