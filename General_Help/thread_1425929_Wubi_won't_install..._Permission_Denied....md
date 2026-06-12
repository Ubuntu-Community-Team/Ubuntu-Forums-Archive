---
title: "Wubi won't install... Permission Denied..."
date: 2010-03-09
forum: General Help
---

### Post by bobthetwit on 2010-03-09
I tried to install ubuntu 9.10 using live CD and wubi. In wubi, I tried to install inside windows, on a partition of my hard drive. The partition was completely empty, and was 11GB. Wubi said something about permission being denied. I have windows 7, and wish to boot ubuntu 9.10 as a 2ndary OS. The log said:
```
[COLOR="DarkSlateGray"][COLOR="Lime"][COLOR="Blue"]02-27 19:04 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-27 19:04 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-27 19:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
02-27 19:04 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\data
02-27 19:04 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\bin\7z.exe
02-27 19:04 DEBUG  CommonBackend: Fetching basic info...
02-27 19:04 DEBUG  CommonBackend: original_exe=E:\wubi.exe
02-27 19:04 DEBUG  CommonBackend: platform=win32
02-27 19:04 DEBUG  CommonBackend: osname=nt
02-27 19:04 DEBUG  CommonBackend: language=en_US
02-27 19:04 DEBUG  CommonBackend: encoding=cp1252
02-27 19:04 DEBUG  WindowsBackend: arch=amd64
02-27 19:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\data\isolist.ini
02-27 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 19:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 19:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-27 19:04 DEBUG  WindowsBackend: Fetching host info...
02-27 19:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 19:04 DEBUG  WindowsBackend: windows version=vista
02-27 19:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-27 19:04 DEBUG  WindowsBackend: windows_sp=None
02-27 19:04 DEBUG  WindowsBackend: windows_build=7600
02-27 19:04 DEBUG  WindowsBackend: gmt=-5
02-27 19:04 DEBUG  WindowsBackend: country=US
02-27 19:04 DEBUG  WindowsBackend: timezone=America/New_York
02-27 19:04 DEBUG  WindowsBackend: windows_username=BobTheTwit
02-27 19:04 DEBUG  WindowsBackend: user_full_name=BobTheTwit
02-27 19:04 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
02-27 19:04 DEBUG  WindowsBackend: windows_language_code=1033
02-27 19:04 DEBUG  WindowsBackend: windows_language=English
02-27 19:04 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
02-27 19:04 DEBUG  WindowsBackend: bootloader=vista
02-27 19:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 57049.6992188 mb free ntfs)
02-27 19:04 DEBUG  WindowsBackend: drive=Drive(B: hd 15268.8007813 mb free ntfs)
02-27 19:04 DEBUG  WindowsBackend: drive=Drive(C: hd 57049.6992188 mb free ntfs)
02-27 19:04 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
02-27 19:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
02-27 19:04 DEBUG  WindowsBackend: drive=Drive(Z: remote 0.0 mb free )
02-27 19:04 DEBUG  WindowsBackend: uninstaller_path=None
02-27 19:04 DEBUG  WindowsBackend: previous_target_dir=None
02-27 19:04 DEBUG  WindowsBackend: previous_distro_name=None
02-27 19:04 DEBUG  WindowsBackend: keyboard_id=67699721
02-27 19:04 DEBUG  WindowsBackend: keyboard_layout=us
02-27 19:04 DEBUG  WindowsBackend: keyboard_variant=
02-27 19:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-27 19:04 DEBUG  CommonBackend: locale=en_US.UTF-8
02-27 19:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-27 19:04 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 19:04 DEBUG  CommonBackend: Searching for local CDs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
02-27 19:04 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Ubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Ubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Ubuntu Netbook Remix CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Kubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Kubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Kubuntu Netbook CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Xubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Xubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Mythbuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp is a valid Mythbuntu CD
02-27 19:04 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 19:04 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
02-27 19:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-27 19:04 INFO   Distro: Found a valid CD for Ubuntu: E:\
02-27 19:04 INFO   root: Running the CD menu...
02-27 19:04 DEBUG  WindowsFrontend: __init__...
02-27 19:04 DEBUG  WindowsFrontend: on_init...
02-27 19:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\translations, languages=['en_US', 'en']
02-27 19:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl8C7F.tmp\translations, languages=['en_US', 'en']
02-27 19:04 INFO   WindowsFrontend: Operation cancelled
02-27 19:04 DEBUG  WindowsFrontend: frontend.quit
02-27 19:04 DEBUG  WindowsFrontend: frontend.on_quit
02-27 19:04 DEBUG  root: application.on_quit
02-27 19:04 INFO   root: sys.exit
02-28 20:26 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-28 20:26 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-28 20:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
02-28 20:26 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\data
02-28 20:26 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\bin\7z.exe
02-28 20:26 DEBUG  CommonBackend: Fetching basic info...
02-28 20:26 DEBUG  CommonBackend: original_exe=E:\wubi.exe
02-28 20:26 DEBUG  CommonBackend: platform=win32
02-28 20:26 DEBUG  CommonBackend: osname=nt
02-28 20:26 DEBUG  CommonBackend: language=en_US
02-28 20:26 DEBUG  CommonBackend: encoding=cp1252
02-28 20:26 DEBUG  WindowsBackend: arch=amd64
02-28 20:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\data\isolist.ini
02-28 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-28 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-28 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-28 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-28 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-28 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-28 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-28 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-28 20:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-28 20:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-28 20:26 DEBUG  WindowsBackend: Fetching host info...
02-28 20:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-28 20:26 DEBUG  WindowsBackend: windows version=vista
02-28 20:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-28 20:26 DEBUG  WindowsBackend: windows_sp=None
02-28 20:26 DEBUG  WindowsBackend: windows_build=7600
02-28 20:26 DEBUG  WindowsBackend: gmt=-5
02-28 20:26 DEBUG  WindowsBackend: country=US
02-28 20:26 DEBUG  WindowsBackend: timezone=America/New_York
02-28 20:26 DEBUG  WindowsBackend: windows_username=BobTheTwit
02-28 20:26 DEBUG  WindowsBackend: user_full_name=BobTheTwit
02-28 20:26 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
02-28 20:26 DEBUG  WindowsBackend: windows_language_code=1033
02-28 20:26 DEBUG  WindowsBackend: windows_language=English
02-28 20:26 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
02-28 20:26 DEBUG  WindowsBackend: bootloader=vista
02-28 20:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60569.9375 mb free ntfs)
02-28 20:26 DEBUG  WindowsBackend: drive=Drive(C: hd 60569.9375 mb free ntfs)
02-28 20:26 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
02-28 20:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
02-28 20:26 DEBUG  WindowsBackend: drive=Drive(Q: hd 10226.9765625 mb free fat32)
02-28 20:26 DEBUG  WindowsBackend: uninstaller_path=None
02-28 20:26 DEBUG  WindowsBackend: previous_target_dir=None
02-28 20:26 DEBUG  WindowsBackend: previous_distro_name=None
02-28 20:26 DEBUG  WindowsBackend: keyboard_id=67699721
02-28 20:26 DEBUG  WindowsBackend: keyboard_layout=us
02-28 20:26 DEBUG  WindowsBackend: keyboard_variant=
02-28 20:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-28 20:26 DEBUG  CommonBackend: locale=en_US.UTF-8
02-28 20:26 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-28 20:26 DEBUG  CommonBackend: Searching ISOs on USB devices
02-28 20:26 DEBUG  CommonBackend: Searching for local CDs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Ubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Ubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Ubuntu Netbook Remix CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Kubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Kubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Kubuntu Netbook CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Xubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Xubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Mythbuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp is a valid Mythbuntu CD
02-28 20:26 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 20:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 20:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-28 20:26 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
02-28 20:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-28 20:26 INFO   Distro: Found a valid CD for Ubuntu: E:\
02-28 20:26 INFO   root: Running the CD menu...
02-28 20:26 DEBUG  WindowsFrontend: __init__...
02-28 20:26 DEBUG  WindowsFrontend: on_init...
02-28 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\translations, languages=['en_US', 'en']
02-28 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\translations, languages=['en_US', 'en']
02-28 20:26 INFO   root: CD menu finished
02-28 20:26 INFO   root: Running the installer...
02-28 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\translations, languages=['en_US', 'en']
02-28 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\translations, languages=['en_US', 'en']
02-28 20:27 DEBUG  WinuiInstallationPage: target_drive=Q:, installation_size=9000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bob
02-28 20:27 INFO   root: Received settings
02-28 20:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\translations, languages=['en_US', 'en']
02-28 20:27 DEBUG  TaskList: # Running tasklist...
02-28 20:27 DEBUG  TaskList: ## Running select_target_dir...
02-28 20:27 INFO   WindowsBackend: Installing into Q:\ubuntu
02-28 20:27 DEBUG  TaskList: ## Finished select_target_dir
02-28 20:27 DEBUG  TaskList: ## Running create_dir_structure...
02-28 20:27 DEBUG  CommonBackend: Creating dir Q:\ubuntu
02-28 20:27 DEBUG  CommonBackend: Creating dir Q:\ubuntu\disks
02-28 20:27 DEBUG  CommonBackend: Creating dir Q:\ubuntu\install
02-28 20:27 DEBUG  CommonBackend: Creating dir Q:\ubuntu\install\boot
02-28 20:27 DEBUG  CommonBackend: Creating dir Q:\ubuntu\disks\boot
02-28 20:27 DEBUG  CommonBackend: Creating dir Q:\ubuntu\disks\boot\grub
02-28 20:27 DEBUG  CommonBackend: Creating dir Q:\ubuntu\install\boot\grub
02-28 20:27 DEBUG  TaskList: ## Finished create_dir_structure
02-28 20:27 DEBUG  TaskList: ## Running uncompress_target_dir...
02-28 20:27 DEBUG  TaskList: ## Finished uncompress_target_dir
02-28 20:27 DEBUG  TaskList: ## Running create_uninstaller...
02-28 20:27 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> Q:\ubuntu\uninstall-wubi.exe
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString Q:\ubuntu\uninstall-wubi.exe
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir Q:\ubuntu
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon Q:\ubuntu\Ubuntu.ico
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-28 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-28 20:27 DEBUG  TaskList: ## Finished create_uninstaller
02-28 20:27 DEBUG  TaskList: ## Running copy_installation_files...
02-28 20:27 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\data\custom-installation -> Q:\ubuntu\install\custom-installation
02-28 20:27 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\winboot -> Q:\ubuntu\winboot
02-28 20:27 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pylFED2.tmp\data\images\Ubuntu.ico -> Q:\ubuntu\Ubuntu.ico
02-28 20:27 DEBUG  TaskList: ## Finished copy_installation_files
02-28 20:27 DEBUG  TaskList: ## Running get_iso...
02-28 20:27 DEBUG  TaskList: New task copy_file
02-28 20:27 DEBUG  TaskList: ### Running copy_file...
02-28 20:29 DEBUG  TaskList: ### Finished copy_file
02-28 20:29 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-28 20:29 DEBUG  TaskList: # Cancelling tasklist
02-28 20:29 DEBUG  TaskList: New task check_iso
02-28 20:29 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-28 20:29 DEBUG  CommonBackend: Searching for local ISO
02-28 20:29 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-28 20:29 DEBUG  TaskList: New task get_metalink
02-28 20:29 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-28 20:29 DEBUG  TaskList: # Cancelling tasklist
02-28 20:29 DEBUG  TaskList: # Finished tasklist
03-01 00:12 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 00:12 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-01 00:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="Q:\\ubuntu\\uninstall-wubi.exe"']
03-01 00:12 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\data
03-01 00:12 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\bin\7z.exe
03-01 00:12 DEBUG  CommonBackend: Fetching basic info...
03-01 00:12 DEBUG  CommonBackend: original_exe=Q:\ubuntu\uninstall-wubi.exe
03-01 00:12 DEBUG  CommonBackend: platform=win32
03-01 00:12 DEBUG  CommonBackend: osname=nt
03-01 00:12 DEBUG  CommonBackend: language=en_US
03-01 00:12 DEBUG  CommonBackend: encoding=cp1252
03-01 00:12 DEBUG  WindowsBackend: arch=amd64
03-01 00:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\data\isolist.ini
03-01 00:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 00:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 00:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 00:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 00:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 00:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 00:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 00:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 00:12 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 00:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 00:12 DEBUG  WindowsBackend: Fetching host info...
03-01 00:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 00:12 DEBUG  WindowsBackend: windows version=vista
03-01 00:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 00:12 DEBUG  WindowsBackend: windows_sp=None
03-01 00:12 DEBUG  WindowsBackend: windows_build=7600
03-01 00:12 DEBUG  WindowsBackend: gmt=-5
03-01 00:12 DEBUG  WindowsBackend: country=US
03-01 00:12 DEBUG  WindowsBackend: timezone=America/New_York
03-01 00:12 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 00:12 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 00:12 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 00:12 DEBUG  WindowsBackend: windows_language_code=1033
03-01 00:12 DEBUG  WindowsBackend: windows_language=English
03-01 00:12 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 00:12 DEBUG  WindowsBackend: bootloader=vista
03-01 00:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 98902.9296875 mb free ntfs)
03-01 00:12 DEBUG  WindowsBackend: drive=Drive(C: hd 98902.9296875 mb free ntfs)
03-01 00:12 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 00:12 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 00:12 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-01 00:12 DEBUG  WindowsBackend: drive=Drive(G: removable 4962.28125 mb free fat32)
03-01 00:12 DEBUG  WindowsBackend: drive=Drive(Q: hd 9536.328125 mb free fat32)
03-01 00:12 DEBUG  WindowsBackend: uninstaller_path=Q:\ubuntu\uninstall-wubi.exe
03-01 00:12 DEBUG  WindowsBackend: previous_target_dir=Q:\ubuntu
03-01 00:12 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 00:12 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 00:12 DEBUG  WindowsBackend: keyboard_layout=us
03-01 00:12 DEBUG  WindowsBackend: keyboard_variant=
03-01 00:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 00:12 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 00:12 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 00:12 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 00:12 DEBUG  CommonBackend: Searching for local CDs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Ubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Ubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Ubuntu Netbook Remix CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Kubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Kubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Kubuntu Netbook CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Xubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Xubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Mythbuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp is a valid Mythbuntu CD
03-01 00:12 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 00:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 00:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 00:12 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-01 00:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 00:12 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 00:12 INFO   root: Running the uninstaller...
03-01 00:12 INFO   CommonBackend: This is the uninstaller running
03-01 00:12 DEBUG  WindowsFrontend: __init__...
03-01 00:12 DEBUG  WindowsFrontend: on_init...
03-01 00:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\translations, languages=['en_US', 'en']
03-01 00:12 INFO   root: Received settings
03-01 00:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\translations, languages=['en_US', 'en']
03-01 00:12 DEBUG  TaskList: # Running tasklist...
03-01 00:12 DEBUG  TaskList: ## Running Backup ISO...
03-01 00:12 DEBUG  TaskList: ## Finished Backup ISO
03-01 00:12 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 00:12 DEBUG  WindowsBackend: Could not find bcd id
03-01 00:12 DEBUG  WindowsBackend: undo_bootini C:
03-01 00:12 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 98902.9296875 mb free ntfs)
03-01 00:12 DEBUG  WindowsBackend: undo_bootini D:
03-01 00:12 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 8433.47265625 mb free ntfs)
03-01 00:12 DEBUG  WindowsBackend: undo_bootini G:
03-01 00:12 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 4962.28125 mb free fat32)
03-01 00:12 DEBUG  WindowsBackend: undo_bootini Q:
03-01 00:12 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 9536.328125 mb free fat32)
03-01 00:12 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 00:12 DEBUG  TaskList: ## Running Remove target dir...
03-01 00:12 DEBUG  CommonBackend: Deleting Q:\ubuntu
03-01 00:12 DEBUG  TaskList: ## Finished Remove target dir
03-01 00:12 DEBUG  TaskList: ## Running Remove registry key...
03-01 00:12 DEBUG  TaskList: ## Finished Remove registry key
03-01 00:12 DEBUG  TaskList: # Finished tasklist
03-01 00:12 INFO   root: Almost finished uninstalling
03-01 00:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2460.tmp\translations, languages=['en_US', 'en']
03-01 00:12 INFO   root: Finished uninstallation
03-01 00:12 DEBUG  root: application.quit
03-01 00:12 DEBUG  WindowsFrontend: frontend.quit
03-01 00:12 DEBUG  WindowsFrontend: frontend.on_quit
03-01 00:12 DEBUG  root: application.on_quit
03-01 00:12 INFO   root: sys.exit
03-01 15:55 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 15:55 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-01 15:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-01 15:55 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\data
03-01 15:55 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\bin\7z.exe
03-01 15:55 DEBUG  CommonBackend: Fetching basic info...
03-01 15:55 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-01 15:55 DEBUG  CommonBackend: platform=win32
03-01 15:55 DEBUG  CommonBackend: osname=nt
03-01 15:55 DEBUG  CommonBackend: language=en_US
03-01 15:55 DEBUG  CommonBackend: encoding=cp1252
03-01 15:55 DEBUG  WindowsBackend: arch=amd64
03-01 15:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\data\isolist.ini
03-01 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 15:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 15:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 15:55 DEBUG  WindowsBackend: Fetching host info...
03-01 15:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 15:55 DEBUG  WindowsBackend: windows version=vista
03-01 15:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 15:55 DEBUG  WindowsBackend: windows_sp=None
03-01 15:55 DEBUG  WindowsBackend: windows_build=7600
03-01 15:55 DEBUG  WindowsBackend: gmt=-5
03-01 15:55 DEBUG  WindowsBackend: country=US
03-01 15:55 DEBUG  WindowsBackend: timezone=America/New_York
03-01 15:55 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 15:55 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 15:55 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 15:55 DEBUG  WindowsBackend: windows_language_code=1033
03-01 15:55 DEBUG  WindowsBackend: windows_language=English
03-01 15:55 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 15:55 DEBUG  WindowsBackend: bootloader=vista
03-01 15:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 98928.0898438 mb free ntfs)
03-01 15:55 DEBUG  WindowsBackend: drive=Drive(C: hd 98928.0898438 mb free ntfs)
03-01 15:55 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 15:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 15:55 DEBUG  WindowsBackend: drive=Drive(Q: hd 10226.9765625 mb free fat32)
03-01 15:55 DEBUG  WindowsBackend: uninstaller_path=None
03-01 15:55 DEBUG  WindowsBackend: previous_target_dir=None
03-01 15:55 DEBUG  WindowsBackend: previous_distro_name=None
03-01 15:55 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 15:55 DEBUG  WindowsBackend: keyboard_layout=us
03-01 15:55 DEBUG  WindowsBackend: keyboard_variant=
03-01 15:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 15:55 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 15:55 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 15:55 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 15:55 DEBUG  CommonBackend: Searching for local CDs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Ubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Ubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Ubuntu Netbook Remix CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Kubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Kubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Kubuntu Netbook CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Xubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Xubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Mythbuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp is a valid Mythbuntu CD
03-01 15:55 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 15:55 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-01 15:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 15:55 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 15:55 INFO   root: Running the CD menu...
03-01 15:55 DEBUG  WindowsFrontend: __init__...
03-01 15:55 DEBUG  WindowsFrontend: on_init...
03-01 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\translations, languages=['en_US', 'en']
03-01 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\translations, languages=['en_US', 'en']
03-01 15:55 INFO   root: CD menu finished
03-01 15:55 INFO   root: Running the installer...
03-01 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\translations, languages=['en_US', 'en']
03-01 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\translations, languages=['en_US', 'en']
03-01 15:56 DEBUG  WinuiInstallationPage: target_drive=Q:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bob
03-01 15:56 INFO   root: Received settings
03-01 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\translations, languages=['en_US', 'en']
03-01 15:56 DEBUG  TaskList: # Running tasklist...
03-01 15:56 DEBUG  TaskList: ## Running select_target_dir...
03-01 15:56 INFO   WindowsBackend: Installing into Q:\ubuntu
03-01 15:56 DEBUG  TaskList: ## Finished select_target_dir
03-01 15:56 DEBUG  TaskList: ## Running create_dir_structure...
03-01 15:56 DEBUG  CommonBackend: Creating dir Q:\ubuntu
03-01 15:56 DEBUG  CommonBackend: Creating dir Q:\ubuntu\disks
03-01 15:56 DEBUG  CommonBackend: Creating dir Q:\ubuntu\install
03-01 15:56 DEBUG  CommonBackend: Creating dir Q:\ubuntu\install\boot
03-01 15:56 DEBUG  CommonBackend: Creating dir Q:\ubuntu\disks\boot
03-01 15:56 DEBUG  CommonBackend: Creating dir Q:\ubuntu\disks\boot\grub
03-01 15:56 DEBUG  CommonBackend: Creating dir Q:\ubuntu\install\boot\grub
03-01 15:56 DEBUG  TaskList: ## Finished create_dir_structure
03-01 15:56 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 15:56 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 15:56 DEBUG  TaskList: ## Running create_uninstaller...
03-01 15:56 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> Q:\ubuntu\uninstall-wubi.exe
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString Q:\ubuntu\uninstall-wubi.exe
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir Q:\ubuntu
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon Q:\ubuntu\Ubuntu.ico
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-01 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-01 15:56 DEBUG  TaskList: ## Finished create_uninstaller
03-01 15:56 DEBUG  TaskList: ## Running copy_installation_files...
03-01 15:56 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\data\custom-installation -> Q:\ubuntu\install\custom-installation
03-01 15:56 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\winboot -> Q:\ubuntu\winboot
03-01 15:56 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl93CC.tmp\data\images\Ubuntu.ico -> Q:\ubuntu\Ubuntu.ico
03-01 15:56 DEBUG  TaskList: ## Finished copy_installation_files
03-01 15:56 DEBUG  TaskList: ## Running get_iso...
03-01 15:56 DEBUG  TaskList: New task copy_file
03-01 15:56 DEBUG  TaskList: ### Running copy_file...
03-01 15:59 DEBUG  TaskList: ### Finished copy_file
03-01 15:59 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-01 15:59 DEBUG  TaskList: # Cancelling tasklist
03-01 15:59 DEBUG  TaskList: New task check_iso
03-01 15:59 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-01 15:59 DEBUG  CommonBackend: Searching for local ISO
03-01 15:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-01 15:59 DEBUG  TaskList: New task get_metalink
03-01 15:59 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-01 15:59 DEBUG  TaskList: # Cancelling tasklist
03-01 15:59 DEBUG  TaskList: # Finished tasklist
03-01 16:16 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 16:16 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-01 16:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-01 16:16 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\data
03-01 16:16 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\bin\7z.exe
03-01 16:16 DEBUG  CommonBackend: Fetching basic info...
03-01 16:16 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-01 16:16 DEBUG  CommonBackend: platform=win32
03-01 16:16 DEBUG  CommonBackend: osname=nt
03-01 16:16 DEBUG  CommonBackend: language=en_US
03-01 16:16 DEBUG  CommonBackend: encoding=cp1252
03-01 16:16 DEBUG  WindowsBackend: arch=amd64
03-01 16:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\data\isolist.ini
03-01 16:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 16:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 16:16 DEBUG  WindowsBackend: Fetching host info...
03-01 16:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:16 DEBUG  WindowsBackend: windows version=vista
03-01 16:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 16:16 DEBUG  WindowsBackend: windows_sp=None
03-01 16:16 DEBUG  WindowsBackend: windows_build=7600
03-01 16:16 DEBUG  WindowsBackend: gmt=-5
03-01 16:16 DEBUG  WindowsBackend: country=US
03-01 16:16 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:16 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 16:16 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 16:16 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 16:16 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:16 DEBUG  WindowsBackend: windows_language=English
03-01 16:16 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 16:16 DEBUG  WindowsBackend: bootloader=vista
03-01 16:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 98942.5976563 mb free ntfs)
03-01 16:16 DEBUG  WindowsBackend: drive=Drive(C: hd 98942.5976563 mb free ntfs)
03-01 16:16 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 16:16 DEBUG  WindowsBackend: drive=Drive(Q: hd 9536.328125 mb free fat32)
03-01 16:16 DEBUG  WindowsBackend: uninstaller_path=Q:\ubuntu\uninstall-wubi.exe
03-01 16:16 DEBUG  WindowsBackend: previous_target_dir=Q:\ubuntu
03-01 16:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 16:16 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:16 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:16 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 16:16 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 16:16 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 16:16 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:16 DEBUG  CommonBackend: Searching for local CDs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Ubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Ubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Ubuntu Netbook Remix CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Kubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Kubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Kubuntu Netbook CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Xubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Xubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Mythbuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp is a valid Mythbuntu CD
03-01 16:16 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:16 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-01 16:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 16:16 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 16:16 INFO   root: Running the CD menu...
03-01 16:16 DEBUG  WindowsFrontend: __init__...
03-01 16:16 DEBUG  WindowsFrontend: on_init...
03-01 16:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\translations, languages=['en_US', 'en']
03-01 16:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\translations, languages=['en_US', 'en']
03-01 16:16 INFO   root: CD menu finished
03-01 16:16 INFO   root: Already installed, running the uninstaller...
03-01 16:16 INFO   root: Running the uninstaller...
03-01 16:16 INFO   CommonBackend: This is the uninstaller running
03-01 16:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl98DB.tmp\translations, languages=['en_US', 'en']
03-01 16:16 INFO   WindowsFrontend: Operation cancelled
03-01 16:16 DEBUG  WindowsFrontend: frontend.quit
03-01 16:16 DEBUG  WindowsFrontend: frontend.on_quit
03-01 16:16 DEBUG  root: application.on_quit
03-01 16:16 INFO   root: sys.exit
03-01 16:18 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 16:18 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-01 16:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="Q:\\ubuntu\\uninstall-wubi.exe"']
03-01 16:18 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\data
03-01 16:18 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\bin\7z.exe
03-01 16:18 DEBUG  CommonBackend: Fetching basic info...
03-01 16:18 DEBUG  CommonBackend: original_exe=Q:\ubuntu\uninstall-wubi.exe
03-01 16:18 DEBUG  CommonBackend: platform=win32
03-01 16:18 DEBUG  CommonBackend: osname=nt
03-01 16:18 DEBUG  CommonBackend: language=en_US
03-01 16:18 DEBUG  CommonBackend: encoding=cp1252
03-01 16:18 DEBUG  WindowsBackend: arch=amd64
03-01 16:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\data\isolist.ini
03-01 16:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 16:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 16:18 DEBUG  WindowsBackend: Fetching host info...
03-01 16:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:18 DEBUG  WindowsBackend: windows version=vista
03-01 16:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 16:18 DEBUG  WindowsBackend: windows_sp=None
03-01 16:18 DEBUG  WindowsBackend: windows_build=7600
03-01 16:18 DEBUG  WindowsBackend: gmt=-5
03-01 16:18 DEBUG  WindowsBackend: country=US
03-01 16:18 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:18 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 16:18 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 16:18 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 16:18 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:18 DEBUG  WindowsBackend: windows_language=English
03-01 16:18 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 16:18 DEBUG  WindowsBackend: bootloader=vista
03-01 16:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 98937.6132813 mb free ntfs)
03-01 16:18 DEBUG  WindowsBackend: drive=Drive(C: hd 98937.6132813 mb free ntfs)
03-01 16:18 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 16:18 DEBUG  WindowsBackend: drive=Drive(Q: hd 9536.328125 mb free fat32)
03-01 16:18 DEBUG  WindowsBackend: uninstaller_path=Q:\ubuntu\uninstall-wubi.exe
03-01 16:18 DEBUG  WindowsBackend: previous_target_dir=Q:\ubuntu
03-01 16:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 16:18 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:18 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:18 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 16:18 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 16:18 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 16:18 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:18 DEBUG  CommonBackend: Searching for local CDs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Ubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Ubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Ubuntu Netbook Remix CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Kubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Kubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Kubuntu Netbook CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Xubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Xubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Mythbuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp is a valid Mythbuntu CD
03-01 16:18 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:18 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-01 16:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 16:18 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 16:18 INFO   root: Running the uninstaller...
03-01 16:18 INFO   CommonBackend: This is the uninstaller running
03-01 16:18 DEBUG  WindowsFrontend: __init__...
03-01 16:18 DEBUG  WindowsFrontend: on_init...
03-01 16:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\translations, languages=['en_US', 'en']
03-01 16:18 INFO   root: Received settings
03-01 16:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\translations, languages=['en_US', 'en']
03-01 16:18 DEBUG  TaskList: # Running tasklist...
03-01 16:18 DEBUG  TaskList: ## Running Backup ISO...
03-01 16:18 DEBUG  TaskList: ## Finished Backup ISO
03-01 16:18 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 16:18 DEBUG  WindowsBackend: Could not find bcd id
03-01 16:18 DEBUG  WindowsBackend: undo_bootini C:
03-01 16:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 98937.6132813 mb free ntfs)
03-01 16:18 DEBUG  WindowsBackend: undo_bootini D:
03-01 16:18 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:18 DEBUG  WindowsBackend: undo_bootini Q:
03-01 16:18 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 9536.328125 mb free fat32)
03-01 16:18 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 16:18 DEBUG  TaskList: ## Running Remove target dir...
03-01 16:18 DEBUG  CommonBackend: Deleting Q:\ubuntu
03-01 16:18 DEBUG  TaskList: ## Finished Remove target dir
03-01 16:18 DEBUG  TaskList: ## Running Remove registry key...
03-01 16:18 DEBUG  TaskList: ## Finished Remove registry key
03-01 16:18 DEBUG  TaskList: # Finished tasklist
03-01 16:18 INFO   root: Almost finished uninstalling
03-01 16:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2754.tmp\translations, languages=['en_US', 'en']
03-01 16:18 INFO   root: Finished uninstallation
03-01 16:18 DEBUG  root: application.quit
03-01 16:18 DEBUG  WindowsFrontend: frontend.quit
03-01 16:18 DEBUG  WindowsFrontend: frontend.on_quit
03-01 16:18 DEBUG  root: application.on_quit
03-01 16:18 INFO   root: sys.exit
03-01 16:30 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 16:30 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-01 16:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-01 16:30 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\data
03-01 16:30 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\bin\7z.exe
03-01 16:30 DEBUG  CommonBackend: Fetching basic info...
03-01 16:30 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-01 16:30 DEBUG  CommonBackend: platform=win32
03-01 16:30 DEBUG  CommonBackend: osname=nt
03-01 16:30 DEBUG  CommonBackend: language=en_US
03-01 16:30 DEBUG  CommonBackend: encoding=cp1252
03-01 16:30 DEBUG  WindowsBackend: arch=amd64
03-01 16:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\data\isolist.ini
03-01 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 16:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 16:30 DEBUG  WindowsBackend: Fetching host info...
03-01 16:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:30 DEBUG  WindowsBackend: windows version=vista
03-01 16:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 16:30 DEBUG  WindowsBackend: windows_sp=None
03-01 16:30 DEBUG  WindowsBackend: windows_build=7600
03-01 16:30 DEBUG  WindowsBackend: gmt=-5
03-01 16:30 DEBUG  WindowsBackend: country=US
03-01 16:30 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:30 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 16:30 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 16:30 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 16:30 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:30 DEBUG  WindowsBackend: windows_language=English
03-01 16:30 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 16:30 DEBUG  WindowsBackend: bootloader=vista
03-01 16:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 93598.7382813 mb free ntfs)
03-01 16:30 DEBUG  WindowsBackend: drive=Drive(C: hd 93598.7382813 mb free ntfs)
03-01 16:30 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 16:30 DEBUG  WindowsBackend: drive=Drive(F: removable 813.25390625 mb free fat32)
03-01 16:30 DEBUG  WindowsBackend: uninstaller_path=None
03-01 16:30 DEBUG  WindowsBackend: previous_target_dir=None
03-01 16:30 DEBUG  WindowsBackend: previous_distro_name=None
03-01 16:30 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:30 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:30 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 16:30 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 16:30 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 16:30 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:30 DEBUG  CommonBackend: Searching for local CDs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Ubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Ubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Ubuntu Netbook Remix CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Kubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Kubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Kubuntu Netbook CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Xubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Xubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Mythbuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp is a valid Mythbuntu CD
03-01 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:30 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-01 16:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 16:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 16:30 INFO   root: Running the CD menu...
03-01 16:30 DEBUG  WindowsFrontend: __init__...
03-01 16:30 DEBUG  WindowsFrontend: on_init...
03-01 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\translations, languages=['en_US', 'en']
03-01 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl2716.tmp\translations, languages=['en_US', 'en']
03-01 16:30 INFO   WindowsFrontend: Operation cancelled
03-01 16:30 DEBUG  WindowsFrontend: frontend.quit
03-01 16:30 DEBUG  WindowsFrontend: frontend.on_quit
03-01 16:30 DEBUG  root: application.on_quit
03-01 16:30 INFO   root: sys.exit
03-01 16:33 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 16:33 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-01 16:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-01 16:33 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\data
03-01 16:33 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\bin\7z.exe
03-01 16:33 DEBUG  CommonBackend: Fetching basic info...
03-01 16:33 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-01 16:33 DEBUG  CommonBackend: platform=win32
03-01 16:33 DEBUG  CommonBackend: osname=nt
03-01 16:33 DEBUG  CommonBackend: language=en_US
03-01 16:33 DEBUG  CommonBackend: encoding=cp1252
03-01 16:33 DEBUG  WindowsBackend: arch=amd64
03-01 16:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\data\isolist.ini
03-01 16:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 16:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 16:33 DEBUG  WindowsBackend: Fetching host info...
03-01 16:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:33 DEBUG  WindowsBackend: windows version=vista
03-01 16:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 16:33 DEBUG  WindowsBackend: windows_sp=None
03-01 16:33 DEBUG  WindowsBackend: windows_build=7600
03-01 16:33 DEBUG  WindowsBackend: gmt=-5
03-01 16:33 DEBUG  WindowsBackend: country=US
03-01 16:33 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:33 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 16:33 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 16:33 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 16:33 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:33 DEBUG  WindowsBackend: windows_language=English
03-01 16:33 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 16:33 DEBUG  WindowsBackend: bootloader=vista
03-01 16:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 93519.6992188 mb free ntfs)
03-01 16:33 DEBUG  WindowsBackend: drive=Drive(B: hd 14757.8203125 mb free ntfs)
03-01 16:33 DEBUG  WindowsBackend: drive=Drive(C: hd 93519.6992188 mb free ntfs)
03-01 16:33 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 16:33 DEBUG  WindowsBackend: drive=Drive(F: removable 343.00390625 mb free fat32)
03-01 16:33 DEBUG  WindowsBackend: uninstaller_path=None
03-01 16:33 DEBUG  WindowsBackend: previous_target_dir=None
03-01 16:33 DEBUG  WindowsBackend: previous_distro_name=None
03-01 16:33 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:33 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:33 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 16:33 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 16:33 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 16:33 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:33 DEBUG  CommonBackend: Searching for local CDs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
03-01 16:33 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Ubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Ubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Ubuntu Netbook Remix CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Kubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Kubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Kubuntu Netbook CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Xubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Xubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Mythbuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp is a valid Mythbuntu CD
03-01 16:33 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:33 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-01 16:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 16:33 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 16:33 INFO   root: Running the CD menu...
03-01 16:33 DEBUG  WindowsFrontend: __init__...
03-01 16:33 DEBUG  WindowsFrontend: on_init...
03-01 16:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\translations, languages=['en_US', 'en']
03-01 16:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\translations, languages=['en_US', 'en']
03-01 16:33 INFO   root: CD menu finished
03-01 16:33 INFO   root: Running the installer...
03-01 16:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\translations, languages=['en_US', 'en']
03-01 16:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\translations, languages=['en_US', 'en']
03-01 16:34 DEBUG  WinuiInstallationPage: target_drive=B:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bob
03-01 16:34 INFO   root: Received settings
03-01 16:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\translations, languages=['en_US', 'en']
03-01 16:34 DEBUG  TaskList: # Running tasklist...
03-01 16:34 DEBUG  TaskList: ## Running select_target_dir...
03-01 16:34 INFO   WindowsBackend: Installing into B:\ubuntu
03-01 16:34 DEBUG  TaskList: ## Finished select_target_dir
03-01 16:34 DEBUG  TaskList: ## Running create_dir_structure...
03-01 16:34 DEBUG  CommonBackend: Creating dir B:\ubuntu
03-01 16:34 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks
03-01 16:34 DEBUG  CommonBackend: Creating dir B:\ubuntu\install
03-01 16:34 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot
03-01 16:34 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot
03-01 16:34 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot\grub
03-01 16:34 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot\grub
03-01 16:34 DEBUG  TaskList: ## Finished create_dir_structure
03-01 16:34 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 16:34 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 16:34 DEBUG  TaskList: ## Running create_uninstaller...
03-01 16:34 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> B:\ubuntu\uninstall-wubi.exe
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString B:\ubuntu\uninstall-wubi.exe
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir B:\ubuntu
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon B:\ubuntu\Ubuntu.ico
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-01 16:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-01 16:34 DEBUG  TaskList: ## Finished create_uninstaller
03-01 16:34 DEBUG  TaskList: ## Running copy_installation_files...
03-01 16:34 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\data\custom-installation -> B:\ubuntu\install\custom-installation
03-01 16:34 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\winboot -> B:\ubuntu\winboot
03-01 16:34 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl3EFA.tmp\data\images\Ubuntu.ico -> B:\ubuntu\Ubuntu.ico
03-01 16:34 DEBUG  TaskList: ## Finished copy_installation_files
03-01 16:34 DEBUG  TaskList: ## Running get_iso...
03-01 16:34 DEBUG  TaskList: New task copy_file
03-01 16:34 DEBUG  TaskList: ### Running copy_file...
03-01 16:36 DEBUG  TaskList: ### Finished copy_file
03-01 16:36 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-01 16:36 DEBUG  TaskList: # Cancelling tasklist
03-01 16:36 DEBUG  TaskList: New task check_iso
03-01 16:36 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-01 16:36 DEBUG  CommonBackend: Searching for local ISO
03-01 16:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-01 16:36 DEBUG  TaskList: New task get_metalink
03-01 16:36 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-01 16:36 DEBUG  TaskList: # Cancelling tasklist
03-01 16:36 DEBUG  TaskList: # Finished tasklist
03-01 16:37 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 16:37 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-01 16:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-01 16:37 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\data
03-01 16:37 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\bin\7z.exe
03-01 16:37 DEBUG  CommonBackend: Fetching basic info...
03-01 16:37 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-01 16:37 DEBUG  CommonBackend: platform=win32
03-01 16:37 DEBUG  CommonBackend: osname=nt
03-01 16:37 DEBUG  CommonBackend: language=en_US
03-01 16:37 DEBUG  CommonBackend: encoding=cp1252
03-01 16:37 DEBUG  WindowsBackend: arch=amd64
03-01 16:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\data\isolist.ini
03-01 16:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 16:37 DEBUG  WindowsBackend: Fetching host info...
03-01 16:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:37 DEBUG  WindowsBackend: windows version=vista
03-01 16:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 16:37 DEBUG  WindowsBackend: windows_sp=None
03-01 16:37 DEBUG  WindowsBackend: windows_build=7600
03-01 16:37 DEBUG  WindowsBackend: gmt=-5
03-01 16:37 DEBUG  WindowsBackend: country=US
03-01 16:37 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:37 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 16:37 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 16:37 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 16:37 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:37 DEBUG  WindowsBackend: windows_language=English
03-01 16:37 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 16:37 DEBUG  WindowsBackend: bootloader=vista
03-01 16:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 93444.515625 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(B: hd 14067.2851563 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(C: hd 93444.515625 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(F: removable 275.7109375 mb free fat32)
03-01 16:37 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
03-01 16:37 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
03-01 16:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 16:37 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:37 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:37 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 16:37 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 16:37 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 16:37 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:37 DEBUG  CommonBackend: Searching for local CDs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Ubuntu Netbook Remix CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Kubuntu Netbook CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-01 16:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 16:37 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 16:37 INFO   root: Running the CD menu...
03-01 16:37 DEBUG  WindowsFrontend: __init__...
03-01 16:37 DEBUG  WindowsFrontend: on_init...
03-01 16:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\translations, languages=['en_US', 'en']
03-01 16:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\translations, languages=['en_US', 'en']
03-01 16:37 INFO   root: CD menu finished
03-01 16:37 INFO   root: Already installed, running the uninstaller...
03-01 16:37 INFO   root: Running the uninstaller...
03-01 16:37 INFO   CommonBackend: This is the uninstaller running
03-01 16:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\translations, languages=['en_US', 'en']
03-01 16:37 INFO   root: Received settings
03-01 16:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\translations, languages=['en_US', 'en']
03-01 16:37 DEBUG  TaskList: # Running tasklist...
03-01 16:37 DEBUG  TaskList: ## Running Backup ISO...
03-01 16:37 DEBUG  TaskList: ## Finished Backup ISO
03-01 16:37 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 16:37 DEBUG  WindowsBackend: Could not find bcd id
03-01 16:37 DEBUG  WindowsBackend: undo_bootini B:
03-01 16:37 DEBUG  WindowsBackend: undo_configsys Drive(B: hd 14067.2851563 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: undo_bootini C:
03-01 16:37 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 93444.515625 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: undo_bootini D:
03-01 16:37 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: undo_bootini F:
03-01 16:37 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 275.7109375 mb free fat32)
03-01 16:37 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 16:37 DEBUG  TaskList: ## Running Remove target dir...
03-01 16:37 DEBUG  CommonBackend: Deleting B:\ubuntu
03-01 16:37 DEBUG  TaskList: ## Finished Remove target dir
03-01 16:37 DEBUG  TaskList: ## Running Remove registry key...
03-01 16:37 DEBUG  TaskList: ## Finished Remove registry key
03-01 16:37 DEBUG  TaskList: # Finished tasklist
03-01 16:37 INFO   root: Almost finished uninstalling
03-01 16:37 INFO   root: Finished uninstallation
03-01 16:37 DEBUG  CommonBackend: Fetching basic info...
03-01 16:37 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-01 16:37 DEBUG  CommonBackend: platform=win32
03-01 16:37 DEBUG  CommonBackend: osname=nt
03-01 16:37 DEBUG  WindowsBackend: arch=amd64
03-01 16:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\data\isolist.ini
03-01 16:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 16:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 16:37 DEBUG  WindowsBackend: Fetching host info...
03-01 16:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:37 DEBUG  WindowsBackend: windows version=vista
03-01 16:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-01 16:37 DEBUG  WindowsBackend: windows_sp=None
03-01 16:37 DEBUG  WindowsBackend: windows_build=7600
03-01 16:37 DEBUG  WindowsBackend: gmt=-5
03-01 16:37 DEBUG  WindowsBackend: country=US
03-01 16:37 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:37 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-01 16:37 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-01 16:37 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-01 16:37 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:37 DEBUG  WindowsBackend: windows_language=English
03-01 16:37 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-01 16:37 DEBUG  WindowsBackend: bootloader=vista
03-01 16:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 93442.78125 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(B: hd 14757.8164063 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(C: hd 93442.78125 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-01 16:37 DEBUG  WindowsBackend: drive=Drive(F: removable 275.7109375 mb free fat32)
03-01 16:37 DEBUG  WindowsBackend: uninstaller_path=None
03-01 16:37 DEBUG  WindowsBackend: previous_target_dir=None
03-01 16:37 DEBUG  WindowsBackend: previous_distro_name=None
03-01 16:37 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:37 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:37 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:37 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 16:37 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:37 DEBUG  CommonBackend: Searching for local CDs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Ubuntu Netbook Remix CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Kubuntu Netbook CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:37 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-01 16:37 INFO   root: Running the installer...
03-01 16:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\translations, languages=['en_US', 'en']
03-01 16:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\translations, languages=['en_US', 'en']
03-01 16:37 DEBUG  WinuiInstallationPage: target_drive=B:, installation_size=13000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bob
03-01 16:37 INFO   root: Received settings
03-01 16:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\translations, languages=['en_US', 'en']
03-01 16:37 DEBUG  TaskList: # Running tasklist...
03-01 16:37 DEBUG  TaskList: ## Running select_target_dir...
03-01 16:37 INFO   WindowsBackend: Installing into B:\ubuntu
03-01 16:37 DEBUG  TaskList: ## Finished select_target_dir
03-01 16:37 DEBUG  TaskList: ## Running create_dir_structure...
03-01 16:37 DEBUG  CommonBackend: Creating dir B:\ubuntu
03-01 16:37 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks
03-01 16:37 DEBUG  CommonBackend: Creating dir B:\ubuntu\install
03-01 16:37 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot
03-01 16:37 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot
03-01 16:37 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot\grub
03-01 16:37 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot\grub
03-01 16:37 DEBUG  TaskList: ## Finished create_dir_structure
03-01 16:37 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 16:37 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 16:37 DEBUG  TaskList: ## Running create_uninstaller...
03-01 16:37 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> B:\ubuntu\uninstall-wubi.exe
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString B:\ubuntu\uninstall-wubi.exe
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir B:\ubuntu
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon B:\ubuntu\Ubuntu.ico
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-01 16:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-01 16:37 DEBUG  TaskList: ## Finished create_uninstaller
03-01 16:37 DEBUG  TaskList: ## Running copy_installation_files...
03-01 16:37 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\data\custom-installation -> B:\ubuntu\install\custom-installation
03-01 16:37 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\winboot -> B:\ubuntu\winboot
03-01 16:37 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9AFE.tmp\data\images\Ubuntu.ico -> B:\ubuntu\Ubuntu.ico
03-01 16:37 DEBUG  TaskList: ## Finished copy_installation_files
03-01 16:37 DEBUG  TaskList: ## Running get_iso...
03-01 16:37 DEBUG  TaskList: New task copy_file
03-01 16:37 DEBUG  TaskList: ### Running copy_file...
03-01 16:40 DEBUG  TaskList: ### Finished copy_file
03-01 16:40 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-01 16:40 DEBUG  TaskList: # Cancelling tasklist
03-01 16:40 DEBUG  TaskList: New task check_iso
03-01 16:40 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-01 16:40 DEBUG  CommonBackend: Searching for local ISO
03-01 16:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-01 16:40 DEBUG  TaskList: New task get_metalink
03-01 16:40 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-01 16:40 DEBUG  TaskList: # Cancelling tasklist
03-01 16:40 DEBUG  TaskList: # Finished tasklist
03-02 15:52 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-02 15:52 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-02 15:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-02 15:52 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\data
03-02 15:52 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\bin\7z.exe
03-02 15:52 DEBUG  CommonBackend: Fetching basic info...
03-02 15:52 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-02 15:52 DEBUG  CommonBackend: platform=win32
03-02 15:52 DEBUG  CommonBackend: osname=nt
03-02 15:52 DEBUG  CommonBackend: language=en_US
03-02 15:52 DEBUG  CommonBackend: encoding=cp1252
03-02 15:52 DEBUG  WindowsBackend: arch=amd64
03-02 15:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\data\isolist.ini
03-02 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-02 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-02 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-02 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-02 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-02 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-02 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-02 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-02 15:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-02 15:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-02 15:52 DEBUG  WindowsBackend: Fetching host info...
03-02 15:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-02 15:52 DEBUG  WindowsBackend: windows version=vista
03-02 15:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-02 15:52 DEBUG  WindowsBackend: windows_sp=None
03-02 15:52 DEBUG  WindowsBackend: windows_build=7600
03-02 15:52 DEBUG  WindowsBackend: gmt=-5
03-02 15:52 DEBUG  WindowsBackend: country=US
03-02 15:52 DEBUG  WindowsBackend: timezone=America/New_York
03-02 15:52 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-02 15:52 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-02 15:52 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-02 15:52 DEBUG  WindowsBackend: windows_language_code=1033
03-02 15:52 DEBUG  WindowsBackend: windows_language=English
03-02 15:52 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-02 15:52 DEBUG  WindowsBackend: bootloader=vista
03-02 15:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 120479.152344 mb free ntfs)
03-02 15:52 DEBUG  WindowsBackend: drive=Drive(C: hd 120479.152344 mb free ntfs)
03-02 15:52 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-02 15:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-02 15:52 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
03-02 15:52 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
03-02 15:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-02 15:52 DEBUG  WindowsBackend: keyboard_id=67699721
03-02 15:52 DEBUG  WindowsBackend: keyboard_layout=us
03-02 15:52 DEBUG  WindowsBackend: keyboard_variant=
03-02 15:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-02 15:52 DEBUG  CommonBackend: locale=en_US.UTF-8
03-02 15:52 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-02 15:52 DEBUG  CommonBackend: Searching ISOs on USB devices
03-02 15:52 DEBUG  CommonBackend: Searching for local CDs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Ubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Ubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Ubuntu Netbook Remix CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Kubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Kubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Kubuntu Netbook CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Xubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Xubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Mythbuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp is a valid Mythbuntu CD
03-02 15:52 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 15:52 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-02 15:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-02 15:52 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-02 15:52 INFO   root: Running the CD menu...
03-02 15:52 DEBUG  WindowsFrontend: __init__...
03-02 15:52 DEBUG  WindowsFrontend: on_init...
03-02 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\translations, languages=['en_US', 'en']
03-02 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\translations, languages=['en_US', 'en']
03-02 15:52 INFO   root: CD menu finished
03-02 15:52 INFO   root: Running the installer...
03-02 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\translations, languages=['en_US', 'en']
03-02 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE15.tmp\translations, languages=['en_US', 'en']
03-02 16:02 INFO   WindowsFrontend: Operation cancelled
03-02 16:02 DEBUG  WindowsFrontend: frontend.quit
03-02 16:02 DEBUG  WindowsFrontend: frontend.on_quit
03-02 16:02 DEBUG  root: application.on_quit
03-02 16:02 INFO   root: sys.exit
03-02 16:30 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-02 16:30 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-02 16:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-02 16:30 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\data
03-02 16:30 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\bin\7z.exe
03-02 16:30 DEBUG  CommonBackend: Fetching basic info...
03-02 16:30 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-02 16:30 DEBUG  CommonBackend: platform=win32
03-02 16:30 DEBUG  CommonBackend: osname=nt
03-02 16:30 DEBUG  CommonBackend: language=en_US
03-02 16:30 DEBUG  CommonBackend: encoding=cp1252
03-02 16:30 DEBUG  WindowsBackend: arch=amd64
03-02 16:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\data\isolist.ini
03-02 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-02 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-02 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-02 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-02 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-02 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-02 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-02 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-02 16:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-02 16:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-02 16:30 DEBUG  WindowsBackend: Fetching host info...
03-02 16:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-02 16:30 DEBUG  WindowsBackend: windows version=vista
03-02 16:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-02 16:30 DEBUG  WindowsBackend: windows_sp=None
03-02 16:30 DEBUG  WindowsBackend: windows_build=7600
03-02 16:30 DEBUG  WindowsBackend: gmt=-5
03-02 16:30 DEBUG  WindowsBackend: country=US
03-02 16:30 DEBUG  WindowsBackend: timezone=America/New_York
03-02 16:30 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-02 16:30 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-02 16:30 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-02 16:30 DEBUG  WindowsBackend: windows_language_code=1033
03-02 16:30 DEBUG  WindowsBackend: windows_language=English
03-02 16:30 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-02 16:30 DEBUG  WindowsBackend: bootloader=vista
03-02 16:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 113800.289063 mb free ntfs)
03-02 16:30 DEBUG  WindowsBackend: drive=Drive(C: hd 113800.285156 mb free ntfs)
03-02 16:30 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-02 16:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-02 16:30 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
03-02 16:30 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
03-02 16:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-02 16:30 DEBUG  WindowsBackend: keyboard_id=67699721
03-02 16:30 DEBUG  WindowsBackend: keyboard_layout=us
03-02 16:30 DEBUG  WindowsBackend: keyboard_variant=
03-02 16:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-02 16:30 DEBUG  CommonBackend: locale=en_US.UTF-8
03-02 16:30 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-02 16:30 DEBUG  CommonBackend: Searching ISOs on USB devices
03-02 16:30 DEBUG  CommonBackend: Searching for local CDs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Ubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Ubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Ubuntu Netbook Remix CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Kubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Kubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Kubuntu Netbook CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Xubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Xubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Mythbuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp is a valid Mythbuntu CD
03-02 16:30 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 16:30 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-02 16:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-02 16:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-02 16:30 INFO   root: Running the CD menu...
03-02 16:30 DEBUG  WindowsFrontend: __init__...
03-02 16:30 DEBUG  WindowsFrontend: on_init...
03-02 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\translations, languages=['en_US', 'en']
03-02 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\translations, languages=['en_US', 'en']
03-02 16:56 INFO   root: CD menu finished
03-02 16:56 INFO   root: Running the installer...
03-02 16:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\translations, languages=['en_US', 'en']
03-02 16:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylE7CF.tmp\translations, languages=['en_US', 'en']
03-02 16:56 INFO   WindowsFrontend: Operation cancelled
03-02 16:56 DEBUG  WindowsFrontend: frontend.quit
03-02 16:56 DEBUG  WindowsFrontend: frontend.on_quit
03-02 16:56 DEBUG  root: application.on_quit
03-02 16:56 INFO   root: sys.exit
03-02 16:56 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-02 16:56 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-02 16:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-02 16:56 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\data
03-02 16:56 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\bin\7z.exe
03-02 16:56 DEBUG  CommonBackend: Fetching basic info...
03-02 16:56 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-02 16:56 DEBUG  CommonBackend: platform=win32
03-02 16:56 DEBUG  CommonBackend: osname=nt
03-02 16:56 DEBUG  CommonBackend: language=en_US
03-02 16:56 DEBUG  CommonBackend: encoding=cp1252
03-02 16:56 DEBUG  WindowsBackend: arch=amd64
03-02 16:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\data\isolist.ini
03-02 16:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-02 16:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-02 16:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-02 16:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-02 16:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-02 16:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-02 16:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-02 16:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-02 16:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-02 16:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-02 16:56 DEBUG  WindowsBackend: Fetching host info...
03-02 16:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-02 16:56 DEBUG  WindowsBackend: windows version=vista
03-02 16:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-02 16:56 DEBUG  WindowsBackend: windows_sp=None
03-02 16:56 DEBUG  WindowsBackend: windows_build=7600
03-02 16:56 DEBUG  WindowsBackend: gmt=-5
03-02 16:56 DEBUG  WindowsBackend: country=US
03-02 16:56 DEBUG  WindowsBackend: timezone=America/New_York
03-02 16:56 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-02 16:56 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-02 16:56 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-02 16:56 DEBUG  WindowsBackend: windows_language_code=1033
03-02 16:56 DEBUG  WindowsBackend: windows_language=English
03-02 16:56 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-02 16:56 DEBUG  WindowsBackend: bootloader=vista
03-02 16:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 102535.148438 mb free ntfs)
03-02 16:56 DEBUG  WindowsBackend: drive=Drive(C: hd 102535.148438 mb free ntfs)
03-02 16:56 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-02 16:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-02 16:56 DEBUG  WindowsBackend: drive=Drive(U: hd 11178.6015625 mb free ntfs)
03-02 16:56 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
03-02 16:56 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
03-02 16:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-02 16:56 DEBUG  WindowsBackend: keyboard_id=67699721
03-02 16:56 DEBUG  WindowsBackend: keyboard_layout=us
03-02 16:56 DEBUG  WindowsBackend: keyboard_variant=
03-02 16:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-02 16:56 DEBUG  CommonBackend: locale=en_US.UTF-8
03-02 16:56 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-02 16:56 DEBUG  CommonBackend: Searching ISOs on USB devices
03-02 16:56 DEBUG  CommonBackend: Searching for local CDs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Ubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Ubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Ubuntu Netbook Remix CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Kubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Kubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Kubuntu Netbook CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Xubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Xubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Mythbuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp is a valid Mythbuntu CD
03-02 16:56 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 16:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 16:56 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-02 16:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-02 16:56 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-02 16:56 INFO   root: Running the CD menu...
03-02 16:56 DEBUG  WindowsFrontend: __init__...
03-02 16:56 DEBUG  WindowsFrontend: on_init...
03-02 16:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\translations, languages=['en_US', 'en']
03-02 16:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\translations, languages=['en_US', 'en']
03-02 16:56 INFO   root: CD menu finished
03-02 16:56 INFO   root: Running the installer...
03-02 16:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\translations, languages=['en_US', 'en']
03-02 16:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\translations, languages=['en_US', 'en']
03-02 16:57 DEBUG  WinuiInstallationPage: target_drive=U:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bob
03-02 16:57 INFO   root: Received settings
03-02 16:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\translations, languages=['en_US', 'en']
03-02 16:57 DEBUG  TaskList: # Running tasklist...
03-02 16:57 DEBUG  TaskList: ## Running select_target_dir...
03-02 16:57 INFO   WindowsBackend: Installing into U:\ubuntu
03-02 16:57 DEBUG  TaskList: ## Finished select_target_dir
03-02 16:57 DEBUG  TaskList: ## Running create_dir_structure...
03-02 16:57 DEBUG  CommonBackend: Creating dir U:\ubuntu
03-02 16:57 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks
03-02 16:57 DEBUG  CommonBackend: Creating dir U:\ubuntu\install
03-02 16:57 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot
03-02 16:57 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot
03-02 16:57 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot\grub
03-02 16:57 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot\grub
03-02 16:57 DEBUG  TaskList: ## Finished create_dir_structure
03-02 16:57 DEBUG  TaskList: ## Running uncompress_target_dir...
03-02 16:57 DEBUG  TaskList: ## Finished uncompress_target_dir
03-02 16:57 DEBUG  TaskList: ## Running create_uninstaller...
03-02 16:57 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> U:\ubuntu\uninstall-wubi.exe
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString U:\ubuntu\uninstall-wubi.exe
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir U:\ubuntu
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon U:\ubuntu\Ubuntu.ico
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-02 16:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-02 16:57 DEBUG  TaskList: ## Finished create_uninstaller
03-02 16:57 DEBUG  TaskList: ## Running copy_installation_files...
03-02 16:57 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\data\custom-installation -> U:\ubuntu\install\custom-installation
03-02 16:57 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\winboot -> U:\ubuntu\winboot
03-02 16:57 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl52E0.tmp\data\images\Ubuntu.ico -> U:\ubuntu\Ubuntu.ico
03-02 16:57 DEBUG  TaskList: ## Finished copy_installation_files
03-02 16:57 DEBUG  TaskList: ## Running get_iso...
03-02 16:57 DEBUG  TaskList: New task copy_file
03-02 16:57 DEBUG  TaskList: ### Running copy_file...
03-02 17:00 DEBUG  TaskList: ### Finished copy_file
03-02 17:00 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-02 17:00 DEBUG  TaskList: # Cancelling tasklist
03-02 17:00 DEBUG  TaskList: New task check_iso
03-02 17:00 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-02 17:00 DEBUG  CommonBackend: Searching for local ISO
03-02 17:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-02 17:00 DEBUG  TaskList: New task get_metalink
03-02 17:00 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-02 17:00 DEBUG  TaskList: # Cancelling tasklist
03-02 17:00 DEBUG  TaskList: # Finished tasklist
03-02 17:01 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-02 17:01 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-02 17:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="U:\\ubuntu\\uninstall-wubi.exe"']
03-02 17:01 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\data
03-02 17:01 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\bin\7z.exe
03-02 17:01 DEBUG  CommonBackend: Fetching basic info...
03-02 17:01 DEBUG  CommonBackend: original_exe=U:\ubuntu\uninstall-wubi.exe
03-02 17:01 DEBUG  CommonBackend: platform=win32
03-02 17:01 DEBUG  CommonBackend: osname=nt
03-02 17:01 DEBUG  CommonBackend: language=en_US
03-02 17:01 DEBUG  CommonBackend: encoding=cp1252
03-02 17:01 DEBUG  WindowsBackend: arch=amd64
03-02 17:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\data\isolist.ini
03-02 17:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-02 17:01 DEBUG  WindowsBackend: Fetching host info...
03-02 17:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-02 17:01 DEBUG  WindowsBackend: windows version=vista
03-02 17:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-02 17:01 DEBUG  WindowsBackend: windows_sp=None
03-02 17:01 DEBUG  WindowsBackend: windows_build=7600
03-02 17:01 DEBUG  WindowsBackend: gmt=-5
03-02 17:01 DEBUG  WindowsBackend: country=US
03-02 17:01 DEBUG  WindowsBackend: timezone=America/New_York
03-02 17:01 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-02 17:01 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-02 17:01 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-02 17:01 DEBUG  WindowsBackend: windows_language_code=1033
03-02 17:01 DEBUG  WindowsBackend: windows_language=English
03-02 17:01 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-02 17:01 DEBUG  WindowsBackend: bootloader=vista
03-02 17:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 102534.363281 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(C: hd 102534.363281 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.47265625 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(U: hd 10488.0664063 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: uninstaller_path=U:\ubuntu\uninstall-wubi.exe
03-02 17:01 DEBUG  WindowsBackend: previous_target_dir=U:\ubuntu
03-02 17:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-02 17:01 DEBUG  WindowsBackend: keyboard_id=67699721
03-02 17:01 DEBUG  WindowsBackend: keyboard_layout=us
03-02 17:01 DEBUG  WindowsBackend: keyboard_variant=
03-02 17:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-02 17:01 DEBUG  CommonBackend: locale=en_US.UTF-8
03-02 17:01 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-02 17:01 DEBUG  CommonBackend: Searching ISOs on USB devices
03-02 17:01 DEBUG  CommonBackend: Searching for local CDs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-02 17:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-02 17:01 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-02 17:01 INFO   root: Running the uninstaller...
03-02 17:01 INFO   CommonBackend: This is the uninstaller running
03-02 17:01 DEBUG  WindowsFrontend: __init__...
03-02 17:01 DEBUG  WindowsFrontend: on_init...
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\translations, languages=['en_US', 'en']
03-02 17:01 INFO   root: Received settings
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\translations, languages=['en_US', 'en']
03-02 17:01 DEBUG  TaskList: # Running tasklist...
03-02 17:01 DEBUG  TaskList: ## Running Backup ISO...
03-02 17:01 DEBUG  TaskList: ## Finished Backup ISO
03-02 17:01 DEBUG  TaskList: ## Running Remove bootloader entry...
03-02 17:01 DEBUG  WindowsBackend: Could not find bcd id
03-02 17:01 DEBUG  WindowsBackend: undo_bootini C:
03-02 17:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 102534.363281 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: undo_bootini D:
03-02 17:01 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 8433.47265625 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: undo_bootini U:
03-02 17:01 DEBUG  WindowsBackend: undo_configsys Drive(U: hd 10488.0664063 mb free ntfs)
03-02 17:01 DEBUG  TaskList: ## Finished Remove bootloader entry
03-02 17:01 DEBUG  TaskList: ## Running Remove target dir...
03-02 17:01 DEBUG  CommonBackend: Deleting U:\ubuntu
03-02 17:01 DEBUG  TaskList: ## Finished Remove target dir
03-02 17:01 DEBUG  TaskList: ## Running Remove registry key...
03-02 17:01 DEBUG  TaskList: ## Finished Remove registry key
03-02 17:01 DEBUG  TaskList: # Finished tasklist
03-02 17:01 INFO   root: Almost finished uninstalling
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl9B45.tmp\translations, languages=['en_US', 'en']
03-02 17:01 INFO   root: Finished uninstallation
03-02 17:01 DEBUG  root: application.quit
03-02 17:01 DEBUG  WindowsFrontend: frontend.quit
03-02 17:01 DEBUG  WindowsFrontend: frontend.on_quit
03-02 17:01 DEBUG  root: application.on_quit
03-02 17:01 INFO   root: sys.exit
03-09 07:00 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-09 07:00 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-09 07:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="c:\\Users\\BobTheTwit\\Documents\\Downloads\\wubi.exe"']
03-09 07:00 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\data
03-09 07:00 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\bin\7z.exe
03-09 07:00 DEBUG  CommonBackend: Fetching basic info...
03-09 07:00 DEBUG  CommonBackend: original_exe=c:\Users\BobTheTwit\Documents\Downloads\wubi.exe
03-09 07:00 DEBUG  CommonBackend: platform=win32
03-09 07:00 DEBUG  CommonBackend: osname=nt
03-09 07:00 DEBUG  CommonBackend: language=en_US
03-09 07:00 DEBUG  CommonBackend: encoding=cp1252
03-09 07:00 DEBUG  WindowsBackend: arch=amd64
03-09 07:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\data\isolist.ini
03-09 07:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 07:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 07:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 07:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 07:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 07:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 07:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 07:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 07:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 07:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 07:00 DEBUG  WindowsBackend: Fetching host info...
03-09 07:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 07:00 DEBUG  WindowsBackend: windows version=vista
03-09 07:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 07:00 DEBUG  WindowsBackend: windows_sp=None
03-09 07:00 DEBUG  WindowsBackend: windows_build=7600
03-09 07:00 DEBUG  WindowsBackend: gmt=-5
03-09 07:00 DEBUG  WindowsBackend: country=US
03-09 07:00 DEBUG  WindowsBackend: timezone=America/New_York
03-09 07:00 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-09 07:00 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-09 07:00 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-09 07:00 DEBUG  WindowsBackend: windows_language_code=1033
03-09 07:00 DEBUG  WindowsBackend: windows_language=English
03-09 07:00 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-09 07:00 DEBUG  WindowsBackend: bootloader=vista
03-09 07:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 106194.285156 mb free ntfs)
03-09 07:00 DEBUG  WindowsBackend: drive=Drive(C: hd 106194.285156 mb free ntfs)
03-09 07:00 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.46875 mb free ntfs)
03-09 07:00 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 07:00 DEBUG  WindowsBackend: drive=Drive(U: hd 11178.5742188 mb free ntfs)
03-09 07:00 DEBUG  WindowsBackend: uninstaller_path=None
03-09 07:00 DEBUG  WindowsBackend: previous_target_dir=None
03-09 07:00 DEBUG  WindowsBackend: previous_distro_name=None
03-09 07:00 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 07:00 DEBUG  WindowsBackend: keyboard_layout=us
03-09 07:00 DEBUG  WindowsBackend: keyboard_variant=
03-09 07:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-09 07:00 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 07:00 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-09 07:00 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 07:00 DEBUG  CommonBackend: Searching for local CDs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Ubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Ubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Ubuntu Netbook Remix CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Kubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Kubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Kubuntu Netbook CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Xubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Xubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Mythbuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp is a valid Mythbuntu CD
03-09 07:00 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 07:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 07:00 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-09 07:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-09 07:00 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 07:00 INFO   root: Running the CD menu...
03-09 07:00 DEBUG  WindowsFrontend: __init__...
03-09 07:00 DEBUG  WindowsFrontend: on_init...
03-09 07:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\translations, languages=['en_US', 'en']
03-09 07:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\translations, languages=['en_US', 'en']
03-09 07:00 INFO   root: CD menu finished
03-09 07:00 INFO   root: Running the installer...
03-09 07:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\translations, languages=['en_US', 'en']
03-09 07:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\translations, languages=['en_US', 'en']
03-09 07:01 DEBUG  WinuiInstallationPage: target_drive=U:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bob
03-09 07:01 INFO   root: Received settings
03-09 07:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\translations, languages=['en_US', 'en']
03-09 07:01 DEBUG  TaskList: # Running tasklist...
03-09 07:01 DEBUG  TaskList: ## Running select_target_dir...
03-09 07:01 INFO   WindowsBackend: Installing into U:\ubuntu
03-09 07:01 DEBUG  TaskList: ## Finished select_target_dir
03-09 07:01 DEBUG  TaskList: ## Running create_dir_structure...
03-09 07:01 DEBUG  CommonBackend: Creating dir U:\ubuntu
03-09 07:01 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks
03-09 07:01 DEBUG  CommonBackend: Creating dir U:\ubuntu\install
03-09 07:01 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot
03-09 07:01 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot
03-09 07:01 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot\grub
03-09 07:01 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot\grub
03-09 07:01 DEBUG  TaskList: ## Finished create_dir_structure
03-09 07:01 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 07:01 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 07:01 DEBUG  TaskList: ## Running create_uninstaller...
03-09 07:01 DEBUG  WindowsBackend: Copying uninstaller c:\Users\BobTheTwit\Documents\Downloads\wubi.exe -> U:\ubuntu\uninstall-wubi.exe
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString U:\ubuntu\uninstall-wubi.exe
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir U:\ubuntu
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon U:\ubuntu\Ubuntu.ico
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 07:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 07:01 DEBUG  TaskList: ## Finished create_uninstaller
03-09 07:01 DEBUG  TaskList: ## Running copy_installation_files...
03-09 07:01 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\data\custom-installation -> U:\ubuntu\install\custom-installation
03-09 07:01 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\winboot -> U:\ubuntu\winboot
03-09 07:01 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pyl948C.tmp\data\images\Ubuntu.ico -> U:\ubuntu\Ubuntu.ico
03-09 07:01 DEBUG  TaskList: ## Finished copy_installation_files
03-09 07:01 DEBUG  TaskList: ## Running get_iso...
03-09 07:01 DEBUG  TaskList: New task copy_file
03-09 07:01 DEBUG  TaskList: ### Running copy_file...
03-09 07:03 DEBUG  TaskList: ### Finished copy_file
03-09 07:03 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 07:03 DEBUG  TaskList: # Cancelling tasklist
03-09 07:03 DEBUG  TaskList: New task check_iso
03-09 07:03 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 07:03 DEBUG  CommonBackend: Searching for local ISO
03-09 07:03 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 07:03 DEBUG  TaskList: New task get_metalink
03-09 07:03 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-09 07:03 DEBUG  TaskList: # Cancelling tasklist
03-09 07:03 DEBUG  TaskList: # Finished tasklist
03-09 17:10 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-09 17:10 DEBUG  root: Logfile is c:\users\bobthe~1\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-09 17:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="c:\\Users\\BobTheTwit\\Documents\\Downloads\\wubi.exe"']
03-09 17:10 DEBUG  CommonBackend: data_dir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\data
03-09 17:10 DEBUG  WindowsBackend: 7z=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\bin\7z.exe
03-09 17:10 DEBUG  CommonBackend: Fetching basic info...
03-09 17:10 DEBUG  CommonBackend: original_exe=c:\Users\BobTheTwit\Documents\Downloads\wubi.exe
03-09 17:10 DEBUG  CommonBackend: platform=win32
03-09 17:10 DEBUG  CommonBackend: osname=nt
03-09 17:10 DEBUG  CommonBackend: language=en_US
03-09 17:10 DEBUG  CommonBackend: encoding=cp1252
03-09 17:10 DEBUG  WindowsBackend: arch=amd64
03-09 17:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\data\isolist.ini
03-09 17:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 17:10 DEBUG  WindowsBackend: Fetching host info...
03-09 17:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 17:10 DEBUG  WindowsBackend: windows version=vista
03-09 17:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 17:10 DEBUG  WindowsBackend: windows_sp=None
03-09 17:10 DEBUG  WindowsBackend: windows_build=7600
03-09 17:10 DEBUG  WindowsBackend: gmt=-5
03-09 17:10 DEBUG  WindowsBackend: country=US
03-09 17:10 DEBUG  WindowsBackend: timezone=America/New_York
03-09 17:10 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-09 17:10 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-09 17:10 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-09 17:10 DEBUG  WindowsBackend: windows_language_code=1033
03-09 17:10 DEBUG  WindowsBackend: windows_language=English
03-09 17:10 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-09 17:10 DEBUG  WindowsBackend: bootloader=vista
03-09 17:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 106180.292969 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(C: hd 106180.292969 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.46875 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(U: hd 10488.0429688 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(Z: remote 0.0 mb free )
03-09 17:10 DEBUG  WindowsBackend: uninstaller_path=U:\ubuntu\uninstall-wubi.exe
03-09 17:10 DEBUG  WindowsBackend: previous_target_dir=U:\ubuntu
03-09 17:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 17:10 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 17:10 DEBUG  WindowsBackend: keyboard_layout=us
03-09 17:10 DEBUG  WindowsBackend: keyboard_variant=
03-09 17:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-09 17:10 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 17:10 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-09 17:10 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 17:10 DEBUG  CommonBackend: Searching for local CDs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Ubuntu Netbook Remix CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Kubuntu Netbook CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-09 17:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-09 17:10 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 17:10 INFO   root: Running the CD menu...
03-09 17:10 DEBUG  WindowsFrontend: __init__...
03-09 17:10 DEBUG  WindowsFrontend: on_init...
03-09 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\translations, languages=['en_US', 'en']
03-09 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\translations, languages=['en_US', 'en']
03-09 17:10 INFO   root: CD menu finished
03-09 17:10 INFO   root: Already installed, running the uninstaller...
03-09 17:10 INFO   root: Running the uninstaller...
03-09 17:10 INFO   CommonBackend: This is the uninstaller running
03-09 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\translations, languages=['en_US', 'en']
03-09 17:10 INFO   root: Received settings
03-09 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\translations, languages=['en_US', 'en']
03-09 17:10 DEBUG  TaskList: # Running tasklist...
03-09 17:10 DEBUG  TaskList: ## Running Backup ISO...
03-09 17:10 DEBUG  TaskList: ## Finished Backup ISO
03-09 17:10 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 17:10 DEBUG  WindowsBackend: Could not find bcd id
03-09 17:10 DEBUG  WindowsBackend: undo_bootini C:
03-09 17:10 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 106180.292969 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: undo_bootini D:
03-09 17:10 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 8433.46875 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: undo_bootini U:
03-09 17:10 DEBUG  WindowsBackend: undo_configsys Drive(U: hd 10488.0429688 mb free ntfs)
03-09 17:10 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 17:10 DEBUG  TaskList: ## Running Remove target dir...
03-09 17:10 DEBUG  CommonBackend: Deleting U:\ubuntu
03-09 17:10 DEBUG  TaskList: ## Finished Remove target dir
03-09 17:10 DEBUG  TaskList: ## Running Remove registry key...
03-09 17:10 DEBUG  TaskList: ## Finished Remove registry key
03-09 17:10 DEBUG  TaskList: # Finished tasklist
03-09 17:10 INFO   root: Almost finished uninstalling
03-09 17:10 INFO   root: Finished uninstallation
03-09 17:10 DEBUG  CommonBackend: Fetching basic info...
03-09 17:10 DEBUG  CommonBackend: original_exe=c:\Users\BobTheTwit\Documents\Downloads\wubi.exe
03-09 17:10 DEBUG  CommonBackend: platform=win32
03-09 17:10 DEBUG  CommonBackend: osname=nt
03-09 17:10 DEBUG  WindowsBackend: arch=amd64
03-09 17:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\data\isolist.ini
03-09 17:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 17:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 17:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 17:10 DEBUG  WindowsBackend: Fetching host info...
03-09 17:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 17:10 DEBUG  WindowsBackend: windows version=vista
03-09 17:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 17:10 DEBUG  WindowsBackend: windows_sp=None
03-09 17:10 DEBUG  WindowsBackend: windows_build=7600
03-09 17:10 DEBUG  WindowsBackend: gmt=-5
03-09 17:10 DEBUG  WindowsBackend: country=US
03-09 17:10 DEBUG  WindowsBackend: timezone=America/New_York
03-09 17:10 DEBUG  WindowsBackend: windows_username=BobTheTwit
03-09 17:10 DEBUG  WindowsBackend: user_full_name=BobTheTwit
03-09 17:10 DEBUG  WindowsBackend: user_directory=C:\Users\BobTheTwit
03-09 17:10 DEBUG  WindowsBackend: windows_language_code=1033
03-09 17:10 DEBUG  WindowsBackend: windows_language=English
03-09 17:10 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
03-09 17:10 DEBUG  WindowsBackend: bootloader=vista
03-09 17:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 106180.269531 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(C: hd 106180.269531 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(D: hd 8433.46875 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(U: hd 11178.5742188 mb free ntfs)
03-09 17:10 DEBUG  WindowsBackend: drive=Drive(Z: remote 0.0 mb free )
03-09 17:10 DEBUG  WindowsBackend: uninstaller_path=None
03-09 17:10 DEBUG  WindowsBackend: previous_target_dir=None
03-09 17:10 DEBUG  WindowsBackend: previous_distro_name=None
03-09 17:10 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 17:10 DEBUG  WindowsBackend: keyboard_layout=us
03-09 17:10 DEBUG  WindowsBackend: keyboard_variant=
03-09 17:10 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-09 17:10 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 17:10 DEBUG  CommonBackend: Searching for local CDs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Ubuntu Netbook Remix CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Kubuntu Netbook CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 17:10 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 17:10 INFO   root: Running the installer...
03-09 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\translations, languages=['en_US', 'en']
03-09 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\translations, languages=['en_US', 'en']
03-09 17:11 DEBUG  WinuiInstallationPage: target_drive=U:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bob
03-09 17:11 INFO   root: Received settings
03-09 17:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\translations, languages=['en_US', 'en']
03-09 17:11 DEBUG  TaskList: # Running tasklist...
03-09 17:11 DEBUG  TaskList: ## Running select_target_dir...
03-09 17:11 INFO   WindowsBackend: Installing into U:\ubuntu
03-09 17:11 DEBUG  TaskList: ## Finished select_target_dir
03-09 17:11 DEBUG  TaskList: ## Running create_dir_structure...
03-09 17:11 DEBUG  CommonBackend: Creating dir U:\ubuntu
03-09 17:11 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks
03-09 17:11 DEBUG  CommonBackend: Creating dir U:\ubuntu\install
03-09 17:11 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot
03-09 17:11 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot
03-09 17:11 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot\grub
03-09 17:11 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot\grub
03-09 17:11 DEBUG  TaskList: ## Finished create_dir_structure
03-09 17:11 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 17:11 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 17:11 DEBUG  TaskList: ## Running create_uninstaller...
03-09 17:11 DEBUG  WindowsBackend: Copying uninstaller c:\Users\BobTheTwit\Documents\Downloads\wubi.exe -> U:\ubuntu\uninstall-wubi.exe
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString U:\ubuntu\uninstall-wubi.exe
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir U:\ubuntu
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon U:\ubuntu\Ubuntu.ico
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 17:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 17:11 DEBUG  TaskList: ## Finished create_uninstaller
03-09 17:11 DEBUG  TaskList: ## Running copy_installation_files...
03-09 17:11 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\data\custom-installation -> U:\ubuntu\install\custom-installation
03-09 17:11 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\winboot -> U:\ubuntu\winboot
03-09 17:11 DEBUG  WindowsBackend: Copying C:\Users\BOBTHE~1\AppData\Local\Temp\pylA219.tmp\data\images\Ubuntu.ico -> U:\ubuntu\Ubuntu.ico
03-09 17:11 DEBUG  TaskList: ## Finished copy_installation_files
03-09 17:11 DEBUG  TaskList: ## Running get_iso...
03-09 17:11 DEBUG  TaskList: New task copy_file
03-09 17:11 DEBUG  TaskList: ### Running copy_file...
03-09 17:14 DEBUG  TaskList: ### Finished copy_file
03-09 17:14 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 17:14 DEBUG  TaskList: # Cancelling tasklist
03-09 17:14 DEBUG  TaskList: New task check_iso
03-09 17:14 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 17:14 DEBUG  CommonBackend: Searching for local ISO
03-09 17:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 17:14 DEBUG  TaskList: New task get_metalink
03-09 17:14 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-09 17:14 DEBUG  TaskList: # Cancelling tasklist
03-09 17:14 DEBUG  TaskList: # Finished tasklist[/COLOR][/COLOR][/COLOR]

```

---

