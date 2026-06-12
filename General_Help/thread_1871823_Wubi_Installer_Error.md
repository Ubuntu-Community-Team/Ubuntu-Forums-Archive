---
title: "Wubi Installer Error"
date: 2011-10-29
forum: General Help
---

### Post by EpicTTR on 2011-10-29
I'm trying to install Xubuntu using Wubi, however, once I start the installer, it runs all the way through (on the Installing Xubuntu-11.10 page with the two loading bars), and it gets to "Remaining time approximately 0s". Then, it gives me an error in a message box: /

```
An error occurred:

Error executing command
>>command=C:\Winows\sysnative\bcdedit /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.
The system cannot find the file specified.

>>stdout=

For more information see the log file:
..\local\temp\wubi-11.10-rev245.log
```Here is my entire log file, I've been trying it both today and yesterday (hence the two entry dates):
```

10-28 22:34 INFO   root: === wubi 11.10 rev245 ===
10-28 22:34 DEBUG  root: Logfile is c:\users\jacob\appdata\local\temp\wubi-11.10-rev245.log
10-28 22:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jacob\\Downloads\\wubi.exe"']
10-28 22:34 DEBUG  CommonBackend: data_dir=C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\data
10-28 22:34 DEBUG  WindowsBackend: 7z=C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\bin\7z.exe
10-28 22:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 22:34 DEBUG  CommonBackend: Fetching basic info...
10-28 22:34 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-28 22:34 DEBUG  CommonBackend: platform=win32
10-28 22:34 DEBUG  CommonBackend: osname=nt
10-28 22:34 DEBUG  CommonBackend: language=en_US
10-28 22:34 DEBUG  CommonBackend: encoding=cp1252
10-28 22:34 DEBUG  WindowsBackend: arch=amd64
10-28 22:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\data\isolist.ini
10-28 22:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-28 22:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-28 22:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 22:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 22:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 22:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 22:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 22:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 22:34 DEBUG  WindowsBackend: Fetching host info...
10-28 22:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 22:34 DEBUG  WindowsBackend: windows version=vista
10-28 22:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-28 22:34 DEBUG  WindowsBackend: windows_sp=None
10-28 22:34 DEBUG  WindowsBackend: windows_build=7601
10-28 22:34 DEBUG  WindowsBackend: gmt=-8
10-28 22:34 DEBUG  WindowsBackend: country=US
10-28 22:34 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-28 22:34 DEBUG  WindowsBackend: windows_username=Jacob
10-28 22:34 DEBUG  WindowsBackend: user_full_name=Jacob
10-28 22:34 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-28 22:34 DEBUG  WindowsBackend: windows_language_code=1033
10-28 22:34 DEBUG  WindowsBackend: windows_language=English
10-28 22:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-28 22:34 DEBUG  WindowsBackend: bootloader=vista
10-28 22:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 407064.675781 mb free ntfs)
10-28 22:34 DEBUG  WindowsBackend: drive=Drive(C: hd 407064.675781 mb free ntfs)
10-28 22:34 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:34 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 22:34 DEBUG  WindowsBackend: drive=Drive(G: removable 3160.046875 mb free fat32)
10-28 22:34 DEBUG  WindowsBackend: uninstaller_path=None
10-28 22:34 DEBUG  WindowsBackend: previous_target_dir=None
10-28 22:34 DEBUG  WindowsBackend: previous_distro_name=None
10-28 22:34 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 22:34 DEBUG  WindowsBackend: keyboard_layout=us
10-28 22:34 DEBUG  WindowsBackend: keyboard_variant=
10-28 22:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 22:34 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 22:34 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-28 22:34 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 22:34 DEBUG  CommonBackend: Searching for local CDs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-28 22:34 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-28 22:34 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
10-28 22:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-28 22:34 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
10-28 22:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
10-28 22:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-28 22:34 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
10-28 22:34 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-28 22:34 INFO   Distro: Found a valid CD for Xubuntu: G:\
10-28 22:34 INFO   root: Running the CD menu...
10-28 22:34 DEBUG  WindowsFrontend: __init__...
10-28 22:34 DEBUG  WindowsFrontend: on_init...
10-28 22:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\translations, languages=['en_US', 'en']
10-28 22:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl5273.tmp\translations, languages=['en_US', 'en']
10-28 22:34 INFO   root: CD menu finished
10-28 22:34 DEBUG  CommonBackend: Showing info
10-28 22:34 DEBUG  root: application.quit
10-28 22:34 DEBUG  WindowsFrontend: frontend.quit
10-28 22:34 DEBUG  WindowsFrontend: frontend.on_quit
10-28 22:34 DEBUG  root: application.on_quit
10-28 22:34 INFO   root: sys.exit
10-28 22:35 INFO   root: === wubi 11.10 rev245 ===
10-28 22:35 DEBUG  root: Logfile is c:\users\jacob\appdata\local\temp\wubi-11.10-rev245.log
10-28 22:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jacob\\Downloads\\wubi.exe"']
10-28 22:35 DEBUG  CommonBackend: data_dir=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\data
10-28 22:35 DEBUG  WindowsBackend: 7z=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\bin\7z.exe
10-28 22:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 22:35 DEBUG  CommonBackend: Fetching basic info...
10-28 22:35 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-28 22:35 DEBUG  CommonBackend: platform=win32
10-28 22:35 DEBUG  CommonBackend: osname=nt
10-28 22:35 DEBUG  CommonBackend: language=en_US
10-28 22:35 DEBUG  CommonBackend: encoding=cp1252
10-28 22:35 DEBUG  WindowsBackend: arch=amd64
10-28 22:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\data\isolist.ini
10-28 22:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-28 22:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-28 22:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 22:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 22:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 22:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 22:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 22:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 22:35 DEBUG  WindowsBackend: Fetching host info...
10-28 22:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 22:35 DEBUG  WindowsBackend: windows version=vista
10-28 22:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-28 22:35 DEBUG  WindowsBackend: windows_sp=None
10-28 22:35 DEBUG  WindowsBackend: windows_build=7601
10-28 22:35 DEBUG  WindowsBackend: gmt=-8
10-28 22:35 DEBUG  WindowsBackend: country=US
10-28 22:35 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-28 22:35 DEBUG  WindowsBackend: windows_username=Jacob
10-28 22:35 DEBUG  WindowsBackend: user_full_name=Jacob
10-28 22:35 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-28 22:35 DEBUG  WindowsBackend: windows_language_code=1033
10-28 22:35 DEBUG  WindowsBackend: windows_language=English
10-28 22:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-28 22:35 DEBUG  WindowsBackend: bootloader=vista
10-28 22:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 407064.367188 mb free ntfs)
10-28 22:35 DEBUG  WindowsBackend: drive=Drive(C: hd 407064.367188 mb free ntfs)
10-28 22:35 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:35 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 22:35 DEBUG  WindowsBackend: drive=Drive(G: removable 3160.046875 mb free fat32)
10-28 22:35 DEBUG  WindowsBackend: uninstaller_path=None
10-28 22:35 DEBUG  WindowsBackend: previous_target_dir=None
10-28 22:35 DEBUG  WindowsBackend: previous_distro_name=None
10-28 22:35 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 22:35 DEBUG  WindowsBackend: keyboard_layout=us
10-28 22:35 DEBUG  WindowsBackend: keyboard_variant=
10-28 22:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 22:35 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 22:35 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-28 22:35 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 22:35 DEBUG  CommonBackend: Searching for local CDs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-28 22:35 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-28 22:35 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
10-28 22:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-28 22:35 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
10-28 22:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
10-28 22:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-28 22:35 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
10-28 22:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-28 22:35 INFO   Distro: Found a valid CD for Xubuntu: G:\
10-28 22:35 INFO   root: Running the CD menu...
10-28 22:35 DEBUG  WindowsFrontend: __init__...
10-28 22:35 DEBUG  WindowsFrontend: on_init...
10-28 22:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\translations, languages=['en_US', 'en']
10-28 22:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\translations, languages=['en_US', 'en']
10-28 22:35 INFO   root: CD menu finished
10-28 22:35 INFO   root: Running the installer...
10-28 22:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\translations, languages=['en_US', 'en']
10-28 22:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\translations, languages=['en_US', 'en']
10-28 22:35 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=jacob
10-28 22:35 INFO   root: Received settings
10-28 22:35 DEBUG  CommonBackend: Searching for local CD
10-28 22:35 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-28 22:35 INFO   Distro: Found a valid CD for Xubuntu: G:\
10-28 22:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\translations, languages=['en_US', 'en']
10-28 22:35 DEBUG  TaskList: # Running tasklist...
10-28 22:35 DEBUG  TaskList: ## Running select_target_dir...
10-28 22:35 INFO   WindowsBackend: Installing into C:\ubuntu
10-28 22:35 DEBUG  TaskList: ## Finished select_target_dir
10-28 22:35 DEBUG  TaskList: ## Running create_dir_structure...
10-28 22:35 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-28 22:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-28 22:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-28 22:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-28 22:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-28 22:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-28 22:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-28 22:35 DEBUG  TaskList: ## Finished create_dir_structure
10-28 22:35 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 22:35 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 22:35 DEBUG  TaskList: ## Running create_uninstaller...
10-28 22:35 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jacob\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Xubuntu.ico
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.xubuntu.org
10-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-28 22:35 DEBUG  TaskList: ## Finished create_uninstaller
10-28 22:35 DEBUG  TaskList: ## Running copy_installation_files...
10-28 22:35 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-28 22:35 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\winboot -> C:\ubuntu\winboot
10-28 22:35 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pylF9C9.tmp\data\images\Xubuntu.ico -> C:\ubuntu\Xubuntu.ico
10-28 22:35 DEBUG  TaskList: ## Finished copy_installation_files
10-28 22:35 DEBUG  TaskList: ## Running get_iso...
10-28 22:35 DEBUG  TaskList: New task copy_file
10-28 22:35 DEBUG  TaskList: ### Running copy_file...
10-28 22:40 DEBUG  TaskList: ### Finished copy_file
10-28 22:40 DEBUG  TaskList: New task check_iso
10-28 22:40 DEBUG  TaskList: ### Running check_iso...
10-28 22:40 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
10-28 22:40 DEBUG  Distro:   checking Xubuntu ISO C:\ubuntu\install\installation.iso
10-28 22:40 DEBUG  Distro:     wrong size: 4051697152 > 900000000
10-28 22:40 DEBUG  TaskList: ### Finished check_iso
10-28 22:40 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 589, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 568, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
10-28 22:40 DEBUG  TaskList: # Cancelling tasklist
10-28 22:40 DEBUG  TaskList: # Finished tasklist
10-28 22:40 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 589, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 568, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
10-28 22:43 INFO   root: === wubi 11.10 rev245 ===
10-28 22:43 DEBUG  root: Logfile is c:\users\jacob\appdata\local\temp\wubi-11.10-rev245.log
10-28 22:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jacob\\Downloads\\wubi.exe"']
10-28 22:43 DEBUG  CommonBackend: data_dir=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\data
10-28 22:43 DEBUG  WindowsBackend: 7z=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\bin\7z.exe
10-28 22:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 22:43 DEBUG  CommonBackend: Fetching basic info...
10-28 22:43 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-28 22:43 DEBUG  CommonBackend: platform=win32
10-28 22:43 DEBUG  CommonBackend: osname=nt
10-28 22:43 DEBUG  CommonBackend: language=en_US
10-28 22:43 DEBUG  CommonBackend: encoding=cp1252
10-28 22:43 DEBUG  WindowsBackend: arch=amd64
10-28 22:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\data\isolist.ini
10-28 22:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-28 22:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 22:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 22:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 22:43 DEBUG  WindowsBackend: Fetching host info...
10-28 22:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 22:43 DEBUG  WindowsBackend: windows version=vista
10-28 22:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-28 22:43 DEBUG  WindowsBackend: windows_sp=None
10-28 22:43 DEBUG  WindowsBackend: windows_build=7601
10-28 22:43 DEBUG  WindowsBackend: gmt=-8
10-28 22:43 DEBUG  WindowsBackend: country=US
10-28 22:43 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-28 22:43 DEBUG  WindowsBackend: windows_username=Jacob
10-28 22:43 DEBUG  WindowsBackend: user_full_name=Jacob
10-28 22:43 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-28 22:43 DEBUG  WindowsBackend: windows_language_code=1033
10-28 22:43 DEBUG  WindowsBackend: windows_language=English
10-28 22:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-28 22:43 DEBUG  WindowsBackend: bootloader=vista
10-28 22:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 403193.5 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(C: hd 403193.5 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 22:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-28 22:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-28 22:43 DEBUG  WindowsBackend: previous_distro_name=Xubuntu
10-28 22:43 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 22:43 DEBUG  WindowsBackend: keyboard_layout=us
10-28 22:43 DEBUG  WindowsBackend: keyboard_variant=
10-28 22:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 22:43 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 22:43 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-28 22:43 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 22:43 DEBUG  CommonBackend: Searching for local CDs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 INFO   root: Already installed, running the uninstaller...
10-28 22:43 INFO   root: Running the uninstaller...
10-28 22:43 INFO   CommonBackend: This is the uninstaller running
10-28 22:43 DEBUG  WindowsFrontend: __init__...
10-28 22:43 DEBUG  WindowsFrontend: on_init...
10-28 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\translations, languages=['en_US', 'en']
10-28 22:43 INFO   root: Received settings
10-28 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\translations, languages=['en_US', 'en']
10-28 22:43 DEBUG  TaskList: # Running tasklist...
10-28 22:43 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 22:43 DEBUG  WindowsBackend: Could not find bcd id
10-28 22:43 DEBUG  WindowsBackend: undo_bootini C:
10-28 22:43 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 403193.5 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: undo_bootini D:
10-28 22:43 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: undo_bootini E:
10-28 22:43 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:43 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 22:43 DEBUG  TaskList: ## Running Remove target dir...
10-28 22:43 DEBUG  CommonBackend: Deleting C:\ubuntu
10-28 22:43 DEBUG  TaskList: ## Finished Remove target dir
10-28 22:43 DEBUG  TaskList: ## Running Remove registry key...
10-28 22:43 DEBUG  TaskList: ## Finished Remove registry key
10-28 22:43 DEBUG  TaskList: # Finished tasklist
10-28 22:43 INFO   root: Almost finished uninstalling
10-28 22:43 INFO   root: Finished uninstallation
10-28 22:43 DEBUG  CommonBackend: Fetching basic info...
10-28 22:43 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-28 22:43 DEBUG  CommonBackend: platform=win32
10-28 22:43 DEBUG  CommonBackend: osname=nt
10-28 22:43 DEBUG  WindowsBackend: arch=amd64
10-28 22:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\data\isolist.ini
10-28 22:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-28 22:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 22:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 22:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 22:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 22:43 DEBUG  WindowsBackend: Fetching host info...
10-28 22:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 22:43 DEBUG  WindowsBackend: windows version=vista
10-28 22:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-28 22:43 DEBUG  WindowsBackend: windows_sp=None
10-28 22:43 DEBUG  WindowsBackend: windows_build=7601
10-28 22:43 DEBUG  WindowsBackend: gmt=-8
10-28 22:43 DEBUG  WindowsBackend: country=US
10-28 22:43 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-28 22:43 DEBUG  WindowsBackend: windows_username=Jacob
10-28 22:43 DEBUG  WindowsBackend: user_full_name=Jacob
10-28 22:43 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-28 22:43 DEBUG  WindowsBackend: windows_language_code=1033
10-28 22:43 DEBUG  WindowsBackend: windows_language=English
10-28 22:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-28 22:43 DEBUG  WindowsBackend: bootloader=vista
10-28 22:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 407060.351563 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(C: hd 407060.351563 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 22:43 DEBUG  WindowsBackend: uninstaller_path=None
10-28 22:43 DEBUG  WindowsBackend: previous_target_dir=None
10-28 22:43 DEBUG  WindowsBackend: previous_distro_name=None
10-28 22:43 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 22:43 DEBUG  WindowsBackend: keyboard_layout=us
10-28 22:43 DEBUG  WindowsBackend: keyboard_variant=
10-28 22:43 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-28 22:43 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 22:43 DEBUG  CommonBackend: Searching for local CDs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 INFO   root: Running the installer...
10-28 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\translations, languages=['en_US', 'en']
10-28 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\translations, languages=['en_US', 'en']
10-28 22:43 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=jacob
10-28 22:43 INFO   root: Received settings
10-28 22:43 DEBUG  CommonBackend: Searching for local CD
10-28 22:43 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:43 DEBUG  CommonBackend: Searching for local ISO
10-28 22:43 DEBUG  Distro:   checking Xubuntu ISO C:\Users\Jacob\Downloads\linuxmint-11-gnome-dvd-32bit.iso
10-28 22:43 DEBUG  Distro:     wrong size: 909107200 > 900000000
10-28 22:43 DEBUG  Distro:   checking Xubuntu ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:43 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:43 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-28 22:43 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-28 22:43 INFO   Distro: Found a valid iso for Xubuntu: C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\translations, languages=['en_US', 'en']
10-28 22:43 DEBUG  TaskList: # Running tasklist...
10-28 22:43 DEBUG  TaskList: ## Running select_target_dir...
10-28 22:43 INFO   WindowsBackend: Installing into C:\ubuntu
10-28 22:43 DEBUG  TaskList: ## Finished select_target_dir
10-28 22:43 DEBUG  TaskList: ## Running create_dir_structure...
10-28 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-28 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-28 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-28 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-28 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-28 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-28 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-28 22:43 DEBUG  TaskList: ## Finished create_dir_structure
10-28 22:43 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 22:43 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 22:43 DEBUG  TaskList: ## Running create_uninstaller...
10-28 22:43 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jacob\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Xubuntu.ico
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.xubuntu.org
10-28 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-28 22:43 DEBUG  TaskList: ## Finished create_uninstaller
10-28 22:43 DEBUG  TaskList: ## Running copy_installation_files...
10-28 22:43 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-28 22:43 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\winboot -> C:\ubuntu\winboot
10-28 22:43 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pyl142B.tmp\data\images\Xubuntu.ico -> C:\ubuntu\Xubuntu.ico
10-28 22:43 DEBUG  TaskList: ## Finished copy_installation_files
10-28 22:43 DEBUG  TaskList: ## Running get_iso...
10-28 22:43 DEBUG  CommonBackend: Trying to use ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:43 DEBUG  TaskList: New task check_iso
10-28 22:43 DEBUG  TaskList: ### Running check_iso...
10-28 22:43 DEBUG  CommonBackend: Checking C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:43 DEBUG  Distro:   checking Xubuntu ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:43 INFO   Distro: Found a valid iso for Xubuntu: C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:43 DEBUG  CommonBackend: Using distro Xubuntu i386 instead of Xubuntu amd64
10-28 22:43 DEBUG  TaskList: New task get_metalink
10-28 22:43 DEBUG  TaskList: #### Running get_metalink...
10-28 22:43 DEBUG  downloader: downloading http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/xubuntu-11.10-desktop-i386.metalink > C:\ubuntu\install
10-28 22:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\xubuntu-11.10-desktop-i386.metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/xubuntu-11.10-desktop-i386.metalink, basename=xubuntu-11.10-desktop-i386.metalink, length=1037, text=None
10-28 22:43 DEBUG  downloader: download finished (read 1037 bytes)
10-28 22:43 DEBUG  downloader: downloading http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink > C:\ubuntu\install
10-28 22:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=286, text=None
10-28 22:43 DEBUG  downloader: download finished (read 286 bytes)
10-28 22:43 DEBUG  downloader: downloading http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink.gpg > C:\ubuntu\install
10-28 22:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-28 22:43 DEBUG  downloader: download finished (read 198 bytes)
10-28 22:43 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-28 22:43 INFO   saplog: Checking block bindings..
10-28 22:43 INFO   saplog: Key verified successfully.
10-28 22:43 DEBUG  CommonBackend: metalink md5sums:
2201df3c8078b566fe504d1ffa776643  xubuntu-11.10-alternate-amd64.metalink
a13ac9bc08c6e93be24848c49b1af8d8  xubuntu-11.10-alternate-i386.metalink
91dc17958496adcd43a90fd951ca0fe4  xubuntu-11.10-desktop-amd64.metalink
2e38c2e2ff93dd9199c8df440d46655c  xubuntu-11.10-desktop-i386.metalink

10-28 22:43 DEBUG  TaskList: #### Finished get_metalink
10-28 22:43 DEBUG  TaskList: New task get_file_md5
10-28 22:43 DEBUG  TaskList: #### Running get_file_md5...
10-28 22:44 DEBUG  TaskList: #### Finished get_file_md5
10-28 22:44 DEBUG  TaskList: ### Finished check_iso
10-28 22:44 DEBUG  TaskList: New task copy_file
10-28 22:44 DEBUG  CommonBackend: Copying C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso > C:\ubuntu\install\installation.iso
10-28 22:44 DEBUG  TaskList: ### Running copy_file...
10-28 22:44 DEBUG  TaskList: ### Finished copy_file
10-28 22:44 DEBUG  TaskList: ## Finished get_iso
10-28 22:44 DEBUG  TaskList: ## Running extract_kernel...
10-28 22:44 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
10-28 22:44 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
10-28 22:44 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
10-28 22:44 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
10-28 22:44 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 22:44 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
10-28 22:44 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = fde150f5c6fd2de66ed7876efbfcc4c7 == fde150f5c6fd2de66ed7876efbfcc4c7
10-28 22:44 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
10-28 22:44 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = afd8fca57b25719c88f7b1b16cfd1afb == afd8fca57b25719c88f7b1b16cfd1afb
10-28 22:44 DEBUG  TaskList: ## Finished extract_kernel
10-28 22:44 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 22:44 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
10-28 22:44 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 22:44 DEBUG  TaskList: ## Running create_preseed...
10-28 22:44 DEBUG  TaskList: ## Finished create_preseed
10-28 22:44 DEBUG  TaskList: ## Running modify_bootloader...
10-28 22:44 DEBUG  TaskList: New task modify_bcd
10-28 22:44 DEBUG  TaskList: ### Running modify_bcd...
10-28 22:44 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 407060.351563 mb free ntfs)
10-28 22:44 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
10-28 22:44 DEBUG  TaskList: # Cancelling tasklist
10-28 22:44 DEBUG  TaskList: New task modify_bcd
10-28 22:44 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
10-28 22:44 DEBUG  TaskList: New task modify_bcd
10-28 22:44 DEBUG  TaskList: ## Finished modify_bootloader
10-28 22:44 DEBUG  TaskList: # Finished tasklist
10-28 22:44 INFO   root: === wubi 11.10 rev245 ===
10-28 22:44 DEBUG  root: Logfile is c:\users\jacob\appdata\local\temp\wubi-11.10-rev245.log
10-28 22:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jacob\\Downloads\\wubi.exe"']
10-28 22:44 DEBUG  CommonBackend: data_dir=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\data
10-28 22:44 DEBUG  WindowsBackend: 7z=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\bin\7z.exe
10-28 22:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 22:44 DEBUG  CommonBackend: Fetching basic info...
10-28 22:44 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-28 22:44 DEBUG  CommonBackend: platform=win32
10-28 22:44 DEBUG  CommonBackend: osname=nt
10-28 22:44 DEBUG  CommonBackend: language=en_US
10-28 22:44 DEBUG  CommonBackend: encoding=cp1252
10-28 22:44 DEBUG  WindowsBackend: arch=amd64
10-28 22:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\data\isolist.ini
10-28 22:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-28 22:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 22:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 22:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 22:44 DEBUG  WindowsBackend: Fetching host info...
10-28 22:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 22:44 DEBUG  WindowsBackend: windows version=vista
10-28 22:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-28 22:44 DEBUG  WindowsBackend: windows_sp=None
10-28 22:44 DEBUG  WindowsBackend: windows_build=7601
10-28 22:44 DEBUG  WindowsBackend: gmt=-8
10-28 22:44 DEBUG  WindowsBackend: country=US
10-28 22:44 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-28 22:44 DEBUG  WindowsBackend: windows_username=Jacob
10-28 22:44 DEBUG  WindowsBackend: user_full_name=Jacob
10-28 22:44 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-28 22:44 DEBUG  WindowsBackend: windows_language_code=1033
10-28 22:44 DEBUG  WindowsBackend: windows_language=English
10-28 22:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-28 22:44 DEBUG  WindowsBackend: bootloader=vista
10-28 22:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 406362.292969 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(C: hd 406362.292969 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 22:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-28 22:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-28 22:44 DEBUG  WindowsBackend: previous_distro_name=Xubuntu
10-28 22:44 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 22:44 DEBUG  WindowsBackend: keyboard_layout=us
10-28 22:44 DEBUG  WindowsBackend: keyboard_variant=
10-28 22:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 22:44 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 22:44 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-28 22:44 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 22:44 DEBUG  CommonBackend: Searching for local CDs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 INFO   root: Already installed, running the uninstaller...
10-28 22:44 INFO   root: Running the uninstaller...
10-28 22:44 INFO   CommonBackend: This is the uninstaller running
10-28 22:44 DEBUG  WindowsFrontend: __init__...
10-28 22:44 DEBUG  WindowsFrontend: on_init...
10-28 22:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\translations, languages=['en_US', 'en']
10-28 22:44 INFO   root: Received settings
10-28 22:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\translations, languages=['en_US', 'en']
10-28 22:44 DEBUG  TaskList: # Running tasklist...
10-28 22:44 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 22:44 DEBUG  WindowsBackend: Could not find bcd id
10-28 22:44 DEBUG  WindowsBackend: undo_bootini C:
10-28 22:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 406362.292969 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: undo_bootini D:
10-28 22:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: undo_bootini E:
10-28 22:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:44 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 22:44 DEBUG  TaskList: ## Running Remove target dir...
10-28 22:44 DEBUG  CommonBackend: Deleting C:\ubuntu
10-28 22:44 DEBUG  TaskList: ## Finished Remove target dir
10-28 22:44 DEBUG  TaskList: ## Running Remove registry key...
10-28 22:44 DEBUG  TaskList: ## Finished Remove registry key
10-28 22:44 DEBUG  TaskList: # Finished tasklist
10-28 22:44 INFO   root: Almost finished uninstalling
10-28 22:44 INFO   root: Finished uninstallation
10-28 22:44 DEBUG  CommonBackend: Fetching basic info...
10-28 22:44 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-28 22:44 DEBUG  CommonBackend: platform=win32
10-28 22:44 DEBUG  CommonBackend: osname=nt
10-28 22:44 DEBUG  WindowsBackend: arch=amd64
10-28 22:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\data\isolist.ini
10-28 22:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-28 22:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 22:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 22:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 22:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 22:44 DEBUG  WindowsBackend: Fetching host info...
10-28 22:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 22:44 DEBUG  WindowsBackend: windows version=vista
10-28 22:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-28 22:44 DEBUG  WindowsBackend: windows_sp=None
10-28 22:44 DEBUG  WindowsBackend: windows_build=7601
10-28 22:44 DEBUG  WindowsBackend: gmt=-8
10-28 22:44 DEBUG  WindowsBackend: country=US
10-28 22:44 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-28 22:44 DEBUG  WindowsBackend: windows_username=Jacob
10-28 22:44 DEBUG  WindowsBackend: user_full_name=Jacob
10-28 22:44 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-28 22:44 DEBUG  WindowsBackend: windows_language_code=1033
10-28 22:44 DEBUG  WindowsBackend: windows_language=English
10-28 22:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-28 22:44 DEBUG  WindowsBackend: bootloader=vista
10-28 22:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 407061.382813 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(C: hd 407061.382813 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-28 22:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 22:44 DEBUG  WindowsBackend: uninstaller_path=None
10-28 22:44 DEBUG  WindowsBackend: previous_target_dir=None
10-28 22:44 DEBUG  WindowsBackend: previous_distro_name=None
10-28 22:44 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 22:44 DEBUG  WindowsBackend: keyboard_layout=us
10-28 22:44 DEBUG  WindowsBackend: keyboard_variant=
10-28 22:44 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-28 22:44 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 22:44 DEBUG  CommonBackend: Searching for local CDs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:44 INFO   root: Running the installer...
10-28 22:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\translations, languages=['en_US', 'en']
10-28 22:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\translations, languages=['en_US', 'en']
10-28 22:45 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jacob
10-28 22:45 INFO   root: Received settings
10-28 22:45 DEBUG  CommonBackend: Searching for local CD
10-28 22:45 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp is a valid Ubuntu CD
10-28 22:45 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\casper\filesystem.squashfs
10-28 22:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 22:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 22:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 22:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 22:45 DEBUG  CommonBackend: Searching for local ISO
10-28 22:45 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Jacob\Downloads\linuxmint-11-gnome-dvd-32bit.iso
10-28 22:45 DEBUG  Distro:     wrong size: 909107200 > 900000000
10-28 22:45 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:45 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-28 22:45 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-28 22:45 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-28 22:45 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
10-28 22:45 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386.iso
10-28 22:45 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386.iso
10-28 22:45 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-28 22:45 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-28 22:45 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
10-28 22:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl9E31.tmp\translations, languages=['en_US', 'en']
10-28 22:45 DEBUG  TaskList: # Running tasklist...
10-28 22:45 DEBUG  TaskList: ## Running select_target_dir...
10-28 22:45 INFO   WindowsBackend: Installing into C:\ubuntu
10-28 22:45 DEBUG  TaskList: ## Finished select_target_dir
10-28 22:45 DEBUG  TaskList: ## Running create_dir_structure...
10-28 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-28 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-28 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-28 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-28 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-28 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-28 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-28 22:45 DEBUG  TaskList: ## Finished create_dir_structure
10-28 22:45 DEBUG  TaskList: ## Running create_uninstaller...
10-28 22:45 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jacob\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-28 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-28 22:45 DEBUG  TaskList: ## Finished create_uninstaller
10-28 22:45 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-28 22:45 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-28 22:45 DEBUG  TaskList: ## Running get_diskimage...
10-28 22:45 DEBUG  TaskList: New task download
10-28 22:45 DEBUG  TaskList: ### Running download...
10-28 22:45 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-28 22:45 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-28 22:50 DEBUG  TaskList: ### Finished download
10-28 22:50 DEBUG  downloader: download finished (read 507143012 bytes)
10-28 22:50 DEBUG  TaskList: ## Finished get_diskimage
10-28 22:50 DEBUG  TaskList: ## Running extract_diskimage...
10-28 22:51 DEBUG  TaskList: ## Finished extract_diskimage
10-28 22:51 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 22:51 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
10-28 22:51 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 22:51 DEBUG  TaskList: ## Running expand_diskimage...
10-28 22:52 DEBUG  TaskList: ## Finished expand_diskimage
10-28 22:52 DEBUG  TaskList: ## Running create_swap_diskimage...
10-28 22:52 DEBUG  TaskList: ## Finished create_swap_diskimage
10-28 22:52 DEBUG  TaskList: ## Running modify_bootloader...
10-28 22:52 DEBUG  TaskList: New task modify_bcd
10-28 22:52 DEBUG  TaskList: ### Running modify_bcd...
10-28 22:52 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 407061.382813 mb free ntfs)
10-28 22:52 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
10-28 22:52 DEBUG  TaskList: # Cancelling tasklist
10-28 22:52 DEBUG  TaskList: New task modify_bcd
10-28 22:52 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
10-28 22:52 DEBUG  TaskList: New task modify_bcd
10-28 22:52 DEBUG  TaskList: ## Finished modify_bootloader
10-28 22:52 DEBUG  TaskList: # Finished tasklist
10-29 11:01 INFO   root: === wubi 11.10 rev245 ===
10-29 11:01 DEBUG  root: Logfile is c:\users\jacob\appdata\local\temp\wubi-11.10-rev245.log
10-29 11:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jacob\\Downloads\\wubi.exe"']
10-29 11:01 DEBUG  CommonBackend: data_dir=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\data
10-29 11:01 DEBUG  WindowsBackend: 7z=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\bin\7z.exe
10-29 11:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-29 11:01 DEBUG  CommonBackend: Fetching basic info...
10-29 11:01 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-29 11:01 DEBUG  CommonBackend: platform=win32
10-29 11:01 DEBUG  CommonBackend: osname=nt
10-29 11:01 DEBUG  CommonBackend: language=en_US
10-29 11:01 DEBUG  CommonBackend: encoding=cp1252
10-29 11:01 DEBUG  WindowsBackend: arch=amd64
10-29 11:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\data\isolist.ini
10-29 11:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-29 11:01 DEBUG  WindowsBackend: Fetching host info...
10-29 11:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-29 11:01 DEBUG  WindowsBackend: windows version=vista
10-29 11:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-29 11:01 DEBUG  WindowsBackend: windows_sp=None
10-29 11:01 DEBUG  WindowsBackend: windows_build=7601
10-29 11:01 DEBUG  WindowsBackend: gmt=-8
10-29 11:01 DEBUG  WindowsBackend: country=US
10-29 11:01 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-29 11:01 DEBUG  WindowsBackend: windows_username=Jacob
10-29 11:01 DEBUG  WindowsBackend: user_full_name=Jacob
10-29 11:01 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-29 11:01 DEBUG  WindowsBackend: windows_language_code=1033
10-29 11:01 DEBUG  WindowsBackend: windows_language=English
10-29 11:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-29 11:01 DEBUG  WindowsBackend: bootloader=vista
10-29 11:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 403947.921875 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(C: hd 403947.921875 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-29 11:01 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-29 11:01 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-29 11:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-29 11:01 DEBUG  WindowsBackend: keyboard_id=67699721
10-29 11:01 DEBUG  WindowsBackend: keyboard_layout=us
10-29 11:01 DEBUG  WindowsBackend: keyboard_variant=
10-29 11:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-29 11:01 DEBUG  CommonBackend: locale=en_US.UTF-8
10-29 11:01 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-29 11:01 DEBUG  CommonBackend: Searching ISOs on USB devices
10-29 11:01 DEBUG  CommonBackend: Searching for local CDs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 INFO   root: Already installed, running the uninstaller...
10-29 11:01 INFO   root: Running the uninstaller...
10-29 11:01 INFO   CommonBackend: This is the uninstaller running
10-29 11:01 DEBUG  WindowsFrontend: __init__...
10-29 11:01 DEBUG  WindowsFrontend: on_init...
10-29 11:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\translations, languages=['en_US', 'en']
10-29 11:01 INFO   root: Received settings
10-29 11:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\translations, languages=['en_US', 'en']
10-29 11:01 DEBUG  TaskList: # Running tasklist...
10-29 11:01 DEBUG  TaskList: ## Running Remove bootloader entry...
10-29 11:01 DEBUG  WindowsBackend: Could not find bcd id
10-29 11:01 DEBUG  WindowsBackend: undo_bootini C:
10-29 11:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 403947.921875 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: undo_bootini D:
10-29 11:01 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1740.95703125 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: undo_bootini E:
10-29 11:01 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1107.87890625 mb free fat32)
10-29 11:01 DEBUG  TaskList: ## Finished Remove bootloader entry
10-29 11:01 DEBUG  TaskList: ## Running Remove target dir...
10-29 11:01 DEBUG  CommonBackend: Deleting C:\ubuntu
10-29 11:01 DEBUG  TaskList: ## Finished Remove target dir
10-29 11:01 DEBUG  TaskList: ## Running Remove registry key...
10-29 11:01 DEBUG  TaskList: ## Finished Remove registry key
10-29 11:01 DEBUG  TaskList: # Finished tasklist
10-29 11:01 INFO   root: Almost finished uninstalling
10-29 11:01 INFO   root: Finished uninstallation
10-29 11:01 DEBUG  CommonBackend: Fetching basic info...
10-29 11:01 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-29 11:01 DEBUG  CommonBackend: platform=win32
10-29 11:01 DEBUG  CommonBackend: osname=nt
10-29 11:01 DEBUG  WindowsBackend: arch=amd64
10-29 11:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\data\isolist.ini
10-29 11:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-29 11:01 DEBUG  WindowsBackend: Fetching host info...
10-29 11:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-29 11:01 DEBUG  WindowsBackend: windows version=vista
10-29 11:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-29 11:01 DEBUG  WindowsBackend: windows_sp=None
10-29 11:01 DEBUG  WindowsBackend: windows_build=7601
10-29 11:01 DEBUG  WindowsBackend: gmt=-8
10-29 11:01 DEBUG  WindowsBackend: country=US
10-29 11:01 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-29 11:01 DEBUG  WindowsBackend: windows_username=Jacob
10-29 11:01 DEBUG  WindowsBackend: user_full_name=Jacob
10-29 11:01 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-29 11:01 DEBUG  WindowsBackend: windows_language_code=1033
10-29 11:01 DEBUG  WindowsBackend: windows_language=English
10-29 11:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-29 11:01 DEBUG  WindowsBackend: bootloader=vista
10-29 11:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 407034.390625 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(C: hd 407034.390625 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-29 11:01 DEBUG  WindowsBackend: uninstaller_path=None
10-29 11:01 DEBUG  WindowsBackend: previous_target_dir=None
10-29 11:01 DEBUG  WindowsBackend: previous_distro_name=None
10-29 11:01 DEBUG  WindowsBackend: keyboard_id=67699721
10-29 11:01 DEBUG  WindowsBackend: keyboard_layout=us
10-29 11:01 DEBUG  WindowsBackend: keyboard_variant=
10-29 11:01 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-29 11:01 DEBUG  CommonBackend: Searching ISOs on USB devices
10-29 11:01 DEBUG  CommonBackend: Searching for local CDs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 INFO   root: Running the installer...
10-29 11:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\translations, languages=['en_US', 'en']
10-29 11:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pylE436.tmp\translations, languages=['en_US', 'en']
10-29 11:01 INFO   WindowsFrontend: Operation cancelled
10-29 11:01 DEBUG  WindowsFrontend: frontend.quit
10-29 11:01 DEBUG  WindowsFrontend: frontend.on_quit
10-29 11:01 DEBUG  root: application.on_quit
10-29 11:01 INFO   root: sys.exit
10-29 11:01 INFO   root: === wubi 11.10 rev245 ===
10-29 11:01 DEBUG  root: Logfile is c:\users\jacob\appdata\local\temp\wubi-11.10-rev245.log
10-29 11:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jacob\\Downloads\\wubi.exe"']
10-29 11:01 DEBUG  CommonBackend: data_dir=C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\data
10-29 11:01 DEBUG  WindowsBackend: 7z=C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\bin\7z.exe
10-29 11:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-29 11:01 DEBUG  CommonBackend: Fetching basic info...
10-29 11:01 DEBUG  CommonBackend: original_exe=C:\Users\Jacob\Downloads\wubi.exe
10-29 11:01 DEBUG  CommonBackend: platform=win32
10-29 11:01 DEBUG  CommonBackend: osname=nt
10-29 11:01 DEBUG  CommonBackend: language=en_US
10-29 11:01 DEBUG  CommonBackend: encoding=cp1252
10-29 11:01 DEBUG  WindowsBackend: arch=amd64
10-29 11:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\data\isolist.ini
10-29 11:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-29 11:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-29 11:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-29 11:01 DEBUG  WindowsBackend: Fetching host info...
10-29 11:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-29 11:01 DEBUG  WindowsBackend: windows version=vista
10-29 11:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-29 11:01 DEBUG  WindowsBackend: windows_sp=None
10-29 11:01 DEBUG  WindowsBackend: windows_build=7601
10-29 11:01 DEBUG  WindowsBackend: gmt=-8
10-29 11:01 DEBUG  WindowsBackend: country=US
10-29 11:01 DEBUG  WindowsBackend: timezone=America/Los_Angeles
10-29 11:01 DEBUG  WindowsBackend: windows_username=Jacob
10-29 11:01 DEBUG  WindowsBackend: user_full_name=Jacob
10-29 11:01 DEBUG  WindowsBackend: user_directory=C:\Users\Jacob
10-29 11:01 DEBUG  WindowsBackend: windows_language_code=1033
10-29 11:01 DEBUG  WindowsBackend: windows_language=English
10-29 11:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
10-29 11:01 DEBUG  WindowsBackend: bootloader=vista
10-29 11:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 407033.675781 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(C: hd 407033.675781 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(D: hd 1740.95703125 mb free ntfs)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(E: hd 1107.87890625 mb free fat32)
10-29 11:01 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-29 11:01 DEBUG  WindowsBackend: uninstaller_path=None
10-29 11:01 DEBUG  WindowsBackend: previous_target_dir=None
10-29 11:01 DEBUG  WindowsBackend: previous_distro_name=None
10-29 11:01 DEBUG  WindowsBackend: keyboard_id=67699721
10-29 11:01 DEBUG  WindowsBackend: keyboard_layout=us
10-29 11:01 DEBUG  WindowsBackend: keyboard_variant=
10-29 11:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-29 11:01 DEBUG  CommonBackend: locale=en_US.UTF-8
10-29 11:01 DEBUG  WindowsBackend: total_memory_mb=4043.859375
10-29 11:01 DEBUG  CommonBackend: Searching ISOs on USB devices
10-29 11:01 DEBUG  CommonBackend: Searching for local CDs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-29 11:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:01 INFO   root: Running the installer...
10-29 11:01 DEBUG  WindowsFrontend: __init__...
10-29 11:01 DEBUG  WindowsFrontend: on_init...
10-29 11:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\translations, languages=['en_US', 'en']
10-29 11:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\translations, languages=['en_US', 'en']
10-29 11:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=jacob
10-29 11:02 INFO   root: Received settings
10-29 11:02 DEBUG  CommonBackend: Searching for local CD
10-29 11:02 DEBUG  Distro:   checking whether C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp is a valid Xubuntu CD
10-29 11:02 DEBUG  Distro:     does not contain C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\casper\filesystem.squashfs
10-29 11:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-29 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-29 11:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-29 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-29 11:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-29 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-29 11:02 DEBUG  CommonBackend: Searching for local ISO
10-29 11:02 DEBUG  Distro:   checking Xubuntu ISO C:\Users\Jacob\Downloads\linuxmint-11-gnome-dvd-32bit.iso
10-29 11:02 DEBUG  Distro:     wrong size: 909107200 > 900000000
10-29 11:02 DEBUG  Distro:   checking Xubuntu ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-29 11:02 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-29 11:02 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-29 11:02 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-29 11:02 INFO   Distro: Found a valid iso for Xubuntu: C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-29 11:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\translations, languages=['en_US', 'en']
10-29 11:02 DEBUG  TaskList: # Running tasklist...
10-29 11:02 DEBUG  TaskList: ## Running select_target_dir...
10-29 11:02 INFO   WindowsBackend: Installing into C:\ubuntu
10-29 11:02 DEBUG  TaskList: ## Finished select_target_dir
10-29 11:02 DEBUG  TaskList: ## Running create_dir_structure...
10-29 11:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-29 11:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-29 11:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-29 11:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-29 11:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-29 11:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-29 11:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-29 11:02 DEBUG  TaskList: ## Finished create_dir_structure
10-29 11:02 DEBUG  TaskList: ## Running uncompress_target_dir...
10-29 11:02 DEBUG  TaskList: ## Finished uncompress_target_dir
10-29 11:02 DEBUG  TaskList: ## Running create_uninstaller...
10-29 11:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jacob\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Xubuntu.ico
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.xubuntu.org
10-29 11:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-29 11:02 DEBUG  TaskList: ## Finished create_uninstaller
10-29 11:02 DEBUG  TaskList: ## Running copy_installation_files...
10-29 11:02 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-29 11:02 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\winboot -> C:\ubuntu\winboot
10-29 11:02 DEBUG  WindowsBackend: Copying C:\Users\Jacob\AppData\Local\Temp\pyl277D.tmp\data\images\Xubuntu.ico -> C:\ubuntu\Xubuntu.ico
10-29 11:02 DEBUG  TaskList: ## Finished copy_installation_files
10-29 11:02 DEBUG  TaskList: ## Running get_iso...
10-29 11:02 DEBUG  CommonBackend: Trying to use ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-29 11:02 DEBUG  TaskList: New task check_iso
10-29 11:02 DEBUG  TaskList: ### Running check_iso...
10-29 11:02 DEBUG  CommonBackend: Checking C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-29 11:02 DEBUG  Distro:   checking Xubuntu ISO C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-29 11:02 INFO   Distro: Found a valid iso for Xubuntu: C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso
10-29 11:02 DEBUG  CommonBackend: Using distro Xubuntu i386 instead of Xubuntu amd64
10-29 11:02 DEBUG  TaskList: New task get_metalink
10-29 11:02 DEBUG  TaskList: #### Running get_metalink...
10-29 11:02 DEBUG  downloader: downloading http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/xubuntu-11.10-desktop-i386.metalink > C:\ubuntu\install
10-29 11:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\xubuntu-11.10-desktop-i386.metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/xubuntu-11.10-desktop-i386.metalink, basename=xubuntu-11.10-desktop-i386.metalink, length=1037, text=None
10-29 11:02 DEBUG  downloader: download finished (read 1037 bytes)
10-29 11:02 DEBUG  downloader: downloading http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink > C:\ubuntu\install
10-29 11:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=286, text=None
10-29 11:02 DEBUG  downloader: download finished (read 286 bytes)
10-29 11:02 DEBUG  downloader: downloading http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink.gpg > C:\ubuntu\install
10-29 11:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/xubuntu/releases/11.10/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-29 11:02 DEBUG  downloader: download finished (read 198 bytes)
10-29 11:02 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-29 11:02 INFO   saplog: Checking block bindings..
10-29 11:02 INFO   saplog: Key verified successfully.
10-29 11:02 DEBUG  CommonBackend: metalink md5sums:
2201df3c8078b566fe504d1ffa776643  xubuntu-11.10-alternate-amd64.metalink
a13ac9bc08c6e93be24848c49b1af8d8  xubuntu-11.10-alternate-i386.metalink
91dc17958496adcd43a90fd951ca0fe4  xubuntu-11.10-desktop-amd64.metalink
2e38c2e2ff93dd9199c8df440d46655c  xubuntu-11.10-desktop-i386.metalink

10-29 11:02 DEBUG  TaskList: #### Finished get_metalink
10-29 11:02 DEBUG  TaskList: New task get_file_md5
10-29 11:02 DEBUG  TaskList: #### Running get_file_md5...
10-29 11:02 DEBUG  TaskList: #### Finished get_file_md5
10-29 11:02 DEBUG  TaskList: ### Finished check_iso
10-29 11:02 DEBUG  TaskList: New task copy_file
10-29 11:02 DEBUG  CommonBackend: Copying C:\Users\Jacob\Downloads\xubuntu-11.10-desktop-i386(1).iso > C:\ubuntu\install\installation.iso
10-29 11:02 DEBUG  TaskList: ### Running copy_file...
10-29 11:02 DEBUG  TaskList: ### Finished copy_file
10-29 11:02 DEBUG  TaskList: ## Finished get_iso
10-29 11:02 DEBUG  TaskList: ## Running extract_kernel...
10-29 11:02 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
10-29 11:02 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
10-29 11:02 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
10-29 11:02 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
10-29 11:02 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-29 11:02 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
10-29 11:02 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = fde150f5c6fd2de66ed7876efbfcc4c7 == fde150f5c6fd2de66ed7876efbfcc4c7
10-29 11:02 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
10-29 11:02 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = afd8fca57b25719c88f7b1b16cfd1afb == afd8fca57b25719c88f7b1b16cfd1afb
10-29 11:02 DEBUG  TaskList: ## Finished extract_kernel
10-29 11:02 DEBUG  TaskList: ## Running choose_disk_sizes...
10-29 11:02 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
10-29 11:02 DEBUG  TaskList: ## Finished choose_disk_sizes
10-29 11:02 DEBUG  TaskList: ## Running create_preseed...
10-29 11:02 DEBUG  TaskList: ## Finished create_preseed
10-29 11:02 DEBUG  TaskList: ## Running modify_bootloader...
10-29 11:02 DEBUG  TaskList: New task modify_bcd
10-29 11:02 DEBUG  TaskList: ### Running modify_bcd...
10-29 11:02 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 407033.675781 mb free ntfs)
10-29 11:02 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
10-29 11:02 DEBUG  TaskList: # Cancelling tasklist
10-29 11:02 DEBUG  TaskList: New task modify_bcd
10-29 11:02 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Xubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
10-29 11:02 DEBUG  TaskList: New task modify_bcd
10-29 11:02 DEBUG  TaskList: ## Finished modify_bootloader
10-29 11:02 DEBUG  TaskList: # Finished tasklist

```Can someone please help me resolve this?

---

### Post by LinuxFan999 on 2011-10-29
Are you going to be using Wubi to check out Xubuntu, or as a permanent installation?
Using Wubi as a permanent installation is not recommended.

---

### Post by garvinrick4 on 2011-10-29
I have not seen it before but a Few good wubi users around here.
Could not open your BCD (boot loader) to add a Wubi entry in BCD so as dual boot.
Wubi is a folder inside of Windows or the size you stipulated and hooks up to its
boot loader. In a partition install Ubuntu uses its own bootloader. If there is 
a folder inside of Windows right next to USERS in C: drive uninstall it or use the
remove program app in windows to do so and try again. Why it did not give authority
to get into BCD I do not know but might have it set that way yourself. Again maybe
a wubi user around here has seen it. This will bump you up to start of Forum, good luck partner.

---

### Post by bcbc on 2011-10-29
This is a windows problem. Open up an administrator command prompt and run: bcdedit (which outputs your current bcd store) and it will likely give you the same error.

---

### Post by EpicTTR on 2011-10-29
> **bcbc said:**
> This is a windows problem. Open up an administrator command prompt and run: bcdedit (which outputs your current bcd store) and it will likely give you the same error.

You were right, when I run bcdedit from the command prompt I get the error:

```
The boot configuration data store could not be opened. The system cannot find the file specified.
```

How can I fix that? I am running CMD as admin.

---

### Post by Shmits on 2011-10-29
i

---

### Post by bcbc on 2011-10-30
> **EpicTTR said:**
> You were right, when I run bcdedit from the command prompt I get the error:

```
The boot configuration data store could not be opened. The system cannot find the file specified.
```

How can I fix that? I am running CMD as admin.

[This article]("http://support.microsoft.com/kb/2419286") is for servers but seems to apply. (In most cases, the \bcd directory is on the hidden boot partition, not on C:\)
> ssue: 3: 



“The boot configuration data store could not be opened. The system cannot find the file specified.”


Symptoms

When you run Bcdedit /enum all you get the following error

“The boot configuration data store could not be opened. The system cannot find the file specified.” 


Look for the following registry key HKEY_LOCAL_MACHINE\BCD00000000
If we check under HKLM you will not find the key BCD00000000 


Cause

If some 3rd party storage Disk or Storage Management software is installed it may bring all the volume without drive letter offline 

Generally 100 MB partition is system partition which contains Boot configuration Database and does not have a drive letter assigned.



Resolution

From command prompt

C:\>Diskpart

C:\Diskpart> List volume

C:\Diskpart> Select volume 1 (Considering this is 100 MB system partition)

c:\Diskpart> Online volume

C:\Diskpart> exit

OR 

From the Disk Management console assign the drive letter to the 100MB partition it should bring the disk online.

To access Disk Management, open command prompt 

C:\>Diskmgmt.msc

Select the 100 MB volume; Right click on the volume Change drive letter & Path; Assign a drive letter.

Assigning the drive letter will ensure the volume is not offline again after a reboot.


The volumes may go offline if AUTOMOUNT is disabled either while using a 3rd party storage software or if the user manually disabled the AUTOMOUNT for the volume. To check this type the following command after running diskpart in the administrator command prompt 

DISKPART> automount

Automatic mounting of new volumes is disabled.

To enable AUTOMOUNT run the following command

DISKPART> automount enable

Reboot the server and the volume will not go offline. 

Note This is a "FAST PUBLISH" article created directly from within the Microsoft support organization. The information contained herein is provided as-is in response to emerging issues. As a result of the speed in making it available, the materials may include typographical errors and may be revised at any time without notice. See Terms of Use for other considerations.

---

### Post by EpicTTR on 2011-10-30
> **bcbc said:**
> [This article]("http://support.microsoft.com/kb/2419286") is for servers but seems to apply. (In most cases, the \bcd directory is on the hidden boot partition, not on C:\)

Thank you for your help! 

Running the commands below solved the problem for me!
```

C:\>Diskpart

C:\Diskpart> List volume

C:\Diskpart> Select volume 1 (Considering this is 100 MB system partition)

c:\Diskpart> Online volume

C:\Diskpart> exit

```

---

### Post by bcbc on 2011-10-30
Great! And thanks for the feedback. This one's been a bit puzzling and I haven't been able to reproduce it so it's good to know what works!

---

