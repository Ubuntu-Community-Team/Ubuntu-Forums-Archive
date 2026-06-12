---
title: "Ubuntu Error/ Won't start on Windows 7"
date: 2010-11-28
forum: General Help
---

### Post by Traitors1991 on 2010-11-28
I've tried installing Ubuntu 10.10 several times on my computer and i keep getting an invalid argument and I've tried running it off the cd but The computer boots straight into Windows and i've tried to boot from the cd but the computer bypasses it and boots straight to Windows
this is the log error i received.



```
11-24 16:51 INFO   root: === wubi 10.10 rev197 ===
11-24 16:51 DEBUG  root: Logfile is c:\users\javier\appdata\local\temp\wubi-10.10-rev197.log
11-24 16:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
11-24 16:51 DEBUG  CommonBackend: data_dir=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\data
11-24 16:51 DEBUG  WindowsBackend: 7z=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\bin\7z.exe
11-24 16:51 DEBUG  CommonBackend: Fetching basic info...
11-24 16:51 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-24 16:51 DEBUG  CommonBackend: platform=win32
11-24 16:51 DEBUG  CommonBackend: osname=nt
11-24 16:51 DEBUG  CommonBackend: language=en_US
11-24 16:51 DEBUG  CommonBackend: encoding=cp1252
11-24 16:51 DEBUG  WindowsBackend: arch=amd64
11-24 16:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\data\isolist.ini
11-24 16:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-24 16:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-24 16:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-24 16:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-24 16:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-24 16:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-24 16:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-24 16:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-24 16:51 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-24 16:51 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-24 16:51 DEBUG  WindowsBackend: Fetching host info...
11-24 16:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-24 16:51 DEBUG  WindowsBackend: windows version=vista
11-24 16:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-24 16:51 DEBUG  WindowsBackend: windows_sp=None
11-24 16:51 DEBUG  WindowsBackend: windows_build=7600
11-24 16:51 DEBUG  WindowsBackend: gmt=-8
11-24 16:51 DEBUG  WindowsBackend: country=US
11-24 16:51 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-24 16:51 DEBUG  WindowsBackend: windows_username=Javier
11-24 16:51 DEBUG  WindowsBackend: user_full_name=Javier
11-24 16:51 DEBUG  WindowsBackend: user_directory=C:\Users\Javier
11-24 16:51 DEBUG  WindowsBackend: windows_language_code=1033
11-24 16:51 DEBUG  WindowsBackend: windows_language=English
11-24 16:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-24 16:51 DEBUG  WindowsBackend: bootloader=vista
11-24 16:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153307.253906 mb free ntfs)
11-24 16:51 DEBUG  WindowsBackend: drive=Drive(C: hd 153307.253906 mb free ntfs)
11-24 16:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-24 16:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-24 16:51 DEBUG  WindowsBackend: uninstaller_path=None
11-24 16:51 DEBUG  WindowsBackend: previous_target_dir=None
11-24 16:51 DEBUG  WindowsBackend: previous_distro_name=None
11-24 16:51 DEBUG  WindowsBackend: keyboard_id=67699721
11-24 16:51 DEBUG  WindowsBackend: keyboard_layout=us
11-24 16:51 DEBUG  WindowsBackend: keyboard_variant=
11-24 16:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-24 16:51 DEBUG  CommonBackend: locale=en_US.UTF-8
11-24 16:51 DEBUG  WindowsBackend: total_memory_mb=3764.5
11-24 16:51 DEBUG  CommonBackend: Searching ISOs on USB devices
11-24 16:51 DEBUG  CommonBackend: Searching for local CDs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Ubuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Ubuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Ubuntu Netbook CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Kubuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Kubuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Kubuntu Netbook CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Xubuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Xubuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Mythbuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp is a valid Mythbuntu CD
11-24 16:51 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\casper\filesystem.squashfs
11-24 16:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-24 16:51 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-24 16:51 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-24 16:51 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-24 16:51 INFO   root: Running the CD menu...
11-24 16:51 DEBUG  WindowsFrontend: __init__...
11-24 16:51 DEBUG  WindowsFrontend: on_init...
11-24 16:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\translations, languages=['en_US', 'en']
11-24 16:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\translations, languages=['en_US', 'en']
11-24 16:51 INFO   root: CD menu finished
11-24 16:51 INFO   root: Running the installer...
11-24 16:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\translations, languages=['en_US', 'en']
11-24 16:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\translations, languages=['en_US', 'en']
11-24 16:51 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=javier
11-24 16:51 INFO   root: Received settings
11-24 16:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\translations, languages=['en_US', 'en']
11-24 16:51 DEBUG  TaskList: # Running tasklist...
11-24 16:51 DEBUG  TaskList: ## Running select_target_dir...
11-24 16:51 INFO   WindowsBackend: Installing into C:\ubuntu
11-24 16:51 DEBUG  TaskList: ## Finished select_target_dir
11-24 16:51 DEBUG  TaskList: ## Running create_dir_structure...
11-24 16:51 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-24 16:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-24 16:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-24 16:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-24 16:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-24 16:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-24 16:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-24 16:51 DEBUG  TaskList: ## Finished create_dir_structure
11-24 16:51 DEBUG  TaskList: ## Running uncompress_target_dir...
11-24 16:51 DEBUG  TaskList: ## Finished uncompress_target_dir
11-24 16:51 DEBUG  TaskList: ## Running create_uninstaller...
11-24 16:51 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-24 16:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-24 16:51 DEBUG  TaskList: ## Finished create_uninstaller
11-24 16:51 DEBUG  TaskList: ## Running copy_installation_files...
11-24 16:51 DEBUG  WindowsBackend: Copying C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-24 16:51 DEBUG  WindowsBackend: Copying C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\winboot -> C:\ubuntu\winboot
11-24 16:51 DEBUG  WindowsBackend: Copying C:\Users\Javier\AppData\Local\Temp\pylCA49.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-24 16:51 DEBUG  TaskList: ## Finished copy_installation_files
11-24 16:51 DEBUG  TaskList: ## Running get_iso...
11-24 16:51 DEBUG  TaskList: New task copy_file
11-24 16:51 DEBUG  TaskList: ### Running copy_file...
11-24 16:56 DEBUG  TaskList: ### Finished copy_file
11-24 16:59 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-24 16:59 DEBUG  TaskList: # Cancelling tasklist
11-24 16:59 DEBUG  TaskList: New task check_iso
11-24 16:59 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-24 16:59 DEBUG  CommonBackend: Searching for local ISO
11-24 16:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-24 16:59 DEBUG  TaskList: New task get_metalink
11-24 16:59 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-24 16:59 DEBUG  TaskList: # Cancelling tasklist
11-24 16:59 DEBUG  TaskList: # Finished tasklist
11-24 17:02 INFO   root: === wubi 10.10 rev197 ===
11-24 17:02 DEBUG  root: Logfile is c:\users\javier\appdata\local\temp\wubi-10.10-rev197.log
11-24 17:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
11-24 17:02 DEBUG  CommonBackend: data_dir=C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\data
11-24 17:02 DEBUG  WindowsBackend: 7z=C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\bin\7z.exe
11-24 17:02 DEBUG  CommonBackend: Fetching basic info...
11-24 17:02 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-24 17:02 DEBUG  CommonBackend: platform=win32
11-24 17:02 DEBUG  CommonBackend: osname=nt
11-24 17:02 DEBUG  CommonBackend: language=en_US
11-24 17:02 DEBUG  CommonBackend: encoding=cp1252
11-24 17:02 DEBUG  WindowsBackend: arch=amd64
11-24 17:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\data\isolist.ini
11-24 17:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-24 17:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-24 17:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-24 17:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-24 17:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-24 17:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-24 17:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-24 17:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-24 17:02 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-24 17:02 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-24 17:02 DEBUG  WindowsBackend: Fetching host info...
11-24 17:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-24 17:02 DEBUG  WindowsBackend: windows version=vista
11-24 17:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-24 17:02 DEBUG  WindowsBackend: windows_sp=None
11-24 17:02 DEBUG  WindowsBackend: windows_build=7600
11-24 17:02 DEBUG  WindowsBackend: gmt=-8
11-24 17:02 DEBUG  WindowsBackend: country=US
11-24 17:02 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-24 17:02 DEBUG  WindowsBackend: windows_username=Javier
11-24 17:02 DEBUG  WindowsBackend: user_full_name=Javier
11-24 17:02 DEBUG  WindowsBackend: user_directory=C:\Users\Javier
11-24 17:02 DEBUG  WindowsBackend: windows_language_code=1033
11-24 17:02 DEBUG  WindowsBackend: windows_language=English
11-24 17:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-24 17:02 DEBUG  WindowsBackend: bootloader=vista
11-24 17:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152589.4375 mb free ntfs)
11-24 17:02 DEBUG  WindowsBackend: drive=Drive(C: hd 152589.4375 mb free ntfs)
11-24 17:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-24 17:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-24 17:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-24 17:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-24 17:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-24 17:02 DEBUG  WindowsBackend: keyboard_id=67699721
11-24 17:02 DEBUG  WindowsBackend: keyboard_layout=us
11-24 17:02 DEBUG  WindowsBackend: keyboard_variant=
11-24 17:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-24 17:02 DEBUG  CommonBackend: locale=en_US.UTF-8
11-24 17:02 DEBUG  WindowsBackend: total_memory_mb=3764.5
11-24 17:02 DEBUG  CommonBackend: Searching ISOs on USB devices
11-24 17:02 DEBUG  CommonBackend: Searching for local CDs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Ubuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Ubuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Ubuntu Netbook CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Kubuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Kubuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Kubuntu Netbook CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Xubuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Xubuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Mythbuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp is a valid Mythbuntu CD
11-24 17:02 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\casper\filesystem.squashfs
11-24 17:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-24 17:02 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-24 17:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-24 17:02 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-24 17:02 INFO   root: Running the uninstaller...
11-24 17:02 INFO   CommonBackend: This is the uninstaller running
11-24 17:02 DEBUG  WindowsFrontend: __init__...
11-24 17:02 DEBUG  WindowsFrontend: on_init...
11-24 17:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylDB49.tmp\translations, languages=['en_US', 'en']
11-24 17:02 INFO   WindowsFrontend: Operation cancelled
11-24 17:02 DEBUG  WindowsFrontend: frontend.quit
11-24 17:02 DEBUG  WindowsFrontend: frontend.on_quit
11-24 17:02 DEBUG  root: application.on_quit
11-24 17:02 INFO   root: sys.exit
11-24 17:08 INFO   root: === wubi 10.10 rev197 ===
11-24 17:08 DEBUG  root: Logfile is c:\users\javier\appdata\local\temp\wubi-10.10-rev197.log
11-24 17:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
11-24 17:08 DEBUG  CommonBackend: data_dir=C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\data
11-24 17:08 DEBUG  WindowsBackend: 7z=C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\bin\7z.exe
11-24 17:08 DEBUG  CommonBackend: Fetching basic info...
11-24 17:08 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-24 17:08 DEBUG  CommonBackend: platform=win32
11-24 17:08 DEBUG  CommonBackend: osname=nt
11-24 17:08 DEBUG  CommonBackend: language=en_US
11-24 17:08 DEBUG  CommonBackend: encoding=cp1252
11-24 17:08 DEBUG  WindowsBackend: arch=amd64
11-24 17:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\data\isolist.ini
11-24 17:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-24 17:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-24 17:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-24 17:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-24 17:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-24 17:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-24 17:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-24 17:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-24 17:08 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-24 17:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-24 17:08 DEBUG  WindowsBackend: Fetching host info...
11-24 17:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-24 17:08 DEBUG  WindowsBackend: windows version=vista
11-24 17:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-24 17:08 DEBUG  WindowsBackend: windows_sp=None
11-24 17:08 DEBUG  WindowsBackend: windows_build=7600
11-24 17:08 DEBUG  WindowsBackend: gmt=-8
11-24 17:08 DEBUG  WindowsBackend: country=US
11-24 17:08 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-24 17:08 DEBUG  WindowsBackend: windows_username=Javier
11-24 17:08 DEBUG  WindowsBackend: user_full_name=Javier
11-24 17:08 DEBUG  WindowsBackend: user_directory=C:\Users\Javier
11-24 17:08 DEBUG  WindowsBackend: windows_language_code=1033
11-24 17:08 DEBUG  WindowsBackend: windows_language=English
11-24 17:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-24 17:08 DEBUG  WindowsBackend: bootloader=vista
11-24 17:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152666.5 mb free ntfs)
11-24 17:08 DEBUG  WindowsBackend: drive=Drive(C: hd 152666.5 mb free ntfs)
11-24 17:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-24 17:08 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-24 17:08 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-24 17:08 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-24 17:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-24 17:08 DEBUG  WindowsBackend: keyboard_id=67699721
11-24 17:08 DEBUG  WindowsBackend: keyboard_layout=us
11-24 17:08 DEBUG  WindowsBackend: keyboard_variant=
11-24 17:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-24 17:08 DEBUG  CommonBackend: locale=en_US.UTF-8
11-24 17:08 DEBUG  WindowsBackend: total_memory_mb=3764.5
11-24 17:08 DEBUG  CommonBackend: Searching ISOs on USB devices
11-24 17:08 DEBUG  CommonBackend: Searching for local CDs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Ubuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Ubuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Ubuntu Netbook CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Kubuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Kubuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Kubuntu Netbook CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Xubuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Xubuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Mythbuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pylD097.tmp is a valid Mythbuntu CD
11-24 17:08 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\casper\filesystem.squashfs
11-24 17:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-24 17:08 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-24 17:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-24 17:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-24 17:08 INFO   root: Running the uninstaller...
11-24 17:08 INFO   CommonBackend: This is the uninstaller running
11-24 17:08 DEBUG  WindowsFrontend: __init__...
11-24 17:08 DEBUG  WindowsFrontend: on_init...
11-24 17:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\translations, languages=['en_US', 'en']
11-24 17:08 INFO   root: Received settings
11-24 17:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\translations, languages=['en_US', 'en']
11-24 17:08 DEBUG  TaskList: # Running tasklist...
11-24 17:08 DEBUG  TaskList: ## Running Backup ISO...
11-24 17:08 DEBUG  TaskList: ## Finished Backup ISO
11-24 17:08 DEBUG  TaskList: ## Running Remove bootloader entry...
11-24 17:08 DEBUG  WindowsBackend: Could not find bcd id
11-24 17:08 DEBUG  WindowsBackend: undo_bootini C:
11-24 17:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 152666.5 mb free ntfs)
11-24 17:08 DEBUG  TaskList: ## Finished Remove bootloader entry
11-24 17:08 DEBUG  TaskList: ## Running Remove target dir...
11-24 17:08 DEBUG  CommonBackend: Deleting C:\ubuntu
11-24 17:08 DEBUG  TaskList: ## Finished Remove target dir
11-24 17:08 DEBUG  TaskList: ## Running Remove registry key...
11-24 17:08 DEBUG  TaskList: ## Finished Remove registry key
11-24 17:08 DEBUG  TaskList: # Finished tasklist
11-24 17:08 INFO   root: Almost finished uninstalling
11-24 17:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pylD097.tmp\translations, languages=['en_US', 'en']
11-24 17:08 INFO   root: Finished uninstallation
11-24 17:08 DEBUG  root: application.quit
11-24 17:08 DEBUG  WindowsFrontend: frontend.quit
11-24 17:08 DEBUG  WindowsFrontend: frontend.on_quit
11-24 17:08 DEBUG  root: application.on_quit
11-24 17:08 INFO   root: sys.exit
11-27 11:36 INFO   root: === wubi 10.10 rev197 ===
11-27 11:36 DEBUG  root: Logfile is c:\users\javier\appdata\local\temp\wubi-10.10-rev197.log
11-27 11:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
11-27 11:36 DEBUG  CommonBackend: data_dir=C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\data
11-27 11:36 DEBUG  WindowsBackend: 7z=C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\bin\7z.exe
11-27 11:36 DEBUG  CommonBackend: Fetching basic info...
11-27 11:36 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-27 11:36 DEBUG  CommonBackend: platform=win32
11-27 11:36 DEBUG  CommonBackend: osname=nt
11-27 11:36 DEBUG  CommonBackend: language=en_US
11-27 11:36 DEBUG  CommonBackend: encoding=cp1252
11-27 11:36 DEBUG  WindowsBackend: arch=amd64
11-27 11:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\data\isolist.ini
11-27 11:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-27 11:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-27 11:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-27 11:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-27 11:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-27 11:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-27 11:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-27 11:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-27 11:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-27 11:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-27 11:36 DEBUG  WindowsBackend: Fetching host info...
11-27 11:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-27 11:36 DEBUG  WindowsBackend: windows version=vista
11-27 11:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-27 11:36 DEBUG  WindowsBackend: windows_sp=None
11-27 11:36 DEBUG  WindowsBackend: windows_build=7600
11-27 11:36 DEBUG  WindowsBackend: gmt=-8
11-27 11:36 DEBUG  WindowsBackend: country=US
11-27 11:36 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-27 11:36 DEBUG  WindowsBackend: windows_username=Javier
11-27 11:36 DEBUG  WindowsBackend: user_full_name=Javier
11-27 11:36 DEBUG  WindowsBackend: user_directory=C:\Users\Javier
11-27 11:36 DEBUG  WindowsBackend: windows_language_code=1033
11-27 11:36 DEBUG  WindowsBackend: windows_language=English
11-27 11:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-27 11:36 DEBUG  WindowsBackend: bootloader=vista
11-27 11:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 154000.054688 mb free ntfs)
11-27 11:36 DEBUG  WindowsBackend: drive=Drive(C: hd 154000.054688 mb free ntfs)
11-27 11:36 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-27 11:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-27 11:36 DEBUG  WindowsBackend: uninstaller_path=None
11-27 11:36 DEBUG  WindowsBackend: previous_target_dir=None
11-27 11:36 DEBUG  WindowsBackend: previous_distro_name=None
11-27 11:36 DEBUG  WindowsBackend: keyboard_id=67699721
11-27 11:36 DEBUG  WindowsBackend: keyboard_layout=us
11-27 11:36 DEBUG  WindowsBackend: keyboard_variant=
11-27 11:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-27 11:36 DEBUG  CommonBackend: locale=en_US.UTF-8
11-27 11:36 DEBUG  WindowsBackend: total_memory_mb=3764.5
11-27 11:36 DEBUG  CommonBackend: Searching ISOs on USB devices
11-27 11:36 DEBUG  CommonBackend: Searching for local CDs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Ubuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Ubuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Ubuntu Netbook CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Kubuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Kubuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Kubuntu Netbook CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Xubuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Xubuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Mythbuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp is a valid Mythbuntu CD
11-27 11:36 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\casper\filesystem.squashfs
11-27 11:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 11:36 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-27 11:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-27 11:36 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-27 11:36 INFO   root: Running the CD menu...
11-27 11:36 DEBUG  WindowsFrontend: __init__...
11-27 11:36 DEBUG  WindowsFrontend: on_init...
11-27 11:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\translations, languages=['en_US', 'en']
11-27 11:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pyl21DC.tmp\translations, languages=['en_US', 'en']
11-27 11:36 INFO   root: CD menu finished
11-27 11:36 INFO   root: Rebooting
11-27 11:36 DEBUG  TaskList: # Running tasklist...
11-27 11:36 DEBUG  TaskList: ## Running reboot...
11-27 11:36 DEBUG  TaskList: ## Finished reboot
11-27 11:36 DEBUG  TaskList: # Finished tasklist
11-27 11:36 DEBUG  root: application.quit
11-27 11:36 DEBUG  WindowsFrontend: frontend.quit
11-27 11:36 DEBUG  WindowsFrontend: frontend.on_quit
11-27 11:36 DEBUG  root: application.on_quit
11-27 11:36 INFO   root: sys.exit
11-28 00:45 INFO   root: === wubi 10.10 rev197 ===
11-28 00:45 DEBUG  root: Logfile is c:\users\javier\appdata\local\temp\wubi-10.10-rev197.log
11-28 00:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
11-28 00:45 DEBUG  CommonBackend: data_dir=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\data
11-28 00:45 DEBUG  WindowsBackend: 7z=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\bin\7z.exe
11-28 00:45 DEBUG  CommonBackend: Fetching basic info...
11-28 00:45 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-28 00:45 DEBUG  CommonBackend: platform=win32
11-28 00:45 DEBUG  CommonBackend: osname=nt
11-28 00:45 DEBUG  CommonBackend: language=en_US
11-28 00:45 DEBUG  CommonBackend: encoding=cp1252
11-28 00:45 DEBUG  WindowsBackend: arch=amd64
11-28 00:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\data\isolist.ini
11-28 00:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-28 00:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-28 00:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-28 00:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-28 00:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-28 00:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-28 00:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-28 00:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-28 00:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-28 00:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-28 00:45 DEBUG  WindowsBackend: Fetching host info...
11-28 00:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-28 00:45 DEBUG  WindowsBackend: windows version=vista
11-28 00:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-28 00:45 DEBUG  WindowsBackend: windows_sp=None
11-28 00:45 DEBUG  WindowsBackend: windows_build=7600
11-28 00:45 DEBUG  WindowsBackend: gmt=-8
11-28 00:45 DEBUG  WindowsBackend: country=US
11-28 00:45 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-28 00:45 DEBUG  WindowsBackend: windows_username=Javier
11-28 00:45 DEBUG  WindowsBackend: user_full_name=Javier
11-28 00:45 DEBUG  WindowsBackend: user_directory=C:\Users\Javier
11-28 00:45 DEBUG  WindowsBackend: windows_language_code=1033
11-28 00:45 DEBUG  WindowsBackend: windows_language=English
11-28 00:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-28 00:45 DEBUG  WindowsBackend: bootloader=vista
11-28 00:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152026.976563 mb free ntfs)
11-28 00:45 DEBUG  WindowsBackend: drive=Drive(C: hd 152026.976563 mb free ntfs)
11-28 00:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-28 00:45 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-28 00:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-28 00:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-28 00:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-28 00:45 DEBUG  WindowsBackend: keyboard_id=67699721
11-28 00:45 DEBUG  WindowsBackend: keyboard_layout=us
11-28 00:45 DEBUG  WindowsBackend: keyboard_variant=
11-28 00:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-28 00:45 DEBUG  CommonBackend: locale=en_US.UTF-8
11-28 00:45 DEBUG  WindowsBackend: total_memory_mb=3764.5
11-28 00:45 DEBUG  CommonBackend: Searching ISOs on USB devices
11-28 00:45 DEBUG  CommonBackend: Searching for local CDs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Ubuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Ubuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Ubuntu Netbook CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Kubuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Kubuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Kubuntu Netbook CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Xubuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Xubuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Mythbuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp is a valid Mythbuntu CD
11-28 00:45 DEBUG  Distro:     does not contain C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\casper\filesystem.squashfs
11-28 00:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 00:45 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-28 00:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-28 00:45 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-28 00:45 INFO   root: Running the CD menu...
11-28 00:45 DEBUG  WindowsFrontend: __init__...
11-28 00:45 DEBUG  WindowsFrontend: on_init...
11-28 00:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\translations, languages=['en_US', 'en']
11-28 00:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\translations, languages=['en_US', 'en']
11-28 00:47 INFO   root: CD menu finished
11-28 00:47 INFO   root: Running the installer...
11-28 00:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\translations, languages=['en_US', 'en']
11-28 00:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\translations, languages=['en_US', 'en']
11-28 00:47 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=javier
11-28 00:47 INFO   root: Received settings
11-28 00:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\translations, languages=['en_US', 'en']
11-28 00:47 DEBUG  TaskList: # Running tasklist...
11-28 00:47 DEBUG  TaskList: ## Running select_target_dir...
11-28 00:47 INFO   WindowsBackend: Installing into C:\ubuntu
11-28 00:47 DEBUG  TaskList: ## Finished select_target_dir
11-28 00:47 DEBUG  TaskList: ## Running create_dir_structure...
11-28 00:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-28 00:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-28 00:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-28 00:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-28 00:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-28 00:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-28 00:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-28 00:47 DEBUG  TaskList: ## Finished create_dir_structure
11-28 00:47 DEBUG  TaskList: ## Running uncompress_target_dir...
11-28 00:47 DEBUG  TaskList: ## Finished uncompress_target_dir
11-28 00:47 DEBUG  TaskList: ## Running create_uninstaller...
11-28 00:47 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-28 00:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-28 00:47 DEBUG  TaskList: ## Finished create_uninstaller
11-28 00:47 DEBUG  TaskList: ## Running copy_installation_files...
11-28 00:47 DEBUG  WindowsBackend: Copying C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-28 00:47 DEBUG  WindowsBackend: Copying C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\winboot -> C:\ubuntu\winboot
11-28 00:47 DEBUG  WindowsBackend: Copying C:\Users\Javier\AppData\Local\Temp\pyl3F9D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-28 00:47 DEBUG  TaskList: ## Finished copy_installation_files
11-28 00:47 DEBUG  TaskList: ## Running get_iso...
11-28 00:47 DEBUG  TaskList: New task copy_file
11-28 00:47 DEBUG  TaskList: ### Running copy_file...
11-28 00:52 DEBUG  TaskList: ### Finished copy_file
11-28 00:54 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-28 00:54 DEBUG  TaskList: # Cancelling tasklist
11-28 00:54 DEBUG  TaskList: New task check_iso
11-28 00:54 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-28 00:54 DEBUG  CommonBackend: Searching for local ISO
11-28 00:54 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-28 00:54 DEBUG  TaskList: New task get_metalink
11-28 00:54 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-28 00:54 DEBUG  TaskList: # Cancelling tasklist
11-28 00:54 DEBUG  TaskList: # Finished tasklist
```

---

### Post by wilee-nilee on 2010-11-28
First look in my signature for code tags and tag that text then follow this information to get the bootscript posted. You can also just open the edit on that text; **in the first post** click advanced highlight the text then click on the # in the reply panel.
[B]
This is information for the boot script in my sig:[/B]
To make this easiest lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags [code ][/code ] paste all the text in between.

---

### Post by Traitors1991 on 2010-11-28
i did and nothing, I'm not a forum kinda guy and i didn't want to post that all but since the size of attachments on this forum its stupidly tiny i could upload a 20kb text document so i had to, aside from that all the log is right there i really need help finding out why my computer is doing this

---

### Post by wilee-nilee on 2010-11-28
> **Traitors1991 said:**
> i did and nothing, I'm not a forum kinda guy and i didn't want to post that all but since the size of attachments on this forum its stupidly tiny i could upload a 20kb text document so i had to, aside from that all the log is right there i really need help finding out why my computer is doing this

well since you can't follow my advice and just have attitude you know none of us get paid here I'm outta here. If you can follow my advice the pm me. it is not magic man it is give the correct information, when asked.

---

### Post by Traitors1991 on 2010-11-28
> **wilee-nilee said:**
> well since you can't follow my advice and just have attitude you know none of us get paid here I'm outta here. If you can follow my advice the pm me. it is not magic man it is give the correct information, when asked.
i wasn't giving an attitude, whatever man, I did what you said i put the code things at the beginning and the end look at it, It didnt do anything.

---

### Post by sikander3786 on 2010-11-28
> **Traitors1991 said:**
> i wasn't giving an attitude, whatever man, I did what you said i put the code things at the beginning and the end look at it, It didnt do anything.
No problem I would try to sort this out and **wilee-nilee** would be back soon I hope ;-)

At the end where you type [/code ] it contains a space. It needs to look like this [/code] without any spaces between any characters.

Please edit accordingly and we are taking a look at all that stuff meanwhile.

Thanks.

---

### Post by sikander3786 on 2010-11-28
Taking a look at your initial problem, seems like you've installed Ubuntu inside Windows using the Wubi installer. It is an easier way to install Ubuntu alongside Windows but that is a little problematic sometimes.

I would recommend to install Ubuntu on its own partition if you've got some free space on your HDD. It would be far more stable and faster than Wubi.

Please read this page and you'll have many queries I know. We'll try to clear your doubts to the best of our knowledge.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Regarding the Live CD boot issue, make sure CD-ROM is selected as the first boot device in your Bios menu. It **should** boot easily.

---

### Post by bcbc on 2010-11-28
This bug is usually either a CD or hardware issue (with the CD/DVD drive) - and probably something to do with the built-in utilities in Wubi.  The simplest workaround is to place the downloaded Ubuntu image (.iso) file in the same folder as wubi.exe, and run wubi from there.

It's still good to have the Ubuntu CD.

---

### Post by Traitors1991 on 2010-11-28
> **bcbc said:**
> This bug is usually either a CD or hardware issue (with the CD/DVD drive) - and probably something to do with the built-in utilities in Wubi.  The simplest workaround is to place the downloaded Ubuntu image (.iso) file in the same folder as wubi.exe, and run wubi from there.

It's still good to have the Ubuntu CD.

I have actually run WUBI and i do have the cd, what happens with WUBI is that it starts downloading the image from the web then in completely stop at like 5 minutes left and won't go any further forcing me to cancel, I left it running all night and to no surprise it was still at 5 minutes, I tried using my 10.10 cd and it installs then at the very end it says invalid argument and rolls back everything and tells me to look at that log file, I also havethe log files from WUBI and the cd is you need them, I tried running it off the cd, and Windows No matter if i set the first boot device to my CD drive by passes it and goes straight to Windows. On a side note i HATE windows 7 I've always had linux and never had a problem installing it on windows vista and lower and I NEVER needed a 2nd partition for it, it installed right on my primary HD and ran just fine. So if anyone could help me with my problem it would be greatly apreciated

---

### Post by bcbc on 2010-11-29
> **Traitors1991 said:**
> I have actually run WUBI and i do have the cd, what happens with WUBI is that it starts downloading the image from the web then in completely stop at like 5 minutes left and won't go any further forcing me to cancel, I left it running all night and to no surprise it was still at 5 minutes, I tried using my 10.10 cd and it installs then at the very end it says invalid argument and rolls back everything and tells me to look at that log file, I also havethe log files from WUBI and the cd is you need them, I tried running it off the cd, and Windows No matter if i set the first boot device to my CD drive by passes it and goes straight to Windows. On a side note i HATE windows 7 I've always had linux and never had a problem installing it on windows vista and lower and I NEVER needed a 2nd partition for it, it installed right on my primary HD and ran just fine. So if anyone could help me with my problem it would be greatly apreciated

I've seen reports (recently) of people who can install wubi on one machine with a CD, but getting errno 22 on another with the same CD. Therefore it appears to be hardware related. The workaround is to install with wubi.exe and the .iso in the same folder on the hard drive.

---

