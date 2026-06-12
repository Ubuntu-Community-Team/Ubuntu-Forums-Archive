---
title: "Permission Denied? Cancels installation. (11.10)"
date: 2011-12-18
forum: General Help
---

### Post by jkp95 on 2011-12-18
```
12-11 16:19 INFO   root: === wubi 11.10 rev245 ===
12-11 16:19 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-11 16:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jack\\Downloads\\wubi.exe"']
12-11 16:19 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\data
12-11 16:19 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\bin\7z.exe
12-11 16:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-11 16:19 DEBUG  CommonBackend: Fetching basic info...
12-11 16:19 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi.exe
12-11 16:19 DEBUG  CommonBackend: platform=win32
12-11 16:19 DEBUG  CommonBackend: osname=nt
12-11 16:19 DEBUG  CommonBackend: language=en_CA
12-11 16:19 DEBUG  CommonBackend: encoding=cp1252
12-11 16:19 DEBUG  WindowsBackend: arch=amd64
12-11 16:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\data\isolist.ini
12-11 16:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-11 16:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-11 16:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-11 16:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-11 16:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-11 16:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-11 16:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-11 16:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-11 16:19 DEBUG  WindowsBackend: Fetching host info...
12-11 16:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-11 16:19 DEBUG  WindowsBackend: windows version=vista
12-11 16:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-11 16:19 DEBUG  WindowsBackend: windows_sp=None
12-11 16:19 DEBUG  WindowsBackend: windows_build=7601
12-11 16:19 DEBUG  WindowsBackend: gmt=-5
12-11 16:19 DEBUG  WindowsBackend: country=CA
12-11 16:19 DEBUG  WindowsBackend: timezone=America/Montreal
12-11 16:19 DEBUG  WindowsBackend: windows_username=Jack
12-11 16:19 DEBUG  WindowsBackend: user_full_name=Jack
12-11 16:19 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-11 16:19 DEBUG  WindowsBackend: windows_language_code=1033
12-11 16:19 DEBUG  WindowsBackend: windows_language=English
12-11 16:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-11 16:19 DEBUG  WindowsBackend: bootloader=vista
12-11 16:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 318685.261719 mb free ntfs)
12-11 16:19 DEBUG  WindowsBackend: drive=Drive(C: hd 318685.261719 mb free ntfs)
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.21484375 mb free ntfs)
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
12-11 16:20 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-11 16:20 DEBUG  WindowsBackend: uninstaller_path=None
12-11 16:20 DEBUG  WindowsBackend: previous_target_dir=None
12-11 16:20 DEBUG  WindowsBackend: previous_distro_name=None
12-11 16:20 DEBUG  WindowsBackend: keyboard_id=67702793
12-11 16:20 DEBUG  WindowsBackend: keyboard_layout=us
12-11 16:20 DEBUG  WindowsBackend: keyboard_variant=
12-11 16:20 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-11 16:20 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-11 16:20 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-11 16:20 DEBUG  CommonBackend: Searching ISOs on USB devices
12-11 16:20 DEBUG  CommonBackend: Searching for local CDs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 INFO   root: Running the installer...
12-11 16:20 DEBUG  WindowsFrontend: __init__...
12-11 16:20 DEBUG  WindowsFrontend: on_init...
12-11 16:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\translations, languages=['en_CA', 'en']
12-11 16:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\translations, languages=['en_CA', 'en']
12-11 16:20 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jack
12-11 16:20 INFO   root: Received settings
12-11 16:20 DEBUG  CommonBackend: Searching for local CD
12-11 16:20 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylE43.tmp is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-11 16:20 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-11 16:20 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-11 16:20 DEBUG  CommonBackend: Searching for local ISO
12-11 16:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\translations, languages=['en_US', 'en']
12-11 16:20 DEBUG  TaskList: # Running tasklist...
12-11 16:20 DEBUG  TaskList: ## Running select_target_dir...
12-11 16:20 INFO   WindowsBackend: Installing into C:\ubuntu
12-11 16:20 DEBUG  TaskList: ## Finished select_target_dir
12-11 16:20 DEBUG  TaskList: ## Running create_dir_structure...
12-11 16:20 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-11 16:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-11 16:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-11 16:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-11 16:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-11 16:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-11 16:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-11 16:20 DEBUG  TaskList: ## Finished create_dir_structure
12-11 16:20 DEBUG  TaskList: ## Running create_uninstaller...
12-11 16:20 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jack\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-11 16:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-11 16:20 DEBUG  TaskList: ## Finished create_uninstaller
12-11 16:20 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-11 16:20 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-11 16:20 DEBUG  TaskList: ## Running get_diskimage...
12-11 16:20 DEBUG  TaskList: New task download
12-11 16:20 DEBUG  TaskList: ### Running download...
12-11 16:20 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-11 16:20 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-11 16:26 DEBUG  TaskList: ### Finished download
12-11 16:26 DEBUG  downloader: download finished (read 507143012 bytes)
12-11 16:26 DEBUG  TaskList: ## Finished get_diskimage
12-11 16:26 DEBUG  TaskList: ## Running extract_diskimage...
12-11 16:27 DEBUG  TaskList: ## Finished extract_diskimage
12-11 16:27 DEBUG  TaskList: ## Running choose_disk_sizes...
12-11 16:27 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-11 16:27 DEBUG  TaskList: ## Finished choose_disk_sizes
12-11 16:27 DEBUG  TaskList: ## Running expand_diskimage...
12-11 16:30 DEBUG  TaskList: ## Finished expand_diskimage
12-11 16:30 DEBUG  TaskList: ## Running create_swap_diskimage...
12-11 16:30 DEBUG  TaskList: ## Finished create_swap_diskimage
12-11 16:30 DEBUG  TaskList: ## Running modify_bootloader...
12-11 16:30 DEBUG  TaskList: New task modify_bcd
12-11 16:30 DEBUG  TaskList: ### Running modify_bcd...
12-11 16:30 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 318685.261719 mb free ntfs)
12-11 16:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {dc59b0bb-fded-11e0-89c9-6431503ef3aa}
12-11 16:30 DEBUG  TaskList: ### Finished modify_bcd
12-11 16:30 DEBUG  TaskList: New task modify_bcd
12-11 16:30 DEBUG  TaskList: ### Running modify_bcd...
12-11 16:30 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1692.21484375 mb free ntfs)
12-11 16:30 DEBUG  WindowsBackend: BCD has already been modified
12-11 16:30 DEBUG  TaskList: ### Finished modify_bcd
12-11 16:30 DEBUG  TaskList: New task modify_bcd
12-11 16:30 DEBUG  TaskList: ### Running modify_bcd...
12-11 16:30 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
12-11 16:30 DEBUG  WindowsBackend: BCD has already been modified
12-11 16:30 DEBUG  TaskList: ### Finished modify_bcd
12-11 16:30 DEBUG  TaskList: New task modify_bcd
12-11 16:30 DEBUG  TaskList: ### Running modify_bcd...
12-11 16:30 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
12-11 16:30 DEBUG  WindowsBackend: BCD has already been modified
12-11 16:30 DEBUG  TaskList: ### Finished modify_bcd
12-11 16:30 DEBUG  TaskList: New task modify_bcd
12-11 16:30 DEBUG  TaskList: ### Running modify_bcd...
12-11 16:30 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
12-11 16:30 DEBUG  WindowsBackend: BCD has already been modified
12-11 16:30 DEBUG  TaskList: ### Finished modify_bcd
12-11 16:30 DEBUG  TaskList: New task modify_bcd
12-11 16:30 DEBUG  TaskList: ### Running modify_bcd...
12-11 16:30 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
12-11 16:30 DEBUG  WindowsBackend: BCD has already been modified
12-11 16:30 DEBUG  TaskList: ### Finished modify_bcd
12-11 16:30 DEBUG  TaskList: New task modify_bcd
12-11 16:30 DEBUG  TaskList: ### Running modify_bcd...
12-11 16:30 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
12-11 16:30 DEBUG  WindowsBackend: BCD has already been modified
12-11 16:30 DEBUG  TaskList: ### Finished modify_bcd
12-11 16:30 DEBUG  TaskList: ## Finished modify_bootloader
12-11 16:30 DEBUG  TaskList: ## Running diskimage_bootloader...
12-11 16:30 DEBUG  WindowsBackend: Copying C:\Users\Jack\AppData\Local\Temp\pylE43.tmp\winboot -> C:\ubuntu\winboot
12-11 16:30 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-11 16:30 DEBUG  TaskList: # Cancelling tasklist
12-11 16:30 DEBUG  TaskList: # Finished tasklist
12-11 16:30 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 10:45 INFO   root: === wubi 11.10 rev245 ===
12-18 10:45 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 10:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-18 10:45 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\data
12-18 10:45 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\bin\7z.exe
12-18 10:45 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 10:45 DEBUG  CommonBackend: Fetching basic info...
12-18 10:45 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-18 10:45 DEBUG  CommonBackend: platform=win32
12-18 10:45 DEBUG  CommonBackend: osname=nt
12-18 10:45 DEBUG  CommonBackend: language=en_CA
12-18 10:45 DEBUG  CommonBackend: encoding=cp1252
12-18 10:45 DEBUG  WindowsBackend: arch=amd64
12-18 10:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\data\isolist.ini
12-18 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 10:45 DEBUG  WindowsBackend: Fetching host info...
12-18 10:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 10:45 DEBUG  WindowsBackend: windows version=vista
12-18 10:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 10:45 DEBUG  WindowsBackend: windows_sp=None
12-18 10:45 DEBUG  WindowsBackend: windows_build=7601
12-18 10:45 DEBUG  WindowsBackend: gmt=-5
12-18 10:45 DEBUG  WindowsBackend: country=CA
12-18 10:45 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 10:45 DEBUG  WindowsBackend: windows_username=Jack
12-18 10:45 DEBUG  WindowsBackend: user_full_name=Jack
12-18 10:45 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 10:45 DEBUG  WindowsBackend: windows_language_code=1033
12-18 10:45 DEBUG  WindowsBackend: windows_language=English
12-18 10:45 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 10:45 DEBUG  WindowsBackend: bootloader=vista
12-18 10:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 258580.332031 mb free ntfs)
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(C: hd 258580.332031 mb free ntfs)
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.0859375 mb free ntfs)
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 10:45 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
12-18 10:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-18 10:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-18 10:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 10:45 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 10:45 DEBUG  WindowsBackend: keyboard_layout=us
12-18 10:45 DEBUG  WindowsBackend: keyboard_variant=
12-18 10:45 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 10:45 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 10:45 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 10:45 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 10:45 DEBUG  CommonBackend: Searching for local CDs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 10:45 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:45 INFO   root: Running the uninstaller...
12-18 10:45 INFO   CommonBackend: This is the uninstaller running
12-18 10:45 DEBUG  WindowsFrontend: __init__...
12-18 10:45 DEBUG  WindowsFrontend: on_init...
12-18 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl46D1.tmp\translations, languages=['en_CA', 'en']
12-18 10:46 INFO   WindowsFrontend: Operation cancelled
12-18 10:46 DEBUG  WindowsFrontend: frontend.quit
12-18 10:46 DEBUG  WindowsFrontend: frontend.on_quit
12-18 10:46 DEBUG  root: application.on_quit
12-18 10:46 INFO   root: sys.exit
12-18 10:46 INFO   root: === wubi 11.10 rev245 ===
12-18 10:46 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 10:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-18 10:46 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\data
12-18 10:46 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\bin\7z.exe
12-18 10:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 10:46 DEBUG  CommonBackend: Fetching basic info...
12-18 10:46 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-18 10:46 DEBUG  CommonBackend: platform=win32
12-18 10:46 DEBUG  CommonBackend: osname=nt
12-18 10:46 DEBUG  CommonBackend: language=en_CA
12-18 10:46 DEBUG  CommonBackend: encoding=cp1252
12-18 10:46 DEBUG  WindowsBackend: arch=amd64
12-18 10:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\data\isolist.ini
12-18 10:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 10:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 10:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 10:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 10:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 10:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 10:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 10:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 10:46 DEBUG  WindowsBackend: Fetching host info...
12-18 10:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 10:46 DEBUG  WindowsBackend: windows version=vista
12-18 10:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 10:46 DEBUG  WindowsBackend: windows_sp=None
12-18 10:46 DEBUG  WindowsBackend: windows_build=7601
12-18 10:46 DEBUG  WindowsBackend: gmt=-5
12-18 10:46 DEBUG  WindowsBackend: country=CA
12-18 10:46 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 10:46 DEBUG  WindowsBackend: windows_username=Jack
12-18 10:46 DEBUG  WindowsBackend: user_full_name=Jack
12-18 10:46 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 10:46 DEBUG  WindowsBackend: windows_language_code=1033
12-18 10:46 DEBUG  WindowsBackend: windows_language=English
12-18 10:46 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 10:46 DEBUG  WindowsBackend: bootloader=vista
12-18 10:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 258579.601563 mb free ntfs)
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(C: hd 258579.601563 mb free ntfs)
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.0859375 mb free ntfs)
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 10:46 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
12-18 10:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-18 10:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-18 10:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 10:46 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 10:46 DEBUG  WindowsBackend: keyboard_layout=us
12-18 10:46 DEBUG  WindowsBackend: keyboard_variant=
12-18 10:46 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 10:46 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 10:46 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 10:46 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 10:46 DEBUG  CommonBackend: Searching for local CDs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 10:46 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:46 INFO   root: Running the uninstaller...
12-18 10:46 INFO   CommonBackend: This is the uninstaller running
12-18 10:46 DEBUG  WindowsFrontend: __init__...
12-18 10:46 DEBUG  WindowsFrontend: on_init...
12-18 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\translations, languages=['en_CA', 'en']
12-18 10:46 INFO   root: Received settings
12-18 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\translations, languages=['en_CA', 'en']
12-18 10:46 DEBUG  TaskList: # Running tasklist...
12-18 10:46 DEBUG  TaskList: ## Running Remove bootloader entry...
12-18 10:46 DEBUG  WindowsBackend: Removing bcd entry {dc59b0bb-fded-11e0-89c9-6431503ef3aa}
12-18 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-18 10:46 DEBUG  WindowsBackend: undo_bootini C:
12-18 10:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 258579.601563 mb free ntfs)
12-18 10:46 DEBUG  WindowsBackend: undo_bootini D:
12-18 10:46 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1692.0859375 mb free ntfs)
12-18 10:46 DEBUG  WindowsBackend: undo_bootini F:
12-18 10:46 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
12-18 10:46 DEBUG  WindowsBackend: undo_bootini G:
12-18 10:46 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
12-18 10:46 DEBUG  WindowsBackend: undo_bootini H:
12-18 10:46 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
12-18 10:46 DEBUG  WindowsBackend: undo_bootini I:
12-18 10:46 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
12-18 10:46 DEBUG  TaskList: ## Finished Remove bootloader entry
12-18 10:46 DEBUG  TaskList: ## Running Remove target dir...
12-18 10:46 DEBUG  CommonBackend: Deleting C:\ubuntu
12-18 10:46 DEBUG  TaskList: ## Finished Remove target dir
12-18 10:46 DEBUG  TaskList: ## Running Remove registry key...
12-18 10:46 DEBUG  TaskList: ## Finished Remove registry key
12-18 10:46 DEBUG  TaskList: # Finished tasklist
12-18 10:46 INFO   root: Almost finished uninstalling
12-18 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl7CFE.tmp\translations, languages=['en_CA', 'en']
12-18 10:46 INFO   root: Finished uninstallation
12-18 10:46 DEBUG  root: application.quit
12-18 10:46 DEBUG  WindowsFrontend: frontend.quit
12-18 10:46 DEBUG  WindowsFrontend: frontend.on_quit
12-18 10:46 DEBUG  root: application.on_quit
12-18 10:46 INFO   root: sys.exit
12-18 10:47 INFO   root: === wubi 11.10 rev245 ===
12-18 10:47 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 10:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jack\\Downloads\\wubi (1).exe"']
12-18 10:47 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\data
12-18 10:47 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\bin\7z.exe
12-18 10:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 10:47 DEBUG  CommonBackend: Fetching basic info...
12-18 10:47 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi (1).exe
12-18 10:47 DEBUG  CommonBackend: platform=win32
12-18 10:47 DEBUG  CommonBackend: osname=nt
12-18 10:47 DEBUG  CommonBackend: language=en_CA
12-18 10:47 DEBUG  CommonBackend: encoding=cp1252
12-18 10:47 DEBUG  WindowsBackend: arch=amd64
12-18 10:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\data\isolist.ini
12-18 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 10:47 DEBUG  WindowsBackend: Fetching host info...
12-18 10:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 10:47 DEBUG  WindowsBackend: windows version=vista
12-18 10:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 10:47 DEBUG  WindowsBackend: windows_sp=None
12-18 10:47 DEBUG  WindowsBackend: windows_build=7601
12-18 10:47 DEBUG  WindowsBackend: gmt=-5
12-18 10:47 DEBUG  WindowsBackend: country=CA
12-18 10:47 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 10:47 DEBUG  WindowsBackend: windows_username=Jack
12-18 10:47 DEBUG  WindowsBackend: user_full_name=Jack
12-18 10:47 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 10:47 DEBUG  WindowsBackend: windows_language_code=1033
12-18 10:47 DEBUG  WindowsBackend: windows_language=English
12-18 10:47 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 10:47 DEBUG  WindowsBackend: bootloader=vista
12-18 10:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 261754.894531 mb free ntfs)
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(C: hd 261754.894531 mb free ntfs)
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.21484375 mb free ntfs)
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 10:47 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
12-18 10:47 DEBUG  WindowsBackend: uninstaller_path=None
12-18 10:47 DEBUG  WindowsBackend: previous_target_dir=None
12-18 10:47 DEBUG  WindowsBackend: previous_distro_name=None
12-18 10:47 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 10:47 DEBUG  WindowsBackend: keyboard_layout=us
12-18 10:47 DEBUG  WindowsBackend: keyboard_variant=
12-18 10:47 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 10:47 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 10:47 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 10:47 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 10:47 DEBUG  CommonBackend: Searching for local CDs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 INFO   root: Running the installer...
12-18 10:47 DEBUG  WindowsFrontend: __init__...
12-18 10:47 DEBUG  WindowsFrontend: on_init...
12-18 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\translations, languages=['en_CA', 'en']
12-18 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\translations, languages=['en_CA', 'en']
12-18 10:47 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jack
12-18 10:47 INFO   root: Received settings
12-18 10:47 DEBUG  CommonBackend: Searching for local CD
12-18 10:47 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 10:47 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 10:47 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 10:47 DEBUG  CommonBackend: Searching for local ISO
12-18 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\translations, languages=['en_US', 'en']
12-18 10:47 DEBUG  TaskList: # Running tasklist...
12-18 10:47 DEBUG  TaskList: ## Running select_target_dir...
12-18 10:47 INFO   WindowsBackend: Installing into C:\ubuntu
12-18 10:47 DEBUG  TaskList: ## Finished select_target_dir
12-18 10:47 DEBUG  TaskList: ## Running create_dir_structure...
12-18 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-18 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-18 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-18 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-18 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-18 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-18 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-18 10:47 DEBUG  TaskList: ## Finished create_dir_structure
12-18 10:47 DEBUG  TaskList: ## Running create_uninstaller...
12-18 10:47 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jack\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-18 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-18 10:47 DEBUG  TaskList: ## Finished create_uninstaller
12-18 10:47 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-18 10:47 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-18 10:47 DEBUG  TaskList: ## Running get_diskimage...
12-18 10:47 DEBUG  TaskList: New task download
12-18 10:47 DEBUG  TaskList: ### Running download...
12-18 10:47 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-18 10:47 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-18 10:52 DEBUG  TaskList: ### Finished download
12-18 10:52 DEBUG  downloader: download finished (read 507143012 bytes)
12-18 10:52 DEBUG  TaskList: ## Finished get_diskimage
12-18 10:52 DEBUG  TaskList: ## Running extract_diskimage...
12-18 10:53 DEBUG  TaskList: ## Finished extract_diskimage
12-18 10:53 DEBUG  TaskList: ## Running choose_disk_sizes...
12-18 10:53 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-18 10:53 DEBUG  TaskList: ## Finished choose_disk_sizes
12-18 10:53 DEBUG  TaskList: ## Running expand_diskimage...
12-18 10:58 DEBUG  TaskList: ## Finished expand_diskimage
12-18 10:58 DEBUG  TaskList: ## Running create_swap_diskimage...
12-18 10:58 DEBUG  TaskList: ## Finished create_swap_diskimage
12-18 10:58 DEBUG  TaskList: ## Running modify_bootloader...
12-18 10:58 DEBUG  TaskList: New task modify_bcd
12-18 10:58 DEBUG  TaskList: ### Running modify_bcd...
12-18 10:58 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 261754.894531 mb free ntfs)
12-18 10:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {dc59b0bc-fded-11e0-89c9-6431503ef3aa}
12-18 10:58 DEBUG  TaskList: ### Finished modify_bcd
12-18 10:58 DEBUG  TaskList: New task modify_bcd
12-18 10:58 DEBUG  TaskList: ### Running modify_bcd...
12-18 10:58 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1692.21484375 mb free ntfs)
12-18 10:58 DEBUG  WindowsBackend: BCD has already been modified
12-18 10:58 DEBUG  TaskList: ### Finished modify_bcd
12-18 10:58 DEBUG  TaskList: New task modify_bcd
12-18 10:58 DEBUG  TaskList: ### Running modify_bcd...
12-18 10:58 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
12-18 10:58 DEBUG  WindowsBackend: BCD has already been modified
12-18 10:58 DEBUG  TaskList: ### Finished modify_bcd
12-18 10:58 DEBUG  TaskList: New task modify_bcd
12-18 10:58 DEBUG  TaskList: ### Running modify_bcd...
12-18 10:58 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
12-18 10:58 DEBUG  WindowsBackend: BCD has already been modified
12-18 10:58 DEBUG  TaskList: ### Finished modify_bcd
12-18 10:58 DEBUG  TaskList: New task modify_bcd
12-18 10:58 DEBUG  TaskList: ### Running modify_bcd...
12-18 10:58 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
12-18 10:58 DEBUG  WindowsBackend: BCD has already been modified
12-18 10:58 DEBUG  TaskList: ### Finished modify_bcd
12-18 10:58 DEBUG  TaskList: New task modify_bcd
12-18 10:58 DEBUG  TaskList: ### Running modify_bcd...
12-18 10:58 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
12-18 10:58 DEBUG  WindowsBackend: BCD has already been modified
12-18 10:58 DEBUG  TaskList: ### Finished modify_bcd
12-18 10:58 DEBUG  TaskList: ## Finished modify_bootloader
12-18 10:58 DEBUG  TaskList: ## Running diskimage_bootloader...
12-18 10:58 DEBUG  WindowsBackend: Copying C:\Users\Jack\AppData\Local\Temp\pyl3B8B.tmp\winboot -> C:\ubuntu\winboot
12-18 10:58 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 10:58 DEBUG  TaskList: # Cancelling tasklist
12-18 10:58 DEBUG  TaskList: # Finished tasklist
12-18 10:58 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 11:00 INFO   root: === wubi 11.10 rev245 ===
12-18 11:00 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 11:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jack\\Downloads\\wubi (1).exe"']
12-18 11:00 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\data
12-18 11:00 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\bin\7z.exe
12-18 11:00 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 11:00 DEBUG  CommonBackend: Fetching basic info...
12-18 11:00 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi (1).exe
12-18 11:00 DEBUG  CommonBackend: platform=win32
12-18 11:00 DEBUG  CommonBackend: osname=nt
12-18 11:00 DEBUG  CommonBackend: language=en_CA
12-18 11:00 DEBUG  CommonBackend: encoding=cp1252
12-18 11:00 DEBUG  WindowsBackend: arch=amd64
12-18 11:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\data\isolist.ini
12-18 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:00 DEBUG  WindowsBackend: Fetching host info...
12-18 11:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:00 DEBUG  WindowsBackend: windows version=vista
12-18 11:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:00 DEBUG  WindowsBackend: windows_sp=None
12-18 11:00 DEBUG  WindowsBackend: windows_build=7601
12-18 11:00 DEBUG  WindowsBackend: gmt=-5
12-18 11:00 DEBUG  WindowsBackend: country=CA
12-18 11:00 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:00 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:00 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:00 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:00 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:00 DEBUG  WindowsBackend: windows_language=English
12-18 11:00 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:00 DEBUG  WindowsBackend: bootloader=vista
12-18 11:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 259661.605469 mb free ntfs)
12-18 11:00 DEBUG  WindowsBackend: drive=Drive(C: hd 259661.605469 mb free ntfs)
12-18 11:00 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.0859375 mb free ntfs)
12-18 11:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:02 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:02 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:02 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:02 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:02 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-18 11:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-18 11:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 11:02 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:02 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:02 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:02 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 11:02 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 11:02 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:02 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:02 DEBUG  CommonBackend: Searching for local CDs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:02 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:03 INFO   root: Already installed, running the uninstaller...
12-18 11:03 INFO   root: Running the uninstaller...
12-18 11:03 INFO   CommonBackend: This is the uninstaller running
12-18 11:03 DEBUG  WindowsFrontend: __init__...
12-18 11:03 DEBUG  WindowsFrontend: on_init...
12-18 11:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\translations, languages=['en_CA', 'en']
12-18 11:03 INFO   root: Received settings
12-18 11:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\translations, languages=['en_CA', 'en']
12-18 11:03 DEBUG  TaskList: # Running tasklist...
12-18 11:03 DEBUG  TaskList: ## Running Remove bootloader entry...
12-18 11:03 DEBUG  WindowsBackend: Removing bcd entry {dc59b0bc-fded-11e0-89c9-6431503ef3aa}
12-18 11:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-18 11:03 DEBUG  WindowsBackend: undo_bootini C:
12-18 11:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 259661.605469 mb free ntfs)
12-18 11:03 DEBUG  WindowsBackend: undo_bootini D:
12-18 11:03 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1692.0859375 mb free ntfs)
12-18 11:03 DEBUG  WindowsBackend: undo_bootini F:
12-18 11:03 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: undo_bootini G:
12-18 11:03 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: undo_bootini H:
12-18 11:03 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: undo_bootini I:
12-18 11:03 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
12-18 11:03 DEBUG  TaskList: ## Finished Remove bootloader entry
12-18 11:03 DEBUG  TaskList: ## Running Remove target dir...
12-18 11:03 DEBUG  CommonBackend: Deleting C:\ubuntu
12-18 11:03 DEBUG  TaskList: ## Finished Remove target dir
12-18 11:03 DEBUG  TaskList: ## Running Remove registry key...
12-18 11:03 DEBUG  TaskList: ## Finished Remove registry key
12-18 11:03 DEBUG  TaskList: # Finished tasklist
12-18 11:03 INFO   root: Almost finished uninstalling
12-18 11:03 INFO   root: Finished uninstallation
12-18 11:03 DEBUG  CommonBackend: Fetching basic info...
12-18 11:03 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi (1).exe
12-18 11:03 DEBUG  CommonBackend: platform=win32
12-18 11:03 DEBUG  CommonBackend: osname=nt
12-18 11:03 DEBUG  WindowsBackend: arch=amd64
12-18 11:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\data\isolist.ini
12-18 11:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:03 DEBUG  WindowsBackend: Fetching host info...
12-18 11:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:03 DEBUG  WindowsBackend: windows version=vista
12-18 11:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:03 DEBUG  WindowsBackend: windows_sp=None
12-18 11:03 DEBUG  WindowsBackend: windows_build=7601
12-18 11:03 DEBUG  WindowsBackend: gmt=-5
12-18 11:03 DEBUG  WindowsBackend: country=CA
12-18 11:03 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:03 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:03 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:03 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:03 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:03 DEBUG  WindowsBackend: windows_language=English
12-18 11:03 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:03 DEBUG  WindowsBackend: bootloader=vista
12-18 11:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 262866.136719 mb free ntfs)
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(C: hd 262866.136719 mb free ntfs)
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:03 DEBUG  WindowsBackend: uninstaller_path=None
12-18 11:03 DEBUG  WindowsBackend: previous_target_dir=None
12-18 11:03 DEBUG  WindowsBackend: previous_distro_name=None
12-18 11:03 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:03 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:03 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:03 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:03 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:03 DEBUG  CommonBackend: Searching for local CDs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylAC19.tmp\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:03 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:06 INFO   root: === wubi 11.10 rev245 ===
12-18 11:06 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 11:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jack\\Downloads\\wubi (1).exe"']
12-18 11:06 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\data
12-18 11:06 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\bin\7z.exe
12-18 11:06 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 11:06 DEBUG  CommonBackend: Fetching basic info...
12-18 11:06 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi (1).exe
12-18 11:06 DEBUG  CommonBackend: platform=win32
12-18 11:06 DEBUG  CommonBackend: osname=nt
12-18 11:06 DEBUG  CommonBackend: language=en_CA
12-18 11:06 DEBUG  CommonBackend: encoding=cp1252
12-18 11:06 DEBUG  WindowsBackend: arch=amd64
12-18 11:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\data\isolist.ini
12-18 11:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:06 DEBUG  WindowsBackend: Fetching host info...
12-18 11:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:06 DEBUG  WindowsBackend: windows version=vista
12-18 11:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:06 DEBUG  WindowsBackend: windows_sp=None
12-18 11:06 DEBUG  WindowsBackend: windows_build=7601
12-18 11:06 DEBUG  WindowsBackend: gmt=-5
12-18 11:06 DEBUG  WindowsBackend: country=CA
12-18 11:06 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:06 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:06 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:06 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:06 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:06 DEBUG  WindowsBackend: windows_language=English
12-18 11:06 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:06 DEBUG  WindowsBackend: bootloader=vista
12-18 11:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 262882.792969 mb free ntfs)
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(C: hd 262882.792969 mb free ntfs)
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:06 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:06 DEBUG  WindowsBackend: uninstaller_path=None
12-18 11:06 DEBUG  WindowsBackend: previous_target_dir=None
12-18 11:06 DEBUG  WindowsBackend: previous_distro_name=None
12-18 11:06 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:06 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:06 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:06 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 11:06 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 11:06 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:06 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:06 DEBUG  CommonBackend: Searching for local CDs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:06 INFO   root: Running the installer...
12-18 11:06 DEBUG  WindowsFrontend: __init__...
12-18 11:06 DEBUG  WindowsFrontend: on_init...
12-18 11:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\translations, languages=['en_CA', 'en']
12-18 11:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\translations, languages=['en_CA', 'en']
12-18 11:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jack
12-18 11:07 INFO   root: Received settings
12-18 11:07 DEBUG  CommonBackend: Searching for local CD
12-18 11:07 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\casper\filesystem.squashfs
12-18 11:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:07 DEBUG  CommonBackend: Searching for local ISO
12-18 11:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\translations, languages=['en_US', 'en']
12-18 11:07 DEBUG  TaskList: # Running tasklist...
12-18 11:07 DEBUG  TaskList: ## Running select_target_dir...
12-18 11:07 INFO   WindowsBackend: Installing into C:\ubuntu
12-18 11:07 DEBUG  TaskList: ## Finished select_target_dir
12-18 11:07 DEBUG  TaskList: ## Running create_dir_structure...
12-18 11:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-18 11:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-18 11:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-18 11:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-18 11:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-18 11:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-18 11:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-18 11:07 DEBUG  TaskList: ## Finished create_dir_structure
12-18 11:07 DEBUG  TaskList: ## Running create_uninstaller...
12-18 11:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jack\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-18 11:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-18 11:07 DEBUG  TaskList: ## Finished create_uninstaller
12-18 11:07 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-18 11:07 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-18 11:07 DEBUG  TaskList: ## Running get_diskimage...
12-18 11:07 DEBUG  TaskList: New task download
12-18 11:07 DEBUG  TaskList: ### Running download...
12-18 11:07 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-18 11:07 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-18 11:11 DEBUG  TaskList: ### Finished download
12-18 11:11 DEBUG  downloader: download finished (read 507143012 bytes)
12-18 11:11 DEBUG  TaskList: ## Finished get_diskimage
12-18 11:11 DEBUG  TaskList: ## Running extract_diskimage...
12-18 11:12 DEBUG  TaskList: ## Finished extract_diskimage
12-18 11:12 DEBUG  TaskList: ## Running choose_disk_sizes...
12-18 11:12 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-18 11:12 DEBUG  TaskList: ## Finished choose_disk_sizes
12-18 11:12 DEBUG  TaskList: ## Running expand_diskimage...
12-18 11:16 DEBUG  TaskList: ## Finished expand_diskimage
12-18 11:16 DEBUG  TaskList: ## Running create_swap_diskimage...
12-18 11:16 DEBUG  TaskList: ## Finished create_swap_diskimage
12-18 11:16 DEBUG  TaskList: ## Running modify_bootloader...
12-18 11:16 DEBUG  TaskList: New task modify_bcd
12-18 11:16 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:16 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 262882.792969 mb free ntfs)
12-18 11:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {dc59b0bd-fded-11e0-89c9-6431503ef3aa}
12-18 11:16 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:16 DEBUG  TaskList: New task modify_bcd
12-18 11:16 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:16 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:16 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:16 DEBUG  TaskList: New task modify_bcd
12-18 11:16 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:16 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:16 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:16 DEBUG  TaskList: New task modify_bcd
12-18 11:16 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:16 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:16 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:16 DEBUG  TaskList: New task modify_bcd
12-18 11:16 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:16 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:16 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:16 DEBUG  TaskList: New task modify_bcd
12-18 11:16 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:16 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:16 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:16 DEBUG  TaskList: ## Finished modify_bootloader
12-18 11:16 DEBUG  TaskList: ## Running diskimage_bootloader...
12-18 11:16 DEBUG  WindowsBackend: Copying C:\Users\Jack\AppData\Local\Temp\pylBB26.tmp\winboot -> C:\ubuntu\winboot
12-18 11:16 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 11:16 DEBUG  TaskList: # Cancelling tasklist
12-18 11:16 DEBUG  TaskList: # Finished tasklist
12-18 11:16 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 11:16 INFO   root: === wubi 11.10 rev245 ===
12-18 11:16 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 11:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-18 11:16 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\data
12-18 11:16 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\bin\7z.exe
12-18 11:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 11:16 DEBUG  CommonBackend: Fetching basic info...
12-18 11:16 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-18 11:16 DEBUG  CommonBackend: platform=win32
12-18 11:16 DEBUG  CommonBackend: osname=nt
12-18 11:16 DEBUG  CommonBackend: language=en_CA
12-18 11:16 DEBUG  CommonBackend: encoding=cp1252
12-18 11:16 DEBUG  WindowsBackend: arch=amd64
12-18 11:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\data\isolist.ini
12-18 11:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:16 DEBUG  WindowsBackend: Fetching host info...
12-18 11:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:16 DEBUG  WindowsBackend: windows version=vista
12-18 11:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:16 DEBUG  WindowsBackend: windows_sp=None
12-18 11:16 DEBUG  WindowsBackend: windows_build=7601
12-18 11:16 DEBUG  WindowsBackend: gmt=-5
12-18 11:16 DEBUG  WindowsBackend: country=CA
12-18 11:16 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:16 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:16 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:16 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:16 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:16 DEBUG  WindowsBackend: windows_language=English
12-18 11:16 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:16 DEBUG  WindowsBackend: bootloader=vista
12-18 11:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 259675.117188 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(C: hd 259675.117188 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.0859375 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-18 11:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-18 11:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 11:16 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:16 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:16 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:16 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 11:16 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 11:16 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:16 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:16 DEBUG  CommonBackend: Searching for local CDs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:16 INFO   root: Running the uninstaller...
12-18 11:16 INFO   CommonBackend: This is the uninstaller running
12-18 11:16 DEBUG  WindowsFrontend: __init__...
12-18 11:16 DEBUG  WindowsFrontend: on_init...
12-18 11:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\translations, languages=['en_CA', 'en']
12-18 11:16 INFO   root: Received settings
12-18 11:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\translations, languages=['en_CA', 'en']
12-18 11:16 DEBUG  TaskList: # Running tasklist...
12-18 11:16 DEBUG  TaskList: ## Running Remove bootloader entry...
12-18 11:16 DEBUG  WindowsBackend: Removing bcd entry {dc59b0bd-fded-11e0-89c9-6431503ef3aa}
12-18 11:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-18 11:16 DEBUG  WindowsBackend: undo_bootini C:
12-18 11:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 259675.117188 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: undo_bootini D:
12-18 11:16 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1692.0859375 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: undo_bootini F:
12-18 11:16 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: undo_bootini G:
12-18 11:16 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: undo_bootini H:
12-18 11:16 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: undo_bootini I:
12-18 11:16 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
12-18 11:16 DEBUG  TaskList: ## Finished Remove bootloader entry
12-18 11:16 DEBUG  TaskList: ## Running Remove target dir...
12-18 11:16 DEBUG  CommonBackend: Deleting C:\ubuntu
12-18 11:16 DEBUG  TaskList: ## Finished Remove target dir
12-18 11:16 DEBUG  TaskList: ## Running Remove registry key...
12-18 11:16 DEBUG  TaskList: ## Finished Remove registry key
12-18 11:16 DEBUG  TaskList: # Finished tasklist
12-18 11:16 INFO   root: Almost finished uninstalling
12-18 11:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl7189.tmp\translations, languages=['en_CA', 'en']
12-18 11:16 INFO   root: Finished uninstallation
12-18 11:16 DEBUG  root: application.quit
12-18 11:16 DEBUG  WindowsFrontend: frontend.quit
12-18 11:16 DEBUG  WindowsFrontend: frontend.on_quit
12-18 11:16 DEBUG  root: application.on_quit
12-18 11:16 INFO   root: sys.exit
12-18 11:16 INFO   root: === wubi 11.10 rev245 ===
12-18 11:16 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 11:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jack\\Downloads\\wubi (1).exe"']
12-18 11:16 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\data
12-18 11:16 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\bin\7z.exe
12-18 11:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 11:16 DEBUG  CommonBackend: Fetching basic info...
12-18 11:16 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi (1).exe
12-18 11:16 DEBUG  CommonBackend: platform=win32
12-18 11:16 DEBUG  CommonBackend: osname=nt
12-18 11:16 DEBUG  CommonBackend: language=en_CA
12-18 11:16 DEBUG  CommonBackend: encoding=cp1252
12-18 11:16 DEBUG  WindowsBackend: arch=amd64
12-18 11:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\data\isolist.ini
12-18 11:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:16 DEBUG  WindowsBackend: Fetching host info...
12-18 11:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:16 DEBUG  WindowsBackend: windows version=vista
12-18 11:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:16 DEBUG  WindowsBackend: windows_sp=None
12-18 11:16 DEBUG  WindowsBackend: windows_build=7601
12-18 11:16 DEBUG  WindowsBackend: gmt=-5
12-18 11:16 DEBUG  WindowsBackend: country=CA
12-18 11:16 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:16 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:16 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:16 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:16 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:16 DEBUG  WindowsBackend: windows_language=English
12-18 11:16 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:16 DEBUG  WindowsBackend: bootloader=vista
12-18 11:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 262880.179688 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(C: hd 262880.179688 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:16 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:17 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:17 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:17 DEBUG  WindowsBackend: uninstaller_path=None
12-18 11:17 DEBUG  WindowsBackend: previous_target_dir=None
12-18 11:17 DEBUG  WindowsBackend: previous_distro_name=None
12-18 11:17 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:17 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:17 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:17 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 11:17 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 11:17 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:17 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:17 DEBUG  CommonBackend: Searching for local CDs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:17 INFO   root: Running the installer...
12-18 11:17 DEBUG  WindowsFrontend: __init__...
12-18 11:17 DEBUG  WindowsFrontend: on_init...
12-18 11:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\translations, languages=['en_CA', 'en']
12-18 11:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\translations, languages=['en_CA', 'en']
12-18 11:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jack
12-18 11:18 INFO   root: Received settings
12-18 11:18 DEBUG  CommonBackend: Searching for local CD
12-18 11:18 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\casper\filesystem.squashfs
12-18 11:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:18 DEBUG  CommonBackend: Searching for local ISO
12-18 11:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\translations, languages=['en_US', 'en']
12-18 11:18 DEBUG  TaskList: # Running tasklist...
12-18 11:18 DEBUG  TaskList: ## Running select_target_dir...
12-18 11:18 INFO   WindowsBackend: Installing into C:\ubuntu
12-18 11:18 DEBUG  TaskList: ## Finished select_target_dir
12-18 11:18 DEBUG  TaskList: ## Running create_dir_structure...
12-18 11:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-18 11:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-18 11:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-18 11:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-18 11:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-18 11:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-18 11:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-18 11:18 DEBUG  TaskList: ## Finished create_dir_structure
12-18 11:18 DEBUG  TaskList: ## Running create_uninstaller...
12-18 11:18 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jack\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-18 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-18 11:18 DEBUG  TaskList: ## Finished create_uninstaller
12-18 11:18 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-18 11:18 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-18 11:18 DEBUG  TaskList: ## Running get_diskimage...
12-18 11:18 DEBUG  TaskList: New task download
12-18 11:18 DEBUG  TaskList: ### Running download...
12-18 11:18 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-18 11:18 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-18 11:22 DEBUG  TaskList: ### Finished download
12-18 11:22 DEBUG  downloader: download finished (read 507143012 bytes)
12-18 11:22 DEBUG  TaskList: ## Finished get_diskimage
12-18 11:22 DEBUG  TaskList: ## Running extract_diskimage...
12-18 11:23 DEBUG  TaskList: ## Finished extract_diskimage
12-18 11:23 DEBUG  TaskList: ## Running choose_disk_sizes...
12-18 11:23 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-18 11:23 DEBUG  TaskList: ## Finished choose_disk_sizes
12-18 11:23 DEBUG  TaskList: ## Running expand_diskimage...
12-18 11:26 DEBUG  TaskList: ## Finished expand_diskimage
12-18 11:26 DEBUG  TaskList: ## Running create_swap_diskimage...
12-18 11:26 DEBUG  TaskList: ## Finished create_swap_diskimage
12-18 11:26 DEBUG  TaskList: ## Running modify_bootloader...
12-18 11:26 DEBUG  TaskList: New task modify_bcd
12-18 11:26 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:26 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 262880.179688 mb free ntfs)
12-18 11:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {dc59b0be-fded-11e0-89c9-6431503ef3aa}
12-18 11:26 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:26 DEBUG  TaskList: New task modify_bcd
12-18 11:26 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:26 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:26 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:26 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:26 DEBUG  TaskList: New task modify_bcd
12-18 11:26 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:26 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
12-18 11:26 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:26 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:26 DEBUG  TaskList: New task modify_bcd
12-18 11:26 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:26 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
12-18 11:26 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:26 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:26 DEBUG  TaskList: New task modify_bcd
12-18 11:26 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:26 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
12-18 11:26 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:26 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:26 DEBUG  TaskList: New task modify_bcd
12-18 11:26 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:26 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
12-18 11:26 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:26 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:26 DEBUG  TaskList: ## Finished modify_bootloader
12-18 11:26 DEBUG  TaskList: ## Running diskimage_bootloader...
12-18 11:26 DEBUG  WindowsBackend: Copying C:\Users\Jack\AppData\Local\Temp\pyl9E44.tmp\winboot -> C:\ubuntu\winboot
12-18 11:26 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 11:26 DEBUG  TaskList: # Cancelling tasklist
12-18 11:26 DEBUG  TaskList: # Finished tasklist
12-18 11:26 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 11:27 INFO   root: === wubi 11.10 rev245 ===
12-18 11:27 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 11:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-18 11:27 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\data
12-18 11:27 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\bin\7z.exe
12-18 11:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 11:27 DEBUG  CommonBackend: Fetching basic info...
12-18 11:27 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-18 11:27 DEBUG  CommonBackend: platform=win32
12-18 11:27 DEBUG  CommonBackend: osname=nt
12-18 11:27 DEBUG  CommonBackend: language=en_CA
12-18 11:27 DEBUG  CommonBackend: encoding=cp1252
12-18 11:27 DEBUG  WindowsBackend: arch=amd64
12-18 11:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\data\isolist.ini
12-18 11:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:27 DEBUG  WindowsBackend: Fetching host info...
12-18 11:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:27 DEBUG  WindowsBackend: windows version=vista
12-18 11:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:27 DEBUG  WindowsBackend: windows_sp=None
12-18 11:27 DEBUG  WindowsBackend: windows_build=7601
12-18 11:27 DEBUG  WindowsBackend: gmt=-5
12-18 11:27 DEBUG  WindowsBackend: country=CA
12-18 11:27 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:27 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:27 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:27 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:27 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:27 DEBUG  WindowsBackend: windows_language=English
12-18 11:27 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:27 DEBUG  WindowsBackend: bootloader=vista
12-18 11:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 259668.894531 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(C: hd 259668.894531 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.0859375 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-18 11:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-18 11:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 11:27 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:27 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:27 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:27 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 11:27 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 11:27 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:27 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:27 DEBUG  CommonBackend: Searching for local CDs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:27 INFO   root: Running the uninstaller...
12-18 11:27 INFO   CommonBackend: This is the uninstaller running
12-18 11:27 DEBUG  WindowsFrontend: __init__...
12-18 11:27 DEBUG  WindowsFrontend: on_init...
12-18 11:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\translations, languages=['en_CA', 'en']
12-18 11:27 INFO   root: Received settings
12-18 11:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\translations, languages=['en_CA', 'en']
12-18 11:27 DEBUG  TaskList: # Running tasklist...
12-18 11:27 DEBUG  TaskList: ## Running Remove bootloader entry...
12-18 11:27 DEBUG  WindowsBackend: Removing bcd entry {dc59b0be-fded-11e0-89c9-6431503ef3aa}
12-18 11:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-18 11:27 DEBUG  WindowsBackend: undo_bootini C:
12-18 11:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 259668.894531 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: undo_bootini D:
12-18 11:27 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1692.0859375 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: undo_bootini F:
12-18 11:27 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: undo_bootini G:
12-18 11:27 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: undo_bootini H:
12-18 11:27 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: undo_bootini I:
12-18 11:27 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
12-18 11:27 DEBUG  TaskList: ## Finished Remove bootloader entry
12-18 11:27 DEBUG  TaskList: ## Running Remove target dir...
12-18 11:27 DEBUG  CommonBackend: Deleting C:\ubuntu
12-18 11:27 DEBUG  TaskList: ## Finished Remove target dir
12-18 11:27 DEBUG  TaskList: ## Running Remove registry key...
12-18 11:27 DEBUG  TaskList: ## Finished Remove registry key
12-18 11:27 DEBUG  TaskList: # Finished tasklist
12-18 11:27 INFO   root: Almost finished uninstalling
12-18 11:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl48C5.tmp\translations, languages=['en_CA', 'en']
12-18 11:27 INFO   root: Finished uninstallation
12-18 11:27 DEBUG  root: application.quit
12-18 11:27 DEBUG  WindowsFrontend: frontend.quit
12-18 11:27 DEBUG  WindowsFrontend: frontend.on_quit
12-18 11:27 DEBUG  root: application.on_quit
12-18 11:27 INFO   root: sys.exit
12-18 11:27 INFO   root: === wubi 11.10 rev245 ===
12-18 11:27 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 11:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jack\\Downloads\\wubi (1).exe"']
12-18 11:27 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\data
12-18 11:27 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\bin\7z.exe
12-18 11:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 11:27 DEBUG  CommonBackend: Fetching basic info...
12-18 11:27 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi (1).exe
12-18 11:27 DEBUG  CommonBackend: platform=win32
12-18 11:27 DEBUG  CommonBackend: osname=nt
12-18 11:27 DEBUG  CommonBackend: language=en_CA
12-18 11:27 DEBUG  CommonBackend: encoding=cp1252
12-18 11:27 DEBUG  WindowsBackend: arch=amd64
12-18 11:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\data\isolist.ini
12-18 11:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:27 DEBUG  WindowsBackend: Fetching host info...
12-18 11:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:27 DEBUG  WindowsBackend: windows version=vista
12-18 11:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:27 DEBUG  WindowsBackend: windows_sp=None
12-18 11:27 DEBUG  WindowsBackend: windows_build=7601
12-18 11:27 DEBUG  WindowsBackend: gmt=-5
12-18 11:27 DEBUG  WindowsBackend: country=CA
12-18 11:27 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:27 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:27 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:27 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:27 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:27 DEBUG  WindowsBackend: windows_language=English
12-18 11:27 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:27 DEBUG  WindowsBackend: bootloader=vista
12-18 11:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 262878.050781 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(C: hd 262878.050781 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:27 DEBUG  WindowsBackend: uninstaller_path=None
12-18 11:27 DEBUG  WindowsBackend: previous_target_dir=None
12-18 11:27 DEBUG  WindowsBackend: previous_distro_name=None
12-18 11:27 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:27 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:27 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:27 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 11:27 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 11:27 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:27 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:27 DEBUG  CommonBackend: Searching for local CDs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pylA0B4.tmp\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:32 INFO   root: === wubi 11.10 rev245 ===
12-18 11:32 DEBUG  root: Logfile is c:\users\jack\appdata\local\temp\wubi-11.10-rev245.log
12-18 11:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jack\\Downloads\\wubi (1).exe"']
12-18 11:32 DEBUG  CommonBackend: data_dir=C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\data
12-18 11:32 DEBUG  WindowsBackend: 7z=C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\bin\7z.exe
12-18 11:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-18 11:32 DEBUG  CommonBackend: Fetching basic info...
12-18 11:32 DEBUG  CommonBackend: original_exe=C:\Users\Jack\Downloads\wubi (1).exe
12-18 11:32 DEBUG  CommonBackend: platform=win32
12-18 11:32 DEBUG  CommonBackend: osname=nt
12-18 11:32 DEBUG  CommonBackend: language=en_CA
12-18 11:32 DEBUG  CommonBackend: encoding=cp1252
12-18 11:32 DEBUG  WindowsBackend: arch=amd64
12-18 11:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\data\isolist.ini
12-18 11:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 11:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 11:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 11:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 11:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 11:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 11:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 11:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 11:32 DEBUG  WindowsBackend: Fetching host info...
12-18 11:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 11:32 DEBUG  WindowsBackend: windows version=vista
12-18 11:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-18 11:32 DEBUG  WindowsBackend: windows_sp=None
12-18 11:32 DEBUG  WindowsBackend: windows_build=7601
12-18 11:32 DEBUG  WindowsBackend: gmt=-5
12-18 11:32 DEBUG  WindowsBackend: country=CA
12-18 11:32 DEBUG  WindowsBackend: timezone=America/Montreal
12-18 11:32 DEBUG  WindowsBackend: windows_username=Jack
12-18 11:32 DEBUG  WindowsBackend: user_full_name=Jack
12-18 11:32 DEBUG  WindowsBackend: user_directory=C:\Users\Jack
12-18 11:32 DEBUG  WindowsBackend: windows_language_code=1033
12-18 11:32 DEBUG  WindowsBackend: windows_language=English
12-18 11:32 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X3 445 Processor
12-18 11:32 DEBUG  WindowsBackend: bootloader=vista
12-18 11:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 262639.832031 mb free ntfs)
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(C: hd 262639.832031 mb free ntfs)
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-18 11:32 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-18 11:32 DEBUG  WindowsBackend: uninstaller_path=None
12-18 11:32 DEBUG  WindowsBackend: previous_target_dir=None
12-18 11:32 DEBUG  WindowsBackend: previous_distro_name=None
12-18 11:32 DEBUG  WindowsBackend: keyboard_id=67702793
12-18 11:32 DEBUG  WindowsBackend: keyboard_layout=us
12-18 11:32 DEBUG  WindowsBackend: keyboard_variant=
12-18 11:32 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
12-18 11:32 DEBUG  CommonBackend: locale=en_CA.UTF-8
12-18 11:32 DEBUG  WindowsBackend: total_memory_mb=4095.28515625
12-18 11:32 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 11:32 DEBUG  CommonBackend: Searching for local CDs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 INFO   root: Running the installer...
12-18 11:32 DEBUG  WindowsFrontend: __init__...
12-18 11:32 DEBUG  WindowsFrontend: on_init...
12-18 11:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\translations, languages=['en_CA', 'en']
12-18 11:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\translations, languages=['en_CA', 'en']
12-18 11:32 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jack
12-18 11:32 INFO   root: Received settings
12-18 11:32 DEBUG  CommonBackend: Searching for local CD
12-18 11:32 DEBUG  Distro:   checking whether C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-18 11:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-18 11:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-18 11:32 DEBUG  CommonBackend: Searching for local ISO
12-18 11:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\translations, languages=['en_US', 'en']
12-18 11:32 DEBUG  TaskList: # Running tasklist...
12-18 11:32 DEBUG  TaskList: ## Running select_target_dir...
12-18 11:32 INFO   WindowsBackend: Installing into C:\ubuntu
12-18 11:32 DEBUG  TaskList: ## Finished select_target_dir
12-18 11:32 DEBUG  TaskList: ## Running create_dir_structure...
12-18 11:32 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-18 11:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-18 11:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-18 11:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-18 11:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-18 11:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-18 11:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-18 11:32 DEBUG  TaskList: ## Finished create_dir_structure
12-18 11:32 DEBUG  TaskList: ## Running create_uninstaller...
12-18 11:32 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jack\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-18 11:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-18 11:32 DEBUG  TaskList: ## Finished create_uninstaller
12-18 11:32 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-18 11:32 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-18 11:32 DEBUG  TaskList: ## Running get_diskimage...
12-18 11:32 DEBUG  TaskList: New task download
12-18 11:32 DEBUG  TaskList: ### Running download...
12-18 11:32 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-18 11:32 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-18 11:37 DEBUG  TaskList: ### Finished download
12-18 11:37 DEBUG  downloader: download finished (read 507143012 bytes)
12-18 11:37 DEBUG  TaskList: ## Finished get_diskimage
12-18 11:37 DEBUG  TaskList: ## Running extract_diskimage...
12-18 11:38 DEBUG  TaskList: ## Finished extract_diskimage
12-18 11:38 DEBUG  TaskList: ## Running choose_disk_sizes...
12-18 11:38 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-18 11:38 DEBUG  TaskList: ## Finished choose_disk_sizes
12-18 11:38 DEBUG  TaskList: ## Running expand_diskimage...
12-18 11:42 DEBUG  TaskList: ## Finished expand_diskimage
12-18 11:42 DEBUG  TaskList: ## Running create_swap_diskimage...
12-18 11:42 DEBUG  TaskList: ## Finished create_swap_diskimage
12-18 11:42 DEBUG  TaskList: ## Running modify_bootloader...
12-18 11:42 DEBUG  TaskList: New task modify_bcd
12-18 11:42 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:42 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 262639.832031 mb free ntfs)
12-18 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {dc59b0bf-fded-11e0-89c9-6431503ef3aa}
12-18 11:42 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:42 DEBUG  TaskList: New task modify_bcd
12-18 11:42 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:42 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1692.21484375 mb free ntfs)
12-18 11:42 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:42 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:42 DEBUG  TaskList: New task modify_bcd
12-18 11:42 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:42 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
12-18 11:42 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:42 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:42 DEBUG  TaskList: New task modify_bcd
12-18 11:42 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:42 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
12-18 11:42 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:42 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:42 DEBUG  TaskList: New task modify_bcd
12-18 11:42 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:42 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
12-18 11:42 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:42 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:42 DEBUG  TaskList: New task modify_bcd
12-18 11:42 DEBUG  TaskList: ### Running modify_bcd...
12-18 11:42 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
12-18 11:42 DEBUG  WindowsBackend: BCD has already been modified
12-18 11:42 DEBUG  TaskList: ### Finished modify_bcd
12-18 11:42 DEBUG  TaskList: ## Finished modify_bootloader
12-18 11:42 DEBUG  TaskList: ## Running diskimage_bootloader...
12-18 11:42 DEBUG  WindowsBackend: Copying C:\Users\Jack\AppData\Local\Temp\pyl19B7.tmp\winboot -> C:\ubuntu\winboot
12-18 11:42 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
12-18 11:42 DEBUG  TaskList: # Cancelling tasklist
12-18 11:42 DEBUG  TaskList: # Finished tasklist
12-18 11:42 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'

```


I get this message whenever I try to install Ubuntu. I'm running Windows 7 Home Premium. It gets to the last step then gives me an error message with only 1 option.

---

### Post by Mark Phelps on 2011-12-18
What is mounted in "F"?  The log shows it's trying to install to "F", but according to the same log, there is no room there -- which would be the case if "F" was the identity (for example) of a memory card reader.

Make sure that the Wubi loader file and Ubuntu ISO file are in the same directory.

---

### Post by bcbc on 2011-12-18
The install is likely successful. This looks like bug [lpbug]862003[/lpbug]

---

### Post by liar78 on 2012-01-03
Download the .iso from the Ubuntu website and put it in the same folder as wubi.exe. Then run wubi.exe.

---

