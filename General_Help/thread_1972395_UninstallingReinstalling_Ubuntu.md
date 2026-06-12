---
title: "Uninstalling/Reinstalling Ubuntu"
date: 2012-05-03
forum: General Help
---

### Post by Linux1990 on 2012-05-03
I am using a Dell Studio 1557 with Windows 7 Ultimate installed.

At one point, I had a dual boot of Windows 7 and the latest version of Ubuntu available.

Here's the issue:

I uninstalled Ubuntu and was told it was successful.However, upon reinstalling Ubuntu, I was told there was a previous version found and was given the following error message:


PLEASE HELP! I miss my Ubuntu  :( 


[IMG]http://i436.photobucket.com/albums/qq85/MDSantmyer/Ubuntu.jpg[/IMG]

I also attached the log file:



[B]
05-01 12:40 INFO   root: === wubi 11.10 rev245 ===
05-01 12:40 DEBUG  root: Logfile is c:\users\santmyer\appdata\local\temp\wubi-11.10-rev245.log
05-01 12:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
05-01 12:40 DEBUG  CommonBackend: data_dir=C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\data
05-01 12:40 DEBUG  WindowsBackend: 7z=C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\bin\7z.exe
05-01 12:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-01 12:40 DEBUG  CommonBackend: Fetching basic info...
05-01 12:40 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-01 12:40 DEBUG  CommonBackend: platform=win32
05-01 12:40 DEBUG  CommonBackend: osname=nt
05-01 12:40 DEBUG  CommonBackend: language=en_US
05-01 12:40 DEBUG  CommonBackend: encoding=cp1252
05-01 12:40 DEBUG  WindowsBackend: arch=amd64
05-01 12:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\data\isolist.ini
05-01 12:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-01 12:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-01 12:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-01 12:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-01 12:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-01 12:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-01 12:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-01 12:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-01 12:40 DEBUG  WindowsBackend: Fetching host info...
05-01 12:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-01 12:40 DEBUG  WindowsBackend: windows version=vista
05-01 12:40 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-01 12:40 DEBUG  WindowsBackend: windows_sp=None
05-01 12:40 DEBUG  WindowsBackend: windows_build=6000
05-01 12:40 DEBUG  WindowsBackend: gmt=-5
05-01 12:40 DEBUG  WindowsBackend: country=US
05-01 12:40 DEBUG  WindowsBackend: timezone=America/New_York
05-01 12:40 DEBUG  WindowsBackend: windows_username=Santmyer
05-01 12:40 DEBUG  WindowsBackend: user_full_name=Santmyer
05-01 12:40 DEBUG  WindowsBackend: user_directory=C:\Users\Santmyer
05-01 12:40 DEBUG  WindowsBackend: windows_language_code=1033
05-01 12:40 DEBUG  WindowsBackend: windows_language=English
05-01 12:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
05-01 12:40 DEBUG  WindowsBackend: bootloader=vista
05-01 12:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 54609.8984375 mb free ntfs)
05-01 12:40 DEBUG  WindowsBackend: drive=Drive(C: hd 54609.8984375 mb free ntfs)
05-01 12:40 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-01 12:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-01 12:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-01 12:40 DEBUG  WindowsBackend: drive=Drive(W: hd 3881.59375 mb free ntfs)
05-01 12:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-01 12:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-01 12:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-01 12:40 DEBUG  WindowsBackend: keyboard_id=67699721
05-01 12:40 DEBUG  WindowsBackend: keyboard_layout=us
05-01 12:40 DEBUG  WindowsBackend: keyboard_variant=
05-01 12:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-01 12:40 DEBUG  CommonBackend: locale=en_US.UTF-8
05-01 12:40 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
05-01 12:40 DEBUG  CommonBackend: Searching ISOs on USB devices
05-01 12:40 DEBUG  Distro:   checking Ubuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  Distro:   checking Ubuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  Distro:   checking Kubuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  Distro:   checking Kubuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  Distro:   checking Xubuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  Distro:   checking Xubuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  Distro:   checking Mythbuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  Distro:   checking Mythbuntu ISO C:\NBRT.iso
05-01 12:40 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-01 12:40 DEBUG  CommonBackend: Searching for local CDs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
05-01 12:40 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-01 12:40 INFO   root: Running the uninstaller...
05-01 12:40 INFO   CommonBackend: This is the uninstaller running
05-01 12:40 DEBUG  WindowsFrontend: __init__...
05-01 12:40 DEBUG  WindowsFrontend: on_init...
05-01 12:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\translations, languages=['en_US', 'en']
05-01 12:40 INFO   root: Received settings
05-01 12:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Santmyer\AppData\Local\Temp\pylDB33.tmp\translations, languages=['en_US', 'en']
05-01 12:40 DEBUG  TaskList: # Running tasklist...
05-01 12:40 DEBUG  TaskList: ## Running Remove bootloader entry...
05-01 12:40 DEBUG  WindowsBackend: Removing bcd entry {6869c588-1c48-11e0-b0b8-00188b2d3075}
05-01 12:40 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
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
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-01 12:40 DEBUG  TaskList: # Cancelling tasklist
05-01 12:40 DEBUG  TaskList: # Finished tasklist
05-01 12:40 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
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
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-03 12:52 INFO   root: === wubi 11.10 rev245 ===
05-03 12:52 DEBUG  root: Logfile is c:\users\santmyer\appdata\local\temp\wubi-11.10-rev245.log
05-03 12:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-03 12:52 DEBUG  CommonBackend: data_dir=C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\data
05-03 12:52 DEBUG  WindowsBackend: 7z=C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\bin\7z.exe
05-03 12:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-03 12:52 DEBUG  CommonBackend: Fetching basic info...
05-03 12:52 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-03 12:52 DEBUG  CommonBackend: platform=win32
05-03 12:52 DEBUG  CommonBackend: osname=nt
05-03 12:52 DEBUG  CommonBackend: language=en_US
05-03 12:52 DEBUG  CommonBackend: encoding=cp1252
05-03 12:52 DEBUG  WindowsBackend: arch=amd64
05-03 12:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\data\isolist.ini
05-03 12:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 12:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 12:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 12:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 12:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 12:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 12:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 12:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 12:52 DEBUG  WindowsBackend: Fetching host info...
05-03 12:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 12:52 DEBUG  WindowsBackend: windows version=vista
05-03 12:52 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-03 12:52 DEBUG  WindowsBackend: windows_sp=None
05-03 12:52 DEBUG  WindowsBackend: windows_build=6000
05-03 12:52 DEBUG  WindowsBackend: gmt=-5
05-03 12:52 DEBUG  WindowsBackend: country=US
05-03 12:52 DEBUG  WindowsBackend: timezone=America/New_York
05-03 12:52 DEBUG  WindowsBackend: windows_username=Santmyer
05-03 12:52 DEBUG  WindowsBackend: user_full_name=Santmyer
05-03 12:52 DEBUG  WindowsBackend: user_directory=C:\Users\Santmyer
05-03 12:52 DEBUG  WindowsBackend: windows_language_code=1033
05-03 12:52 DEBUG  WindowsBackend: windows_language=English
05-03 12:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
05-03 12:52 DEBUG  WindowsBackend: bootloader=vista
05-03 12:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 70286.5859375 mb free ntfs)
05-03 12:52 DEBUG  WindowsBackend: drive=Drive(C: hd 70286.5859375 mb free ntfs)
05-03 12:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-03 12:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 12:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 12:52 DEBUG  WindowsBackend: drive=Drive(W: hd 3853.2421875 mb free ntfs)
05-03 12:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 12:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 12:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 12:52 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 12:52 DEBUG  WindowsBackend: keyboard_layout=us
05-03 12:52 DEBUG  WindowsBackend: keyboard_variant=
05-03 12:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 12:52 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 12:52 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
05-03 12:52 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 12:52 DEBUG  Distro:   checking Ubuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  Distro:   checking Ubuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  Distro:   checking Kubuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  Distro:   checking Kubuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  Distro:   checking Xubuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  Distro:   checking Xubuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  Distro:   checking Mythbuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  Distro:   checking Mythbuntu ISO C:\NBRT.iso
05-03 12:52 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 12:52 DEBUG  CommonBackend: Searching for local CDs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
05-03 12:52 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 12:52 INFO   root: Running the uninstaller...
05-03 12:52 INFO   CommonBackend: This is the uninstaller running
05-03 12:52 DEBUG  WindowsFrontend: __init__...
05-03 12:52 DEBUG  WindowsFrontend: on_init...
05-03 12:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\translations, languages=['en_US', 'en']
05-03 12:53 INFO   root: Received settings
05-03 12:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Santmyer\AppData\Local\Temp\pylE1A7.tmp\translations, languages=['en_US', 'en']
05-03 12:53 DEBUG  TaskList: # Running tasklist...
05-03 12:53 DEBUG  TaskList: ## Running Remove bootloader entry...
05-03 12:53 DEBUG  WindowsBackend: Removing bcd entry {6869c588-1c48-11e0-b0b8-00188b2d3075}
05-03 12:53 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
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
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-03 12:53 DEBUG  TaskList: # Cancelling tasklist
05-03 12:53 DEBUG  TaskList: # Finished tasklist
05-03 12:53 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
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
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-03 13:04 INFO   root: === wubi 11.10 rev245 ===
05-03 13:04 DEBUG  root: Logfile is c:\users\santmyer\appdata\local\temp\wubi-11.10-rev245.log
05-03 13:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-03 13:04 DEBUG  CommonBackend: data_dir=C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\data
05-03 13:04 DEBUG  WindowsBackend: 7z=C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\bin\7z.exe
05-03 13:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-03 13:04 DEBUG  CommonBackend: Fetching basic info...
05-03 13:04 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-03 13:04 DEBUG  CommonBackend: platform=win32
05-03 13:04 DEBUG  CommonBackend: osname=nt
05-03 13:04 DEBUG  CommonBackend: language=en_US
05-03 13:04 DEBUG  CommonBackend: encoding=cp1252
05-03 13:04 DEBUG  WindowsBackend: arch=amd64
05-03 13:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\data\isolist.ini
05-03 13:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 13:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 13:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 13:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 13:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 13:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 13:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 13:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 13:04 DEBUG  WindowsBackend: Fetching host info...
05-03 13:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 13:04 DEBUG  WindowsBackend: windows version=vista
05-03 13:04 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-03 13:04 DEBUG  WindowsBackend: windows_sp=None
05-03 13:04 DEBUG  WindowsBackend: windows_build=6000
05-03 13:04 DEBUG  WindowsBackend: gmt=-5
05-03 13:04 DEBUG  WindowsBackend: country=US
05-03 13:04 DEBUG  WindowsBackend: timezone=America/New_York
05-03 13:04 DEBUG  WindowsBackend: windows_username=Santmyer
05-03 13:04 DEBUG  WindowsBackend: user_full_name=Santmyer
05-03 13:04 DEBUG  WindowsBackend: user_directory=C:\Users\Santmyer
05-03 13:04 DEBUG  WindowsBackend: windows_language_code=1033
05-03 13:04 DEBUG  WindowsBackend: windows_language=English
05-03 13:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
05-03 13:04 DEBUG  WindowsBackend: bootloader=vista
05-03 13:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 70272.3554688 mb free ntfs)
05-03 13:04 DEBUG  WindowsBackend: drive=Drive(C: hd 70272.3554688 mb free ntfs)
05-03 13:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-03 13:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 13:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 13:04 DEBUG  WindowsBackend: drive=Drive(W: hd 3853.2421875 mb free ntfs)
05-03 13:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 13:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 13:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 13:04 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 13:04 DEBUG  WindowsBackend: keyboard_layout=us
05-03 13:04 DEBUG  WindowsBackend: keyboard_variant=
05-03 13:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 13:04 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 13:04 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
05-03 13:04 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 13:04 DEBUG  Distro:   checking Ubuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  Distro:   checking Ubuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  Distro:   checking Kubuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  Distro:   checking Kubuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  Distro:   checking Xubuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  Distro:   checking Xubuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  Distro:   checking Mythbuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  Distro:   checking Mythbuntu ISO C:\NBRT.iso
05-03 13:04 DEBUG  Distro:     wrong size: 532905984 < 600000000
05-03 13:04 DEBUG  CommonBackend: Searching for local CDs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
05-03 13:04 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
05-03 13:04 INFO   root: Running the uninstaller...
05-03 13:04 INFO   CommonBackend: This is the uninstaller running
05-03 13:04 DEBUG  WindowsFrontend: __init__...
05-03 13:04 DEBUG  WindowsFrontend: on_init...
05-03 13:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\translations, languages=['en_US', 'en']
05-03 13:04 INFO   root: Received settings
05-03 13:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Santmyer\AppData\Local\Temp\pyl24EE.tmp\translations, languages=['en_US', 'en']
05-03 13:04 DEBUG  TaskList: # Running tasklist...
05-03 13:04 DEBUG  TaskList: ## Running Remove bootloader entry...
05-03 13:04 DEBUG  WindowsBackend: Removing bcd entry {6869c588-1c48-11e0-b0b8-00188b2d3075}
05-03 13:04 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
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
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-03 13:04 DEBUG  TaskList: # Cancelling tasklist
05-03 13:04 DEBUG  TaskList: # Finished tasklist
05-03 13:04 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
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
>>command=C:\Windows\sysnative\bcdedit.exe /delete {6869c588-1c48-11e0-b0b8-00188b2d3075} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=[/B]

---

### Post by Chazara on 2012-05-03
I'm no expert on anything ubuntu, but how about formatting the partition that you originally installed ubuntu onto, and then reinstalling afterwards. 
There should be options during installation 

Hope this helps :S

---

### Post by Linux1990 on 2012-05-03
I believe I deleted the volume (F) that had Ubuntu and installed Windows 8 Consumer Preview on it.  Should I uninstall Windows 8?

---

### Post by Linux1990 on 2012-05-03
> **Linux1990 said:**
> I believe I deleted the volume (F) that had Ubuntu and installed Windows 8 Consumer Preview on it.  Should I uninstall Windows 8?

I uninstalled Windows 8 and I still can't seem to remove wubi.exe (Ubuntu).

By the way, I installed Ubuntu via the Windows Installer. I didn't boot from a USB or CD-ROM. Maybe that's irrelevant...

---

### Post by Chazara on 2012-05-04
> **Linux1990 said:**
> I uninstalled Windows 8 and I still can't seem to remove wubi.exe (Ubuntu).

By the way, I installed Ubuntu via the Windows Installer. I didn't boot from a USB or CD-ROM. Maybe that's irrelevant...


Sorry its taken a while to get back, been away.

Firstly, wubi.exe. I did a little searching for you and its appears that using the "wubi" application has a lot of problems and I personally think (although a good idea in principle) its sloppy.

So are you trying to get away from windows all together? I assume you were only testing win8 as an OS before its official release.

If you have an external hard drive, I would suggest backing up your important files and install ubuntu from a memory stick, theres a guide on how to turn a flash drive into a bootable installation if you need it. The program you will most likely be using is one called "unetbootin"

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Let me know what your planning on doing and I will try and help :)

---

