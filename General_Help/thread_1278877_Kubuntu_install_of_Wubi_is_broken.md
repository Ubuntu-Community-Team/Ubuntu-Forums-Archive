---
title: "Kubuntu install of Wubi is broken"
date: 2009-09-30
forum: General Help
---

### Post by knockNrod on 2009-09-30
09-30 03:34 INFO   root: === wubi 9.04 rev129 ===
09-30 03:34 DEBUG  root: Logfile is c:\docume~1\test\locals~1\temp\wubi-9.04-rev129.log
09-30 03:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\test\\Local Settings\\Temporary Internet Files\\Content.IE5\\HH4UVJFD\\wubi[1].exe"']
09-30 03:34 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\data
09-30 03:34 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\bin\7z.exe
09-30 03:34 DEBUG  CommonBackend: Fetching basic info...
09-30 03:34 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\test\Local Settings\Temporary Internet Files\Content.IE5\HH4UVJFD\wubi[1].exe
09-30 03:34 DEBUG  CommonBackend: platform=win32
09-30 03:34 DEBUG  CommonBackend: osname=nt
09-30 03:34 DEBUG  CommonBackend: language=en_US
09-30 03:34 DEBUG  CommonBackend: encoding=cp1252
09-30 03:34 DEBUG  WindowsBackend: arch=amd64
09-30 03:34 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\data\isolist.ini
09-30 03:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:34 DEBUG  WindowsBackend: Fetching host info...
09-30 03:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:34 DEBUG  WindowsBackend: windows version=xp
09-30 03:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-30 03:34 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-30 03:34 DEBUG  WindowsBackend: windows_build=2600
09-30 03:34 DEBUG  WindowsBackend: gmt=-5
09-30 03:34 DEBUG  WindowsBackend: country=US
09-30 03:34 DEBUG  WindowsBackend: timezone=America/New_York
09-30 03:34 DEBUG  WindowsBackend: windows_username=test
09-30 03:34 DEBUG  WindowsBackend: user_full_name=test
09-30 03:34 DEBUG  WindowsBackend: user_directory=test
09-30 03:34 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:34 DEBUG  WindowsBackend: windows_language=English
09-30 03:34 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
09-30 03:34 DEBUG  WindowsBackend: bootloader=xp
09-30 03:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65387.5234375 mb free )
09-30 03:34 DEBUG  WindowsBackend: drive=Drive(C: hd 65387.5234375 mb free )
09-30 03:34 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
09-30 03:34 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:34 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:34 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:34 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:34 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:34 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:34 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:34 DEBUG  WindowsBackend: total_memory_mb=1022.48046875
09-30 03:34 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:34 DEBUG  CommonBackend: Searching for local CDs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Ubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Ubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Kubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Kubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Xubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Xubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Mythbuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Mythbuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 INFO   root: Running the installer...
09-30 03:34 DEBUG  WindowsFrontend: __init__...
09-30 03:34 DEBUG  WindowsFrontend: on_init...
09-30 03:34 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Kubuntu, language=English, username=rod
09-30 03:34 INFO   root: Received settings
09-30 03:34 DEBUG  TaskList: # Running tasklist...
09-30 03:34 DEBUG  TaskList: ## Running select_target_dir...
09-30 03:34 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 03:34 DEBUG  TaskList: ## Finished select_target_dir
09-30 03:34 DEBUG  TaskList: ## Running create_dir_structure...
09-30 03:34 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 03:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 03:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 03:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 03:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 03:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 03:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 03:34 DEBUG  TaskList: ## Finished create_dir_structure
09-30 03:34 DEBUG  TaskList: ## Running uncompress_target_dir...
09-30 03:34 DEBUG  TaskList: ## Finished uncompress_target_dir
09-30 03:34 DEBUG  TaskList: ## Running create_uninstaller...
09-30 03:34 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\test\Local Settings\Temporary Internet Files\Content.IE5\HH4UVJFD\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
09-30 03:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-30 03:34 DEBUG  TaskList: ## Finished create_uninstaller
09-30 03:34 DEBUG  TaskList: ## Running copy_installation_files...
09-30 03:34 DEBUG  WindowsBackend: Copying C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-30 03:34 DEBUG  WindowsBackend: Copying C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\winboot -> C:\ubuntu\winboot
09-30 03:34 DEBUG  WindowsBackend: Copying C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
09-30 03:34 DEBUG  TaskList: ## Finished copy_installation_files
09-30 03:34 DEBUG  TaskList: ## Running get_iso...
09-30 03:34 DEBUG  CommonBackend: Searching for local CD
09-30 03:34 DEBUG  Distro:   checking whether C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp is a valid Kubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
09-30 03:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:34 DEBUG  CommonBackend: Searching for local ISO
09-30 03:34 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-30 03:34 DEBUG  TaskList: New task get_metalink
09-30 03:34 DEBUG  TaskList: ### Running get_metalink...
09-30 03:34 DEBUG  downloader: downloading releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink > C:\ubuntu\install
09-30 03:34 ERROR  CommonBackend: Cannot download metalink file releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink err=[Errno 2] Local file does not exist: C:\DOCUME~1\test\LOCALS~1\Temp\pylCB.tmp\releases.ubuntu.com\kubuntu\9.04\kubuntu-9.04-desktop-i386.metalink
09-30 03:34 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink) > C:\ubuntu\install
09-30 03:34 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink) err=[Errno 14] HTTP Error 404: Not Found
09-30 03:34 DEBUG  TaskList: ### Finished get_metalink
09-30 03:34 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-30 03:34 DEBUG  TaskList: # Cancelling tasklist
09-30 03:34 DEBUG  TaskList: # Finished tasklist
09-30 03:34 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Cannot download the metalink and therefore the ISO

---

