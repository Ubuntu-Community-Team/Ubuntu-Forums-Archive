---
title: "It's impossible to run the installer"
date: 2009-07-11
forum: General Help
---

### Post by c33abf254 on 2009-07-11
[img]http://www.pctunerup.com/up//results/_200907/20090711183649_wubi.PNG[/img]
This error page appears indifferently if I choose Xubuntu, Ubuntu or others, also trying and retrying continuously the installation...

Below the log:
[I]07-11 18:30 INFO   root: === wubi 9.04 rev129 ===
07-11 18:30 DEBUG  root: Logfile is c:\docume~1\ammini~1\impost~1\temp\wubi-9.04-rev129.log
07-11 18:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Amministratore\\Desktop\\wubi.exe"']
07-11 18:30 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\data
07-11 18:30 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\bin\7z.exe
07-11 18:30 DEBUG  CommonBackend: Fetching basic info...
07-11 18:30 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Amministratore\Desktop\wubi.exe
07-11 18:30 DEBUG  CommonBackend: platform=win32
07-11 18:30 DEBUG  CommonBackend: osname=nt
07-11 18:30 DEBUG  CommonBackend: language=it_IT
07-11 18:30 DEBUG  CommonBackend: encoding=cp1252
07-11 18:30 DEBUG  WindowsBackend: arch=i386
07-11 18:30 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\data\isolist.ini
07-11 18:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 18:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 18:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 18:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 18:30 DEBUG  WindowsBackend: Fetching host info...
07-11 18:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 18:30 DEBUG  WindowsBackend: windows version=xp
07-11 18:30 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-11 18:30 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-11 18:30 DEBUG  WindowsBackend: windows_build=2600
07-11 18:30 DEBUG  WindowsBackend: gmt=1
07-11 18:30 DEBUG  WindowsBackend: country=IT
07-11 18:30 DEBUG  WindowsBackend: timezone=Europe/Rome
07-11 18:30 DEBUG  WindowsBackend: windows_username=Amministratore
07-11 18:30 DEBUG  WindowsBackend: user_full_name=Amministratore
07-11 18:30 DEBUG  WindowsBackend: user_directory=Amministratore
07-11 18:30 DEBUG  WindowsBackend: windows_language_code=1040
07-11 18:30 DEBUG  WindowsBackend: windows_language=Italian
07-11 18:30 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 
07-11 18:30 DEBUG  WindowsBackend: bootloader=xp
07-11 18:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 128748.683594 mb free )
07-11 18:30 DEBUG  WindowsBackend: drive=Drive(C: hd 128748.683594 mb free )
07-11 18:30 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
07-11 18:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-11 18:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-11 18:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-11 18:30 DEBUG  WindowsBackend: previous_distro_name=Xubuntu
07-11 18:30 DEBUG  WindowsBackend: keyboard_id=68158480
07-11 18:30 DEBUG  WindowsBackend: keyboard_layout=it
07-11 18:30 DEBUG  WindowsBackend: keyboard_variant=
07-11 18:30 DEBUG  CommonBackend: locale=it_IT.UTF-8
07-11 18:30 DEBUG  WindowsBackend: total_memory_mb=1023.48828125
07-11 18:30 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 18:30 DEBUG  CommonBackend: Searching for local CDs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 INFO   root: Already installed, running the uninstaller...
07-11 18:30 INFO   root: Running the uninstaller...
07-11 18:30 INFO   CommonBackend: This is the uninstaller running
07-11 18:30 DEBUG  WindowsFrontend: __init__...
07-11 18:30 DEBUG  WindowsFrontend: on_init...
07-11 18:30 INFO   root: Received settings
07-11 18:30 DEBUG  TaskList: # Running tasklist...
07-11 18:30 DEBUG  TaskList: ## Running Copia ISO...
07-11 18:30 DEBUG  TaskList: ## Finished Copia ISO
07-11 18:30 DEBUG  TaskList: ## Running Rimozione voce dal gestore di avvio...
07-11 18:30 ERROR  WindowsBackend: Cannot find bcdedit
07-11 18:30 DEBUG  WindowsBackend: undo_bootini C:
07-11 18:30 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 128748.683594 mb free )
07-11 18:30 DEBUG  TaskList: ## Finished Rimozione voce dal gestore di avvio
07-11 18:30 DEBUG  TaskList: ## Running Rimozione directory obiettivo...
07-11 18:30 DEBUG  CommonBackend: Deleting C:\ubuntu
07-11 18:30 DEBUG  TaskList: ## Finished Rimozione directory obiettivo
07-11 18:30 DEBUG  TaskList: ## Running Rimozione chiave di registro...
07-11 18:30 DEBUG  TaskList: ## Finished Rimozione chiave di registro
07-11 18:30 DEBUG  TaskList: # Finished tasklist
07-11 18:30 INFO   root: Almost finished uninstalling
07-11 18:30 INFO   root: Finished uninstallation
07-11 18:30 DEBUG  CommonBackend: Fetching basic info...
07-11 18:30 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Amministratore\Desktop\wubi.exe
07-11 18:30 DEBUG  CommonBackend: platform=win32
07-11 18:30 DEBUG  CommonBackend: osname=nt
07-11 18:30 DEBUG  CommonBackend: language=it_IT
07-11 18:30 DEBUG  CommonBackend: encoding=cp1252
07-11 18:30 DEBUG  WindowsBackend: arch=i386
07-11 18:30 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\data\isolist.ini
07-11 18:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 18:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 18:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 18:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 18:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 18:30 DEBUG  WindowsBackend: Fetching host info...
07-11 18:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 18:30 DEBUG  WindowsBackend: windows version=xp
07-11 18:30 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-11 18:30 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-11 18:30 DEBUG  WindowsBackend: windows_build=2600
07-11 18:30 DEBUG  WindowsBackend: gmt=1
07-11 18:30 DEBUG  WindowsBackend: country=IT
07-11 18:30 DEBUG  WindowsBackend: timezone=Europe/Rome
07-11 18:30 DEBUG  WindowsBackend: windows_username=Amministratore
07-11 18:30 DEBUG  WindowsBackend: user_full_name=Amministratore
07-11 18:30 DEBUG  WindowsBackend: user_directory=Amministratore
07-11 18:30 DEBUG  WindowsBackend: windows_language_code=1040
07-11 18:30 DEBUG  WindowsBackend: windows_language=Italian
07-11 18:30 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 
07-11 18:30 DEBUG  WindowsBackend: bootloader=xp
07-11 18:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 128750.554688 mb free )
07-11 18:30 DEBUG  WindowsBackend: drive=Drive(C: hd 128750.554688 mb free )
07-11 18:30 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
07-11 18:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-11 18:30 DEBUG  WindowsBackend: uninstaller_path=None
07-11 18:30 DEBUG  WindowsBackend: previous_target_dir=None
07-11 18:30 DEBUG  WindowsBackend: previous_distro_name=None
07-11 18:30 DEBUG  WindowsBackend: keyboard_id=68158480
07-11 18:30 DEBUG  WindowsBackend: keyboard_layout=it
07-11 18:30 DEBUG  WindowsBackend: keyboard_variant=
07-11 18:30 DEBUG  CommonBackend: locale=it_IT.UTF-8
07-11 18:30 DEBUG  WindowsBackend: total_memory_mb=1023.48828125
07-11 18:30 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 18:30 DEBUG  CommonBackend: Searching for local CDs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 18:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 18:30 INFO   root: Running the installer...
07-11 18:30 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Xubuntu, language=Italian, username=amministratore
07-11 18:30 INFO   root: Received settings
07-11 18:30 DEBUG  TaskList: # Running tasklist...
07-11 18:30 DEBUG  TaskList: ## Running select_target_dir...
07-11 18:30 INFO   WindowsBackend: Installing into C:\ubuntu
07-11 18:30 DEBUG  TaskList: ## Finished select_target_dir
07-11 18:30 DEBUG  TaskList: ## Running create_dir_structure...
07-11 18:30 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-11 18:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-11 18:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-11 18:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-11 18:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-11 18:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-11 18:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-11 18:30 DEBUG  TaskList: ## Finished create_dir_structure
07-11 18:30 DEBUG  TaskList: ## Running uncompress_target_dir...
07-11 18:30 DEBUG  TaskList: ## Finished uncompress_target_dir
07-11 18:30 DEBUG  TaskList: ## Running create_uninstaller...
07-11 18:30 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Amministratore\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Xubuntu.ico
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
07-11 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-11 18:30 DEBUG  TaskList: ## Finished create_uninstaller
07-11 18:30 DEBUG  TaskList: ## Running copy_installation_files...
07-11 18:30 DEBUG  WindowsBackend: Copying C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-11 18:30 DEBUG  WindowsBackend: Copying C:\DOCUME~1\AMMINI~1\IMPOST~1\Temp\pylB1.tmp\winboot -> C:\ubuntu\winboot
07-11 18:30 ERROR  TaskList: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 152, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 257, in replace_line_in_file
TypeError: writelines() argument must be a sequence of strings
07-11 18:30 DEBUG  TaskList: # Cancelling tasklist
07-11 18:30 ERROR  root: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
TypeError: writelines() argument must be a sequence of strings
07-11 18:30 DEBUG  TaskList: # Finished tasklist
[/I]

---

