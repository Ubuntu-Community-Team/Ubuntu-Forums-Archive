---
title: "cant install ubuntu from CD wubi"
date: 2009-07-26
forum: General Help
---

### Post by mcmotto12 on 2009-07-26
hi i have a dell 1526 in which previously i installed ubuntu (i had vista). but now i cant install it... and now i have windows 7 RC .7100 
is windows 7 a problem?? 
heres the log
[html]http://rapidshare.com/files/260453815/wubi-9.04-rev128.log.html[/html]or 

07-26 22:11 INFO   root: === wubi 9.04 rev128 ===
07-26 22:11 DEBUG  root: Logfile is c:\users\gerardo\appdata\local\temp\wubi-9.04-rev128.log
07-26 22:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
07-26 22:11 DEBUG  CommonBackend: data_dir=C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\data
07-26 22:11 DEBUG  WindowsBackend: 7z=C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\bin\7z.exe
07-26 22:11 DEBUG  CommonBackend: Fetching basic info...
07-26 22:11 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-26 22:11 DEBUG  CommonBackend: platform=win32
07-26 22:11 DEBUG  CommonBackend: osname=nt
07-26 22:11 DEBUG  CommonBackend: language=es_MX
07-26 22:11 DEBUG  CommonBackend: encoding=cp1252
07-26 22:11 DEBUG  WindowsBackend: arch=amd64
07-26 22:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\data\isolist.ini
07-26 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 22:11 DEBUG  WindowsBackend: Fetching host info...
07-26 22:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 22:11 DEBUG  WindowsBackend: windows version=vista
07-26 22:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-26 22:11 DEBUG  WindowsBackend: windows_sp=None
07-26 22:11 DEBUG  WindowsBackend: windows_build=7100
07-26 22:11 DEBUG  WindowsBackend: gmt=-6
07-26 22:11 DEBUG  WindowsBackend: country=US
07-26 22:11 DEBUG  WindowsBackend: timezone=America/Chicago
07-26 22:11 DEBUG  WindowsBackend: windows_username=Gerardo
07-26 22:11 DEBUG  WindowsBackend: user_full_name=Gerardo
07-26 22:11 DEBUG  WindowsBackend: user_directory=Gerardo
07-26 22:11 DEBUG  WindowsBackend: windows_language_code=1034
07-26 22:11 DEBUG  WindowsBackend: windows_language=Spanish
07-26 22:11 DEBUG  WindowsBackend: processor_name=Mobile AMD Sempron(tm) Processor 3600+
07-26 22:11 DEBUG  WindowsBackend: bootloader=vista
07-26 22:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64247.1992188 mb free )
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(C: hd 64247.1992188 mb free )
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(D: hd 5541.91015625 mb free ntfs)
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-26 22:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-26 22:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-26 22:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-26 22:11 DEBUG  WindowsBackend: keyboard_id=134875146
07-26 22:11 DEBUG  WindowsBackend: keyboard_layout=us
07-26 22:11 DEBUG  WindowsBackend: keyboard_variant=
07-26 22:11 DEBUG  CommonBackend: locale=es_MX.UTF-8
07-26 22:11 DEBUG  WindowsBackend: total_memory_mb=1918.00390625
07-26 22:11 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 22:11 DEBUG  CommonBackend: Searching for local CDs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
07-26 22:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
07-26 22:11 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-26 22:11 INFO   root: Running the CD menu...
07-26 22:11 DEBUG  WindowsFrontend: __init__...
07-26 22:11 DEBUG  WindowsFrontend: on_init...
07-26 22:11 INFO   root: CD menu finished
07-26 22:11 INFO   root: Already installed, running the uninstaller...
07-26 22:11 INFO   root: Running the uninstaller...
07-26 22:11 INFO   CommonBackend: This is the uninstaller running
07-26 22:11 INFO   root: Received settings
07-26 22:11 DEBUG  TaskList: # Running tasklist...
07-26 22:11 DEBUG  TaskList: ## Running Backup ISO...
07-26 22:11 DEBUG  TaskList: ## Finished Backup ISO
07-26 22:11 DEBUG  TaskList: ## Running Remove bootloader entry...
07-26 22:11 DEBUG  WindowsBackend: Could not find bcd id
07-26 22:11 DEBUG  WindowsBackend: undo_bootini C:
07-26 22:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 64247.1992188 mb free )
07-26 22:11 DEBUG  WindowsBackend: undo_bootini D:
07-26 22:11 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 5541.91015625 mb free ntfs)
07-26 22:11 DEBUG  TaskList: ## Finished Remove bootloader entry
07-26 22:11 DEBUG  TaskList: ## Running Remove target dir...
07-26 22:11 DEBUG  CommonBackend: Deleting C:\ubuntu
07-26 22:11 DEBUG  TaskList: ## Finished Remove target dir
07-26 22:11 DEBUG  TaskList: ## Running Remove registry key...
07-26 22:11 DEBUG  TaskList: ## Finished Remove registry key
07-26 22:11 DEBUG  TaskList: # Finished tasklist
07-26 22:11 INFO   root: Almost finished uninstalling
07-26 22:11 INFO   root: Finished uninstallation
07-26 22:11 DEBUG  CommonBackend: Fetching basic info...
07-26 22:11 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-26 22:11 DEBUG  CommonBackend: platform=win32
07-26 22:11 DEBUG  CommonBackend: osname=nt
07-26 22:11 DEBUG  CommonBackend: language=es_MX
07-26 22:11 DEBUG  CommonBackend: encoding=cp1252
07-26 22:11 DEBUG  WindowsBackend: arch=amd64
07-26 22:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\data\isolist.ini
07-26 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 22:11 DEBUG  WindowsBackend: Fetching host info...
07-26 22:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 22:11 DEBUG  WindowsBackend: windows version=vista
07-26 22:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-26 22:11 DEBUG  WindowsBackend: windows_sp=None
07-26 22:11 DEBUG  WindowsBackend: windows_build=7100
07-26 22:11 DEBUG  WindowsBackend: gmt=-6
07-26 22:11 DEBUG  WindowsBackend: country=US
07-26 22:11 DEBUG  WindowsBackend: timezone=America/Chicago
07-26 22:11 DEBUG  WindowsBackend: windows_username=Gerardo
07-26 22:11 DEBUG  WindowsBackend: user_full_name=Gerardo
07-26 22:11 DEBUG  WindowsBackend: user_directory=Gerardo
07-26 22:11 DEBUG  WindowsBackend: windows_language_code=1034
07-26 22:11 DEBUG  WindowsBackend: windows_language=Spanish
07-26 22:11 DEBUG  WindowsBackend: processor_name=Mobile AMD Sempron(tm) Processor 3600+
07-26 22:11 DEBUG  WindowsBackend: bootloader=vista
07-26 22:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64945.109375 mb free )
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(C: hd 64945.109375 mb free )
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(D: hd 5541.91015625 mb free ntfs)
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-26 22:11 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-26 22:11 DEBUG  WindowsBackend: uninstaller_path=None
07-26 22:11 DEBUG  WindowsBackend: previous_target_dir=None
07-26 22:11 DEBUG  WindowsBackend: previous_distro_name=None
07-26 22:11 DEBUG  WindowsBackend: keyboard_id=134875146
07-26 22:11 DEBUG  WindowsBackend: keyboard_layout=us
07-26 22:11 DEBUG  WindowsBackend: keyboard_variant=
07-26 22:11 DEBUG  CommonBackend: locale=es_MX.UTF-8
07-26 22:11 DEBUG  WindowsBackend: total_memory_mb=1918.00390625
07-26 22:11 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 22:11 DEBUG  CommonBackend: Searching for local CDs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 22:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 22:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 22:11 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-26 22:11 INFO   root: Running the installer...
07-26 22:11 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=Spanish, username=gerardo
07-26 22:11 INFO   root: Received settings
07-26 22:11 DEBUG  TaskList: # Running tasklist...
07-26 22:11 DEBUG  TaskList: ## Running select_target_dir...
07-26 22:11 INFO   WindowsBackend: Installing into C:\ubuntu
07-26 22:11 DEBUG  TaskList: ## Finished select_target_dir
07-26 22:11 DEBUG  TaskList: ## Running create_dir_structure...
07-26 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-26 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-26 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-26 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-26 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-26 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-26 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-26 22:11 DEBUG  TaskList: ## Finished create_dir_structure
07-26 22:11 DEBUG  TaskList: ## Running uncompress_target_dir...
07-26 22:11 DEBUG  TaskList: ## Finished uncompress_target_dir
07-26 22:11 DEBUG  TaskList: ## Running create_uninstaller...
07-26 22:11 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-26 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-26 22:11 DEBUG  TaskList: ## Finished create_uninstaller
07-26 22:11 DEBUG  TaskList: ## Running copy_installation_files...
07-26 22:11 DEBUG  WindowsBackend: Copying C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-26 22:11 DEBUG  WindowsBackend: Copying C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\winboot -> C:\ubuntu\winboot
07-26 22:11 DEBUG  WindowsBackend: Copying C:\Users\Gerardo\AppData\Local\Temp\pyl80CC.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-26 22:11 DEBUG  TaskList: ## Finished copy_installation_files
07-26 22:11 DEBUG  TaskList: ## Running get_iso...
07-26 22:11 DEBUG  TaskList: New task copy_file
07-26 22:11 DEBUG  TaskList: ### Running copy_file...
07-26 22:16 DEBUG  TaskList: ### Finished copy_file
07-26 22:16 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-26 22:16 DEBUG  TaskList: # Cancelling tasklist
07-26 22:16 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-26 22:16 DEBUG  TaskList: New task check_iso
07-26 22:16 DEBUG  CommonBackend: Searching for local ISO
07-26 22:16 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-26 22:16 DEBUG  TaskList: New task get_metalink
07-26 22:16 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-26 22:16 DEBUG  TaskList: # Cancelling tasklist
07-26 22:16 DEBUG  TaskList: # Finished tasklist

---

### Post by RJ12 on 2009-07-26
Wubi dose not currently work with Windows 7 i think becuase of the bootloader

---

### Post by PukingPenguin on 2009-07-26
And I think wubi doesn't work with win7 because win7 was designed AFTER wubi, allowing the geniuses at Redmond to dis-allow wubi functionality. 

You are better off with a regular (non-wubi) install anyway. wubi is marginally easier, but, as with most things, "easier" brings along it's own set of compromises....

---

### Post by mcmotto12 on 2009-08-01
and, how can i install it without wubi?
it took me like 2 hours to download the cd -.-.-:confused:

---

### Post by mcmotto12 on 2009-08-01
07-26 22:16 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\  wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\  wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\  wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-26 22:16 DEBUG  TaskList: # Cancelling tasklist
07-26 22:16 DEBUG  TaskList: # Finished tasklist

i found that this is the problem 
this error
... can you help me ?

---

### Post by mcmotto12 on 2009-08-03
solved 
it was the CD...
i had to mount the image to solve the problem

---

