---
title: "Help ?"
date: 2012-01-18
forum: General Help
---

### Post by aterisk on 2012-01-18
I was trying to use Wubi to install ubuntu 11.10 and it gave me the error

Permission Denied.

I went into my appdata local and found the file it directed me too and copy pasted the info below.

Can anyone help me ?

```
01-18 15:57 INFO   root: === wubi 11.10 rev245 ===
01-18 15:57 DEBUG  root: Logfile is c:\users\atty\appdata\local\temp\wubi-11.10-rev245.log
01-18 15:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Atty\\Downloads\\wubi (2).exe"']
01-18 15:57 DEBUG  CommonBackend: data_dir=C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\data
01-18 15:57 DEBUG  WindowsBackend: 7z=C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\bin\7z.exe
01-18 15:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-18 15:57 DEBUG  CommonBackend: Fetching basic info...
01-18 15:57 DEBUG  CommonBackend: original_exe=C:\Users\Atty\Downloads\wubi (2).exe
01-18 15:57 DEBUG  CommonBackend: platform=win32
01-18 15:57 DEBUG  CommonBackend: osname=nt
01-18 15:57 DEBUG  CommonBackend: language=en_US
01-18 15:57 DEBUG  CommonBackend: encoding=cp1252
01-18 15:57 DEBUG  WindowsBackend: arch=amd64
01-18 15:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\data\isolist.ini
01-18 15:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 15:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 15:57 DEBUG  WindowsBackend: Fetching host info...
01-18 15:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 15:57 DEBUG  WindowsBackend: windows version=vista
01-18 15:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 15:57 DEBUG  WindowsBackend: windows_sp=None
01-18 15:57 DEBUG  WindowsBackend: windows_build=7600
01-18 15:57 DEBUG  WindowsBackend: gmt=-5
01-18 15:57 DEBUG  WindowsBackend: country=US
01-18 15:57 DEBUG  WindowsBackend: timezone=America/New_York
01-18 15:57 DEBUG  WindowsBackend: windows_username=Atty
01-18 15:57 DEBUG  WindowsBackend: user_full_name=Atty
01-18 15:57 DEBUG  WindowsBackend: user_directory=C:\Users\Atty
01-18 15:57 DEBUG  WindowsBackend: windows_language_code=1033
01-18 15:57 DEBUG  WindowsBackend: windows_language=English
01-18 15:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
01-18 15:57 DEBUG  WindowsBackend: bootloader=vista
01-18 15:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 348086.136719 mb free ntfs)
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(C: hd 348086.136719 mb free ntfs)
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(D: hd 1490.07421875 mb free ntfs)
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-18 15:57 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
01-18 15:57 DEBUG  WindowsBackend: uninstaller_path=None
01-18 15:57 DEBUG  WindowsBackend: previous_target_dir=None
01-18 15:57 DEBUG  WindowsBackend: previous_distro_name=None
01-18 15:57 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 15:57 DEBUG  WindowsBackend: keyboard_layout=us
01-18 15:57 DEBUG  WindowsBackend: keyboard_variant=
01-18 15:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-18 15:57 DEBUG  CommonBackend: locale=en_US.UTF-8
01-18 15:57 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-18 15:57 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 15:57 DEBUG  CommonBackend: Searching for local CDs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 INFO   root: Running the installer...
01-18 15:57 DEBUG  WindowsFrontend: __init__...
01-18 15:57 DEBUG  WindowsFrontend: on_init...
01-18 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\translations, languages=['en_US', 'en']
01-18 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\translations, languages=['en_US', 'en']
01-18 15:57 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=aterisk
01-18 15:57 INFO   root: Received settings
01-18 15:57 DEBUG  CommonBackend: Searching for local CD
01-18 15:57 DEBUG  Distro:   checking whether C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-18 15:57 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-18 15:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-18 15:57 DEBUG  CommonBackend: Searching for local ISO
01-18 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\translations, languages=['en_US', 'en']
01-18 15:57 DEBUG  TaskList: # Running tasklist...
01-18 15:57 DEBUG  TaskList: ## Running select_target_dir...
01-18 15:57 INFO   WindowsBackend: Installing into C:\ubuntu
01-18 15:57 DEBUG  TaskList: ## Finished select_target_dir
01-18 15:57 DEBUG  TaskList: ## Running create_dir_structure...
01-18 15:57 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-18 15:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-18 15:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-18 15:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-18 15:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-18 15:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-18 15:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-18 15:57 DEBUG  TaskList: ## Finished create_dir_structure
01-18 15:57 DEBUG  TaskList: ## Running create_uninstaller...
01-18 15:57 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Atty\Downloads\wubi (2).exe -> C:\ubuntu\uninstall-wubi.exe
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-18 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-18 15:57 DEBUG  TaskList: ## Finished create_uninstaller
01-18 15:57 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-18 15:57 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-18 15:57 DEBUG  TaskList: ## Running get_diskimage...
01-18 15:57 DEBUG  TaskList: New task download
01-18 15:57 DEBUG  TaskList: ### Running download...
01-18 15:57 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-18 15:57 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-18 16:08 DEBUG  TaskList: ### Finished download
01-18 16:08 DEBUG  downloader: download finished (read 507143012 bytes)
01-18 16:08 DEBUG  TaskList: ## Finished get_diskimage
01-18 16:08 DEBUG  TaskList: ## Running extract_diskimage...
01-18 16:09 DEBUG  TaskList: ## Finished extract_diskimage
01-18 16:09 DEBUG  TaskList: ## Running choose_disk_sizes...
01-18 16:09 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
01-18 16:09 DEBUG  TaskList: ## Finished choose_disk_sizes
01-18 16:09 DEBUG  TaskList: ## Running expand_diskimage...
01-18 16:10 DEBUG  TaskList: ## Finished expand_diskimage
01-18 16:10 DEBUG  TaskList: ## Running create_swap_diskimage...
01-18 16:10 DEBUG  TaskList: ## Finished create_swap_diskimage
01-18 16:10 DEBUG  TaskList: ## Running modify_bootloader...
01-18 16:10 DEBUG  TaskList: New task modify_bcd
01-18 16:10 DEBUG  TaskList: ### Running modify_bcd...
01-18 16:10 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 348086.136719 mb free ntfs)
01-18 16:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {2412d7ce-9ebd-11e0-9ce2-bc5d9cc52c75}
01-18 16:10 DEBUG  TaskList: ### Finished modify_bcd
01-18 16:10 DEBUG  TaskList: New task modify_bcd
01-18 16:10 DEBUG  TaskList: ### Running modify_bcd...
01-18 16:10 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1490.07421875 mb free ntfs)
01-18 16:10 DEBUG  WindowsBackend: BCD has already been modified
01-18 16:10 DEBUG  TaskList: ### Finished modify_bcd
01-18 16:10 DEBUG  TaskList: New task modify_bcd
01-18 16:10 DEBUG  TaskList: ### Running modify_bcd...
01-18 16:10 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
01-18 16:10 DEBUG  WindowsBackend: BCD has already been modified
01-18 16:10 DEBUG  TaskList: ### Finished modify_bcd
01-18 16:10 DEBUG  TaskList: New task modify_bcd
01-18 16:10 DEBUG  TaskList: ### Running modify_bcd...
01-18 16:10 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
01-18 16:10 DEBUG  WindowsBackend: BCD has already been modified
01-18 16:10 DEBUG  TaskList: ### Finished modify_bcd
01-18 16:10 DEBUG  TaskList: New task modify_bcd
01-18 16:10 DEBUG  TaskList: ### Running modify_bcd...
01-18 16:10 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
01-18 16:10 DEBUG  WindowsBackend: BCD has already been modified
01-18 16:10 DEBUG  TaskList: ### Finished modify_bcd
01-18 16:10 DEBUG  TaskList: New task modify_bcd
01-18 16:10 DEBUG  TaskList: ### Running modify_bcd...
01-18 16:10 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
01-18 16:10 DEBUG  WindowsBackend: BCD has already been modified
01-18 16:10 DEBUG  TaskList: ### Finished modify_bcd
01-18 16:10 DEBUG  TaskList: ## Finished modify_bootloader
01-18 16:10 DEBUG  TaskList: ## Running diskimage_bootloader...
01-18 16:10 DEBUG  WindowsBackend: Copying C:\Users\Atty\AppData\Local\Temp\pyl3FCB.tmp\winboot -> C:\ubuntu\winboot
01-18 16:10 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
01-18 16:10 DEBUG  TaskList: # Cancelling tasklist
01-18 16:10 DEBUG  TaskList: # Finished tasklist
01-18 16:10 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
```

---

### Post by jonobr on 2012-01-18
Hello


[ Permission denied: 'F:\\wubildr'"]This bug]("TaskList: [Errno 13) seems to relate to the error your seeing,

note that it says there the installation completed.
When you restart do you see an option for ubuntu?

Also, recommend] you change the title of the thread from help to something meaningful so people can search if they have the same issue.
eg Wubi installation - [Errno 13] Permission denied: 'F:\\wubildr'

---

### Post by BC59 on 2012-01-18
As I see you made several attempts to install wubi. Maybe is better to clean first your computer and then do a fresh install.
Remove wubi from Windows applications and delete the Ubuntu directory from c:\
You can download Ccleaner and clean the registry and the computer. Then try again.

---

### Post by bcbc on 2012-01-18
This is bug [lpbug]862003[/lpbug]. The install is successful. Just reboot.

---

