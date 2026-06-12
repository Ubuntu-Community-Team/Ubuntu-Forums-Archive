---
title: "During Ubuntu Install &quot;Access Denied Error&quot;"
date: 2012-03-01
forum: General Help
---

### Post by HeyThereHiThere on 2012-03-01
Okay so I decided to download Ubuntu in order to get used to it when I get a new laptop sometime around Christmas, (I plan to use Ubuntu instead of the Windows 7 or 8 that it'll come with.) And during my install, which is running along side windows, it said Access Denied towards the end of the install. Here is what i did.
1. I chose my username and password, drive size that junk.
2. Downloaded Ubuntu 11.10
3. It said extracting and expanding afterwards i think, it was yesterday
4. a message popped up saying access denied see this file. wubi 11.10-rev245. I'll post a link to it

Oh and i tried this a couple times, so it may have logged every attempt

```
02-29 21:29 INFO   root: === wubi 11.10 rev245 ===
02-29 21:29 DEBUG  root: Logfile is c:\docume~1\joe\locals~1\temp\wubi-11.10-rev245.log
02-29 21:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Joe\\My Documents\\Downloads\\wubi.exe"']
02-29 21:29 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\data
02-29 21:29 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\bin\7z.exe
02-29 21:29 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-29 21:29 DEBUG  CommonBackend: Fetching basic info...
02-29 21:29 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Joe\My Documents\Downloads\wubi.exe
02-29 21:29 DEBUG  CommonBackend: platform=win32
02-29 21:29 DEBUG  CommonBackend: osname=nt
02-29 21:29 DEBUG  CommonBackend: language=en_US
02-29 21:29 DEBUG  CommonBackend: encoding=cp1252
02-29 21:29 DEBUG  WindowsBackend: arch=i386
02-29 21:29 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\data\isolist.ini
02-29 21:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-29 21:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-29 21:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-29 21:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-29 21:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-29 21:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-29 21:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-29 21:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-29 21:29 DEBUG  WindowsBackend: Fetching host info...
02-29 21:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-29 21:29 DEBUG  WindowsBackend: windows version=xp
02-29 21:29 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-29 21:29 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-29 21:29 DEBUG  WindowsBackend: windows_build=2600
02-29 21:29 DEBUG  WindowsBackend: gmt=-5
02-29 21:29 DEBUG  WindowsBackend: country=US
02-29 21:29 DEBUG  WindowsBackend: timezone=America/New_York
02-29 21:29 DEBUG  WindowsBackend: windows_username=Joe
02-29 21:29 DEBUG  WindowsBackend: user_full_name=Joe
02-29 21:29 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Joe
02-29 21:29 DEBUG  WindowsBackend: windows_language_code=1033
02-29 21:29 DEBUG  WindowsBackend: windows_language=English
02-29 21:29 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        410  @ 1.46GHz
02-29 21:29 DEBUG  WindowsBackend: bootloader=xp
02-29 21:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 23772.3359375 mb free ntfs)
02-29 21:29 DEBUG  WindowsBackend: drive=Drive(C: hd 23772.3359375 mb free ntfs)
02-29 21:29 DEBUG  WindowsBackend: drive=Drive(D: hd 1400.3671875 mb free fat32)
02-29 21:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-29 21:29 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-29 21:29 DEBUG  WindowsBackend: uninstaller_path=None
02-29 21:29 DEBUG  WindowsBackend: previous_target_dir=None
02-29 21:29 DEBUG  WindowsBackend: previous_distro_name=None
02-29 21:29 DEBUG  WindowsBackend: keyboard_id=67699721
02-29 21:29 DEBUG  WindowsBackend: keyboard_layout=us
02-29 21:29 DEBUG  WindowsBackend: keyboard_variant=
02-29 21:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-29 21:29 DEBUG  CommonBackend: locale=en_US.UTF-8
02-29 21:29 DEBUG  WindowsBackend: total_memory_mb=2037.98046875
02-29 21:29 DEBUG  CommonBackend: Searching ISOs on USB devices
02-29 21:29 DEBUG  CommonBackend: Searching for local CDs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 21:29 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:29 INFO   root: Running the installer...
02-29 21:29 DEBUG  WindowsFrontend: __init__...
02-29 21:29 DEBUG  WindowsFrontend: on_init...
02-29 21:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\translations, languages=['en_US', 'en']
02-29 21:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\translations, languages=['en_US', 'en']
02-29 21:30 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joe
02-29 21:30 INFO   root: Received settings
02-29 21:30 DEBUG  CommonBackend: Searching for local CD
02-29 21:30 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp is a valid Ubuntu CD
02-29 21:30 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\casper\filesystem.squashfs
02-29 21:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 21:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 21:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 21:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 21:30 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 21:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 21:30 DEBUG  CommonBackend: Searching for local ISO
02-29 21:30 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\translations, languages=['en_US', 'en']
02-29 21:30 DEBUG  TaskList: # Running tasklist...
02-29 21:30 DEBUG  TaskList: ## Running select_target_dir...
02-29 21:30 INFO   WindowsBackend: Installing into C:\ubuntu
02-29 21:30 DEBUG  TaskList: ## Finished select_target_dir
02-29 21:30 DEBUG  TaskList: ## Running create_dir_structure...
02-29 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-29 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-29 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-29 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-29 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-29 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-29 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-29 21:30 DEBUG  TaskList: ## Finished create_dir_structure
02-29 21:30 DEBUG  TaskList: ## Running create_uninstaller...
02-29 21:30 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Joe\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-29 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-29 21:30 DEBUG  TaskList: ## Finished create_uninstaller
02-29 21:30 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-29 21:30 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-29 21:30 DEBUG  TaskList: ## Running get_diskimage...
02-29 21:30 DEBUG  TaskList: New task download
02-29 21:30 DEBUG  TaskList: ### Running download...
02-29 21:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-i386.tar.xz
02-29 21:30 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-i386.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz, basename=ubuntu-11.10-wubi-i386.tar.xz, length=502072400, text=None
02-29 22:21 DEBUG  TaskList: ### Finished download
02-29 22:21 DEBUG  downloader: download finished (read 502072400 bytes)
02-29 22:21 DEBUG  TaskList: ## Finished get_diskimage
02-29 22:21 DEBUG  TaskList: ## Running extract_diskimage...
02-29 22:23 DEBUG  TaskList: ## Finished extract_diskimage
02-29 22:23 DEBUG  TaskList: ## Running choose_disk_sizes...
02-29 22:23 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
02-29 22:23 DEBUG  TaskList: ## Finished choose_disk_sizes
02-29 22:23 DEBUG  TaskList: ## Running expand_diskimage...
02-29 22:24 DEBUG  TaskList: ## Finished expand_diskimage
02-29 22:24 DEBUG  TaskList: ## Running create_swap_diskimage...
02-29 22:24 DEBUG  TaskList: ## Finished create_swap_diskimage
02-29 22:24 DEBUG  TaskList: ## Running modify_bootloader...
02-29 22:24 DEBUG  TaskList: New task modify_bootini
02-29 22:24 DEBUG  TaskList: ### Running modify_bootini...
02-29 22:24 DEBUG  WindowsBackend: modify_bootini C:
02-29 22:24 DEBUG  TaskList: ### Finished modify_bootini
02-29 22:24 DEBUG  TaskList: New task modify_bootini
02-29 22:24 DEBUG  TaskList: ### Running modify_bootini...
02-29 22:24 DEBUG  WindowsBackend: modify_bootini D:
02-29 22:24 DEBUG  TaskList: ### Finished modify_bootini
02-29 22:24 DEBUG  TaskList: New task modify_bootini
02-29 22:24 DEBUG  TaskList: ### Running modify_bootini...
02-29 22:24 DEBUG  WindowsBackend: modify_bootini Q:
02-29 22:24 DEBUG  WindowsBackend: Could not find boot.ini Q:\boot.ini
02-29 22:24 DEBUG  TaskList: ### Finished modify_bootini
02-29 22:24 DEBUG  TaskList: ## Finished modify_bootloader
02-29 22:24 DEBUG  TaskList: ## Running diskimage_bootloader...
02-29 22:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl167.tmp\winboot -> C:\ubuntu\winboot
02-29 22:24 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-29 22:24 DEBUG  TaskList: # Cancelling tasklist
02-29 22:24 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-29 22:24 DEBUG  TaskList: # Finished tasklist
02-29 22:28 INFO   root: === wubi 11.10 rev245 ===
02-29 22:28 DEBUG  root: Logfile is c:\docume~1\joe\locals~1\temp\wubi-11.10-rev245.log
02-29 22:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Joe\\Desktop\\wubi.exe"']
02-29 22:28 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\data
02-29 22:28 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\bin\7z.exe
02-29 22:28 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-29 22:28 DEBUG  CommonBackend: Fetching basic info...
02-29 22:28 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Joe\Desktop\wubi.exe
02-29 22:28 DEBUG  CommonBackend: platform=win32
02-29 22:28 DEBUG  CommonBackend: osname=nt
02-29 22:28 DEBUG  CommonBackend: language=en_US
02-29 22:28 DEBUG  CommonBackend: encoding=cp1252
02-29 22:28 DEBUG  WindowsBackend: arch=i386
02-29 22:28 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\data\isolist.ini
02-29 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-29 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-29 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-29 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-29 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-29 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-29 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-29 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-29 22:28 DEBUG  WindowsBackend: Fetching host info...
02-29 22:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-29 22:28 DEBUG  WindowsBackend: windows version=xp
02-29 22:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-29 22:28 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-29 22:28 DEBUG  WindowsBackend: windows_build=2600
02-29 22:28 DEBUG  WindowsBackend: gmt=-5
02-29 22:28 DEBUG  WindowsBackend: country=US
02-29 22:28 DEBUG  WindowsBackend: timezone=America/New_York
02-29 22:28 DEBUG  WindowsBackend: windows_username=Joe
02-29 22:28 DEBUG  WindowsBackend: user_full_name=Joe
02-29 22:28 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Joe
02-29 22:28 DEBUG  WindowsBackend: windows_language_code=1033
02-29 22:28 DEBUG  WindowsBackend: windows_language=English
02-29 22:28 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        410  @ 1.46GHz
02-29 22:28 DEBUG  WindowsBackend: bootloader=xp
02-29 22:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20979.3164063 mb free ntfs)
02-29 22:28 DEBUG  WindowsBackend: drive=Drive(C: hd 20979.3164063 mb free ntfs)
02-29 22:28 DEBUG  WindowsBackend: drive=Drive(D: hd 1400.1953125 mb free fat32)
02-29 22:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-29 22:28 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-29 22:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-29 22:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-29 22:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-29 22:28 DEBUG  WindowsBackend: keyboard_id=67699721
02-29 22:28 DEBUG  WindowsBackend: keyboard_layout=us
02-29 22:28 DEBUG  WindowsBackend: keyboard_variant=
02-29 22:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-29 22:28 DEBUG  CommonBackend: locale=en_US.UTF-8
02-29 22:28 DEBUG  WindowsBackend: total_memory_mb=2037.98046875
02-29 22:28 DEBUG  CommonBackend: Searching ISOs on USB devices
02-29 22:28 DEBUG  CommonBackend: Searching for local CDs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 22:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:28 INFO   root: Already installed, running the uninstaller...
02-29 22:28 INFO   root: Running the uninstaller...
02-29 22:28 INFO   CommonBackend: This is the uninstaller running
02-29 22:28 DEBUG  WindowsFrontend: __init__...
02-29 22:28 DEBUG  WindowsFrontend: on_init...
02-29 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl17C.tmp\translations, languages=['en_US', 'en']
02-29 22:28 INFO   WindowsFrontend: Operation cancelled
02-29 22:28 DEBUG  WindowsFrontend: frontend.quit
02-29 22:28 DEBUG  WindowsFrontend: frontend.on_quit
02-29 22:28 DEBUG  root: application.on_quit
02-29 22:28 INFO   root: sys.exit
02-29 22:33 INFO   root: === wubi 11.10 rev245 ===
02-29 22:33 DEBUG  root: Logfile is c:\docume~1\joe\locals~1\temp\wubi-11.10-rev245.log
02-29 22:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Joe\\Desktop\\wubi.exe"']
02-29 22:33 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\data
02-29 22:33 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
02-29 22:33 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-29 22:33 DEBUG  CommonBackend: Fetching basic info...
02-29 22:33 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Joe\Desktop\wubi.exe
02-29 22:33 DEBUG  CommonBackend: platform=win32
02-29 22:33 DEBUG  CommonBackend: osname=nt
02-29 22:33 DEBUG  CommonBackend: language=en_US
02-29 22:33 DEBUG  CommonBackend: encoding=cp1252
02-29 22:33 DEBUG  WindowsBackend: arch=i386
02-29 22:33 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
02-29 22:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-29 22:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-29 22:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-29 22:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-29 22:33 DEBUG  WindowsBackend: Fetching host info...
02-29 22:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-29 22:33 DEBUG  WindowsBackend: windows version=xp
02-29 22:33 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-29 22:33 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-29 22:33 DEBUG  WindowsBackend: windows_build=2600
02-29 22:33 DEBUG  WindowsBackend: gmt=-5
02-29 22:33 DEBUG  WindowsBackend: country=US
02-29 22:33 DEBUG  WindowsBackend: timezone=America/New_York
02-29 22:33 DEBUG  WindowsBackend: windows_username=Joe
02-29 22:33 DEBUG  WindowsBackend: user_full_name=Joe
02-29 22:33 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Joe
02-29 22:33 DEBUG  WindowsBackend: windows_language_code=1033
02-29 22:33 DEBUG  WindowsBackend: windows_language=English
02-29 22:33 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        410  @ 1.46GHz
02-29 22:33 DEBUG  WindowsBackend: bootloader=xp
02-29 22:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21037.1054688 mb free ntfs)
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(C: hd 21037.1054688 mb free ntfs)
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(D: hd 1400.203125 mb free fat32)
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-29 22:33 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-29 22:33 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-29 22:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-29 22:33 DEBUG  WindowsBackend: keyboard_id=67699721
02-29 22:33 DEBUG  WindowsBackend: keyboard_layout=us
02-29 22:33 DEBUG  WindowsBackend: keyboard_variant=
02-29 22:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-29 22:33 DEBUG  CommonBackend: locale=en_US.UTF-8
02-29 22:33 DEBUG  WindowsBackend: total_memory_mb=2037.98046875
02-29 22:33 DEBUG  CommonBackend: Searching ISOs on USB devices
02-29 22:33 DEBUG  CommonBackend: Searching for local CDs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 INFO   root: Already installed, running the uninstaller...
02-29 22:33 INFO   root: Running the uninstaller...
02-29 22:33 INFO   CommonBackend: This is the uninstaller running
02-29 22:33 DEBUG  WindowsFrontend: __init__...
02-29 22:33 DEBUG  WindowsFrontend: on_init...
02-29 22:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
02-29 22:33 INFO   root: Received settings
02-29 22:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
02-29 22:33 DEBUG  TaskList: # Running tasklist...
02-29 22:33 DEBUG  TaskList: ## Running Remove bootloader entry...
02-29 22:33 ERROR  WindowsBackend: Cannot find bcdedit
02-29 22:33 DEBUG  WindowsBackend: undo_bootini C:
02-29 22:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 21037.1054688 mb free ntfs)
02-29 22:33 DEBUG  WindowsBackend: undo_bootini D:
02-29 22:33 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1400.203125 mb free fat32)
02-29 22:33 DEBUG  WindowsBackend: undo_bootini Q:
02-29 22:33 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-29 22:33 DEBUG  TaskList: ## Finished Remove bootloader entry
02-29 22:33 DEBUG  TaskList: ## Running Remove target dir...
02-29 22:33 DEBUG  CommonBackend: Deleting C:\ubuntu
02-29 22:33 DEBUG  TaskList: ## Finished Remove target dir
02-29 22:33 DEBUG  TaskList: ## Running Remove registry key...
02-29 22:33 DEBUG  TaskList: ## Finished Remove registry key
02-29 22:33 DEBUG  TaskList: # Finished tasklist
02-29 22:33 INFO   root: Almost finished uninstalling
02-29 22:33 INFO   root: Finished uninstallation
02-29 22:33 DEBUG  CommonBackend: Fetching basic info...
02-29 22:33 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Joe\Desktop\wubi.exe
02-29 22:33 DEBUG  CommonBackend: platform=win32
02-29 22:33 DEBUG  CommonBackend: osname=nt
02-29 22:33 DEBUG  WindowsBackend: arch=i386
02-29 22:33 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
02-29 22:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-29 22:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-29 22:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-29 22:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-29 22:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-29 22:33 DEBUG  WindowsBackend: Fetching host info...
02-29 22:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-29 22:33 DEBUG  WindowsBackend: windows version=xp
02-29 22:33 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-29 22:33 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-29 22:33 DEBUG  WindowsBackend: windows_build=2600
02-29 22:33 DEBUG  WindowsBackend: gmt=-5
02-29 22:33 DEBUG  WindowsBackend: country=US
02-29 22:33 DEBUG  WindowsBackend: timezone=America/New_York
02-29 22:33 DEBUG  WindowsBackend: windows_username=Joe
02-29 22:33 DEBUG  WindowsBackend: user_full_name=Joe
02-29 22:33 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Joe
02-29 22:33 DEBUG  WindowsBackend: windows_language_code=1033
02-29 22:33 DEBUG  WindowsBackend: windows_language=English
02-29 22:33 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        410  @ 1.46GHz
02-29 22:33 DEBUG  WindowsBackend: bootloader=xp
02-29 22:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 23901.2109375 mb free ntfs)
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(C: hd 23901.2109375 mb free ntfs)
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(D: hd 1400.3203125 mb free fat32)
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-29 22:33 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-29 22:33 DEBUG  WindowsBackend: uninstaller_path=None
02-29 22:33 DEBUG  WindowsBackend: previous_target_dir=None
02-29 22:33 DEBUG  WindowsBackend: previous_distro_name=None
02-29 22:33 DEBUG  WindowsBackend: keyboard_id=67699721
02-29 22:33 DEBUG  WindowsBackend: keyboard_layout=us
02-29 22:33 DEBUG  WindowsBackend: keyboard_variant=
02-29 22:33 DEBUG  WindowsBackend: total_memory_mb=2037.98046875
02-29 22:33 DEBUG  CommonBackend: Searching ISOs on USB devices
02-29 22:33 DEBUG  CommonBackend: Searching for local CDs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 INFO   root: Running the installer...
02-29 22:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
02-29 22:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
02-29 22:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joe
02-29 22:33 INFO   root: Received settings
02-29 22:33 DEBUG  CommonBackend: Searching for local CD
02-29 22:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-29 22:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-29 22:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-29 22:33 DEBUG  CommonBackend: Searching for local ISO
02-29 22:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
02-29 22:33 DEBUG  TaskList: # Running tasklist...
02-29 22:33 DEBUG  TaskList: ## Running select_target_dir...
02-29 22:33 INFO   WindowsBackend: Installing into C:\ubuntu
02-29 22:33 DEBUG  TaskList: ## Finished select_target_dir
02-29 22:33 DEBUG  TaskList: ## Running create_dir_structure...
02-29 22:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-29 22:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-29 22:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-29 22:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-29 22:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-29 22:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-29 22:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-29 22:33 DEBUG  TaskList: ## Finished create_dir_structure
02-29 22:33 DEBUG  TaskList: ## Running create_uninstaller...
02-29 22:33 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Joe\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-29 22:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-29 22:33 DEBUG  TaskList: ## Finished create_uninstaller
02-29 22:33 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-29 22:33 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-29 22:33 DEBUG  TaskList: ## Running get_diskimage...
02-29 22:33 DEBUG  TaskList: New task download
02-29 22:33 DEBUG  TaskList: ### Running download...
02-29 22:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-i386.tar.xz
02-29 22:33 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-i386.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz, basename=ubuntu-11.10-wubi-i386.tar.xz, length=502072400, text=None
02-29 23:26 DEBUG  TaskList: ### Finished download
02-29 23:26 DEBUG  downloader: download finished (read 502072400 bytes)
02-29 23:26 DEBUG  TaskList: ## Finished get_diskimage
02-29 23:26 DEBUG  TaskList: ## Running extract_diskimage...
02-29 23:29 DEBUG  TaskList: ## Finished extract_diskimage
02-29 23:29 DEBUG  TaskList: ## Running choose_disk_sizes...
02-29 23:29 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
02-29 23:29 DEBUG  TaskList: ## Finished choose_disk_sizes
02-29 23:29 DEBUG  TaskList: ## Running expand_diskimage...
02-29 23:29 DEBUG  TaskList: ## Finished expand_diskimage
02-29 23:29 DEBUG  TaskList: ## Running create_swap_diskimage...
02-29 23:29 DEBUG  TaskList: ## Finished create_swap_diskimage
02-29 23:29 DEBUG  TaskList: ## Running modify_bootloader...
02-29 23:29 DEBUG  TaskList: New task modify_bootini
02-29 23:29 DEBUG  TaskList: ### Running modify_bootini...
02-29 23:29 DEBUG  WindowsBackend: modify_bootini C:
02-29 23:29 DEBUG  TaskList: ### Finished modify_bootini
02-29 23:29 DEBUG  TaskList: New task modify_bootini
02-29 23:29 DEBUG  TaskList: ### Running modify_bootini...
02-29 23:29 DEBUG  WindowsBackend: modify_bootini D:
02-29 23:29 DEBUG  TaskList: ### Finished modify_bootini
02-29 23:29 DEBUG  TaskList: New task modify_bootini
02-29 23:29 DEBUG  TaskList: ### Running modify_bootini...
02-29 23:29 DEBUG  WindowsBackend: modify_bootini Q:
02-29 23:29 DEBUG  WindowsBackend: Could not find boot.ini Q:\boot.ini
02-29 23:29 DEBUG  TaskList: ### Finished modify_bootini
02-29 23:29 DEBUG  TaskList: ## Finished modify_bootloader
02-29 23:29 DEBUG  TaskList: ## Running diskimage_bootloader...
02-29 23:29 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl9.tmp\winboot -> C:\ubuntu\winboot
02-29 23:29 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-29 23:29 DEBUG  TaskList: # Cancelling tasklist
02-29 23:29 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-29 23:29 DEBUG  TaskList: # Finished tasklist
03-01 16:10 INFO   root: === wubi 11.10 rev245 ===
03-01 16:10 DEBUG  root: Logfile is c:\docume~1\joe\locals~1\temp\wubi-11.10-rev245.log
03-01 16:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Joe\\Desktop\\wubi.exe"']
03-01 16:10 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\data
03-01 16:10 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\bin\7z.exe
03-01 16:10 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
03-01 16:10 DEBUG  CommonBackend: Fetching basic info...
03-01 16:10 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Joe\Desktop\wubi.exe
03-01 16:10 DEBUG  CommonBackend: platform=win32
03-01 16:10 DEBUG  CommonBackend: osname=nt
03-01 16:10 DEBUG  CommonBackend: language=en_US
03-01 16:10 DEBUG  CommonBackend: encoding=cp1252
03-01 16:10 DEBUG  WindowsBackend: arch=i386
03-01 16:10 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\data\isolist.ini
03-01 16:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:10 DEBUG  WindowsBackend: Fetching host info...
03-01 16:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:10 DEBUG  WindowsBackend: windows version=xp
03-01 16:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 16:10 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 16:10 DEBUG  WindowsBackend: windows_build=2600
03-01 16:10 DEBUG  WindowsBackend: gmt=-5
03-01 16:10 DEBUG  WindowsBackend: country=US
03-01 16:10 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:10 DEBUG  WindowsBackend: windows_username=Joe
03-01 16:10 DEBUG  WindowsBackend: user_full_name=Joe
03-01 16:10 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Joe
03-01 16:10 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:10 DEBUG  WindowsBackend: windows_language=English
03-01 16:10 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        410  @ 1.46GHz
03-01 16:10 DEBUG  WindowsBackend: bootloader=xp
03-01 16:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20442.2070313 mb free ntfs)
03-01 16:10 DEBUG  WindowsBackend: drive=Drive(C: hd 20442.2070313 mb free ntfs)
03-01 16:10 DEBUG  WindowsBackend: drive=Drive(D: hd 1400.1484375 mb free fat32)
03-01 16:10 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 16:10 DEBUG  WindowsBackend: drive=Drive(F: removable 6920.1171875 mb free fat32)
03-01 16:10 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-01 16:10 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-01 16:10 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-01 16:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 16:10 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:10 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:10 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 16:10 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 16:10 DEBUG  WindowsBackend: total_memory_mb=2037.98046875
03-01 16:10 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:10 DEBUG  CommonBackend: Searching for local CDs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
03-01 16:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:10 INFO   root: Already installed, running the uninstaller...
03-01 16:10 INFO   root: Running the uninstaller...
03-01 16:10 INFO   CommonBackend: This is the uninstaller running
03-01 16:10 DEBUG  WindowsFrontend: __init__...
03-01 16:10 DEBUG  WindowsFrontend: on_init...
03-01 16:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\translations, languages=['en_US', 'en']
03-01 16:10 INFO   root: Received settings
03-01 16:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\translations, languages=['en_US', 'en']
03-01 16:10 DEBUG  TaskList: # Running tasklist...
03-01 16:10 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 16:10 ERROR  WindowsBackend: Cannot find bcdedit
03-01 16:10 DEBUG  WindowsBackend: undo_bootini C:
03-01 16:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 20442.2070313 mb free ntfs)
03-01 16:11 DEBUG  WindowsBackend: undo_bootini D:
03-01 16:11 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1400.1484375 mb free fat32)
03-01 16:11 DEBUG  WindowsBackend: undo_bootini F:
03-01 16:11 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 6920.1171875 mb free fat32)
03-01 16:11 DEBUG  WindowsBackend: undo_bootini Q:
03-01 16:11 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
03-01 16:11 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 16:11 DEBUG  TaskList: ## Running Remove target dir...
03-01 16:11 DEBUG  CommonBackend: Deleting C:\ubuntu
03-01 16:11 DEBUG  TaskList: ## Finished Remove target dir
03-01 16:11 DEBUG  TaskList: ## Running Remove registry key...
03-01 16:11 DEBUG  TaskList: ## Finished Remove registry key
03-01 16:11 DEBUG  TaskList: # Finished tasklist
03-01 16:11 INFO   root: Almost finished uninstalling
03-01 16:11 INFO   root: Finished uninstallation
03-01 16:11 DEBUG  CommonBackend: Fetching basic info...
03-01 16:11 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Joe\Desktop\wubi.exe
03-01 16:11 DEBUG  CommonBackend: platform=win32
03-01 16:11 DEBUG  CommonBackend: osname=nt
03-01 16:11 DEBUG  WindowsBackend: arch=i386
03-01 16:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\data\isolist.ini
03-01 16:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 16:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 16:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 16:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 16:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 16:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 16:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 16:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 16:11 DEBUG  WindowsBackend: Fetching host info...
03-01 16:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 16:11 DEBUG  WindowsBackend: windows version=xp
03-01 16:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 16:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 16:11 DEBUG  WindowsBackend: windows_build=2600
03-01 16:11 DEBUG  WindowsBackend: gmt=-5
03-01 16:11 DEBUG  WindowsBackend: country=US
03-01 16:11 DEBUG  WindowsBackend: timezone=America/New_York
03-01 16:11 DEBUG  WindowsBackend: windows_username=Joe
03-01 16:11 DEBUG  WindowsBackend: user_full_name=Joe
03-01 16:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Joe
03-01 16:11 DEBUG  WindowsBackend: windows_language_code=1033
03-01 16:11 DEBUG  WindowsBackend: windows_language=English
03-01 16:11 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        410  @ 1.46GHz
03-01 16:11 DEBUG  WindowsBackend: bootloader=xp
03-01 16:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 23298.171875 mb free ntfs)
03-01 16:11 DEBUG  WindowsBackend: drive=Drive(C: hd 23298.171875 mb free ntfs)
03-01 16:11 DEBUG  WindowsBackend: drive=Drive(D: hd 1400.28125 mb free fat32)
03-01 16:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 16:11 DEBUG  WindowsBackend: drive=Drive(F: removable 6920.1171875 mb free fat32)
03-01 16:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-01 16:11 DEBUG  WindowsBackend: uninstaller_path=None
03-01 16:11 DEBUG  WindowsBackend: previous_target_dir=None
03-01 16:11 DEBUG  WindowsBackend: previous_distro_name=None
03-01 16:11 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 16:11 DEBUG  WindowsBackend: keyboard_layout=us
03-01 16:11 DEBUG  WindowsBackend: keyboard_variant=
03-01 16:11 DEBUG  WindowsBackend: total_memory_mb=2037.98046875
03-01 16:11 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 16:11 DEBUG  CommonBackend: Searching for local CDs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
03-01 16:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:11 INFO   root: Running the installer...
03-01 16:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\translations, languages=['en_US', 'en']
03-01 16:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\translations, languages=['en_US', 'en']
03-01 16:12 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joe
03-01 16:12 INFO   root: Received settings
03-01 16:12 DEBUG  CommonBackend: Searching for local CD
03-01 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp is a valid Ubuntu CD
03-01 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\casper\filesystem.squashfs
03-01 16:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 16:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 16:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 16:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
03-01 16:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
03-01 16:12 DEBUG  CommonBackend: Searching for local ISO
03-01 16:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\translations, languages=['en_US', 'en']
03-01 16:12 DEBUG  TaskList: # Running tasklist...
03-01 16:12 DEBUG  TaskList: ## Running select_target_dir...
03-01 16:12 INFO   WindowsBackend: Installing into C:\ubuntu
03-01 16:12 DEBUG  TaskList: ## Finished select_target_dir
03-01 16:12 DEBUG  TaskList: ## Running create_dir_structure...
03-01 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-01 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-01 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-01 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-01 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-01 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-01 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-01 16:12 DEBUG  TaskList: ## Finished create_dir_structure
03-01 16:12 DEBUG  TaskList: ## Running create_uninstaller...
03-01 16:12 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Joe\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-01 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-01 16:12 DEBUG  TaskList: ## Finished create_uninstaller
03-01 16:12 DEBUG  TaskList: ## Running create_preseed_diskimage...
03-01 16:12 DEBUG  TaskList: ## Finished create_preseed_diskimage
03-01 16:12 DEBUG  TaskList: ## Running get_diskimage...
03-01 16:12 DEBUG  TaskList: New task download
03-01 16:12 DEBUG  TaskList: ### Running download...
03-01 16:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-i386.tar.xz
03-01 16:12 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-i386.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-i386.tar.xz, basename=ubuntu-11.10-wubi-i386.tar.xz, length=502072400, text=None
03-01 16:29 DEBUG  TaskList: ### Finished download
03-01 16:29 DEBUG  downloader: download finished (read 502072400 bytes)
03-01 16:29 DEBUG  TaskList: ## Finished get_diskimage
03-01 16:29 DEBUG  TaskList: ## Running extract_diskimage...
03-01 16:31 DEBUG  TaskList: ## Finished extract_diskimage
03-01 16:31 DEBUG  TaskList: ## Running choose_disk_sizes...
03-01 16:31 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
03-01 16:31 DEBUG  TaskList: ## Finished choose_disk_sizes
03-01 16:31 DEBUG  TaskList: ## Running expand_diskimage...
03-01 16:32 DEBUG  TaskList: ## Finished expand_diskimage
03-01 16:32 DEBUG  TaskList: ## Running create_swap_diskimage...
03-01 16:32 DEBUG  TaskList: ## Finished create_swap_diskimage
03-01 16:32 DEBUG  TaskList: ## Running modify_bootloader...
03-01 16:32 DEBUG  TaskList: New task modify_bootini
03-01 16:32 DEBUG  TaskList: ### Running modify_bootini...
03-01 16:32 DEBUG  WindowsBackend: modify_bootini C:
03-01 16:32 DEBUG  TaskList: ### Finished modify_bootini
03-01 16:32 DEBUG  TaskList: New task modify_bootini
03-01 16:32 DEBUG  TaskList: ### Running modify_bootini...
03-01 16:32 DEBUG  WindowsBackend: modify_bootini D:
03-01 16:32 DEBUG  TaskList: ### Finished modify_bootini
03-01 16:32 DEBUG  TaskList: New task modify_bootini
03-01 16:32 DEBUG  TaskList: ### Running modify_bootini...
03-01 16:32 DEBUG  WindowsBackend: modify_bootini F:
03-01 16:32 DEBUG  WindowsBackend: Could not find boot.ini F:\boot.ini
03-01 16:32 DEBUG  TaskList: ### Finished modify_bootini
03-01 16:32 DEBUG  TaskList: New task modify_bootini
03-01 16:32 DEBUG  TaskList: ### Running modify_bootini...
03-01 16:32 DEBUG  WindowsBackend: modify_bootini Q:
03-01 16:32 DEBUG  WindowsBackend: Could not find boot.ini Q:\boot.ini
03-01 16:32 DEBUG  TaskList: ### Finished modify_bootini
03-01 16:32 DEBUG  TaskList: ## Finished modify_bootloader
03-01 16:32 DEBUG  TaskList: ## Running diskimage_bootloader...
03-01 16:32 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Joe\LOCALS~1\Temp\pyl6B.tmp\winboot -> C:\ubuntu\winboot
03-01 16:32 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
03-01 16:32 DEBUG  TaskList: # Cancelling tasklist
03-01 16:32 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
03-01 16:32 DEBUG  TaskList: # Finished tasklist

```

---

### Post by bcbc on 2012-03-02
The install is successful. See bug [lpbug]862003[/lpbug]

If it irritates you that you did the same install a number of times, feel free to +1 on that bug report.

---

