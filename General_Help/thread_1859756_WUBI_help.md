---
title: "WUBI help?"
date: 2011-10-14
forum: General Help
---

### Post by djb6 on 2011-10-14
I'm trying to install 11.10 on my netbook.  I had 11.04 on it and was going to upgrade, but there wasn't enough space so I uninstalled it, and was going to install the new ubuntu using WUBI.  Here is the log file that I'm getting.  Any help would be appreciated.  I'm trying to install basic ubuntu.  I would like ubuntu netbook from WUBI, but that was not an option for the type of distro.
```
10-13 21:47 INFO   root: === wubi 11.10 rev245 ===
10-13 21:47 DEBUG  root: Logfile is c:\users\danbro~1\appdata\local\temp\wubi-11.10-rev245.log
10-13 21:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan Broersma\\Downloads\\wubi.exe"']
10-13 21:47 DEBUG  CommonBackend: data_dir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\data
10-13 21:47 DEBUG  WindowsBackend: 7z=C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\bin\7z.exe
10-13 21:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-13 21:47 DEBUG  CommonBackend: Fetching basic info...
10-13 21:47 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi.exe
10-13 21:47 DEBUG  CommonBackend: platform=win32
10-13 21:47 DEBUG  CommonBackend: osname=nt
10-13 21:47 DEBUG  CommonBackend: language=en_US
10-13 21:47 DEBUG  CommonBackend: encoding=cp1252
10-13 21:47 DEBUG  WindowsBackend: arch=amd64
10-13 21:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\data\isolist.ini
10-13 21:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-13 21:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-13 21:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-13 21:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-13 21:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-13 21:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-13 21:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-13 21:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-13 21:47 DEBUG  WindowsBackend: Fetching host info...
10-13 21:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-13 21:47 DEBUG  WindowsBackend: windows version=vista
10-13 21:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-13 21:47 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-13 21:47 DEBUG  WindowsBackend: windows_build=7601
10-13 21:47 DEBUG  WindowsBackend: gmt=-6
10-13 21:47 DEBUG  WindowsBackend: country=US
10-13 21:47 DEBUG  WindowsBackend: timezone=America/Chicago
10-13 21:47 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-13 21:47 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-13 21:47 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-13 21:47 DEBUG  WindowsBackend: windows_language_code=1033
10-13 21:47 DEBUG  WindowsBackend: windows_language=English
10-13 21:47 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-13 21:47 DEBUG  WindowsBackend: bootloader=vista
10-13 21:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 200015.753906 mb free ntfs)
10-13 21:47 DEBUG  WindowsBackend: drive=Drive(C: hd 200015.753906 mb free ntfs)
10-13 21:47 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-13 21:47 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-13 21:47 DEBUG  WindowsBackend: uninstaller_path=None
10-13 21:47 DEBUG  WindowsBackend: previous_target_dir=None
10-13 21:47 DEBUG  WindowsBackend: previous_distro_name=None
10-13 21:47 DEBUG  WindowsBackend: keyboard_id=67699721
10-13 21:47 DEBUG  WindowsBackend: keyboard_layout=us
10-13 21:47 DEBUG  WindowsBackend: keyboard_variant=
10-13 21:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-13 21:47 DEBUG  CommonBackend: locale=en_US.UTF-8
10-13 21:47 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-13 21:47 DEBUG  CommonBackend: Searching ISOs on USB devices
10-13 21:47 DEBUG  CommonBackend: Searching for local CDs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Ubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Ubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Kubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Kubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Xubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Xubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Mythbuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp is a valid Mythbuntu CD
10-13 21:47 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 21:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 21:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 21:47 INFO   root: Running the installer...
10-13 21:47 DEBUG  WindowsFrontend: __init__...
10-13 21:47 DEBUG  WindowsFrontend: on_init...
10-13 21:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\translations, languages=['en_US', 'en']
10-13 21:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl4191.tmp\translations, languages=['en_US', 'en']
10-13 21:47 INFO   WindowsFrontend: Operation cancelled
10-13 21:47 DEBUG  WindowsFrontend: frontend.quit
10-13 21:47 DEBUG  WindowsFrontend: frontend.on_quit
10-13 21:47 DEBUG  root: application.on_quit
10-13 21:47 INFO   root: sys.exit
10-13 22:01 INFO   root: === wubi 11.10 rev245 ===
10-13 22:01 DEBUG  root: Logfile is c:\users\danbro~1\appdata\local\temp\wubi-11.10-rev245.log
10-13 22:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan Broersma\\Downloads\\wubi (1).exe"']
10-13 22:01 DEBUG  CommonBackend: data_dir=C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\data
10-13 22:01 DEBUG  WindowsBackend: 7z=C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\bin\7z.exe
10-13 22:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-13 22:01 DEBUG  CommonBackend: Fetching basic info...
10-13 22:01 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi (1).exe
10-13 22:01 DEBUG  CommonBackend: platform=win32
10-13 22:01 DEBUG  CommonBackend: osname=nt
10-13 22:01 DEBUG  CommonBackend: language=en_US
10-13 22:01 DEBUG  CommonBackend: encoding=cp1252
10-13 22:01 DEBUG  WindowsBackend: arch=amd64
10-13 22:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\data\isolist.ini
10-13 22:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-13 22:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-13 22:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-13 22:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-13 22:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-13 22:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-13 22:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-13 22:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-13 22:01 DEBUG  WindowsBackend: Fetching host info...
10-13 22:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-13 22:01 DEBUG  WindowsBackend: windows version=vista
10-13 22:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-13 22:01 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-13 22:01 DEBUG  WindowsBackend: windows_build=7601
10-13 22:01 DEBUG  WindowsBackend: gmt=-6
10-13 22:01 DEBUG  WindowsBackend: country=US
10-13 22:01 DEBUG  WindowsBackend: timezone=America/Chicago
10-13 22:01 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-13 22:01 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-13 22:01 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-13 22:01 DEBUG  WindowsBackend: windows_language_code=1033
10-13 22:01 DEBUG  WindowsBackend: windows_language=English
10-13 22:01 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-13 22:01 DEBUG  WindowsBackend: bootloader=vista
10-13 22:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 199910.679688 mb free ntfs)
10-13 22:01 DEBUG  WindowsBackend: drive=Drive(C: hd 199910.679688 mb free ntfs)
10-13 22:01 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-13 22:01 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-13 22:01 DEBUG  WindowsBackend: uninstaller_path=None
10-13 22:01 DEBUG  WindowsBackend: previous_target_dir=None
10-13 22:01 DEBUG  WindowsBackend: previous_distro_name=None
10-13 22:01 DEBUG  WindowsBackend: keyboard_id=67699721
10-13 22:01 DEBUG  WindowsBackend: keyboard_layout=us
10-13 22:01 DEBUG  WindowsBackend: keyboard_variant=
10-13 22:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-13 22:01 DEBUG  CommonBackend: locale=en_US.UTF-8
10-13 22:01 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-13 22:01 DEBUG  CommonBackend: Searching ISOs on USB devices
10-13 22:01 DEBUG  CommonBackend: Searching for local CDs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Kubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Kubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Xubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Xubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Mythbuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Mythbuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 INFO   root: Running the installer...
10-13 22:01 DEBUG  WindowsFrontend: __init__...
10-13 22:01 DEBUG  WindowsFrontend: on_init...
10-13 22:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\translations, languages=['en_US', 'en']
10-13 22:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\translations, languages=['en_US', 'en']
10-13 22:01 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=danbroersma
10-13 22:01 INFO   root: Received settings
10-13 22:01 DEBUG  CommonBackend: Searching for local CD
10-13 22:01 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:01 DEBUG  CommonBackend: Searching for local ISO
10-13 22:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\translations, languages=['en_US', 'en']
10-13 22:01 DEBUG  TaskList: # Running tasklist...
10-13 22:01 DEBUG  TaskList: ## Running select_target_dir...
10-13 22:01 INFO   WindowsBackend: Installing into C:\ubuntu
10-13 22:01 DEBUG  TaskList: ## Finished select_target_dir
10-13 22:01 DEBUG  TaskList: ## Running create_dir_structure...
10-13 22:01 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-13 22:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-13 22:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-13 22:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-13 22:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-13 22:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-13 22:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-13 22:01 DEBUG  TaskList: ## Finished create_dir_structure
10-13 22:01 DEBUG  TaskList: ## Running create_uninstaller...
10-13 22:01 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan Broersma\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-13 22:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-13 22:01 DEBUG  TaskList: ## Finished create_uninstaller
10-13 22:01 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-13 22:01 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-13 22:01 DEBUG  TaskList: ## Running get_diskimage...
10-13 22:01 DEBUG  TaskList: New task download
10-13 22:01 DEBUG  TaskList: ### Running download...
10-13 22:01 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-13 22:01 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-13 22:24 DEBUG  TaskList: ### Finished download
10-13 22:24 DEBUG  downloader: download finished (read 507143012 bytes)
10-13 22:24 DEBUG  TaskList: ## Finished get_diskimage
10-13 22:24 DEBUG  TaskList: ## Running extract_diskimage...
10-13 22:27 DEBUG  TaskList: ## Finished extract_diskimage
10-13 22:27 DEBUG  TaskList: ## Running choose_disk_sizes...
10-13 22:27 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
10-13 22:27 DEBUG  TaskList: ## Finished choose_disk_sizes
10-13 22:27 DEBUG  TaskList: ## Running expand_diskimage...
10-13 22:35 DEBUG  TaskList: ## Finished expand_diskimage
10-13 22:35 DEBUG  TaskList: ## Running create_swap_diskimage...
10-13 22:35 DEBUG  TaskList: ## Finished create_swap_diskimage
10-13 22:35 DEBUG  TaskList: ## Running modify_bootloader...
10-13 22:35 DEBUG  TaskList: New task modify_bcd
10-13 22:35 DEBUG  TaskList: ### Running modify_bcd...
10-13 22:35 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 199910.679688 mb free ntfs)
10-13 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {5484de88-9784-11e0-aa7f-f645f772cb08}
10-13 22:35 DEBUG  TaskList: ### Finished modify_bcd
10-13 22:35 DEBUG  TaskList: New task modify_bcd
10-13 22:35 DEBUG  TaskList: ### Running modify_bcd...
10-13 22:35 DEBUG  WindowsBackend: modify_bcd Drive(D: removable 266.609375 mb free fat)
10-13 22:35 DEBUG  WindowsBackend: BCD has already been modified
10-13 22:35 DEBUG  TaskList: ### Finished modify_bcd
10-13 22:35 DEBUG  TaskList: New task modify_bcd
10-13 22:35 DEBUG  TaskList: ### Running modify_bcd...
10-13 22:35 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
10-13 22:35 DEBUG  WindowsBackend: BCD has already been modified
10-13 22:35 DEBUG  TaskList: ### Finished modify_bcd
10-13 22:35 DEBUG  TaskList: ## Finished modify_bootloader
10-13 22:35 DEBUG  TaskList: ## Running diskimage_bootloader...
10-13 22:35 DEBUG  WindowsBackend: Copying C:\Users\DANBRO~1\AppData\Local\Temp\pylD049.tmp\winboot -> C:\ubuntu\winboot
10-13 22:35 ERROR  TaskList: [Errno 13] Permission denied: 'D:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'D:\\wubildr'
10-13 22:35 DEBUG  TaskList: # Cancelling tasklist
10-13 22:35 DEBUG  TaskList: # Finished tasklist
10-13 22:35 ERROR  root: [Errno 13] Permission denied: 'D:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'D:\\wubildr'
10-13 22:37 INFO   root: === wubi 11.10 rev245 ===
10-13 22:37 DEBUG  root: Logfile is c:\users\danbro~1\appdata\local\temp\wubi-11.10-rev245.log
10-13 22:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan Broersma\\Downloads\\wubi (1).exe"']
10-13 22:37 DEBUG  CommonBackend: data_dir=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\data
10-13 22:37 DEBUG  WindowsBackend: 7z=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\bin\7z.exe
10-13 22:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-13 22:37 DEBUG  CommonBackend: Fetching basic info...
10-13 22:37 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi (1).exe
10-13 22:37 DEBUG  CommonBackend: platform=win32
10-13 22:37 DEBUG  CommonBackend: osname=nt
10-13 22:37 DEBUG  CommonBackend: language=en_US
10-13 22:37 DEBUG  CommonBackend: encoding=cp1252
10-13 22:37 DEBUG  WindowsBackend: arch=amd64
10-13 22:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\data\isolist.ini
10-13 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-13 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-13 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-13 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-13 22:37 DEBUG  WindowsBackend: Fetching host info...
10-13 22:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-13 22:37 DEBUG  WindowsBackend: windows version=vista
10-13 22:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-13 22:37 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-13 22:37 DEBUG  WindowsBackend: windows_build=7601
10-13 22:37 DEBUG  WindowsBackend: gmt=-6
10-13 22:37 DEBUG  WindowsBackend: country=US
10-13 22:37 DEBUG  WindowsBackend: timezone=America/Chicago
10-13 22:37 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-13 22:37 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-13 22:37 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-13 22:37 DEBUG  WindowsBackend: windows_language_code=1033
10-13 22:37 DEBUG  WindowsBackend: windows_language=English
10-13 22:37 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-13 22:37 DEBUG  WindowsBackend: bootloader=vista
10-13 22:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195732.085938 mb free ntfs)
10-13 22:37 DEBUG  WindowsBackend: drive=Drive(C: hd 195732.085938 mb free ntfs)
10-13 22:37 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-13 22:37 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-13 22:37 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-13 22:37 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-13 22:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-13 22:37 DEBUG  WindowsBackend: keyboard_id=67699721
10-13 22:37 DEBUG  WindowsBackend: keyboard_layout=us
10-13 22:37 DEBUG  WindowsBackend: keyboard_variant=
10-13 22:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-13 22:37 DEBUG  CommonBackend: locale=en_US.UTF-8
10-13 22:37 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-13 22:37 DEBUG  CommonBackend: Searching ISOs on USB devices
10-13 22:37 DEBUG  CommonBackend: Searching for local CDs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 INFO   root: Already installed, running the uninstaller...
10-13 22:37 INFO   root: Running the uninstaller...
10-13 22:37 INFO   CommonBackend: This is the uninstaller running
10-13 22:37 DEBUG  WindowsFrontend: __init__...
10-13 22:37 DEBUG  WindowsFrontend: on_init...
10-13 22:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\translations, languages=['en_US', 'en']
10-13 22:37 INFO   root: Received settings
10-13 22:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\translations, languages=['en_US', 'en']
10-13 22:37 DEBUG  TaskList: # Running tasklist...
10-13 22:37 DEBUG  TaskList: ## Running Remove bootloader entry...
10-13 22:37 DEBUG  WindowsBackend: Removing bcd entry {5484de88-9784-11e0-aa7f-f645f772cb08}
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
10-13 22:37 DEBUG  WindowsBackend: undo_bootini C:
10-13 22:37 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195732.085938 mb free ntfs)
10-13 22:37 DEBUG  WindowsBackend: undo_bootini D:
10-13 22:37 DEBUG  WindowsBackend: undo_configsys Drive(D: removable 266.609375 mb free fat)
10-13 22:37 DEBUG  WindowsBackend: undo_bootini Q:
10-13 22:37 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
10-13 22:37 DEBUG  TaskList: ## Finished Remove bootloader entry
10-13 22:37 DEBUG  TaskList: ## Running Remove target dir...
10-13 22:37 DEBUG  CommonBackend: Deleting C:\ubuntu
10-13 22:37 DEBUG  TaskList: ## Finished Remove target dir
10-13 22:37 DEBUG  TaskList: ## Running Remove registry key...
10-13 22:37 DEBUG  TaskList: ## Finished Remove registry key
10-13 22:37 DEBUG  TaskList: # Finished tasklist
10-13 22:37 INFO   root: Almost finished uninstalling
10-13 22:37 INFO   root: Finished uninstallation
10-13 22:37 DEBUG  CommonBackend: Fetching basic info...
10-13 22:37 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi (1).exe
10-13 22:37 DEBUG  CommonBackend: platform=win32
10-13 22:37 DEBUG  CommonBackend: osname=nt
10-13 22:37 DEBUG  WindowsBackend: arch=amd64
10-13 22:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\data\isolist.ini
10-13 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-13 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-13 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-13 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-13 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-13 22:37 DEBUG  WindowsBackend: Fetching host info...
10-13 22:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-13 22:37 DEBUG  WindowsBackend: windows version=vista
10-13 22:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-13 22:37 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-13 22:37 DEBUG  WindowsBackend: windows_build=7601
10-13 22:37 DEBUG  WindowsBackend: gmt=-6
10-13 22:37 DEBUG  WindowsBackend: country=US
10-13 22:37 DEBUG  WindowsBackend: timezone=America/Chicago
10-13 22:37 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-13 22:37 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-13 22:37 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-13 22:37 DEBUG  WindowsBackend: windows_language_code=1033
10-13 22:37 DEBUG  WindowsBackend: windows_language=English
10-13 22:37 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-13 22:37 DEBUG  WindowsBackend: bootloader=vista
10-13 22:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 199407.875 mb free ntfs)
10-13 22:37 DEBUG  WindowsBackend: drive=Drive(C: hd 199407.875 mb free ntfs)
10-13 22:37 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-13 22:37 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-13 22:37 DEBUG  WindowsBackend: uninstaller_path=None
10-13 22:37 DEBUG  WindowsBackend: previous_target_dir=None
10-13 22:37 DEBUG  WindowsBackend: previous_distro_name=None
10-13 22:37 DEBUG  WindowsBackend: keyboard_id=67699721
10-13 22:37 DEBUG  WindowsBackend: keyboard_layout=us
10-13 22:37 DEBUG  WindowsBackend: keyboard_variant=
10-13 22:37 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-13 22:37 DEBUG  CommonBackend: Searching ISOs on USB devices
10-13 22:37 DEBUG  CommonBackend: Searching for local CDs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 INFO   root: Running the installer...
10-13 22:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\translations, languages=['en_US', 'en']
10-13 22:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\translations, languages=['en_US', 'en']
10-13 22:37 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=danbroersma
10-13 22:37 INFO   root: Received settings
10-13 22:37 DEBUG  CommonBackend: Searching for local CD
10-13 22:37 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-13 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-13 22:37 DEBUG  CommonBackend: Searching for local ISO
10-13 22:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pylB931.tmp\translations, languages=['en_US', 'en']
10-13 22:37 DEBUG  TaskList: # Running tasklist...
10-13 22:37 DEBUG  TaskList: ## Running select_target_dir...
10-13 22:37 INFO   WindowsBackend: Installing into C:\ubuntu
10-13 22:37 DEBUG  TaskList: ## Finished select_target_dir
10-13 22:37 DEBUG  TaskList: ## Running create_dir_structure...
10-13 22:37 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-13 22:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-13 22:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-13 22:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-13 22:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-13 22:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-13 22:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-13 22:37 DEBUG  TaskList: ## Finished create_dir_structure
10-13 22:37 DEBUG  TaskList: ## Running create_uninstaller...
10-13 22:37 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan Broersma\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-13 22:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-13 22:37 DEBUG  TaskList: ## Finished create_uninstaller
10-13 22:37 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-13 22:37 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-13 22:37 DEBUG  TaskList: ## Running get_diskimage...
10-13 22:37 DEBUG  TaskList: New task download
10-13 22:37 DEBUG  TaskList: ### Running download...
10-13 22:37 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-13 22:37 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-13 22:44 INFO   WindowsFrontend: Operation cancelled
10-13 22:44 DEBUG  WindowsFrontend: frontend.quit
10-13 22:44 DEBUG  WindowsFrontend: frontend.on_quit
10-13 22:44 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
10-13 22:44 DEBUG  TaskList: # Cancelling tasklist
10-13 22:44 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
10-13 22:44 DEBUG  root: application.on_quit
10-13 22:44 DEBUG  root: Forceful exit
10-13 22:44 INFO   root: sys.exit
10-14 05:35 INFO   root: === wubi 11.10 rev245 ===
10-14 05:35 DEBUG  root: Logfile is c:\users\danbro~1\appdata\local\temp\wubi-11.10-rev245.log
10-14 05:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan Broersma\\Downloads\\wubi (1).exe"']
10-14 05:35 DEBUG  CommonBackend: data_dir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\data
10-14 05:35 DEBUG  WindowsBackend: 7z=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\bin\7z.exe
10-14 05:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-14 05:35 DEBUG  CommonBackend: Fetching basic info...
10-14 05:35 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi (1).exe
10-14 05:35 DEBUG  CommonBackend: platform=win32
10-14 05:35 DEBUG  CommonBackend: osname=nt
10-14 05:35 DEBUG  CommonBackend: language=en_US
10-14 05:35 DEBUG  CommonBackend: encoding=cp1252
10-14 05:35 DEBUG  WindowsBackend: arch=amd64
10-14 05:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\data\isolist.ini
10-14 05:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 05:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 05:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 05:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 05:35 DEBUG  WindowsBackend: Fetching host info...
10-14 05:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 05:35 DEBUG  WindowsBackend: windows version=vista
10-14 05:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-14 05:35 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-14 05:35 DEBUG  WindowsBackend: windows_build=7601
10-14 05:35 DEBUG  WindowsBackend: gmt=-6
10-14 05:35 DEBUG  WindowsBackend: country=US
10-14 05:35 DEBUG  WindowsBackend: timezone=America/Chicago
10-14 05:35 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-14 05:35 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-14 05:35 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-14 05:35 DEBUG  WindowsBackend: windows_language_code=1033
10-14 05:35 DEBUG  WindowsBackend: windows_language=English
10-14 05:35 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-14 05:35 DEBUG  WindowsBackend: bootloader=vista
10-14 05:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 199149.710938 mb free ntfs)
10-14 05:35 DEBUG  WindowsBackend: drive=Drive(C: hd 199149.710938 mb free ntfs)
10-14 05:35 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-14 05:35 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-14 05:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-14 05:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-14 05:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-14 05:35 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 05:35 DEBUG  WindowsBackend: keyboard_layout=us
10-14 05:35 DEBUG  WindowsBackend: keyboard_variant=
10-14 05:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-14 05:35 DEBUG  CommonBackend: locale=en_US.UTF-8
10-14 05:35 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-14 05:35 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 05:35 DEBUG  CommonBackend: Searching for local CDs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 INFO   root: Already installed, running the uninstaller...
10-14 05:35 INFO   root: Running the uninstaller...
10-14 05:35 INFO   CommonBackend: This is the uninstaller running
10-14 05:35 DEBUG  WindowsFrontend: __init__...
10-14 05:35 DEBUG  WindowsFrontend: on_init...
10-14 05:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\translations, languages=['en_US', 'en']
10-14 05:35 INFO   root: Received settings
10-14 05:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\translations, languages=['en_US', 'en']
10-14 05:35 DEBUG  TaskList: # Running tasklist...
10-14 05:35 DEBUG  TaskList: ## Running Remove bootloader entry...
10-14 05:35 DEBUG  WindowsBackend: Could not find bcd id
10-14 05:35 DEBUG  WindowsBackend: undo_bootini C:
10-14 05:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 199149.710938 mb free ntfs)
10-14 05:35 DEBUG  WindowsBackend: undo_bootini D:
10-14 05:35 DEBUG  WindowsBackend: undo_configsys Drive(D: removable 266.609375 mb free fat)
10-14 05:35 DEBUG  WindowsBackend: undo_bootini Q:
10-14 05:35 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
10-14 05:35 DEBUG  TaskList: ## Finished Remove bootloader entry
10-14 05:35 DEBUG  TaskList: ## Running Remove target dir...
10-14 05:35 DEBUG  CommonBackend: Deleting C:\ubuntu
10-14 05:35 DEBUG  TaskList: ## Finished Remove target dir
10-14 05:35 DEBUG  TaskList: ## Running Remove registry key...
10-14 05:35 DEBUG  TaskList: ## Finished Remove registry key
10-14 05:35 DEBUG  TaskList: # Finished tasklist
10-14 05:35 INFO   root: Almost finished uninstalling
10-14 05:35 INFO   root: Finished uninstallation
10-14 05:35 DEBUG  CommonBackend: Fetching basic info...
10-14 05:35 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi (1).exe
10-14 05:35 DEBUG  CommonBackend: platform=win32
10-14 05:35 DEBUG  CommonBackend: osname=nt
10-14 05:35 DEBUG  WindowsBackend: arch=amd64
10-14 05:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\data\isolist.ini
10-14 05:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 05:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 05:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 05:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 05:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 05:35 DEBUG  WindowsBackend: Fetching host info...
10-14 05:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 05:35 DEBUG  WindowsBackend: windows version=vista
10-14 05:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-14 05:35 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-14 05:35 DEBUG  WindowsBackend: windows_build=7601
10-14 05:35 DEBUG  WindowsBackend: gmt=-6
10-14 05:35 DEBUG  WindowsBackend: country=US
10-14 05:35 DEBUG  WindowsBackend: timezone=America/Chicago
10-14 05:35 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-14 05:35 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-14 05:35 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-14 05:35 DEBUG  WindowsBackend: windows_language_code=1033
10-14 05:35 DEBUG  WindowsBackend: windows_language=English
10-14 05:35 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-14 05:35 DEBUG  WindowsBackend: bootloader=vista
10-14 05:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 199289.402344 mb free ntfs)
10-14 05:35 DEBUG  WindowsBackend: drive=Drive(C: hd 199289.402344 mb free ntfs)
10-14 05:35 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-14 05:35 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-14 05:35 DEBUG  WindowsBackend: uninstaller_path=None
10-14 05:35 DEBUG  WindowsBackend: previous_target_dir=None
10-14 05:35 DEBUG  WindowsBackend: previous_distro_name=None
10-14 05:35 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 05:35 DEBUG  WindowsBackend: keyboard_layout=us
10-14 05:35 DEBUG  WindowsBackend: keyboard_variant=
10-14 05:35 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-14 05:35 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 05:35 DEBUG  CommonBackend: Searching for local CDs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:35 INFO   root: Running the installer...
10-14 05:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\translations, languages=['en_US', 'en']
10-14 05:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\translations, languages=['en_US', 'en']
10-14 05:36 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=danbroersma
10-14 05:36 INFO   root: Received settings
10-14 05:36 DEBUG  CommonBackend: Searching for local CD
10-14 05:36 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp is a valid Ubuntu CD
10-14 05:36 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\casper\filesystem.squashfs
10-14 05:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:36 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:36 DEBUG  CommonBackend: Searching for local ISO
10-14 05:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl9296.tmp\translations, languages=['en_US', 'en']
10-14 05:36 DEBUG  TaskList: # Running tasklist...
10-14 05:36 DEBUG  TaskList: ## Running select_target_dir...
10-14 05:36 INFO   WindowsBackend: Installing into C:\ubuntu
10-14 05:36 DEBUG  TaskList: ## Finished select_target_dir
10-14 05:36 DEBUG  TaskList: ## Running create_dir_structure...
10-14 05:36 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-14 05:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-14 05:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-14 05:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-14 05:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-14 05:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-14 05:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-14 05:36 DEBUG  TaskList: ## Finished create_dir_structure
10-14 05:36 DEBUG  TaskList: ## Running create_uninstaller...
10-14 05:36 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan Broersma\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-14 05:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-14 05:36 DEBUG  TaskList: ## Finished create_uninstaller
10-14 05:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-14 05:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-14 05:36 DEBUG  TaskList: ## Running get_diskimage...
10-14 05:36 DEBUG  TaskList: New task download
10-14 05:36 DEBUG  TaskList: ### Running download...
10-14 05:36 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-14 05:36 ERROR  TaskList: unsupported operand type(s) for /: 'NoneType' and 'int'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1114, in _do_open
  File "\lib\wubi\backends\common\downloader.py", line 46, in start
TypeError: unsupported operand type(s) for /: 'NoneType' and 'int'
10-14 05:36 ERROR  TaskList: Non fatal error unsupported operand type(s) for /: 'NoneType' and 'int' in task download
10-14 05:36 DEBUG  TaskList: ### Finished download
10-14 05:36 DEBUG  TaskList: ## Finished get_diskimage
10-14 05:36 DEBUG  TaskList: ## Running extract_diskimage...
10-14 05:36 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
10-14 05:36 DEBUG  TaskList: # Cancelling tasklist
10-14 05:36 DEBUG  TaskList: # Finished tasklist
10-14 05:36 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
10-14 05:38 INFO   root: === wubi 11.10 rev245 ===
10-14 05:38 DEBUG  root: Logfile is c:\users\danbro~1\appdata\local\temp\wubi-11.10-rev245.log
10-14 05:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan Broersma\\Downloads\\wubi (1).exe"']
10-14 05:38 DEBUG  CommonBackend: data_dir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\data
10-14 05:38 DEBUG  WindowsBackend: 7z=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\bin\7z.exe
10-14 05:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-14 05:38 DEBUG  CommonBackend: Fetching basic info...
10-14 05:38 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi (1).exe
10-14 05:38 DEBUG  CommonBackend: platform=win32
10-14 05:38 DEBUG  CommonBackend: osname=nt
10-14 05:38 DEBUG  CommonBackend: language=en_US
10-14 05:38 DEBUG  CommonBackend: encoding=cp1252
10-14 05:38 DEBUG  WindowsBackend: arch=amd64
10-14 05:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\data\isolist.ini
10-14 05:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 05:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 05:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 05:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 05:38 DEBUG  WindowsBackend: Fetching host info...
10-14 05:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 05:38 DEBUG  WindowsBackend: windows version=vista
10-14 05:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-14 05:38 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-14 05:38 DEBUG  WindowsBackend: windows_build=7601
10-14 05:38 DEBUG  WindowsBackend: gmt=-6
10-14 05:38 DEBUG  WindowsBackend: country=US
10-14 05:38 DEBUG  WindowsBackend: timezone=America/Chicago
10-14 05:38 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-14 05:38 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-14 05:38 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-14 05:38 DEBUG  WindowsBackend: windows_language_code=1033
10-14 05:38 DEBUG  WindowsBackend: windows_language=English
10-14 05:38 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-14 05:38 DEBUG  WindowsBackend: bootloader=vista
10-14 05:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 199286.617188 mb free ntfs)
10-14 05:38 DEBUG  WindowsBackend: drive=Drive(C: hd 199286.617188 mb free ntfs)
10-14 05:38 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-14 05:38 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-14 05:38 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-14 05:38 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-14 05:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-14 05:38 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 05:38 DEBUG  WindowsBackend: keyboard_layout=us
10-14 05:38 DEBUG  WindowsBackend: keyboard_variant=
10-14 05:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-14 05:38 DEBUG  CommonBackend: locale=en_US.UTF-8
10-14 05:38 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-14 05:38 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 05:38 DEBUG  CommonBackend: Searching for local CDs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 INFO   root: Already installed, running the uninstaller...
10-14 05:38 INFO   root: Running the uninstaller...
10-14 05:38 INFO   CommonBackend: This is the uninstaller running
10-14 05:38 DEBUG  WindowsFrontend: __init__...
10-14 05:38 DEBUG  WindowsFrontend: on_init...
10-14 05:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\translations, languages=['en_US', 'en']
10-14 05:38 INFO   root: Received settings
10-14 05:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\translations, languages=['en_US', 'en']
10-14 05:38 DEBUG  TaskList: # Running tasklist...
10-14 05:38 DEBUG  TaskList: ## Running Remove bootloader entry...
10-14 05:38 DEBUG  WindowsBackend: Could not find bcd id
10-14 05:38 DEBUG  WindowsBackend: undo_bootini C:
10-14 05:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 199286.617188 mb free ntfs)
10-14 05:38 DEBUG  WindowsBackend: undo_bootini D:
10-14 05:38 DEBUG  WindowsBackend: undo_configsys Drive(D: removable 266.609375 mb free fat)
10-14 05:38 DEBUG  WindowsBackend: undo_bootini Q:
10-14 05:38 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
10-14 05:38 DEBUG  TaskList: ## Finished Remove bootloader entry
10-14 05:38 DEBUG  TaskList: ## Running Remove target dir...
10-14 05:38 DEBUG  CommonBackend: Deleting C:\ubuntu
10-14 05:38 DEBUG  TaskList: ## Finished Remove target dir
10-14 05:38 DEBUG  TaskList: ## Running Remove registry key...
10-14 05:38 DEBUG  TaskList: ## Finished Remove registry key
10-14 05:38 DEBUG  TaskList: # Finished tasklist
10-14 05:38 INFO   root: Almost finished uninstalling
10-14 05:38 INFO   root: Finished uninstallation
10-14 05:38 DEBUG  CommonBackend: Fetching basic info...
10-14 05:38 DEBUG  CommonBackend: original_exe=C:\Users\Dan Broersma\Downloads\wubi (1).exe
10-14 05:38 DEBUG  CommonBackend: platform=win32
10-14 05:38 DEBUG  CommonBackend: osname=nt
10-14 05:38 DEBUG  WindowsBackend: arch=amd64
10-14 05:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\data\isolist.ini
10-14 05:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 05:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 05:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 05:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 05:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 05:38 DEBUG  WindowsBackend: Fetching host info...
10-14 05:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 05:38 DEBUG  WindowsBackend: windows version=vista
10-14 05:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-14 05:38 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-14 05:38 DEBUG  WindowsBackend: windows_build=7601
10-14 05:38 DEBUG  WindowsBackend: gmt=-6
10-14 05:38 DEBUG  WindowsBackend: country=US
10-14 05:38 DEBUG  WindowsBackend: timezone=America/Chicago
10-14 05:38 DEBUG  WindowsBackend: windows_username=Dan Broersma
10-14 05:38 DEBUG  WindowsBackend: user_full_name=Dan Broersma
10-14 05:38 DEBUG  WindowsBackend: user_directory=C:\Users\Dan Broersma
10-14 05:38 DEBUG  WindowsBackend: windows_language_code=1033
10-14 05:38 DEBUG  WindowsBackend: windows_language=English
10-14 05:38 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
10-14 05:38 DEBUG  WindowsBackend: bootloader=vista
10-14 05:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 199288.988281 mb free ntfs)
10-14 05:38 DEBUG  WindowsBackend: drive=Drive(C: hd 199288.988281 mb free ntfs)
10-14 05:38 DEBUG  WindowsBackend: drive=Drive(D: removable 266.609375 mb free fat)
10-14 05:38 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-14 05:38 DEBUG  WindowsBackend: uninstaller_path=None
10-14 05:38 DEBUG  WindowsBackend: previous_target_dir=None
10-14 05:38 DEBUG  WindowsBackend: previous_distro_name=None
10-14 05:38 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 05:38 DEBUG  WindowsBackend: keyboard_layout=us
10-14 05:38 DEBUG  WindowsBackend: keyboard_variant=
10-14 05:38 DEBUG  WindowsBackend: total_memory_mb=1011.8671875
10-14 05:38 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 05:38 DEBUG  CommonBackend: Searching for local CDs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-14 05:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:38 INFO   root: Running the installer...
10-14 05:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\translations, languages=['en_US', 'en']
10-14 05:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\translations, languages=['en_US', 'en']
10-14 05:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=danbroersma
10-14 05:39 INFO   root: Received settings
10-14 05:39 DEBUG  CommonBackend: Searching for local CD
10-14 05:39 DEBUG  Distro:   checking whether C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp is a valid Ubuntu CD
10-14 05:39 DEBUG  Distro:     does not contain C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\casper\filesystem.squashfs
10-14 05:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 05:39 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-14 05:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-14 05:39 DEBUG  CommonBackend: Searching for local ISO
10-14 05:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\translations, languages=['en_US', 'en']
10-14 05:39 DEBUG  TaskList: # Running tasklist...
10-14 05:39 DEBUG  TaskList: ## Running select_target_dir...
10-14 05:39 INFO   WindowsBackend: Installing into C:\ubuntu
10-14 05:39 DEBUG  TaskList: ## Finished select_target_dir
10-14 05:39 DEBUG  TaskList: ## Running create_dir_structure...
10-14 05:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-14 05:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-14 05:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-14 05:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-14 05:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-14 05:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-14 05:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-14 05:39 DEBUG  TaskList: ## Finished create_dir_structure
10-14 05:39 DEBUG  TaskList: ## Running create_uninstaller...
10-14 05:39 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan Broersma\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-14 05:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-14 05:39 DEBUG  TaskList: ## Finished create_uninstaller
10-14 05:39 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-14 05:39 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-14 05:39 DEBUG  TaskList: ## Running get_diskimage...
10-14 05:39 DEBUG  TaskList: New task download
10-14 05:39 DEBUG  TaskList: ### Running download...
10-14 05:39 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-14 05:39 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-14 06:02 DEBUG  TaskList: ### Finished download
10-14 06:02 DEBUG  downloader: download finished (read 507143012 bytes)
10-14 06:02 DEBUG  TaskList: ## Finished get_diskimage
10-14 06:02 DEBUG  TaskList: ## Running extract_diskimage...
10-14 06:05 DEBUG  TaskList: ## Finished extract_diskimage
10-14 06:05 DEBUG  TaskList: ## Running choose_disk_sizes...
10-14 06:05 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
10-14 06:05 DEBUG  TaskList: ## Finished choose_disk_sizes
10-14 06:05 DEBUG  TaskList: ## Running expand_diskimage...
10-14 06:12 DEBUG  TaskList: ## Finished expand_diskimage
10-14 06:12 DEBUG  TaskList: ## Running create_swap_diskimage...
10-14 06:12 DEBUG  TaskList: ## Finished create_swap_diskimage
10-14 06:12 DEBUG  TaskList: ## Running modify_bootloader...
10-14 06:12 DEBUG  TaskList: New task modify_bcd
10-14 06:12 DEBUG  TaskList: ### Running modify_bcd...
10-14 06:12 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 199288.988281 mb free ntfs)
10-14 06:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {5484de89-9784-11e0-aa7f-f645f772cb08}
10-14 06:12 DEBUG  TaskList: ### Finished modify_bcd
10-14 06:12 DEBUG  TaskList: New task modify_bcd
10-14 06:12 DEBUG  TaskList: ### Running modify_bcd...
10-14 06:12 DEBUG  WindowsBackend: modify_bcd Drive(D: removable 266.609375 mb free fat)
10-14 06:12 DEBUG  WindowsBackend: BCD has already been modified
10-14 06:12 DEBUG  TaskList: ### Finished modify_bcd
10-14 06:12 DEBUG  TaskList: New task modify_bcd
10-14 06:12 DEBUG  TaskList: ### Running modify_bcd...
10-14 06:12 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
10-14 06:12 DEBUG  WindowsBackend: BCD has already been modified
10-14 06:12 DEBUG  TaskList: ### Finished modify_bcd
10-14 06:12 DEBUG  TaskList: ## Finished modify_bootloader
10-14 06:12 DEBUG  TaskList: ## Running diskimage_bootloader...
10-14 06:12 DEBUG  WindowsBackend: Copying C:\Users\DANBRO~1\AppData\Local\Temp\pyl98ED.tmp\winboot -> C:\ubuntu\winboot
10-14 06:12 ERROR  TaskList: [Errno 13] Permission denied: 'D:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'D:\\wubildr'
10-14 06:12 DEBUG  TaskList: # Cancelling tasklist
10-14 06:12 DEBUG  TaskList: # Finished tasklist
10-14 06:12 ERROR  root: [Errno 13] Permission denied: 'D:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'D:\\wubildr'

```

---

