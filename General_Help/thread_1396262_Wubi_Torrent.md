---
title: "Wubi Torrent"
date: 2010-02-01
forum: General Help
---

### Post by Razbuntu on 2010-02-01
I Seem to be unable to install  ubuntu... here is the issue:
```
01-28 15:16 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-28 15:16 DEBUG  root: Logfile is c:\users\rac\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-28 15:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\rac\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\Y4X1OH1Y\\wubi[1].exe"']
01-28 15:16 DEBUG  CommonBackend: data_dir=C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\data
01-28 15:16 DEBUG  WindowsBackend: 7z=C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\bin\7z.exe
01-28 15:16 DEBUG  CommonBackend: Fetching basic info...
01-28 15:16 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\Y4X1OH1Y\wubi[1].exe
01-28 15:16 DEBUG  CommonBackend: platform=win32
01-28 15:16 DEBUG  CommonBackend: osname=nt
01-28 15:16 DEBUG  CommonBackend: language=en_US
01-28 15:16 DEBUG  CommonBackend: encoding=cp1252
01-28 15:16 DEBUG  WindowsBackend: arch=amd64
01-28 15:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\data\isolist.ini
01-28 15:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-28 15:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-28 15:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-28 15:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-28 15:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-28 15:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-28 15:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-28 15:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-28 15:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-28 15:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-28 15:16 DEBUG  WindowsBackend: Fetching host info...
01-28 15:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-28 15:16 DEBUG  WindowsBackend: windows version=vista
01-28 15:16 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
01-28 15:16 DEBUG  WindowsBackend: windows_sp=Service Pack 1
01-28 15:16 DEBUG  WindowsBackend: windows_build=6001
01-28 15:16 DEBUG  WindowsBackend: gmt=-5
01-28 15:16 DEBUG  WindowsBackend: country=US
01-28 15:16 DEBUG  WindowsBackend: timezone=America/New_York
01-28 15:16 DEBUG  WindowsBackend: windows_username=rac
01-28 15:16 DEBUG  WindowsBackend: user_full_name=rac
01-28 15:16 DEBUG  WindowsBackend: user_directory=C:\Users\rac
01-28 15:16 DEBUG  WindowsBackend: windows_language_code=1033
01-28 15:16 DEBUG  WindowsBackend: windows_language=English
01-28 15:16 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
01-28 15:16 DEBUG  WindowsBackend: bootloader=vista
01-28 15:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180931.023438 mb free ntfs)
01-28 15:16 DEBUG  WindowsBackend: drive=Drive(C: hd 180931.023438 mb free ntfs)
01-28 15:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-28 15:16 DEBUG  WindowsBackend: uninstaller_path=None
01-28 15:16 DEBUG  WindowsBackend: previous_target_dir=None
01-28 15:16 DEBUG  WindowsBackend: previous_distro_name=None
01-28 15:16 DEBUG  WindowsBackend: keyboard_id=67699721
01-28 15:16 DEBUG  WindowsBackend: keyboard_layout=us
01-28 15:16 DEBUG  WindowsBackend: keyboard_variant=
01-28 15:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-28 15:16 DEBUG  CommonBackend: locale=en_US.UTF-8
01-28 15:16 DEBUG  WindowsBackend: total_memory_mb=1789.375
01-28 15:16 DEBUG  CommonBackend: Searching ISOs on USB devices
01-28 15:16 DEBUG  CommonBackend: Searching for local CDs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Ubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Ubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Ubuntu Netbook Remix CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Kubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Kubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Kubuntu Netbook CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Xubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Xubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Mythbuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Mythbuntu CD
01-28 15:16 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:16 INFO   root: Running the installer...
01-28 15:16 DEBUG  WindowsFrontend: __init__...
01-28 15:16 DEBUG  WindowsFrontend: on_init...
01-28 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\translations, languages=['en_US', 'en']
01-28 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\translations, languages=['en_US', 'en']
01-28 15:17 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu Netbook Remix, language=en_US, locale=en_US.UTF-8, username=razgriz
01-28 15:17 INFO   root: Received settings
01-28 15:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\translations, languages=['en_US', 'en']
01-28 15:17 DEBUG  TaskList: # Running tasklist...
01-28 15:17 DEBUG  TaskList: ## Running select_target_dir...
01-28 15:17 INFO   WindowsBackend: Installing into C:\ubuntu
01-28 15:17 DEBUG  TaskList: ## Finished select_target_dir
01-28 15:17 DEBUG  TaskList: ## Running create_dir_structure...
01-28 15:17 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-28 15:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-28 15:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-28 15:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-28 15:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-28 15:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-28 15:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-28 15:17 DEBUG  TaskList: ## Finished create_dir_structure
01-28 15:17 DEBUG  TaskList: ## Running uncompress_target_dir...
01-28 15:17 DEBUG  TaskList: ## Finished uncompress_target_dir
01-28 15:17 DEBUG  TaskList: ## Running create_uninstaller...
01-28 15:17 DEBUG  WindowsBackend: Copying uninstaller C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\Y4X1OH1Y\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook Remix
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook Remix.ico
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook Remix
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-28 15:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-28 15:17 DEBUG  TaskList: ## Finished create_uninstaller
01-28 15:17 DEBUG  TaskList: ## Running copy_installation_files...
01-28 15:17 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-28 15:17 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\winboot -> C:\ubuntu\winboot
01-28 15:17 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\data\images\Ubuntu Netbook Remix.ico -> C:\ubuntu\Ubuntu Netbook Remix.ico
01-28 15:17 DEBUG  TaskList: ## Finished copy_installation_files
01-28 15:17 DEBUG  TaskList: ## Running get_iso...
01-28 15:17 DEBUG  CommonBackend: Searching for local CD
01-28 15:17 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp is a valid Ubuntu Netbook Remix CD
01-28 15:17 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl49D3.tmp\casper\filesystem.squashfs
01-28 15:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-28 15:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:17 DEBUG  CommonBackend: Searching for local ISO
01-28 15:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-28 15:17 DEBUG  TaskList: New task get_metalink
01-28 15:17 DEBUG  TaskList: ### Running get_metalink...
01-28 15:17 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) > C:\ubuntu\install
01-28 15:17 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
01-28 15:17 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) > C:\ubuntu\install
01-28 15:17 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
01-28 15:17 DEBUG  TaskList: ### Finished get_metalink
01-28 15:17 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-28 15:17 DEBUG  TaskList: # Cancelling tasklist
01-28 15:17 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-28 15:17 DEBUG  TaskList: # Finished tasklist
01-28 15:23 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-28 15:23 DEBUG  root: Logfile is c:\users\rac\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-28 15:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\rac\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\7Y6ZJJP2\\wubi[1].exe"']
01-28 15:23 DEBUG  CommonBackend: data_dir=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\data
01-28 15:23 DEBUG  WindowsBackend: 7z=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\bin\7z.exe
01-28 15:23 DEBUG  CommonBackend: Fetching basic info...
01-28 15:23 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\7Y6ZJJP2\wubi[1].exe
01-28 15:23 DEBUG  CommonBackend: platform=win32
01-28 15:23 DEBUG  CommonBackend: osname=nt
01-28 15:23 DEBUG  CommonBackend: language=en_US
01-28 15:23 DEBUG  CommonBackend: encoding=cp1252
01-28 15:23 DEBUG  WindowsBackend: arch=amd64
01-28 15:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\data\isolist.ini
01-28 15:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-28 15:23 DEBUG  WindowsBackend: Fetching host info...
01-28 15:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-28 15:23 DEBUG  WindowsBackend: windows version=vista
01-28 15:23 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
01-28 15:23 DEBUG  WindowsBackend: windows_sp=Service Pack 1
01-28 15:23 DEBUG  WindowsBackend: windows_build=6001
01-28 15:23 DEBUG  WindowsBackend: gmt=-5
01-28 15:23 DEBUG  WindowsBackend: country=US
01-28 15:23 DEBUG  WindowsBackend: timezone=America/New_York
01-28 15:23 DEBUG  WindowsBackend: windows_username=rac
01-28 15:23 DEBUG  WindowsBackend: user_full_name=rac
01-28 15:23 DEBUG  WindowsBackend: user_directory=C:\Users\rac
01-28 15:23 DEBUG  WindowsBackend: windows_language_code=1033
01-28 15:23 DEBUG  WindowsBackend: windows_language=English
01-28 15:23 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
01-28 15:23 DEBUG  WindowsBackend: bootloader=vista
01-28 15:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180951.925781 mb free ntfs)
01-28 15:23 DEBUG  WindowsBackend: drive=Drive(C: hd 180951.925781 mb free ntfs)
01-28 15:23 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-28 15:23 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-28 15:23 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-28 15:23 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook Remix
01-28 15:23 DEBUG  WindowsBackend: keyboard_id=67699721
01-28 15:23 DEBUG  WindowsBackend: keyboard_layout=us
01-28 15:23 DEBUG  WindowsBackend: keyboard_variant=
01-28 15:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-28 15:23 DEBUG  CommonBackend: locale=en_US.UTF-8
01-28 15:23 DEBUG  WindowsBackend: total_memory_mb=1789.375
01-28 15:23 DEBUG  CommonBackend: Searching ISOs on USB devices
01-28 15:23 DEBUG  CommonBackend: Searching for local CDs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Ubuntu Netbook Remix CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Kubuntu Netbook CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 INFO   root: Already installed, running the uninstaller...
01-28 15:23 INFO   root: Running the uninstaller...
01-28 15:23 INFO   CommonBackend: This is the uninstaller running
01-28 15:23 DEBUG  WindowsFrontend: __init__...
01-28 15:23 DEBUG  WindowsFrontend: on_init...
01-28 15:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\translations, languages=['en_US', 'en']
01-28 15:23 INFO   root: Received settings
01-28 15:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\translations, languages=['en_US', 'en']
01-28 15:23 DEBUG  TaskList: # Running tasklist...
01-28 15:23 DEBUG  TaskList: ## Running Backup ISO...
01-28 15:23 DEBUG  TaskList: ## Finished Backup ISO
01-28 15:23 DEBUG  TaskList: ## Running Remove bootloader entry...
01-28 15:23 DEBUG  WindowsBackend: Could not find bcd id
01-28 15:23 DEBUG  WindowsBackend: undo_bootini C:
01-28 15:23 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 180951.925781 mb free ntfs)
01-28 15:23 DEBUG  TaskList: ## Finished Remove bootloader entry
01-28 15:23 DEBUG  TaskList: ## Running Remove target dir...
01-28 15:23 DEBUG  CommonBackend: Deleting C:\ubuntu
01-28 15:23 DEBUG  TaskList: ## Finished Remove target dir
01-28 15:23 DEBUG  TaskList: ## Running Remove registry key...
01-28 15:23 DEBUG  TaskList: ## Finished Remove registry key
01-28 15:23 DEBUG  TaskList: # Finished tasklist
01-28 15:23 INFO   root: Almost finished uninstalling
01-28 15:23 INFO   root: Finished uninstallation
01-28 15:23 DEBUG  CommonBackend: Fetching basic info...
01-28 15:23 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\7Y6ZJJP2\wubi[1].exe
01-28 15:23 DEBUG  CommonBackend: platform=win32
01-28 15:23 DEBUG  CommonBackend: osname=nt
01-28 15:23 DEBUG  WindowsBackend: arch=amd64
01-28 15:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\data\isolist.ini
01-28 15:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-28 15:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-28 15:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-28 15:23 DEBUG  WindowsBackend: Fetching host info...
01-28 15:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-28 15:23 DEBUG  WindowsBackend: windows version=vista
01-28 15:23 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
01-28 15:23 DEBUG  WindowsBackend: windows_sp=Service Pack 1
01-28 15:23 DEBUG  WindowsBackend: windows_build=6001
01-28 15:23 DEBUG  WindowsBackend: gmt=-5
01-28 15:23 DEBUG  WindowsBackend: country=US
01-28 15:23 DEBUG  WindowsBackend: timezone=America/New_York
01-28 15:23 DEBUG  WindowsBackend: windows_username=rac
01-28 15:23 DEBUG  WindowsBackend: user_full_name=rac
01-28 15:23 DEBUG  WindowsBackend: user_directory=C:\Users\rac
01-28 15:23 DEBUG  WindowsBackend: windows_language_code=1033
01-28 15:23 DEBUG  WindowsBackend: windows_language=English
01-28 15:23 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
01-28 15:23 DEBUG  WindowsBackend: bootloader=vista
01-28 15:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180953.210938 mb free ntfs)
01-28 15:23 DEBUG  WindowsBackend: drive=Drive(C: hd 180953.210938 mb free ntfs)
01-28 15:23 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-28 15:23 DEBUG  WindowsBackend: uninstaller_path=None
01-28 15:23 DEBUG  WindowsBackend: previous_target_dir=None
01-28 15:23 DEBUG  WindowsBackend: previous_distro_name=None
01-28 15:23 DEBUG  WindowsBackend: keyboard_id=67699721
01-28 15:23 DEBUG  WindowsBackend: keyboard_layout=us
01-28 15:23 DEBUG  WindowsBackend: keyboard_variant=
01-28 15:23 DEBUG  WindowsBackend: total_memory_mb=1789.375
01-28 15:23 DEBUG  CommonBackend: Searching ISOs on USB devices
01-28 15:23 DEBUG  CommonBackend: Searching for local CDs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Ubuntu Netbook Remix CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Kubuntu Netbook CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 INFO   root: Running the installer...
01-28 15:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\translations, languages=['en_US', 'en']
01-28 15:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\translations, languages=['en_US', 'en']
01-28 15:23 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Kubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=rac
01-28 15:23 INFO   root: Received settings
01-28 15:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\translations, languages=['en_US', 'en']
01-28 15:23 DEBUG  TaskList: # Running tasklist...
01-28 15:23 DEBUG  TaskList: ## Running select_target_dir...
01-28 15:23 INFO   WindowsBackend: Installing into C:\ubuntu
01-28 15:23 DEBUG  TaskList: ## Finished select_target_dir
01-28 15:23 DEBUG  TaskList: ## Running create_dir_structure...
01-28 15:23 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-28 15:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-28 15:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-28 15:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-28 15:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-28 15:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-28 15:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-28 15:23 DEBUG  TaskList: ## Finished create_dir_structure
01-28 15:23 DEBUG  TaskList: ## Running uncompress_target_dir...
01-28 15:23 DEBUG  TaskList: ## Finished uncompress_target_dir
01-28 15:23 DEBUG  TaskList: ## Running create_uninstaller...
01-28 15:23 DEBUG  WindowsBackend: Copying uninstaller C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\7Y6ZJJP2\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu Netbook
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu Netbook.ico
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu Netbook
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
01-28 15:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-28 15:23 DEBUG  TaskList: ## Finished create_uninstaller
01-28 15:23 DEBUG  TaskList: ## Running copy_installation_files...
01-28 15:23 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-28 15:23 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\winboot -> C:\ubuntu\winboot
01-28 15:23 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\data\images\Kubuntu Netbook.ico -> C:\ubuntu\Kubuntu Netbook.ico
01-28 15:23 DEBUG  TaskList: ## Finished copy_installation_files
01-28 15:23 DEBUG  TaskList: ## Running get_iso...
01-28 15:23 DEBUG  CommonBackend: Searching for local CD
01-28 15:23 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp is a valid Kubuntu Netbook CD
01-28 15:23 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylE6DD.tmp\casper\filesystem.squashfs
01-28 15:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-28 15:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 15:23 DEBUG  CommonBackend: Searching for local ISO
01-28 15:23 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-28 15:23 DEBUG  TaskList: New task get_metalink
01-28 15:23 DEBUG  TaskList: ### Running get_metalink...
01-28 15:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink) > C:\ubuntu\install
01-28 15:23 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
01-28 15:23 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink](http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink) > C:\ubuntu\install
01-28 15:23 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink](http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
01-28 15:23 DEBUG  TaskList: ### Finished get_metalink
01-28 15:23 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-28 15:23 DEBUG  TaskList: # Cancelling tasklist
01-28 15:23 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-28 15:23 DEBUG  TaskList: # Finished tasklist
01-28 21:21 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-28 21:21 DEBUG  root: Logfile is c:\users\rac\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-28 21:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\rac\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\29OAR3LI\\wubi[1].exe"']
01-28 21:21 DEBUG  CommonBackend: data_dir=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\data
01-28 21:21 DEBUG  WindowsBackend: 7z=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\bin\7z.exe
01-28 21:21 DEBUG  CommonBackend: Fetching basic info...
01-28 21:21 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\29OAR3LI\wubi[1].exe
01-28 21:21 DEBUG  CommonBackend: platform=win32
01-28 21:21 DEBUG  CommonBackend: osname=nt
01-28 21:21 DEBUG  CommonBackend: language=en_US
01-28 21:21 DEBUG  CommonBackend: encoding=cp1252
01-28 21:21 DEBUG  WindowsBackend: arch=amd64
01-28 21:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\data\isolist.ini
01-28 21:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-28 21:21 DEBUG  WindowsBackend: Fetching host info...
01-28 21:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-28 21:21 DEBUG  WindowsBackend: windows version=vista
01-28 21:21 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
01-28 21:21 DEBUG  WindowsBackend: windows_sp=Service Pack 1
01-28 21:21 DEBUG  WindowsBackend: windows_build=6001
01-28 21:21 DEBUG  WindowsBackend: gmt=-5
01-28 21:21 DEBUG  WindowsBackend: country=US
01-28 21:21 DEBUG  WindowsBackend: timezone=America/New_York
01-28 21:21 DEBUG  WindowsBackend: windows_username=rac
01-28 21:21 DEBUG  WindowsBackend: user_full_name=rac
01-28 21:21 DEBUG  WindowsBackend: user_directory=C:\Users\rac
01-28 21:21 DEBUG  WindowsBackend: windows_language_code=1033
01-28 21:21 DEBUG  WindowsBackend: windows_language=English
01-28 21:21 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
01-28 21:21 DEBUG  WindowsBackend: bootloader=vista
01-28 21:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180248.542969 mb free ntfs)
01-28 21:21 DEBUG  WindowsBackend: drive=Drive(C: hd 180248.542969 mb free ntfs)
01-28 21:21 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-28 21:21 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-28 21:21 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-28 21:21 DEBUG  WindowsBackend: previous_distro_name=Kubuntu Netbook
01-28 21:21 DEBUG  WindowsBackend: keyboard_id=67699721
01-28 21:21 DEBUG  WindowsBackend: keyboard_layout=us
01-28 21:21 DEBUG  WindowsBackend: keyboard_variant=
01-28 21:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-28 21:21 DEBUG  CommonBackend: locale=en_US.UTF-8
01-28 21:21 DEBUG  WindowsBackend: total_memory_mb=1789.375
01-28 21:21 DEBUG  CommonBackend: Searching ISOs on USB devices
01-28 21:21 DEBUG  CommonBackend: Searching for local CDs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Ubuntu Netbook Remix CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Kubuntu Netbook CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 INFO   root: Already installed, running the uninstaller...
01-28 21:21 INFO   root: Running the uninstaller...
01-28 21:21 INFO   CommonBackend: This is the uninstaller running
01-28 21:21 DEBUG  WindowsFrontend: __init__...
01-28 21:21 DEBUG  WindowsFrontend: on_init...
01-28 21:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\translations, languages=['en_US', 'en']
01-28 21:21 INFO   root: Received settings
01-28 21:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\translations, languages=['en_US', 'en']
01-28 21:21 DEBUG  TaskList: # Running tasklist...
01-28 21:21 DEBUG  TaskList: ## Running Backup ISO...
01-28 21:21 DEBUG  TaskList: ## Finished Backup ISO
01-28 21:21 DEBUG  TaskList: ## Running Remove bootloader entry...
01-28 21:21 DEBUG  WindowsBackend: Could not find bcd id
01-28 21:21 DEBUG  WindowsBackend: undo_bootini C:
01-28 21:21 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 180248.542969 mb free ntfs)
01-28 21:21 DEBUG  TaskList: ## Finished Remove bootloader entry
01-28 21:21 DEBUG  TaskList: ## Running Remove target dir...
01-28 21:21 DEBUG  CommonBackend: Deleting C:\ubuntu
01-28 21:21 DEBUG  TaskList: ## Finished Remove target dir
01-28 21:21 DEBUG  TaskList: ## Running Remove registry key...
01-28 21:21 DEBUG  TaskList: ## Finished Remove registry key
01-28 21:21 DEBUG  TaskList: # Finished tasklist
01-28 21:21 INFO   root: Almost finished uninstalling
01-28 21:21 INFO   root: Finished uninstallation
01-28 21:21 DEBUG  CommonBackend: Fetching basic info...
01-28 21:21 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\29OAR3LI\wubi[1].exe
01-28 21:21 DEBUG  CommonBackend: platform=win32
01-28 21:21 DEBUG  CommonBackend: osname=nt
01-28 21:21 DEBUG  WindowsBackend: arch=amd64
01-28 21:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\data\isolist.ini
01-28 21:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-28 21:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-28 21:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-28 21:21 DEBUG  WindowsBackend: Fetching host info...
01-28 21:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-28 21:21 DEBUG  WindowsBackend: windows version=vista
01-28 21:21 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
01-28 21:21 DEBUG  WindowsBackend: windows_sp=Service Pack 1
01-28 21:21 DEBUG  WindowsBackend: windows_build=6001
01-28 21:21 DEBUG  WindowsBackend: gmt=-5
01-28 21:21 DEBUG  WindowsBackend: country=US
01-28 21:21 DEBUG  WindowsBackend: timezone=America/New_York
01-28 21:21 DEBUG  WindowsBackend: windows_username=rac
01-28 21:21 DEBUG  WindowsBackend: user_full_name=rac
01-28 21:21 DEBUG  WindowsBackend: user_directory=C:\Users\rac
01-28 21:21 DEBUG  WindowsBackend: windows_language_code=1033
01-28 21:21 DEBUG  WindowsBackend: windows_language=English
01-28 21:21 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
01-28 21:21 DEBUG  WindowsBackend: bootloader=vista
01-28 21:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180250.066406 mb free ntfs)
01-28 21:21 DEBUG  WindowsBackend: drive=Drive(C: hd 180250.066406 mb free ntfs)
01-28 21:21 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-28 21:21 DEBUG  WindowsBackend: uninstaller_path=None
01-28 21:21 DEBUG  WindowsBackend: previous_target_dir=None
01-28 21:21 DEBUG  WindowsBackend: previous_distro_name=None
01-28 21:21 DEBUG  WindowsBackend: keyboard_id=67699721
01-28 21:21 DEBUG  WindowsBackend: keyboard_layout=us
01-28 21:21 DEBUG  WindowsBackend: keyboard_variant=
01-28 21:21 DEBUG  WindowsBackend: total_memory_mb=1789.375
01-28 21:21 DEBUG  CommonBackend: Searching ISOs on USB devices
01-28 21:21 DEBUG  CommonBackend: Searching for local CDs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Ubuntu Netbook Remix CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Kubuntu Netbook CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 INFO   root: Running the installer...
01-28 21:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\translations, languages=['en_US', 'en']
01-28 21:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\translations, languages=['en_US', 'en']
01-28 21:21 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook Remix, language=en_US, locale=en_US.UTF-8, username=rac
01-28 21:21 INFO   root: Received settings
01-28 21:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\translations, languages=['en_US', 'en']
01-28 21:21 DEBUG  TaskList: # Running tasklist...
01-28 21:21 DEBUG  TaskList: ## Running select_target_dir...
01-28 21:21 INFO   WindowsBackend: Installing into C:\ubuntu
01-28 21:21 DEBUG  TaskList: ## Finished select_target_dir
01-28 21:21 DEBUG  TaskList: ## Running create_dir_structure...
01-28 21:21 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-28 21:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-28 21:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-28 21:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-28 21:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-28 21:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-28 21:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-28 21:21 DEBUG  TaskList: ## Finished create_dir_structure
01-28 21:21 DEBUG  TaskList: ## Running uncompress_target_dir...
01-28 21:21 DEBUG  TaskList: ## Finished uncompress_target_dir
01-28 21:21 DEBUG  TaskList: ## Running create_uninstaller...
01-28 21:21 DEBUG  WindowsBackend: Copying uninstaller C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\29OAR3LI\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook Remix
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook Remix.ico
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook Remix
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-28 21:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-28 21:21 DEBUG  TaskList: ## Finished create_uninstaller
01-28 21:21 DEBUG  TaskList: ## Running copy_installation_files...
01-28 21:21 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-28 21:21 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\winboot -> C:\ubuntu\winboot
01-28 21:21 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\data\images\Ubuntu Netbook Remix.ico -> C:\ubuntu\Ubuntu Netbook Remix.ico
01-28 21:21 DEBUG  TaskList: ## Finished copy_installation_files
01-28 21:21 DEBUG  TaskList: ## Running get_iso...
01-28 21:21 DEBUG  CommonBackend: Searching for local CD
01-28 21:21 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pylA39D.tmp is a valid Ubuntu Netbook Remix CD
01-28 21:21 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pylA39D.tmp\casper\filesystem.squashfs
01-28 21:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-28 21:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-28 21:21 DEBUG  CommonBackend: Searching for local ISO
01-28 21:21 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-28 21:21 DEBUG  TaskList: New task get_metalink
01-28 21:21 DEBUG  TaskList: ### Running get_metalink...
01-28 21:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) > C:\ubuntu\install
01-28 21:21 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
01-28 21:21 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) > C:\ubuntu\install
01-28 21:21 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
01-28 21:21 DEBUG  TaskList: ### Finished get_metalink
01-28 21:21 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-28 21:21 DEBUG  TaskList: # Cancelling tasklist
01-28 21:21 DEBUG  TaskList: # Finished tasklist
01-28 21:22 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-01 21:05 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-01 21:05 DEBUG  root: Logfile is c:\users\rac\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-01 21:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\rac\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\CCOJOO3H\\wubi[1].exe"']
02-01 21:05 DEBUG  CommonBackend: data_dir=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\data
02-01 21:05 DEBUG  WindowsBackend: 7z=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\bin\7z.exe
02-01 21:05 DEBUG  CommonBackend: Fetching basic info...
02-01 21:05 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\CCOJOO3H\wubi[1].exe
02-01 21:05 DEBUG  CommonBackend: platform=win32
02-01 21:05 DEBUG  CommonBackend: osname=nt
02-01 21:05 DEBUG  CommonBackend: language=en_US
02-01 21:05 DEBUG  CommonBackend: encoding=cp1252
02-01 21:05 DEBUG  WindowsBackend: arch=amd64
02-01 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\data\isolist.ini
02-01 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-01 21:05 DEBUG  WindowsBackend: Fetching host info...
02-01 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-01 21:05 DEBUG  WindowsBackend: windows version=vista
02-01 21:05 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
02-01 21:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-01 21:05 DEBUG  WindowsBackend: windows_build=6001
02-01 21:05 DEBUG  WindowsBackend: gmt=-5
02-01 21:05 DEBUG  WindowsBackend: country=US
02-01 21:05 DEBUG  WindowsBackend: timezone=America/New_York
02-01 21:05 DEBUG  WindowsBackend: windows_username=rac
02-01 21:05 DEBUG  WindowsBackend: user_full_name=rac
02-01 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\rac
02-01 21:05 DEBUG  WindowsBackend: windows_language_code=1033
02-01 21:05 DEBUG  WindowsBackend: windows_language=English
02-01 21:05 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
02-01 21:05 DEBUG  WindowsBackend: bootloader=vista
02-01 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145956.214844 mb free ntfs)
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 145956.210938 mb free ntfs)
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-01 21:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-01 21:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-01 21:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook Remix
02-01 21:05 DEBUG  WindowsBackend: keyboard_id=67699721
02-01 21:05 DEBUG  WindowsBackend: keyboard_layout=us
02-01 21:05 DEBUG  WindowsBackend: keyboard_variant=
02-01 21:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-01 21:05 DEBUG  CommonBackend: locale=en_US.UTF-8
02-01 21:05 DEBUG  WindowsBackend: total_memory_mb=1789.375
02-01 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
02-01 21:05 DEBUG  CommonBackend: Searching for local CDs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 INFO   root: Already installed, running the uninstaller...
02-01 21:05 INFO   root: Running the uninstaller...
02-01 21:05 INFO   CommonBackend: This is the uninstaller running
02-01 21:05 DEBUG  WindowsFrontend: __init__...
02-01 21:05 DEBUG  WindowsFrontend: on_init...
02-01 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\translations, languages=['en_US', 'en']
02-01 21:05 INFO   root: Received settings
02-01 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\translations, languages=['en_US', 'en']
02-01 21:05 DEBUG  TaskList: # Running tasklist...
02-01 21:05 DEBUG  TaskList: ## Running Backup ISO...
02-01 21:05 DEBUG  TaskList: ## Finished Backup ISO
02-01 21:05 DEBUG  TaskList: ## Running Remove bootloader entry...
02-01 21:05 DEBUG  WindowsBackend: Could not find bcd id
02-01 21:05 DEBUG  WindowsBackend: undo_bootini C:
02-01 21:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145956.210938 mb free ntfs)
02-01 21:05 DEBUG  TaskList: ## Finished Remove bootloader entry
02-01 21:05 DEBUG  TaskList: ## Running Remove target dir...
02-01 21:05 DEBUG  CommonBackend: Deleting C:\ubuntu
02-01 21:05 DEBUG  TaskList: ## Finished Remove target dir
02-01 21:05 DEBUG  TaskList: ## Running Remove registry key...
02-01 21:05 DEBUG  TaskList: ## Finished Remove registry key
02-01 21:05 DEBUG  TaskList: # Finished tasklist
02-01 21:05 INFO   root: Almost finished uninstalling
02-01 21:05 INFO   root: Finished uninstallation
02-01 21:05 DEBUG  CommonBackend: Fetching basic info...
02-01 21:05 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\CCOJOO3H\wubi[1].exe
02-01 21:05 DEBUG  CommonBackend: platform=win32
02-01 21:05 DEBUG  CommonBackend: osname=nt
02-01 21:05 DEBUG  WindowsBackend: arch=amd64
02-01 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\data\isolist.ini
02-01 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-01 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-01 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-01 21:05 DEBUG  WindowsBackend: Fetching host info...
02-01 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-01 21:05 DEBUG  WindowsBackend: windows version=vista
02-01 21:05 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
02-01 21:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-01 21:05 DEBUG  WindowsBackend: windows_build=6001
02-01 21:05 DEBUG  WindowsBackend: gmt=-5
02-01 21:05 DEBUG  WindowsBackend: country=US
02-01 21:05 DEBUG  WindowsBackend: timezone=America/New_York
02-01 21:05 DEBUG  WindowsBackend: windows_username=rac
02-01 21:05 DEBUG  WindowsBackend: user_full_name=rac
02-01 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\rac
02-01 21:05 DEBUG  WindowsBackend: windows_language_code=1033
02-01 21:05 DEBUG  WindowsBackend: windows_language=English
02-01 21:05 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
02-01 21:05 DEBUG  WindowsBackend: bootloader=vista
02-01 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145957.738281 mb free ntfs)
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 145957.738281 mb free ntfs)
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-01 21:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-01 21:05 DEBUG  WindowsBackend: uninstaller_path=None
02-01 21:05 DEBUG  WindowsBackend: previous_target_dir=None
02-01 21:05 DEBUG  WindowsBackend: previous_distro_name=None
02-01 21:05 DEBUG  WindowsBackend: keyboard_id=67699721
02-01 21:05 DEBUG  WindowsBackend: keyboard_layout=us
02-01 21:05 DEBUG  WindowsBackend: keyboard_variant=
02-01 21:05 DEBUG  WindowsBackend: total_memory_mb=1789.375
02-01 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
02-01 21:05 DEBUG  CommonBackend: Searching for local CDs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 INFO   root: Running the installer...
02-01 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\translations, languages=['en_US', 'en']
02-01 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\translations, languages=['en_US', 'en']
02-01 21:05 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook Remix, language=en_US, locale=en_US.UTF-8, username=rac
02-01 21:05 INFO   root: Received settings
02-01 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\translations, languages=['en_US', 'en']
02-01 21:05 DEBUG  TaskList: # Running tasklist...
02-01 21:05 DEBUG  TaskList: ## Running select_target_dir...
02-01 21:05 INFO   WindowsBackend: Installing into C:\ubuntu
02-01 21:05 DEBUG  TaskList: ## Finished select_target_dir
02-01 21:05 DEBUG  TaskList: ## Running create_dir_structure...
02-01 21:05 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-01 21:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-01 21:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-01 21:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-01 21:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-01 21:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-01 21:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-01 21:05 DEBUG  TaskList: ## Finished create_dir_structure
02-01 21:05 DEBUG  TaskList: ## Running uncompress_target_dir...
02-01 21:05 DEBUG  TaskList: ## Finished uncompress_target_dir
02-01 21:05 DEBUG  TaskList: ## Running create_uninstaller...
02-01 21:05 DEBUG  WindowsBackend: Copying uninstaller C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\CCOJOO3H\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook Remix
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook Remix.ico
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook Remix
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-01 21:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-01 21:05 DEBUG  TaskList: ## Finished create_uninstaller
02-01 21:05 DEBUG  TaskList: ## Running copy_installation_files...
02-01 21:05 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-01 21:05 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\winboot -> C:\ubuntu\winboot
02-01 21:05 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\data\images\Ubuntu Netbook Remix.ico -> C:\ubuntu\Ubuntu Netbook Remix.ico
02-01 21:05 DEBUG  TaskList: ## Finished copy_installation_files
02-01 21:05 DEBUG  TaskList: ## Running get_iso...
02-01 21:05 DEBUG  CommonBackend: Searching for local CD
02-01 21:05 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl7D5E.tmp\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-01 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:05 DEBUG  CommonBackend: Searching for local ISO
02-01 21:05 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-01 21:05 DEBUG  TaskList: New task get_metalink
02-01 21:05 DEBUG  TaskList: ### Running get_metalink...
02-01 21:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) > C:\ubuntu\install
02-01 21:05 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
02-01 21:05 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) > C:\ubuntu\install
02-01 21:05 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
02-01 21:05 DEBUG  TaskList: ### Finished get_metalink
02-01 21:05 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-01 21:05 DEBUG  TaskList: # Cancelling tasklist
02-01 21:05 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-01 21:05 DEBUG  TaskList: # Finished tasklist
02-01 21:29 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-01 21:29 DEBUG  root: Logfile is c:\users\rac\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-01 21:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\rac\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\CCOJOO3H\\wubi[2].exe"']
02-01 21:29 DEBUG  CommonBackend: data_dir=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\data
02-01 21:29 DEBUG  WindowsBackend: 7z=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\bin\7z.exe
02-01 21:29 DEBUG  CommonBackend: Fetching basic info...
02-01 21:29 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\CCOJOO3H\wubi[2].exe
02-01 21:29 DEBUG  CommonBackend: platform=win32
02-01 21:29 DEBUG  CommonBackend: osname=nt
02-01 21:29 DEBUG  CommonBackend: language=en_US
02-01 21:29 DEBUG  CommonBackend: encoding=cp1252
02-01 21:29 DEBUG  WindowsBackend: arch=amd64
02-01 21:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\data\isolist.ini
02-01 21:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-01 21:29 DEBUG  WindowsBackend: Fetching host info...
02-01 21:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-01 21:29 DEBUG  WindowsBackend: windows version=vista
02-01 21:29 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
02-01 21:29 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-01 21:29 DEBUG  WindowsBackend: windows_build=6001
02-01 21:29 DEBUG  WindowsBackend: gmt=-5
02-01 21:29 DEBUG  WindowsBackend: country=US
02-01 21:29 DEBUG  WindowsBackend: timezone=America/New_York
02-01 21:29 DEBUG  WindowsBackend: windows_username=rac
02-01 21:29 DEBUG  WindowsBackend: user_full_name=rac
02-01 21:29 DEBUG  WindowsBackend: user_directory=C:\Users\rac
02-01 21:29 DEBUG  WindowsBackend: windows_language_code=1033
02-01 21:29 DEBUG  WindowsBackend: windows_language=English
02-01 21:29 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
02-01 21:29 DEBUG  WindowsBackend: bootloader=vista
02-01 21:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145950.480469 mb free ntfs)
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(C: hd 145950.480469 mb free ntfs)
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-01 21:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-01 21:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-01 21:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook Remix
02-01 21:29 DEBUG  WindowsBackend: keyboard_id=67699721
02-01 21:29 DEBUG  WindowsBackend: keyboard_layout=us
02-01 21:29 DEBUG  WindowsBackend: keyboard_variant=
02-01 21:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-01 21:29 DEBUG  CommonBackend: locale=en_US.UTF-8
02-01 21:29 DEBUG  WindowsBackend: total_memory_mb=1789.375
02-01 21:29 DEBUG  CommonBackend: Searching ISOs on USB devices
02-01 21:29 DEBUG  CommonBackend: Searching for local CDs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 INFO   root: Already installed, running the uninstaller...
02-01 21:29 INFO   root: Running the uninstaller...
02-01 21:29 INFO   CommonBackend: This is the uninstaller running
02-01 21:29 DEBUG  WindowsFrontend: __init__...
02-01 21:29 DEBUG  WindowsFrontend: on_init...
02-01 21:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\translations, languages=['en_US', 'en']
02-01 21:29 INFO   root: Received settings
02-01 21:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\translations, languages=['en_US', 'en']
02-01 21:29 DEBUG  TaskList: # Running tasklist...
02-01 21:29 DEBUG  TaskList: ## Running Backup ISO...
02-01 21:29 DEBUG  TaskList: ## Finished Backup ISO
02-01 21:29 DEBUG  TaskList: ## Running Remove bootloader entry...
02-01 21:29 DEBUG  WindowsBackend: Could not find bcd id
02-01 21:29 DEBUG  WindowsBackend: undo_bootini C:
02-01 21:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145950.480469 mb free ntfs)
02-01 21:29 DEBUG  TaskList: ## Finished Remove bootloader entry
02-01 21:29 DEBUG  TaskList: ## Running Remove target dir...
02-01 21:29 DEBUG  CommonBackend: Deleting C:\ubuntu
02-01 21:29 DEBUG  TaskList: ## Finished Remove target dir
02-01 21:29 DEBUG  TaskList: ## Running Remove registry key...
02-01 21:29 DEBUG  TaskList: ## Finished Remove registry key
02-01 21:29 DEBUG  TaskList: # Finished tasklist
02-01 21:29 INFO   root: Almost finished uninstalling
02-01 21:29 INFO   root: Finished uninstallation
02-01 21:29 DEBUG  CommonBackend: Fetching basic info...
02-01 21:29 DEBUG  CommonBackend: original_exe=C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\CCOJOO3H\wubi[2].exe
02-01 21:29 DEBUG  CommonBackend: platform=win32
02-01 21:29 DEBUG  CommonBackend: osname=nt
02-01 21:29 DEBUG  WindowsBackend: arch=amd64
02-01 21:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\data\isolist.ini
02-01 21:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-01 21:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-01 21:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-01 21:29 DEBUG  WindowsBackend: Fetching host info...
02-01 21:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-01 21:29 DEBUG  WindowsBackend: windows version=vista
02-01 21:29 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
02-01 21:29 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-01 21:29 DEBUG  WindowsBackend: windows_build=6001
02-01 21:29 DEBUG  WindowsBackend: gmt=-5
02-01 21:29 DEBUG  WindowsBackend: country=US
02-01 21:29 DEBUG  WindowsBackend: timezone=America/New_York
02-01 21:29 DEBUG  WindowsBackend: windows_username=rac
02-01 21:29 DEBUG  WindowsBackend: user_full_name=rac
02-01 21:29 DEBUG  WindowsBackend: user_directory=C:\Users\rac
02-01 21:29 DEBUG  WindowsBackend: windows_language_code=1033
02-01 21:29 DEBUG  WindowsBackend: windows_language=English
02-01 21:29 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor TF-20
02-01 21:29 DEBUG  WindowsBackend: bootloader=vista
02-01 21:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145952.003906 mb free ntfs)
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(C: hd 145952.003906 mb free ntfs)
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-01 21:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-01 21:29 DEBUG  WindowsBackend: uninstaller_path=None
02-01 21:29 DEBUG  WindowsBackend: previous_target_dir=None
02-01 21:29 DEBUG  WindowsBackend: previous_distro_name=None
02-01 21:29 DEBUG  WindowsBackend: keyboard_id=67699721
02-01 21:29 DEBUG  WindowsBackend: keyboard_layout=us
02-01 21:29 DEBUG  WindowsBackend: keyboard_variant=
02-01 21:29 DEBUG  WindowsBackend: total_memory_mb=1789.375
02-01 21:29 DEBUG  CommonBackend: Searching ISOs on USB devices
02-01 21:29 DEBUG  CommonBackend: Searching for local CDs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-01 21:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:29 INFO   root: Running the installer...
02-01 21:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\translations, languages=['en_US', 'en']
02-01 21:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\translations, languages=['en_US', 'en']
02-01 21:30 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook Remix, language=en_US, locale=en_US.UTF-8, username=rac
02-01 21:30 INFO   root: Received settings
02-01 21:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\translations, languages=['en_US', 'en']
02-01 21:30 DEBUG  TaskList: # Running tasklist...
02-01 21:30 DEBUG  TaskList: ## Running select_target_dir...
02-01 21:30 INFO   WindowsBackend: Installing into C:\ubuntu
02-01 21:30 DEBUG  TaskList: ## Finished select_target_dir
02-01 21:30 DEBUG  TaskList: ## Running create_dir_structure...
02-01 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-01 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-01 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-01 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-01 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-01 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-01 21:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-01 21:30 DEBUG  TaskList: ## Finished create_dir_structure
02-01 21:30 DEBUG  TaskList: ## Running uncompress_target_dir...
02-01 21:30 DEBUG  TaskList: ## Finished uncompress_target_dir
02-01 21:30 DEBUG  TaskList: ## Running create_uninstaller...
02-01 21:30 DEBUG  WindowsBackend: Copying uninstaller C:\Users\rac\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\CCOJOO3H\wubi[2].exe -> C:\ubuntu\uninstall-wubi.exe
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook Remix
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook Remix.ico
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook Remix
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-01 21:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-01 21:30 DEBUG  TaskList: ## Finished create_uninstaller
02-01 21:30 DEBUG  TaskList: ## Running copy_installation_files...
02-01 21:30 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-01 21:30 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\winboot -> C:\ubuntu\winboot
02-01 21:30 DEBUG  WindowsBackend: Copying C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\data\images\Ubuntu Netbook Remix.ico -> C:\ubuntu\Ubuntu Netbook Remix.ico
02-01 21:30 DEBUG  TaskList: ## Finished copy_installation_files
02-01 21:30 DEBUG  TaskList: ## Running get_iso...
02-01 21:30 DEBUG  CommonBackend: Searching for local CD
02-01 21:30 DEBUG  Distro:   checking whether C:\Users\rac\AppData\Local\Temp\pyl395C.tmp is a valid Ubuntu Netbook Remix CD
02-01 21:30 DEBUG  Distro:     does not contain C:\Users\rac\AppData\Local\Temp\pyl395C.tmp\casper\filesystem.squashfs
02-01 21:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-01 21:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-01 21:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-01 21:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-01 21:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-01 21:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-01 21:30 DEBUG  CommonBackend: Searching for local ISO
02-01 21:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-01 21:30 DEBUG  TaskList: New task get_metalink
02-01 21:30 DEBUG  TaskList: ### Running get_metalink...
02-01 21:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) > C:\ubuntu\install
02-01 21:30 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
02-01 21:30 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) > C:\ubuntu\install
02-01 21:30 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
02-01 21:30 DEBUG  TaskList: ### Finished get_metalink
02-01 21:30 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-01 21:30 DEBUG  TaskList: # Cancelling tasklist
02-01 21:30 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-01 21:30 DEBUG  TaskList: # Finished tasklist

```

---

### Post by NightwishFan on 2010-02-01
Are you running Wubi from the Ubuntu CD or just the standalone .exe? I would recommend to use the CD if you have slower internet, as it will download the entire Ubuntu ISO.

---

### Post by Razbuntu on 2010-02-01
Stand Alone, And It Works on my xp and win7 computersAnd it worked on vista before

---

### Post by NightwishFan on 2010-02-01
What platform are you using to install wubi with? Is it networked and how? What edition of Ubuntu are you trying to install?


It seems like it does not want to download the image, though I could be wrong.

Edit: It says something about unable to download metalink, perhaps the server is unreachable at the moment?

---

### Post by Razbuntu on 2010-02-01
Wireless, 9.10  netbook remix

---

### Post by NightwishFan on 2010-02-01
If the standalone method continues to fail, perhaps redownload another .exe. If that fails perhaps download the Ubuntu NBR Live CD and install using wubi from there.

---

### Post by Razbuntu on 2010-02-01
Win vista 32-bit basic is the platform.

---

### Post by Razbuntu on 2010-02-01
tryied the exe failed, where is the nbr cd

---

### Post by NightwishFan on 2010-02-01
Here is a download link for a x86(32-bit) live CD of UNR.
[http://releases.ubuntu.com/karmic/ubuntu-9.10-netbook-remix-i386.iso](http://releases.ubuntu.com/karmic/ubuntu-9.10-netbook-remix-i386.iso)

The whole list is here:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

