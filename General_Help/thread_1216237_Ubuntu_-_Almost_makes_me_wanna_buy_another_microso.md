---
title: "Ubuntu - Almost makes me wanna buy another microsoft OS"
date: 2009-07-18
forum: General Help
---

### Post by drewzor on 2009-07-18
[FONT="Arial"][SIZE="1"][SIZE="2"]Hi, My name is Andrew and I've tried a few different types of linux over the past two years.
When it does load on the rare occasion, none of my peripherals work and I have found it to be difficult to understand how to resolve hardware issues.

Most recently, in a misguided effort to shake my Microsoft commitments, I tried downloading the latest Gnome Ubuntu 9.04

I chose the option to load the program within windows but after installing I receive an error - Permission Denied ??

It writes a log file which I will paste below.[FONT="Arial"][SIZE="1"]
07-18 15:41 INFO   root: === wubi 9.04 rev128 ===
07-18 15:41 DEBUG  root: Logfile is c:\docume~1\drewzor\locals~1\temp\wubi-9.04-rev128.log
07-18 15:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
07-18 15:41 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\data
07-18 15:41 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\bin\7z.exe
07-18 15:41 DEBUG  CommonBackend: Fetching basic info...
07-18 15:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe
07-18 15:41 DEBUG  CommonBackend: platform=win32
07-18 15:41 DEBUG  CommonBackend: osname=nt
07-18 15:41 DEBUG  CommonBackend: language=en_AU
07-18 15:41 DEBUG  CommonBackend: encoding=cp1252
07-18 15:41 DEBUG  WindowsBackend: arch=i386
07-18 15:41 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\data\isolist.ini
07-18 15:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-18 15:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-18 15:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-18 15:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-18 15:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-18 15:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-18 15:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-18 15:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-18 15:41 DEBUG  WindowsBackend: Fetching host info...
07-18 15:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-18 15:41 DEBUG  WindowsBackend: windows version=xp
07-18 15:41 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-18 15:41 DEBUG  WindowsBackend: windows_sp=Service Pack 3, v.3264
07-18 15:41 DEBUG  WindowsBackend: windows_build=2600
07-18 15:41 DEBUG  WindowsBackend: gmt=10
07-18 15:41 DEBUG  WindowsBackend: country=AU
07-18 15:41 DEBUG  WindowsBackend: timezone=Australia/Sydney
07-18 15:41 DEBUG  WindowsBackend: windows_username=Drewzor
07-18 15:41 DEBUG  WindowsBackend: user_full_name=Drewzor
07-18 15:41 DEBUG  WindowsBackend: user_directory=Drewzor
07-18 15:41 DEBUG  WindowsBackend: windows_language_code=1033
07-18 15:41 DEBUG  WindowsBackend: windows_language=English
07-18 15:41 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.80GHz
07-18 15:41 DEBUG  WindowsBackend: bootloader=xp
07-18 15:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27943.5390625 mb free )
07-18 15:41 DEBUG  WindowsBackend: drive=Drive(C: hd 27943.5390625 mb free )
07-18 15:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-18 15:41 DEBUG  WindowsBackend: drive=Drive(E: hd 122941.574219 mb free ntfs)
07-18 15:41 DEBUG  WindowsBackend: drive=Drive(F: hd 25060.8320313 mb free ntfs)
07-18 15:41 DEBUG  WindowsBackend: drive=Drive(G: hd 689751.125 mb free fat32)
07-18 15:41 DEBUG  WindowsBackend: uninstaller_path=None
07-18 15:41 DEBUG  WindowsBackend: previous_target_dir=None
07-18 15:41 DEBUG  WindowsBackend: previous_distro_name=None
07-18 15:41 DEBUG  WindowsBackend: keyboard_id=67699721
07-18 15:41 DEBUG  WindowsBackend: keyboard_layout=au
07-18 15:41 DEBUG  WindowsBackend: keyboard_variant=
07-18 15:41 DEBUG  CommonBackend: locale=en_AU.UTF-8
07-18 15:41 DEBUG  WindowsBackend: total_memory_mb=1023.484375
07-18 15:41 DEBUG  CommonBackend: Searching ISOs on USB devices
07-18 15:41 DEBUG  CommonBackend: Searching for local CDs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Ubuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Ubuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Kubuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Kubuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Xubuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Xubuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Mythbuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp is a valid Mythbuntu CD
07-18 15:41 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl33B.tmp\casper\filesystem.squashfs
07-18 15:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 15:41 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-18 15:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-18 15:41 DEBUG  Distro: wrong arch: i386 != amd64
07-18 15:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 15:41 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-18 15:41 INFO   root: Running the CD menu...
07-18 15:41 DEBUG  WindowsFrontend: __init__...
07-18 15:41 DEBUG  WindowsFrontend: on_init...
07-18 15:41 INFO   root: CD menu finished
07-18 15:41 INFO   root: Running the installer...
07-18 15:42 INFO   WindowsFrontend: Operation cancelled
07-18 15:42 DEBUG  WindowsFrontend: frontend.quit
07-18 15:42 DEBUG  WindowsFrontend: frontend.on_quit
07-18 15:42 DEBUG  root: application.on_quit
07-18 15:42 INFO   root: sys.exit
07-18 15:47 INFO   root: === wubi 9.04 rev128 ===
07-18 15:47 DEBUG  root: Logfile is c:\docume~1\drewzor\locals~1\temp\wubi-9.04-rev128.log
07-18 15:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
07-18 15:47 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\data
07-18 15:47 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\bin\7z.exe
07-18 15:47 DEBUG  CommonBackend: Fetching basic info...
07-18 15:47 DEBUG  CommonBackend: original_exe=D:\wubi.exe
07-18 15:47 DEBUG  CommonBackend: platform=win32
07-18 15:47 DEBUG  CommonBackend: osname=nt
07-18 15:47 DEBUG  CommonBackend: language=en_AU
07-18 15:47 DEBUG  CommonBackend: encoding=cp1252
07-18 15:47 DEBUG  WindowsBackend: arch=i386
07-18 15:47 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\data\isolist.ini
07-18 15:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-18 15:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-18 15:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-18 15:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-18 15:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-18 15:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-18 15:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-18 15:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-18 15:47 DEBUG  WindowsBackend: Fetching host info...
07-18 15:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-18 15:47 DEBUG  WindowsBackend: windows version=xp
07-18 15:47 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-18 15:47 DEBUG  WindowsBackend: windows_sp=Service Pack 3, v.3264
07-18 15:47 DEBUG  WindowsBackend: windows_build=2600
07-18 15:47 DEBUG  WindowsBackend: gmt=10
07-18 15:47 DEBUG  WindowsBackend: country=AU
07-18 15:47 DEBUG  WindowsBackend: timezone=Australia/Sydney
07-18 15:47 DEBUG  WindowsBackend: windows_username=Drewzor
07-18 15:47 DEBUG  WindowsBackend: user_full_name=Drewzor
07-18 15:47 DEBUG  WindowsBackend: user_directory=Drewzor
07-18 15:47 DEBUG  WindowsBackend: windows_language_code=1033
07-18 15:47 DEBUG  WindowsBackend: windows_language=English
07-18 15:47 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.80GHz
07-18 15:47 DEBUG  WindowsBackend: bootloader=xp
07-18 15:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27972.2265625 mb free )
07-18 15:47 DEBUG  WindowsBackend: drive=Drive(C: hd 27972.2265625 mb free )
07-18 15:47 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-18 15:47 DEBUG  WindowsBackend: drive=Drive(E: hd 122941.574219 mb free ntfs)
07-18 15:47 DEBUG  WindowsBackend: drive=Drive(F: hd 25060.8320313 mb free ntfs)
07-18 15:47 DEBUG  WindowsBackend: drive=Drive(G: hd 689751.125 mb free fat32)
07-18 15:47 DEBUG  WindowsBackend: uninstaller_path=None
07-18 15:47 DEBUG  WindowsBackend: previous_target_dir=None
07-18 15:47 DEBUG  WindowsBackend: previous_distro_name=None
07-18 15:47 DEBUG  WindowsBackend: keyboard_id=67699721
07-18 15:47 DEBUG  WindowsBackend: keyboard_layout=au
07-18 15:47 DEBUG  WindowsBackend: keyboard_variant=
07-18 15:47 DEBUG  CommonBackend: locale=en_AU.UTF-8
07-18 15:47 DEBUG  WindowsBackend: total_memory_mb=1023.484375
07-18 15:47 DEBUG  CommonBackend: Searching ISOs on USB devices
07-18 15:47 DEBUG  CommonBackend: Searching for local CDs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Ubuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Ubuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Kubuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Kubuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Xubuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Xubuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Mythbuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp is a valid Mythbuntu CD
07-18 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\casper\filesystem.squashfs
07-18 15:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 15:47 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-18 15:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-18 15:47 DEBUG  Distro: wrong arch: i386 != amd64
07-18 15:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 15:47 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-18 15:47 INFO   root: Running the CD menu...
07-18 15:47 DEBUG  WindowsFrontend: __init__...
07-18 15:47 DEBUG  WindowsFrontend: on_init...
07-18 15:47 INFO   root: CD menu finished
07-18 15:47 INFO   root: Running the installer...
07-18 15:48 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=15000MB, distro_name=Ubuntu, language=English, username=drewzor
07-18 15:48 INFO   root: Received settings
07-18 15:48 DEBUG  TaskList: # Running tasklist...
07-18 15:48 DEBUG  TaskList: ## Running select_target_dir...
07-18 15:48 INFO   WindowsBackend: Installing into E:\ubuntu
07-18 15:48 DEBUG  TaskList: ## Finished select_target_dir
07-18 15:48 DEBUG  TaskList: ## Running create_dir_structure...
07-18 15:48 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-18 15:48 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-18 15:48 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-18 15:48 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-18 15:48 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-18 15:48 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-18 15:48 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-18 15:48 DEBUG  TaskList: ## Finished create_dir_structure
07-18 15:48 DEBUG  TaskList: ## Running uncompress_target_dir...
07-18 15:48 DEBUG  TaskList: ## Finished uncompress_target_dir
07-18 15:48 DEBUG  TaskList: ## Running create_uninstaller...
07-18 15:48 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-18 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-18 15:48 DEBUG  TaskList: ## Finished create_uninstaller
07-18 15:48 DEBUG  TaskList: ## Running copy_installation_files...
07-18 15:48 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-18 15:48 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\winboot -> E:\ubuntu\winboot
07-18 15:48 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl341.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-18 15:48 DEBUG  TaskList: ## Finished copy_installation_files
07-18 15:48 DEBUG  TaskList: ## Running get_iso...
07-18 15:48 DEBUG  TaskList: New task copy_file
07-18 15:48 DEBUG  TaskList: ### Running copy_file...
07-18 15:51 DEBUG  TaskList: ### Finished copy_file
07-18 15:51 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-18 15:51 DEBUG  TaskList: # Cancelling tasklist
07-18 15:51 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-18 15:51 DEBUG  TaskList: New task check_iso
07-18 15:51 DEBUG  CommonBackend: Searching for local ISO
07-18 15:51 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-18 15:51 DEBUG  TaskList: New task get_metalink
07-18 15:51 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-18 15:51 DEBUG  TaskList: # Cancelling tasklist
07-18 15:51 DEBUG  TaskList: # Finished tasklist
07-18 16:08 INFO   root: === wubi 9.04 rev128 ===
07-18 16:08 DEBUG  root: Logfile is c:\docume~1\drewzor\locals~1\temp\wubi-9.04-rev128.log
07-18 16:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
07-18 16:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\data
07-18 16:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\bin\7z.exe
07-18 16:08 DEBUG  CommonBackend: Fetching basic info...
07-18 16:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
07-18 16:08 DEBUG  CommonBackend: platform=win32
07-18 16:08 DEBUG  CommonBackend: osname=nt
07-18 16:08 DEBUG  CommonBackend: language=en_AU
07-18 16:08 DEBUG  CommonBackend: encoding=cp1252
07-18 16:08 DEBUG  WindowsBackend: arch=i386
07-18 16:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\data\isolist.ini
07-18 16:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-18 16:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-18 16:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-18 16:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-18 16:08 DEBUG  WindowsBackend: Fetching host info...
07-18 16:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-18 16:08 DEBUG  WindowsBackend: windows version=xp
07-18 16:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-18 16:08 DEBUG  WindowsBackend: windows_sp=Service Pack 3, v.3264
07-18 16:08 DEBUG  WindowsBackend: windows_build=2600
07-18 16:08 DEBUG  WindowsBackend: gmt=10
07-18 16:08 DEBUG  WindowsBackend: country=AU
07-18 16:08 DEBUG  WindowsBackend: timezone=Australia/Sydney
07-18 16:08 DEBUG  WindowsBackend: windows_username=Drewzor
07-18 16:08 DEBUG  WindowsBackend: user_full_name=Drewzor
07-18 16:08 DEBUG  WindowsBackend: user_directory=Drewzor
07-18 16:08 DEBUG  WindowsBackend: windows_language_code=1033
07-18 16:08 DEBUG  WindowsBackend: windows_language=English
07-18 16:08 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.80GHz
07-18 16:08 DEBUG  WindowsBackend: bootloader=xp
07-18 16:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27970.5351563 mb free )
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(C: hd 27970.5351563 mb free )
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(E: hd 122241.660156 mb free ntfs)
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(F: hd 25060.8320313 mb free ntfs)
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(G: hd 689751.125 mb free fat32)
07-18 16:08 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-18 16:08 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-18 16:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-18 16:08 DEBUG  WindowsBackend: keyboard_id=67699721
07-18 16:08 DEBUG  WindowsBackend: keyboard_layout=au
07-18 16:08 DEBUG  WindowsBackend: keyboard_variant=
07-18 16:08 DEBUG  CommonBackend: locale=en_AU.UTF-8
07-18 16:08 DEBUG  WindowsBackend: total_memory_mb=1023.484375
07-18 16:08 DEBUG  CommonBackend: Searching ISOs on USB devices
07-18 16:08 DEBUG  CommonBackend: Searching for local CDs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Ubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Ubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Kubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Kubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Xubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Xubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Mythbuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Mythbuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 16:08 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-18 16:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-18 16:08 DEBUG  Distro: wrong arch: i386 != amd64
07-18 16:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 16:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-18 16:08 INFO   root: Running the CD menu...
07-18 16:08 DEBUG  WindowsFrontend: __init__...
07-18 16:08 DEBUG  WindowsFrontend: on_init...
07-18 16:08 INFO   root: CD menu finished
07-18 16:08 INFO   root: Already installed, running the uninstaller...
07-18 16:08 INFO   root: Running the uninstaller...
07-18 16:08 INFO   CommonBackend: This is the uninstaller running
07-18 16:08 INFO   root: Received settings
07-18 16:08 DEBUG  TaskList: # Running tasklist...
07-18 16:08 DEBUG  TaskList: ## Running Backup ISO...
07-18 16:08 DEBUG  TaskList: ## Finished Backup ISO
07-18 16:08 DEBUG  TaskList: ## Running Remove bootloader entry...
07-18 16:08 ERROR  WindowsBackend: Cannot find bcdedit
07-18 16:08 DEBUG  WindowsBackend: undo_bootini C:
07-18 16:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 27970.5351563 mb free )
07-18 16:08 DEBUG  WindowsBackend: undo_bootini E:
07-18 16:08 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 122241.660156 mb free ntfs)
07-18 16:08 DEBUG  WindowsBackend: undo_bootini F:
07-18 16:08 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 25060.8320313 mb free ntfs)
07-18 16:08 DEBUG  WindowsBackend: undo_bootini G:
07-18 16:08 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 689751.125 mb free fat32)
07-18 16:08 DEBUG  TaskList: ## Finished Remove bootloader entry
07-18 16:08 DEBUG  TaskList: ## Running Remove target dir...
07-18 16:08 DEBUG  CommonBackend: Deleting E:\ubuntu
07-18 16:08 DEBUG  TaskList: ## Finished Remove target dir
07-18 16:08 DEBUG  TaskList: ## Running Remove registry key...
07-18 16:08 DEBUG  TaskList: ## Finished Remove registry key
07-18 16:08 DEBUG  TaskList: # Finished tasklist
07-18 16:08 INFO   root: Almost finished uninstalling
07-18 16:08 INFO   root: Finished uninstallation
07-18 16:08 DEBUG  CommonBackend: Fetching basic info...
07-18 16:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
07-18 16:08 DEBUG  CommonBackend: platform=win32
07-18 16:08 DEBUG  CommonBackend: osname=nt
07-18 16:08 DEBUG  CommonBackend: language=en_AU
07-18 16:08 DEBUG  CommonBackend: encoding=cp1252
07-18 16:08 DEBUG  WindowsBackend: arch=i386
07-18 16:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\data\isolist.ini
07-18 16:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-18 16:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-18 16:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-18 16:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-18 16:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-18 16:08 DEBUG  WindowsBackend: Fetching host info...
07-18 16:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-18 16:08 DEBUG  WindowsBackend: windows version=xp
07-18 16:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-18 16:08 DEBUG  WindowsBackend: windows_sp=Service Pack 3, v.3264
07-18 16:08 DEBUG  WindowsBackend: windows_build=2600
07-18 16:08 DEBUG  WindowsBackend: gmt=10
07-18 16:08 DEBUG  WindowsBackend: country=AU
07-18 16:08 DEBUG  WindowsBackend: timezone=Australia/Sydney
07-18 16:08 DEBUG  WindowsBackend: windows_username=Drewzor
07-18 16:08 DEBUG  WindowsBackend: user_full_name=Drewzor
07-18 16:08 DEBUG  WindowsBackend: user_directory=Drewzor
07-18 16:08 DEBUG  WindowsBackend: windows_language_code=1033
07-18 16:08 DEBUG  WindowsBackend: windows_language=English
07-18 16:08 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.80GHz
07-18 16:08 DEBUG  WindowsBackend: bootloader=xp
07-18 16:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27970.4453125 mb free )
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(C: hd 27970.4453125 mb free )
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(E: hd 122941.574219 mb free ntfs)
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(F: hd 25060.8320313 mb free ntfs)
07-18 16:08 DEBUG  WindowsBackend: drive=Drive(G: hd 689751.125 mb free fat32)
07-18 16:08 DEBUG  WindowsBackend: uninstaller_path=None
07-18 16:08 DEBUG  WindowsBackend: previous_target_dir=None
07-18 16:08 DEBUG  WindowsBackend: previous_distro_name=None
07-18 16:08 DEBUG  WindowsBackend: keyboard_id=67699721
07-18 16:08 DEBUG  WindowsBackend: keyboard_layout=au
07-18 16:08 DEBUG  WindowsBackend: keyboard_variant=
07-18 16:08 DEBUG  CommonBackend: locale=en_AU.UTF-8
07-18 16:08 DEBUG  WindowsBackend: total_memory_mb=1023.484375
07-18 16:08 DEBUG  CommonBackend: Searching ISOs on USB devices
07-18 16:08 DEBUG  CommonBackend: Searching for local CDs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Ubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Ubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Kubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Kubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Xubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Xubuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Mythbuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp is a valid Mythbuntu CD
07-18 16:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\casper\filesystem.squashfs
07-18 16:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 16:08 DEBUG  Distro: wrong arch: i386 != amd64
07-18 16:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-18 16:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-18 16:08 INFO   root: Running the installer...
07-18 16:09 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=15000MB, distro_name=Ubuntu, language=English, username=drewzor
07-18 16:09 INFO   root: Received settings
07-18 16:09 DEBUG  TaskList: # Running tasklist...
07-18 16:09 DEBUG  TaskList: ## Running select_target_dir...
07-18 16:09 INFO   WindowsBackend: Installing into E:\ubuntu
07-18 16:09 DEBUG  TaskList: ## Finished select_target_dir
07-18 16:09 DEBUG  TaskList: ## Running create_dir_structure...
07-18 16:09 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-18 16:09 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-18 16:09 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-18 16:09 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-18 16:09 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-18 16:09 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-18 16:09 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-18 16:09 DEBUG  TaskList: ## Finished create_dir_structure
07-18 16:09 DEBUG  TaskList: ## Running uncompress_target_dir...
07-18 16:09 DEBUG  TaskList: ## Finished uncompress_target_dir
07-18 16:09 DEBUG  TaskList: ## Running create_uninstaller...
07-18 16:09 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-18 16:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-18 16:09 DEBUG  TaskList: ## Finished create_uninstaller
07-18 16:09 DEBUG  TaskList: ## Running copy_installation_files...
07-18 16:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-18 16:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\winboot -> E:\ubuntu\winboot
07-18 16:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Drewzor\LOCALS~1\Temp\pyl345.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-18 16:09 DEBUG  TaskList: ## Finished copy_installation_files
07-18 16:09 DEBUG  TaskList: ## Running get_iso...
07-18 16:09 DEBUG  TaskList: New task copy_file
07-18 16:09 DEBUG  TaskList: ### Running copy_file...
07-18 16:11 DEBUG  TaskList: ### Finished copy_file
07-18 16:11 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-18 16:11 DEBUG  TaskList: # Cancelling tasklist
07-18 16:11 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-18 16:11 DEBUG  TaskList: New task check_iso
07-18 16:11 DEBUG  CommonBackend: Searching for local ISO
07-18 16:11 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-18 16:11 DEBUG  TaskList: New task get_metalink
07-18 16:11 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-18 16:11 DEBUG  TaskList: # Cancelling tasklist
07-18 16:11 DEBUG  TaskList: # Finished tasklist
[/SIZE][/FONT]

Can anyone tell me whats going on here? 
Please save me from Microsoft!![/SIZE][/SIZE][/FONT]

---

### Post by cooper77z on 2009-07-18
Can't really tell what's up with that list. But, buy a cheap computer and test out a full linux os with broadband. I am willing to guess you will be able to make it work.

---

### Post by qshop on 2009-07-18
wow this is one of the craziest things I've seen in a while

---

### Post by Short__Error on 2009-07-18
are you running off of a live cd or did you partion your drive????

---

### Post by niteshifter on 2009-07-18
Hi,

Significant clue was all those lines with "Windows backend" in them - it's a WUBI install:
> 07-18 16:08 INFO root: === wubi 9.04 rev128 ===

Keep in mind I'm no WUBI expert but I believe the OP is using the buggy one, [see this post]("http://ubuntuforums.org/showthread.php?t=1155817").

---

### Post by drewzor on 2009-07-18
Thanks for checking this one out, it does seem to be the bug #371264 
seems the solution is to download a new copy of 9.04 @ another 686mb of bandwidth :( 
I downloaded my copy from ubuntu's website but as a torrent.
I will try a direct download.

with the copy i have though,
I booted up as a live cd on my desktop but encountered some other issues. If you dont mind, it would be great to turn this thread into a walk through for a noob.

I'm very familiar with MS Windows but cannot yet understand the GUI...where is the equivalent to device manager in ubuntu?

As a live cd I have these problems on desktop;
1) no sound. 
And on laptop (HP PAVILIO ZE4103s) I have sound but no internet.
2)WG111V2 wireless adaptor drivers?

---

### Post by drewzor on 2009-07-18
Oh I just Ubuntu documentation so I will read up and come back more educated rather then hassle you guys on the small stuff. brb

---

### Post by robert shearer on 2009-07-18
This may be of help too.....
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by Risoh on 2009-07-18
I do believe that you should move from wubi to direct instalation  Here is how to partition and install:

[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition/](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition/)

---

