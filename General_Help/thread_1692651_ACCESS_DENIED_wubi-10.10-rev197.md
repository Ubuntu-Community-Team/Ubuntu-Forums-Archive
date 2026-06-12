---
title: "ACCESS DENIED wubi-10.10-rev197"
date: 2011-02-21
forum: General Help
---

### Post by pepperoni517 on 2011-02-21
Probably this is a repost but i cant solve this problem. I want to install ubuntu next to my Vista. The installation stops at like 75% and a problem pops up: 
Access Denied. For more information check:  wubi-10.10-rev197.
Cant do anything against it, and i cant even boot the cd at startup. cant even install the ubuntu cd booting helper software from the cd, because the same problem pops up. The same problem happened on my 2nd pc, where i wanted to install ubuntu next to a Windows XP sp3. Please help me someone. i also tryed to install it from a bootable USB but the same problem happened.
the file contains this:




11-03 11:44 INFO   root: === wubi 10.10 rev197 ===
11-03 11:44 DEBUG  root: Logfile is c:\users\jirka\appdata\local\temp\wubi-10.10-rev197.log
11-03 11:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-03 11:44 DEBUG  CommonBackend: data_dir=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\data
11-03 11:44 DEBUG  WindowsBackend: 7z=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\bin\7z.exe
11-03 11:44 DEBUG  CommonBackend: Fetching basic info...
11-03 11:44 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 11:44 DEBUG  CommonBackend: platform=win32
11-03 11:44 DEBUG  CommonBackend: osname=nt
11-03 11:44 DEBUG  CommonBackend: language=cs_CZ
11-03 11:44 DEBUG  CommonBackend: encoding=cp1250
11-03 11:44 DEBUG  WindowsBackend: arch=amd64
11-03 11:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\data\isolist.ini
11-03 11:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 11:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 11:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 11:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 11:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 11:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 11:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 11:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 11:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 11:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 11:44 DEBUG  WindowsBackend: Fetching host info...
11-03 11:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 11:44 DEBUG  WindowsBackend: windows version=vista
11-03 11:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 11:44 DEBUG  WindowsBackend: windows_sp=None
11-03 11:44 DEBUG  WindowsBackend: windows_build=7600
11-03 11:44 DEBUG  WindowsBackend: gmt=1
11-03 11:44 DEBUG  WindowsBackend: country=CZ
11-03 11:44 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 11:44 DEBUG  WindowsBackend: windows_username=Jirka
11-03 11:44 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 11:44 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 11:44 DEBUG  WindowsBackend: windows_language_code=1029
11-03 11:44 DEBUG  WindowsBackend: windows_language=Czech
11-03 11:44 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 11:44 DEBUG  WindowsBackend: bootloader=vista
11-03 11:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 123408.390625 mb free ntfs)
11-03 11:44 DEBUG  WindowsBackend: drive=Drive(C: hd 123408.390625 mb free ntfs)
11-03 11:44 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 11:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 11:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 11:44 DEBUG  WindowsBackend: uninstaller_path=None
11-03 11:44 DEBUG  WindowsBackend: previous_target_dir=None
11-03 11:44 DEBUG  WindowsBackend: previous_distro_name=None
11-03 11:44 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 11:44 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 11:44 DEBUG  WindowsBackend: keyboard_variant=
11-03 11:44 DEBUG  CommonBackend: python locale=('cs_CZ', 'cp1250')
11-03 11:44 DEBUG  CommonBackend: locale=cs_CZ.UTF-8
11-03 11:44 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 11:44 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 11:44 DEBUG  CommonBackend: Searching for local CDs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Ubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Ubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Ubuntu Netbook CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Kubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Kubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Kubuntu Netbook CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Xubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Xubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Mythbuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp is a valid Mythbuntu CD
11-03 11:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 11:44 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-03 11:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-03 11:44 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 11:44 INFO   root: Running the CD menu...
11-03 11:44 DEBUG  WindowsFrontend: __init__...
11-03 11:44 DEBUG  WindowsFrontend: on_init...
11-03 11:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:44 INFO   root: CD menu finished
11-03 11:44 INFO   root: Running the installer...
11-03 11:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=cs_CZ, locale=cs_CZ.UTF-8, username=jirka
11-03 11:46 INFO   root: Received settings
11-03 11:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:46 DEBUG  TaskList: # Running tasklist...
11-03 11:46 DEBUG  TaskList: ## Running select_target_dir...
11-03 11:46 INFO   WindowsBackend: Installing into C:\ubuntu
11-03 11:46 DEBUG  TaskList: ## Finished select_target_dir
11-03 11:46 DEBUG  TaskList: ## Running create_dir_structure...
11-03 11:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-03 11:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-03 11:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-03 11:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-03 11:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-03 11:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-03 11:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-03 11:46 DEBUG  TaskList: ## Finished create_dir_structure
11-03 11:46 DEBUG  TaskList: ## Running uncompress_target_dir...
11-03 11:46 DEBUG  TaskList: ## Finished uncompress_target_dir
11-03 11:46 DEBUG  TaskList: ## Running create_uninstaller...
11-03 11:46 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-03 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-03 11:46 DEBUG  TaskList: ## Finished create_uninstaller
11-03 11:46 DEBUG  TaskList: ## Running copy_installation_files...
11-03 11:46 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-03 11:46 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\winboot -> C:\ubuntu\winboot
11-03 11:46 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pylE498.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-03 11:46 DEBUG  TaskList: ## Finished copy_installation_files
11-03 11:46 DEBUG  TaskList: ## Running get_iso...
11-03 11:46 DEBUG  TaskList: New task copy_file
11-03 11:46 DEBUG  TaskList: ### Running copy_file...
11-03 11:51 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 11:51 DEBUG  TaskList: # Cancelling tasklist
11-03 11:51 DEBUG  TaskList: New task check_iso
11-03 11:51 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 11:51 DEBUG  CommonBackend: Searching for local ISO
11-03 11:51 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-03 11:51 DEBUG  TaskList: New task get_metalink
11-03 11:51 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-03 11:51 DEBUG  TaskList: # Cancelling tasklist
11-03 11:51 DEBUG  TaskList: # Finished tasklist
11-03 11:51 INFO   root: === wubi 10.10 rev197 ===
11-03 11:51 DEBUG  root: Logfile is c:\users\jirka\appdata\local\temp\wubi-10.10-rev197.log
11-03 11:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-03 11:51 DEBUG  CommonBackend: data_dir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\data
11-03 11:51 DEBUG  WindowsBackend: 7z=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\bin\7z.exe
11-03 11:51 DEBUG  CommonBackend: Fetching basic info...
11-03 11:51 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 11:51 DEBUG  CommonBackend: platform=win32
11-03 11:51 DEBUG  CommonBackend: osname=nt
11-03 11:51 DEBUG  CommonBackend: language=cs_CZ
11-03 11:51 DEBUG  CommonBackend: encoding=cp1250
11-03 11:51 DEBUG  WindowsBackend: arch=amd64
11-03 11:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\data\isolist.ini
11-03 11:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 11:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 11:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 11:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 11:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 11:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 11:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 11:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 11:51 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 11:51 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 11:51 DEBUG  WindowsBackend: Fetching host info...
11-03 11:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 11:51 DEBUG  WindowsBackend: windows version=vista
11-03 11:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 11:51 DEBUG  WindowsBackend: windows_sp=None
11-03 11:51 DEBUG  WindowsBackend: windows_build=7600
11-03 11:51 DEBUG  WindowsBackend: gmt=1
11-03 11:51 DEBUG  WindowsBackend: country=CZ
11-03 11:51 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 11:51 DEBUG  WindowsBackend: windows_username=Jirka
11-03 11:51 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 11:51 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 11:51 DEBUG  WindowsBackend: windows_language_code=1029
11-03 11:51 DEBUG  WindowsBackend: windows_language=Czech
11-03 11:51 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 11:51 DEBUG  WindowsBackend: bootloader=vista
11-03 11:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122292.296875 mb free ntfs)
11-03 11:51 DEBUG  WindowsBackend: drive=Drive(C: hd 122292.296875 mb free ntfs)
11-03 11:51 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 11:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 11:51 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 11:51 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-03 11:51 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-03 11:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 11:51 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 11:51 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 11:51 DEBUG  WindowsBackend: keyboard_variant=
11-03 11:51 DEBUG  CommonBackend: python locale=('cs_CZ', 'cp1250')
11-03 11:51 DEBUG  CommonBackend: locale=cs_CZ.UTF-8
11-03 11:51 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 11:51 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 11:51 DEBUG  CommonBackend: Searching for local CDs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Ubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Ubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Ubuntu Netbook CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Kubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Kubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Kubuntu Netbook CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Xubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Xubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Mythbuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Mythbuntu CD
11-03 11:51 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 11:51 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-03 11:51 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-03 11:51 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 11:51 INFO   root: Running the CD menu...
11-03 11:51 DEBUG  WindowsFrontend: __init__...
11-03 11:51 DEBUG  WindowsFrontend: on_init...
11-03 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:51 INFO   root: CD menu finished
11-03 11:51 INFO   root: Already installed, running the uninstaller...
11-03 11:51 INFO   root: Running the uninstaller...
11-03 11:51 INFO   CommonBackend: This is the uninstaller running
11-03 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:52 INFO   root: Received settings
11-03 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:52 DEBUG  TaskList: # Running tasklist...
11-03 11:52 DEBUG  TaskList: ## Running Zálohovat ISO...
11-03 11:52 DEBUG  TaskList: ## Finished Zálohovat ISO
11-03 11:52 DEBUG  TaskList: ## Running Odstranit položku zavad&#283;&#269;e...
11-03 11:52 DEBUG  WindowsBackend: Could not find bcd id
11-03 11:52 DEBUG  WindowsBackend: undo_bootini C:
11-03 11:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 122292.296875 mb free ntfs)
11-03 11:52 DEBUG  WindowsBackend: undo_bootini D:
11-03 11:52 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 34651.2070313 mb free ntfs)
11-03 11:52 DEBUG  TaskList: ## Finished Odstranit položku zavad&#283;&#269;e
11-03 11:52 DEBUG  TaskList: ## Running Odstranit cílovou složku...
11-03 11:52 DEBUG  CommonBackend: Deleting C:\ubuntu
11-03 11:52 DEBUG  TaskList: ## Finished Odstranit cílovou složku
11-03 11:52 DEBUG  TaskList: ## Running Odstranit klí&#269;e registru...
11-03 11:52 DEBUG  TaskList: ## Finished Odstranit klí&#269;e registru
11-03 11:52 DEBUG  TaskList: # Finished tasklist
11-03 11:52 INFO   root: Almost finished uninstalling
11-03 11:52 INFO   root: Finished uninstallation
11-03 11:52 DEBUG  CommonBackend: Fetching basic info...
11-03 11:52 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 11:52 DEBUG  CommonBackend: platform=win32
11-03 11:52 DEBUG  CommonBackend: osname=nt
11-03 11:52 DEBUG  WindowsBackend: arch=amd64
11-03 11:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\data\isolist.ini
11-03 11:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 11:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 11:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 11:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 11:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 11:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 11:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 11:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 11:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 11:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 11:52 DEBUG  WindowsBackend: Fetching host info...
11-03 11:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 11:52 DEBUG  WindowsBackend: windows version=vista
11-03 11:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 11:52 DEBUG  WindowsBackend: windows_sp=None
11-03 11:52 DEBUG  WindowsBackend: windows_build=7600
11-03 11:52 DEBUG  WindowsBackend: gmt=1
11-03 11:52 DEBUG  WindowsBackend: country=CZ
11-03 11:52 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 11:52 DEBUG  WindowsBackend: windows_username=Jirka
11-03 11:52 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 11:52 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 11:52 DEBUG  WindowsBackend: windows_language_code=1029
11-03 11:52 DEBUG  WindowsBackend: windows_language=Czech
11-03 11:52 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 11:52 DEBUG  WindowsBackend: bootloader=vista
11-03 11:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122964.761719 mb free ntfs)
11-03 11:52 DEBUG  WindowsBackend: drive=Drive(C: hd 122964.761719 mb free ntfs)
11-03 11:52 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 11:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 11:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 11:52 DEBUG  WindowsBackend: uninstaller_path=None
11-03 11:52 DEBUG  WindowsBackend: previous_target_dir=None
11-03 11:52 DEBUG  WindowsBackend: previous_distro_name=None
11-03 11:52 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 11:52 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 11:52 DEBUG  WindowsBackend: keyboard_variant=
11-03 11:52 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 11:52 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 11:52 DEBUG  CommonBackend: Searching for local CDs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Ubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Ubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Ubuntu Netbook CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Kubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Kubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Kubuntu Netbook CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Xubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Xubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Mythbuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp is a valid Mythbuntu CD
11-03 11:52 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 11:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 11:52 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 11:52 INFO   root: Running the installer...
11-03 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:52 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=cs_CZ, locale=cs_CZ.UTF-8, username=jirka
11-03 11:52 INFO   root: Received settings
11-03 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 11:52 DEBUG  TaskList: # Running tasklist...
11-03 11:52 DEBUG  TaskList: ## Running select_target_dir...
11-03 11:52 INFO   WindowsBackend: Installing into C:\ubuntu
11-03 11:52 DEBUG  TaskList: ## Finished select_target_dir
11-03 11:52 DEBUG  TaskList: ## Running create_dir_structure...
11-03 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-03 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-03 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-03 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-03 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-03 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-03 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-03 11:52 DEBUG  TaskList: ## Finished create_dir_structure
11-03 11:52 DEBUG  TaskList: ## Running uncompress_target_dir...
11-03 11:52 DEBUG  TaskList: ## Finished uncompress_target_dir
11-03 11:52 DEBUG  TaskList: ## Running create_uninstaller...
11-03 11:52 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-03 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-03 11:52 DEBUG  TaskList: ## Finished create_uninstaller
11-03 11:52 DEBUG  TaskList: ## Running copy_installation_files...
11-03 11:52 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-03 11:52 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\winboot -> C:\ubuntu\winboot
11-03 11:52 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pylE8EB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-03 11:52 DEBUG  TaskList: ## Finished copy_installation_files
11-03 11:52 DEBUG  TaskList: ## Running get_iso...
11-03 11:52 DEBUG  TaskList: New task copy_file
11-03 11:52 DEBUG  TaskList: ### Running copy_file...
11-03 12:12 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 12:12 DEBUG  TaskList: # Cancelling tasklist
11-03 12:12 DEBUG  TaskList: New task check_iso
11-03 12:12 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 12:12 DEBUG  CommonBackend: Searching for local ISO
11-03 12:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-03 12:12 DEBUG  TaskList: New task get_metalink
11-03 12:12 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-03 12:12 DEBUG  TaskList: # Cancelling tasklist
11-03 12:12 DEBUG  TaskList: # Finished tasklist
11-03 12:13 INFO   root: === wubi 10.10 rev197 ===
11-03 12:13 DEBUG  root: Logfile is c:\users\jirka\appdata\local\temp\wubi-10.10-rev197.log
11-03 12:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-03 12:13 DEBUG  CommonBackend: data_dir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\data
11-03 12:13 DEBUG  WindowsBackend: 7z=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\bin\7z.exe
11-03 12:13 DEBUG  CommonBackend: Fetching basic info...
11-03 12:13 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 12:13 DEBUG  CommonBackend: platform=win32
11-03 12:13 DEBUG  CommonBackend: osname=nt
11-03 12:13 DEBUG  CommonBackend: language=cs_CZ
11-03 12:13 DEBUG  CommonBackend: encoding=cp1250
11-03 12:13 DEBUG  WindowsBackend: arch=amd64
11-03 12:13 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\data\isolist.ini
11-03 12:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 12:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 12:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 12:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 12:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 12:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 12:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 12:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 12:13 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 12:13 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 12:13 DEBUG  WindowsBackend: Fetching host info...
11-03 12:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 12:13 DEBUG  WindowsBackend: windows version=vista
11-03 12:13 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 12:13 DEBUG  WindowsBackend: windows_sp=None
11-03 12:13 DEBUG  WindowsBackend: windows_build=7600
11-03 12:13 DEBUG  WindowsBackend: gmt=1
11-03 12:13 DEBUG  WindowsBackend: country=CZ
11-03 12:13 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 12:13 DEBUG  WindowsBackend: windows_username=Jirka
11-03 12:13 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 12:13 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 12:13 DEBUG  WindowsBackend: windows_language_code=1029
11-03 12:13 DEBUG  WindowsBackend: windows_language=Czech
11-03 12:13 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 12:13 DEBUG  WindowsBackend: bootloader=vista
11-03 12:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122289.804688 mb free ntfs)
11-03 12:13 DEBUG  WindowsBackend: drive=Drive(C: hd 122289.804688 mb free ntfs)
11-03 12:13 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 12:13 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 12:13 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 12:13 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-03 12:13 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-03 12:13 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 12:13 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 12:13 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 12:13 DEBUG  WindowsBackend: keyboard_variant=
11-03 12:13 DEBUG  CommonBackend: python locale=('cs_CZ', 'cp1250')
11-03 12:13 DEBUG  CommonBackend: locale=cs_CZ.UTF-8
11-03 12:13 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 12:13 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 12:13 DEBUG  CommonBackend: Searching for local CDs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Ubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Ubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Ubuntu Netbook CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Kubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Kubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Kubuntu Netbook CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Xubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Xubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Mythbuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Mythbuntu CD
11-03 12:13 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 12:13 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-03 12:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-03 12:13 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 12:13 INFO   root: Running the CD menu...
11-03 12:13 DEBUG  WindowsFrontend: __init__...
11-03 12:13 DEBUG  WindowsFrontend: on_init...
11-03 12:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:14 INFO   root: CD menu finished
11-03 12:14 INFO   root: Already installed, running the uninstaller...
11-03 12:14 INFO   root: Running the uninstaller...
11-03 12:14 INFO   CommonBackend: This is the uninstaller running
11-03 12:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:14 INFO   root: Received settings
11-03 12:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:14 DEBUG  TaskList: # Running tasklist...
11-03 12:14 DEBUG  TaskList: ## Running Zálohovat ISO...
11-03 12:14 DEBUG  TaskList: ## Finished Zálohovat ISO
11-03 12:14 DEBUG  TaskList: ## Running Odstranit položku zavad&#283;&#269;e...
11-03 12:14 DEBUG  WindowsBackend: Could not find bcd id
11-03 12:14 DEBUG  WindowsBackend: undo_bootini C:
11-03 12:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 122289.804688 mb free ntfs)
11-03 12:14 DEBUG  WindowsBackend: undo_bootini D:
11-03 12:14 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 34651.2070313 mb free ntfs)
11-03 12:14 DEBUG  TaskList: ## Finished Odstranit položku zavad&#283;&#269;e
11-03 12:14 DEBUG  TaskList: ## Running Odstranit cílovou složku...
11-03 12:14 DEBUG  CommonBackend: Deleting C:\ubuntu
11-03 12:14 DEBUG  TaskList: ## Finished Odstranit cílovou složku
11-03 12:14 DEBUG  TaskList: ## Running Odstranit klí&#269;e registru...
11-03 12:14 DEBUG  TaskList: ## Finished Odstranit klí&#269;e registru
11-03 12:14 DEBUG  TaskList: # Finished tasklist
11-03 12:14 INFO   root: Almost finished uninstalling
11-03 12:14 INFO   root: Finished uninstallation
11-03 12:14 DEBUG  CommonBackend: Fetching basic info...
11-03 12:14 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 12:14 DEBUG  CommonBackend: platform=win32
11-03 12:14 DEBUG  CommonBackend: osname=nt
11-03 12:14 DEBUG  WindowsBackend: arch=amd64
11-03 12:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\data\isolist.ini
11-03 12:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 12:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 12:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 12:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 12:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 12:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 12:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 12:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 12:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 12:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 12:14 DEBUG  WindowsBackend: Fetching host info...
11-03 12:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 12:14 DEBUG  WindowsBackend: windows version=vista
11-03 12:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 12:14 DEBUG  WindowsBackend: windows_sp=None
11-03 12:14 DEBUG  WindowsBackend: windows_build=7600
11-03 12:14 DEBUG  WindowsBackend: gmt=1
11-03 12:14 DEBUG  WindowsBackend: country=CZ
11-03 12:14 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 12:14 DEBUG  WindowsBackend: windows_username=Jirka
11-03 12:14 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 12:14 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 12:14 DEBUG  WindowsBackend: windows_language_code=1029
11-03 12:14 DEBUG  WindowsBackend: windows_language=Czech
11-03 12:14 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 12:14 DEBUG  WindowsBackend: bootloader=vista
11-03 12:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122962.386719 mb free ntfs)
11-03 12:14 DEBUG  WindowsBackend: drive=Drive(C: hd 122962.386719 mb free ntfs)
11-03 12:14 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 12:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 12:14 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 12:14 DEBUG  WindowsBackend: uninstaller_path=None
11-03 12:14 DEBUG  WindowsBackend: previous_target_dir=None
11-03 12:14 DEBUG  WindowsBackend: previous_distro_name=None
11-03 12:14 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 12:14 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 12:14 DEBUG  WindowsBackend: keyboard_variant=
11-03 12:14 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 12:14 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 12:14 DEBUG  CommonBackend: Searching for local CDs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Ubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Ubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Ubuntu Netbook CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Kubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Kubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Kubuntu Netbook CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Xubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Xubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Mythbuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp is a valid Mythbuntu CD
11-03 12:14 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 12:14 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 12:14 INFO   root: Running the installer...
11-03 12:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:14 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=cs_CZ, locale=cs_CZ.UTF-8, username=jirka
11-03 12:14 INFO   root: Received settings
11-03 12:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:14 DEBUG  TaskList: # Running tasklist...
11-03 12:14 DEBUG  TaskList: ## Running select_target_dir...
11-03 12:14 INFO   WindowsBackend: Installing into D:\ubuntu
11-03 12:14 DEBUG  TaskList: ## Finished select_target_dir
11-03 12:14 DEBUG  TaskList: ## Running create_dir_structure...
11-03 12:14 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-03 12:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-03 12:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-03 12:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-03 12:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-03 12:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-03 12:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-03 12:14 DEBUG  TaskList: ## Finished create_dir_structure
11-03 12:14 DEBUG  TaskList: ## Running uncompress_target_dir...
11-03 12:14 DEBUG  TaskList: ## Finished uncompress_target_dir
11-03 12:14 DEBUG  TaskList: ## Running create_uninstaller...
11-03 12:14 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-03 12:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-03 12:14 DEBUG  TaskList: ## Finished create_uninstaller
11-03 12:14 DEBUG  TaskList: ## Running copy_installation_files...
11-03 12:14 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-03 12:14 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\winboot -> D:\ubuntu\winboot
11-03 12:14 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl2AEB.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-03 12:14 DEBUG  TaskList: ## Finished copy_installation_files
11-03 12:14 DEBUG  TaskList: ## Running get_iso...
11-03 12:14 DEBUG  TaskList: New task copy_file
11-03 12:14 DEBUG  TaskList: ### Running copy_file...
11-03 12:34 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 12:34 DEBUG  TaskList: # Cancelling tasklist
11-03 12:34 DEBUG  TaskList: New task check_iso
11-03 12:34 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 12:34 DEBUG  CommonBackend: Searching for local ISO
11-03 12:34 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-03 12:34 DEBUG  TaskList: New task get_metalink
11-03 12:34 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-03 12:34 DEBUG  TaskList: # Cancelling tasklist
11-03 12:34 DEBUG  TaskList: # Finished tasklist
11-03 12:44 INFO   root: === wubi 10.10 rev197 ===
11-03 12:44 DEBUG  root: Logfile is c:\users\jirka\appdata\local\temp\wubi-10.10-rev197.log
11-03 12:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
11-03 12:44 DEBUG  CommonBackend: data_dir=C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\data
11-03 12:44 DEBUG  WindowsBackend: 7z=C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\bin\7z.exe
11-03 12:44 DEBUG  CommonBackend: Fetching basic info...
11-03 12:44 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
11-03 12:44 DEBUG  CommonBackend: platform=win32
11-03 12:44 DEBUG  CommonBackend: osname=nt
11-03 12:44 DEBUG  CommonBackend: language=cs_CZ
11-03 12:44 DEBUG  CommonBackend: encoding=cp1250
11-03 12:44 DEBUG  WindowsBackend: arch=amd64
11-03 12:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\data\isolist.ini
11-03 12:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 12:44 DEBUG  WindowsBackend: Fetching host info...
11-03 12:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 12:44 DEBUG  WindowsBackend: windows version=vista
11-03 12:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 12:44 DEBUG  WindowsBackend: windows_sp=None
11-03 12:44 DEBUG  WindowsBackend: windows_build=7600
11-03 12:44 DEBUG  WindowsBackend: gmt=1
11-03 12:44 DEBUG  WindowsBackend: country=CZ
11-03 12:44 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 12:44 DEBUG  WindowsBackend: windows_username=Jirka
11-03 12:44 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 12:44 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 12:44 DEBUG  WindowsBackend: windows_language_code=1029
11-03 12:44 DEBUG  WindowsBackend: windows_language=Czech
11-03 12:44 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 12:44 DEBUG  WindowsBackend: bootloader=vista
11-03 12:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122973.851563 mb free ntfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(C: hd 122973.851563 mb free ntfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(D: hd 33976.6171875 mb free ntfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 12:44 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-03 12:44 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-03 12:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 12:44 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 12:44 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 12:44 DEBUG  WindowsBackend: keyboard_variant=
11-03 12:44 DEBUG  CommonBackend: python locale=('cs_CZ', 'cp1250')
11-03 12:44 DEBUG  CommonBackend: locale=cs_CZ.UTF-8
11-03 12:44 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 12:44 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 12:44 DEBUG  CommonBackend: Searching for local CDs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Ubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Kubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-03 12:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-03 12:44 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 12:44 INFO   root: Running the uninstaller...
11-03 12:44 INFO   CommonBackend: This is the uninstaller running
11-03 12:44 DEBUG  WindowsFrontend: __init__...
11-03 12:44 DEBUG  WindowsFrontend: on_init...
11-03 12:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:44 INFO   root: Received settings
11-03 12:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl9C00.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:44 DEBUG  TaskList: # Running tasklist...
11-03 12:44 DEBUG  TaskList: ## Running Zálohovat ISO...
11-03 12:44 DEBUG  TaskList: ## Finished Zálohovat ISO
11-03 12:44 DEBUG  TaskList: ## Running Odstranit položku zavad&#283;&#269;e...
11-03 12:44 DEBUG  WindowsBackend: Could not find bcd id
11-03 12:44 DEBUG  WindowsBackend: undo_bootini C:
11-03 12:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 122973.851563 mb free ntfs)
11-03 12:44 DEBUG  WindowsBackend: undo_bootini D:
11-03 12:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 33976.6171875 mb free ntfs)
11-03 12:44 DEBUG  TaskList: ## Finished Odstranit položku zavad&#283;&#269;e
11-03 12:44 DEBUG  TaskList: ## Running Odstranit cílovou složku...
11-03 12:44 DEBUG  CommonBackend: Deleting D:\ubuntu
11-03 12:44 ERROR  TaskList: [Errno 13] Permission denied removing D:\ubuntu
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing D:\ubuntu
11-03 12:44 DEBUG  TaskList: # Cancelling tasklist
11-03 12:44 DEBUG  TaskList: # Finished tasklist
11-03 12:44 ERROR  root: [Errno 13] Permission denied removing D:\ubuntu
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing D:\ubuntu
11-03 12:44 INFO   root: === wubi 10.10 rev197 ===
11-03 12:44 DEBUG  root: Logfile is c:\users\jirka\appdata\local\temp\wubi-10.10-rev197.log
11-03 12:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-03 12:44 DEBUG  CommonBackend: data_dir=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\data
11-03 12:44 DEBUG  WindowsBackend: 7z=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\bin\7z.exe
11-03 12:44 DEBUG  CommonBackend: Fetching basic info...
11-03 12:44 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 12:44 DEBUG  CommonBackend: platform=win32
11-03 12:44 DEBUG  CommonBackend: osname=nt
11-03 12:44 DEBUG  CommonBackend: language=cs_CZ
11-03 12:44 DEBUG  CommonBackend: encoding=cp1250
11-03 12:44 DEBUG  WindowsBackend: arch=amd64
11-03 12:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\data\isolist.ini
11-03 12:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 12:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 12:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 12:44 DEBUG  WindowsBackend: Fetching host info...
11-03 12:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 12:44 DEBUG  WindowsBackend: windows version=vista
11-03 12:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 12:44 DEBUG  WindowsBackend: windows_sp=None
11-03 12:44 DEBUG  WindowsBackend: windows_build=7600
11-03 12:44 DEBUG  WindowsBackend: gmt=1
11-03 12:44 DEBUG  WindowsBackend: country=CZ
11-03 12:44 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 12:44 DEBUG  WindowsBackend: windows_username=Jirka
11-03 12:44 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 12:44 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 12:44 DEBUG  WindowsBackend: windows_language_code=1029
11-03 12:44 DEBUG  WindowsBackend: windows_language=Czech
11-03 12:44 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 12:44 DEBUG  WindowsBackend: bootloader=vista
11-03 12:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122972.410156 mb free ntfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(C: hd 122972.410156 mb free ntfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 12:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 12:44 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-03 12:44 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-03 12:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 12:44 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 12:44 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 12:44 DEBUG  WindowsBackend: keyboard_variant=
11-03 12:44 DEBUG  CommonBackend: python locale=('cs_CZ', 'cp1250')
11-03 12:44 DEBUG  CommonBackend: locale=cs_CZ.UTF-8
11-03 12:44 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 12:44 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 12:44 DEBUG  CommonBackend: Searching for local CDs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Ubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Kubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 12:44 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-03 12:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-03 12:44 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 12:44 INFO   root: Running the CD menu...
11-03 12:44 DEBUG  WindowsFrontend: __init__...
11-03 12:44 DEBUG  WindowsFrontend: on_init...
11-03 12:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:44 INFO   root: CD menu finished
11-03 12:44 INFO   root: Running the installer...
11-03 12:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:45 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=3000MB, distro_name=Ubuntu, language=cs_CZ, locale=cs_CZ.UTF-8, username=george
11-03 12:45 INFO   root: Received settings
11-03 12:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:45 DEBUG  TaskList: # Running tasklist...
11-03 12:45 DEBUG  TaskList: ## Running select_target_dir...
11-03 12:45 INFO   WindowsBackend: Installing into C:\ubuntu
11-03 12:45 DEBUG  TaskList: ## Finished select_target_dir
11-03 12:45 DEBUG  TaskList: ## Running create_dir_structure...
11-03 12:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-03 12:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-03 12:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-03 12:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-03 12:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-03 12:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-03 12:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-03 12:45 DEBUG  TaskList: ## Finished create_dir_structure
11-03 12:45 DEBUG  TaskList: ## Running uncompress_target_dir...
11-03 12:45 DEBUG  TaskList: ## Finished uncompress_target_dir
11-03 12:45 DEBUG  TaskList: ## Running create_uninstaller...
11-03 12:45 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-03 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-03 12:45 DEBUG  TaskList: ## Finished create_uninstaller
11-03 12:45 DEBUG  TaskList: ## Running copy_installation_files...
11-03 12:45 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-03 12:45 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\winboot -> C:\ubuntu\winboot
11-03 12:45 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl24AF.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-03 12:45 DEBUG  TaskList: ## Finished copy_installation_files
11-03 12:45 DEBUG  TaskList: ## Running get_iso...
11-03 12:45 DEBUG  TaskList: New task copy_file
11-03 12:45 DEBUG  TaskList: ### Running copy_file...
11-03 12:49 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 12:49 DEBUG  TaskList: # Cancelling tasklist
11-03 12:49 DEBUG  TaskList: New task check_iso
11-03 12:49 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 12:49 DEBUG  CommonBackend: Searching for local ISO
11-03 12:49 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-03 12:49 DEBUG  TaskList: New task get_metalink
11-03 12:49 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-03 12:49 DEBUG  TaskList: # Cancelling tasklist
11-03 12:49 DEBUG  TaskList: # Finished tasklist
11-03 12:50 INFO   root: === wubi 10.10 rev197 ===
11-03 12:50 DEBUG  root: Logfile is c:\users\jirka\appdata\local\temp\wubi-10.10-rev197.log
11-03 12:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-03 12:50 DEBUG  CommonBackend: data_dir=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\data
11-03 12:50 DEBUG  WindowsBackend: 7z=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\bin\7z.exe
11-03 12:50 DEBUG  CommonBackend: Fetching basic info...
11-03 12:50 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 12:50 DEBUG  CommonBackend: platform=win32
11-03 12:50 DEBUG  CommonBackend: osname=nt
11-03 12:50 DEBUG  CommonBackend: language=cs_CZ
11-03 12:50 DEBUG  CommonBackend: encoding=cp1250
11-03 12:50 DEBUG  WindowsBackend: arch=amd64
11-03 12:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\data\isolist.ini
11-03 12:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 12:50 DEBUG  WindowsBackend: Fetching host info...
11-03 12:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 12:50 DEBUG  WindowsBackend: windows version=vista
11-03 12:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 12:50 DEBUG  WindowsBackend: windows_sp=None
11-03 12:50 DEBUG  WindowsBackend: windows_build=7600
11-03 12:50 DEBUG  WindowsBackend: gmt=1
11-03 12:50 DEBUG  WindowsBackend: country=CZ
11-03 12:50 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 12:50 DEBUG  WindowsBackend: windows_username=Jirka
11-03 12:50 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 12:50 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 12:50 DEBUG  WindowsBackend: windows_language_code=1029
11-03 12:50 DEBUG  WindowsBackend: windows_language=Czech
11-03 12:50 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 12:50 DEBUG  WindowsBackend: bootloader=vista
11-03 12:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122296.261719 mb free ntfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(C: hd 122296.261719 mb free ntfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 12:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-03 12:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-03 12:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 12:50 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 12:50 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 12:50 DEBUG  WindowsBackend: keyboard_variant=
11-03 12:50 DEBUG  CommonBackend: python locale=('cs_CZ', 'cp1250')
11-03 12:50 DEBUG  CommonBackend: locale=cs_CZ.UTF-8
11-03 12:50 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 12:50 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 12:50 DEBUG  CommonBackend: Searching for local CDs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Ubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Kubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-03 12:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-03 12:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 12:50 INFO   root: Running the CD menu...
11-03 12:50 DEBUG  WindowsFrontend: __init__...
11-03 12:50 DEBUG  WindowsFrontend: on_init...
11-03 12:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:50 INFO   root: CD menu finished
11-03 12:50 INFO   root: Already installed, running the uninstaller...
11-03 12:50 INFO   root: Running the uninstaller...
11-03 12:50 INFO   CommonBackend: This is the uninstaller running
11-03 12:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:50 INFO   root: Received settings
11-03 12:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:50 DEBUG  TaskList: # Running tasklist...
11-03 12:50 DEBUG  TaskList: ## Running Zálohovat ISO...
11-03 12:50 DEBUG  TaskList: ## Finished Zálohovat ISO
11-03 12:50 DEBUG  TaskList: ## Running Odstranit položku zavad&#283;&#269;e...
11-03 12:50 DEBUG  WindowsBackend: Could not find bcd id
11-03 12:50 DEBUG  WindowsBackend: undo_bootini C:
11-03 12:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 122296.261719 mb free ntfs)
11-03 12:50 DEBUG  WindowsBackend: undo_bootini D:
11-03 12:50 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 34651.2070313 mb free ntfs)
11-03 12:50 DEBUG  TaskList: ## Finished Odstranit položku zavad&#283;&#269;e
11-03 12:50 DEBUG  TaskList: ## Running Odstranit cílovou složku...
11-03 12:50 DEBUG  CommonBackend: Deleting C:\ubuntu
11-03 12:50 DEBUG  TaskList: ## Finished Odstranit cílovou složku
11-03 12:50 DEBUG  TaskList: ## Running Odstranit klí&#269;e registru...
11-03 12:50 DEBUG  TaskList: ## Finished Odstranit klí&#269;e registru
11-03 12:50 DEBUG  TaskList: # Finished tasklist
11-03 12:50 INFO   root: Almost finished uninstalling
11-03 12:50 INFO   root: Finished uninstallation
11-03 12:50 DEBUG  CommonBackend: Fetching basic info...
11-03 12:50 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 12:50 DEBUG  CommonBackend: platform=win32
11-03 12:50 DEBUG  CommonBackend: osname=nt
11-03 12:50 DEBUG  WindowsBackend: arch=amd64
11-03 12:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\data\isolist.ini
11-03 12:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 12:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 12:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 12:50 DEBUG  WindowsBackend: Fetching host info...
11-03 12:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 12:50 DEBUG  WindowsBackend: windows version=vista
11-03 12:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 12:50 DEBUG  WindowsBackend: windows_sp=None
11-03 12:50 DEBUG  WindowsBackend: windows_build=7600
11-03 12:50 DEBUG  WindowsBackend: gmt=1
11-03 12:50 DEBUG  WindowsBackend: country=CZ
11-03 12:50 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 12:50 DEBUG  WindowsBackend: windows_username=Jirka
11-03 12:50 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 12:50 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 12:50 DEBUG  WindowsBackend: windows_language_code=1029
11-03 12:50 DEBUG  WindowsBackend: windows_language=Czech
11-03 12:50 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 12:50 DEBUG  WindowsBackend: bootloader=vista
11-03 12:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122970.835938 mb free ntfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(C: hd 122970.835938 mb free ntfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 12:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 12:50 DEBUG  WindowsBackend: uninstaller_path=None
11-03 12:50 DEBUG  WindowsBackend: previous_target_dir=None
11-03 12:50 DEBUG  WindowsBackend: previous_distro_name=None
11-03 12:50 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 12:50 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 12:50 DEBUG  WindowsBackend: keyboard_variant=
11-03 12:50 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 12:50 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 12:50 DEBUG  CommonBackend: Searching for local CDs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Ubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Kubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 12:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 12:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 12:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 12:50 INFO   root: Running the installer...
11-03 12:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl5012.tmp\translations, languages=['cs_CZ', 'cs']
11-03 12:50 INFO   WindowsFrontend: Operation cancelled
11-03 12:50 DEBUG  WindowsFrontend: frontend.quit
11-03 12:50 DEBUG  WindowsFrontend: frontend.on_quit
11-03 12:50 DEBUG  root: application.on_quit
11-03 12:50 INFO   root: sys.exit
11-03 13:16 INFO   root: === wubi 10.10 rev197 ===
11-03 13:16 DEBUG  root: Logfile is c:\users\jirka\appdata\local\temp\wubi-10.10-rev197.log
11-03 13:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-03 13:16 DEBUG  CommonBackend: data_dir=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\data
11-03 13:16 DEBUG  WindowsBackend: 7z=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\bin\7z.exe
11-03 13:16 DEBUG  CommonBackend: Fetching basic info...
11-03 13:16 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-03 13:16 DEBUG  CommonBackend: platform=win32
11-03 13:16 DEBUG  CommonBackend: osname=nt
11-03 13:16 DEBUG  CommonBackend: language=cs_CZ
11-03 13:16 DEBUG  CommonBackend: encoding=cp1250
11-03 13:16 DEBUG  WindowsBackend: arch=amd64
11-03 13:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\data\isolist.ini
11-03 13:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-03 13:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-03 13:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 13:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 13:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 13:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 13:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 13:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 13:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-03 13:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-03 13:16 DEBUG  WindowsBackend: Fetching host info...
11-03 13:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 13:16 DEBUG  WindowsBackend: windows version=vista
11-03 13:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 13:16 DEBUG  WindowsBackend: windows_sp=None
11-03 13:16 DEBUG  WindowsBackend: windows_build=7600
11-03 13:16 DEBUG  WindowsBackend: gmt=1
11-03 13:16 DEBUG  WindowsBackend: country=CZ
11-03 13:16 DEBUG  WindowsBackend: timezone=Europe/Prague
11-03 13:16 DEBUG  WindowsBackend: windows_username=Jirka
11-03 13:16 DEBUG  WindowsBackend: user_full_name=Jirka
11-03 13:16 DEBUG  WindowsBackend: user_directory=C:\Users\Jirka
11-03 13:16 DEBUG  WindowsBackend: windows_language_code=1029
11-03 13:16 DEBUG  WindowsBackend: windows_language=Czech
11-03 13:16 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
11-03 13:16 DEBUG  WindowsBackend: bootloader=vista
11-03 13:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122897.289063 mb free ntfs)
11-03 13:16 DEBUG  WindowsBackend: drive=Drive(C: hd 122897.289063 mb free ntfs)
11-03 13:16 DEBUG  WindowsBackend: drive=Drive(D: hd 34651.2070313 mb free ntfs)
11-03 13:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-03 13:16 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 13:16 DEBUG  WindowsBackend: uninstaller_path=None
11-03 13:16 DEBUG  WindowsBackend: previous_target_dir=None
11-03 13:16 DEBUG  WindowsBackend: previous_distro_name=None
11-03 13:16 DEBUG  WindowsBackend: keyboard_id=67437573
11-03 13:16 DEBUG  WindowsBackend: keyboard_layout=cz
11-03 13:16 DEBUG  WindowsBackend: keyboard_variant=
11-03 13:16 DEBUG  CommonBackend: python locale=('cs_CZ', 'cp1250')
11-03 13:16 DEBUG  CommonBackend: locale=cs_CZ.UTF-8
11-03 13:16 DEBUG  WindowsBackend: total_memory_mb=3838.046875
11-03 13:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 13:16 DEBUG  CommonBackend: Searching for local CDs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Ubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Ubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Ubuntu Netbook CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Kubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Kubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Kubuntu Netbook CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Xubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Xubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Mythbuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp is a valid Mythbuntu CD
11-03 13:16 DEBUG  Distro:     does not contain C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 13:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 13:16 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-03 13:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-03 13:16 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-03 13:16 INFO   root: Running the CD menu...
11-03 13:16 DEBUG  WindowsFrontend: __init__...
11-03 13:16 DEBUG  WindowsFrontend: on_init...
11-03 13:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\translations, languages=['cs_CZ', 'cs']
11-03 13:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\translations, languages=['cs_CZ', 'cs']
11-03 13:16 INFO   root: CD menu finished
11-03 13:16 INFO   root: Running the installer...
11-03 13:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\translations, languages=['cs_CZ', 'cs']
11-03 13:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\translations, languages=['cs_CZ', 'cs']
11-03 13:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=3000MB, distro_name=Ubuntu, language=cs_CZ, locale=cs_CZ.UTF-8, username=jirka
11-03 13:16 INFO   root: Received settings
11-03 13:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\translations, languages=['cs_CZ', 'cs']
11-03 13:16 DEBUG  TaskList: # Running tasklist...
11-03 13:16 DEBUG  TaskList: ## Running select_target_dir...
11-03 13:16 INFO   WindowsBackend: Installing into C:\ubuntu
11-03 13:16 DEBUG  TaskList: ## Finished select_target_dir
11-03 13:16 DEBUG  TaskList: ## Running create_dir_structure...
11-03 13:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-03 13:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-03 13:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-03 13:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-03 13:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-03 13:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-03 13:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-03 13:16 DEBUG  TaskList: ## Finished create_dir_structure
11-03 13:16 DEBUG  TaskList: ## Running uncompress_target_dir...
11-03 13:16 DEBUG  TaskList: ## Finished uncompress_target_dir
11-03 13:16 DEBUG  TaskList: ## Running create_uninstaller...
11-03 13:16 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-03 13:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-03 13:16 DEBUG  TaskList: ## Finished create_uninstaller
11-03 13:16 DEBUG  TaskList: ## Running copy_installation_files...
11-03 13:16 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-03 13:16 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\winboot -> C:\ubuntu\winboot
11-03 13:16 DEBUG  WindowsBackend: Copying C:\Users\Jirka\AppData\Local\Temp\pyl710A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-03 13:16 DEBUG  TaskList: ## Finished copy_installation_files
11-03 13:16 DEBUG  TaskList: ## Running get_iso...
11-03 13:16 DEBUG  TaskList: New task copy_file
11-03 13:16 DEBUG  TaskList: ### Running copy_file...
11-03 13:21 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 13:21 DEBUG  TaskList: # Cancelling tasklist
11-03 13:21 DEBUG  TaskList: New task check_iso
11-03 13:21 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-03 13:21 DEBUG  CommonBackend: Searching for local ISO
11-03 13:21 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-03 13:21 DEBUG  TaskList: New task get_metalink
11-03 13:21 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-03 13:21 DEBUG  TaskList: # Cancelling tasklist
11-03 13:21 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2011-02-21
It's complaining about Errno13 which can occur when the CD is bad - or for some optical drives. The easiest way to install Wubi is described here:[https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?]("https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?") (even if you have an internet connection).

---

