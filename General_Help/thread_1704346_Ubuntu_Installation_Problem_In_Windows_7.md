---
title: "Ubuntu Installation Problem In Windows 7"
date: 2011-03-10
forum: General Help
---

### Post by CyberHax0rs on 2011-03-10
He everybody.
I m new to this forum and also to Ubuntu.
I was trying to install ubuntu on my Windows 7.

While installing ubuntu alongside windows 7 in my system,i get an error message saying…..
"an error has occured for details check c:\documen~1\………\wubi 10.10 rev-197.log"
what does this error mean and how can i get rid of this ???

Here is the log file.

```
03-09 01:09 INFO   root: === wubi 10.10 rev197 ===
03-09 01:09 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 01:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-09 01:09 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\data
03-09 01:09 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\bin\7z.exe
03-09 01:09 DEBUG  CommonBackend: Fetching basic info...
03-09 01:09 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:09 DEBUG  CommonBackend: platform=win32
03-09 01:09 DEBUG  CommonBackend: osname=nt
03-09 01:09 DEBUG  CommonBackend: language=en_US
03-09 01:09 DEBUG  CommonBackend: encoding=cp1256
03-09 01:09 DEBUG  WindowsBackend: arch=amd64
03-09 01:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\data\isolist.ini
03-09 01:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:09 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:09 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:09 DEBUG  WindowsBackend: Fetching host info...
03-09 01:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:09 DEBUG  WindowsBackend: windows version=vista
03-09 01:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:09 DEBUG  WindowsBackend: windows_sp=None
03-09 01:09 DEBUG  WindowsBackend: windows_build=7600
03-09 01:09 DEBUG  WindowsBackend: gmt=4
03-09 01:09 DEBUG  WindowsBackend: country=US
03-09 01:09 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:09 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:09 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:09 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:09 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:09 DEBUG  WindowsBackend: windows_language=English
03-09 01:09 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:09 DEBUG  WindowsBackend: bootloader=vista
03-09 01:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207343.957031 mb free ntfs)
03-09 01:09 DEBUG  WindowsBackend: drive=Drive(C: hd 207343.957031 mb free ntfs)
03-09 01:09 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:09 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:09 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:09 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 01:09 DEBUG  WindowsBackend: uninstaller_path=None
03-09 01:09 DEBUG  WindowsBackend: previous_target_dir=None
03-09 01:09 DEBUG  WindowsBackend: previous_distro_name=None
03-09 01:09 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:09 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:09 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:09 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 01:09 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 01:09 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:09 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:09 DEBUG  CommonBackend: Searching for local CDs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Ubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Ubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Ubuntu Netbook CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Kubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Kubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Kubuntu Netbook CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Xubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Xubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Mythbuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp is a valid Mythbuntu CD
03-09 01:09 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:09 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:09 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:09 INFO   root: Running the CD menu...
03-09 01:09 DEBUG  WindowsFrontend: __init__...
03-09 01:09 DEBUG  WindowsFrontend: on_init...
03-09 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\translations, languages=['en_US', 'en']
03-09 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\translations, languages=['en_US', 'en']
03-09 01:09 INFO   root: CD menu finished
03-09 01:09 INFO   root: Running the installer...
03-09 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\translations, languages=['en_US', 'en']
03-09 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\translations, languages=['en_US', 'en']
03-09 01:11 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-09 01:11 INFO   root: Received settings
03-09 01:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\translations, languages=['en_US', 'en']
03-09 01:11 DEBUG  TaskList: # Running tasklist...
03-09 01:11 DEBUG  TaskList: ## Running select_target_dir...
03-09 01:11 INFO   WindowsBackend: Installing into G:\ubuntu
03-09 01:11 DEBUG  TaskList: ## Finished select_target_dir
03-09 01:11 DEBUG  TaskList: ## Running create_dir_structure...
03-09 01:11 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-09 01:11 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-09 01:11 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-09 01:11 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-09 01:11 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-09 01:11 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-09 01:11 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-09 01:11 DEBUG  TaskList: ## Finished create_dir_structure
03-09 01:11 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 01:11 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 01:11 DEBUG  TaskList: ## Running create_uninstaller...
03-09 01:11 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 01:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 01:11 DEBUG  TaskList: ## Finished create_uninstaller
03-09 01:11 DEBUG  TaskList: ## Running copy_installation_files...
03-09 01:11 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-09 01:11 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\winboot -> G:\ubuntu\winboot
03-09 01:11 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl3A61.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-09 01:11 DEBUG  TaskList: ## Finished copy_installation_files
03-09 01:11 DEBUG  TaskList: ## Running get_iso...
03-09 01:11 DEBUG  TaskList: New task copy_file
03-09 01:11 DEBUG  TaskList: ### Running copy_file...
03-09 01:15 DEBUG  TaskList: ### Finished copy_file
03-09 01:15 DEBUG  TaskList: New task check_iso
03-09 01:15 DEBUG  TaskList: ### Running check_iso...
03-09 01:15 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
03-09 01:15 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
03-09 01:15 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
03-09 01:15 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:15 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
03-09 01:15 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
03-09 01:15 DEBUG  TaskList: New task get_metalink
03-09 01:15 DEBUG  TaskList: #### Running get_metalink...
03-09 01:15 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink > G:\ubuntu\install
03-09 01:15 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
03-09 01:15 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.metalink > G:\ubuntu\install
03-09 01:15 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
03-09 01:15 DEBUG  TaskList: #### Finished get_metalink
03-09 01:15 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
03-09 01:15 DEBUG  TaskList: ### Finished check_iso
03-09 01:15 DEBUG  TaskList: ## Finished get_iso
03-09 01:15 DEBUG  TaskList: ## Running extract_kernel...
03-09 01:15 DEBUG  CommonBackend: Copying files from CD F:\
03-09 01:15 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-09 01:15 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-09 01:15 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-09 01:15 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-09 01:15 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-09 01:15 DEBUG  TaskList: ## Finished extract_kernel
03-09 01:15 DEBUG  TaskList: ## Running choose_disk_sizes...
03-09 01:15 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
03-09 01:15 DEBUG  TaskList: ## Finished choose_disk_sizes
03-09 01:15 DEBUG  TaskList: ## Running create_preseed...
03-09 01:15 DEBUG  TaskList: ## Finished create_preseed
03-09 01:15 DEBUG  TaskList: ## Running modify_bootloader...
03-09 01:15 DEBUG  TaskList: New task modify_bcd
03-09 01:15 DEBUG  TaskList: ### Running modify_bcd...
03-09 01:15 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 207343.957031 mb free ntfs)
03-09 01:15 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933107-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933107-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-09 01:15 DEBUG  TaskList: # Cancelling tasklist
03-09 01:15 DEBUG  TaskList: New task modify_bcd
03-09 01:15 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933107-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933107-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-09 01:15 DEBUG  TaskList: New task modify_bcd
03-09 01:15 DEBUG  TaskList: New task modify_bcd
03-09 01:15 DEBUG  TaskList: ## Finished modify_bootloader
03-09 01:15 DEBUG  TaskList: # Finished tasklist
03-09 01:18 INFO   root: === wubi 10.10 rev197 ===
03-09 01:18 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 01:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
03-09 01:18 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\data
03-09 01:18 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\bin\7z.exe
03-09 01:18 DEBUG  CommonBackend: Fetching basic info...
03-09 01:18 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
03-09 01:18 DEBUG  CommonBackend: platform=win32
03-09 01:18 DEBUG  CommonBackend: osname=nt
03-09 01:18 DEBUG  CommonBackend: language=en_US
03-09 01:18 DEBUG  CommonBackend: encoding=cp1256
03-09 01:18 DEBUG  WindowsBackend: arch=amd64
03-09 01:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\data\isolist.ini
03-09 01:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:18 DEBUG  WindowsBackend: Fetching host info...
03-09 01:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:18 DEBUG  WindowsBackend: windows version=vista
03-09 01:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:18 DEBUG  WindowsBackend: windows_sp=None
03-09 01:18 DEBUG  WindowsBackend: windows_build=7600
03-09 01:18 DEBUG  WindowsBackend: gmt=4
03-09 01:18 DEBUG  WindowsBackend: country=US
03-09 01:18 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:18 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:18 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:18 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:18 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:18 DEBUG  WindowsBackend: windows_language=English
03-09 01:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:18 DEBUG  WindowsBackend: bootloader=vista
03-09 01:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207369.679688 mb free ntfs)
03-09 01:18 DEBUG  WindowsBackend: drive=Drive(C: hd 207369.679688 mb free ntfs)
03-09 01:18 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:18 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:18 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:18 DEBUG  WindowsBackend: drive=Drive(G: hd 69192.1054688 mb free ntfs)
03-09 01:18 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 01:18 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 01:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 01:18 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:18 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:18 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 01:18 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 01:18 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:18 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:18 DEBUG  CommonBackend: Searching for local CDs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Ubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Ubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Ubuntu Netbook CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Kubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Kubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Kubuntu Netbook CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Xubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Xubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Mythbuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp is a valid Mythbuntu CD
03-09 01:18 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:18 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:18 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:18 INFO   root: Running the uninstaller...
03-09 01:18 INFO   CommonBackend: This is the uninstaller running
03-09 01:18 DEBUG  WindowsFrontend: __init__...
03-09 01:18 DEBUG  WindowsFrontend: on_init...
03-09 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\translations, languages=['en_US', 'en']
03-09 01:18 INFO   root: Received settings
03-09 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\translations, languages=['en_US', 'en']
03-09 01:18 DEBUG  TaskList: # Running tasklist...
03-09 01:18 DEBUG  TaskList: ## Running Backup ISO...
03-09 01:18 DEBUG  TaskList: ## Finished Backup ISO
03-09 01:18 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 01:18 DEBUG  WindowsBackend: Could not find bcd id
03-09 01:18 DEBUG  WindowsBackend: undo_bootini C:
03-09 01:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 207369.679688 mb free ntfs)
03-09 01:18 DEBUG  WindowsBackend: undo_bootini D:
03-09 01:18 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:18 DEBUG  WindowsBackend: undo_bootini E:
03-09 01:18 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:18 DEBUG  WindowsBackend: undo_bootini G:
03-09 01:18 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 69192.1054688 mb free ntfs)
03-09 01:18 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 01:18 DEBUG  TaskList: ## Running Remove target dir...
03-09 01:18 DEBUG  CommonBackend: Deleting G:\ubuntu
03-09 01:18 DEBUG  TaskList: ## Finished Remove target dir
03-09 01:18 DEBUG  TaskList: ## Running Remove registry key...
03-09 01:18 DEBUG  TaskList: ## Finished Remove registry key
03-09 01:18 DEBUG  TaskList: # Finished tasklist
03-09 01:18 INFO   root: Almost finished uninstalling
03-09 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl36A9.tmp\translations, languages=['en_US', 'en']
03-09 01:18 INFO   root: Finished uninstallation
03-09 01:18 DEBUG  root: application.quit
03-09 01:18 DEBUG  WindowsFrontend: frontend.quit
03-09 01:18 DEBUG  WindowsFrontend: frontend.on_quit
03-09 01:18 DEBUG  root: application.on_quit
03-09 01:18 INFO   root: sys.exit
03-09 01:19 INFO   root: === wubi 10.10 rev197 ===
03-09 01:19 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 01:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-09 01:19 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\data
03-09 01:19 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\bin\7z.exe
03-09 01:19 DEBUG  CommonBackend: Fetching basic info...
03-09 01:19 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:19 DEBUG  CommonBackend: platform=win32
03-09 01:19 DEBUG  CommonBackend: osname=nt
03-09 01:19 DEBUG  CommonBackend: language=en_US
03-09 01:19 DEBUG  CommonBackend: encoding=cp1256
03-09 01:19 DEBUG  WindowsBackend: arch=amd64
03-09 01:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\data\isolist.ini
03-09 01:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:19 DEBUG  WindowsBackend: Fetching host info...
03-09 01:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:19 DEBUG  WindowsBackend: windows version=vista
03-09 01:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:19 DEBUG  WindowsBackend: windows_sp=None
03-09 01:19 DEBUG  WindowsBackend: windows_build=7600
03-09 01:19 DEBUG  WindowsBackend: gmt=4
03-09 01:19 DEBUG  WindowsBackend: country=US
03-09 01:19 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:19 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:19 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:19 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:19 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:19 DEBUG  WindowsBackend: windows_language=English
03-09 01:19 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:19 DEBUG  WindowsBackend: bootloader=vista
03-09 01:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207376.960938 mb free ntfs)
03-09 01:19 DEBUG  WindowsBackend: drive=Drive(C: hd 207376.960938 mb free ntfs)
03-09 01:19 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:19 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:19 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 01:19 DEBUG  WindowsBackend: uninstaller_path=None
03-09 01:19 DEBUG  WindowsBackend: previous_target_dir=None
03-09 01:19 DEBUG  WindowsBackend: previous_distro_name=None
03-09 01:19 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:19 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:19 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 01:19 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 01:19 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:19 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:19 DEBUG  CommonBackend: Searching for local CDs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Ubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Ubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Ubuntu Netbook CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Kubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Kubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Kubuntu Netbook CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Xubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Xubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Mythbuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp is a valid Mythbuntu CD
03-09 01:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:19 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:19 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:19 INFO   root: Running the CD menu...
03-09 01:19 DEBUG  WindowsFrontend: __init__...
03-09 01:19 DEBUG  WindowsFrontend: on_init...
03-09 01:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\translations, languages=['en_US', 'en']
03-09 01:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\translations, languages=['en_US', 'en']
03-09 01:19 INFO   root: CD menu finished
03-09 01:19 INFO   root: Running the CD boot helper...
03-09 01:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\translations, languages=['en_US', 'en']
03-09 01:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\translations, languages=['en_US', 'en']
03-09 01:19 INFO   root: CD boot helper confirmed
03-09 01:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\translations, languages=['en_US', 'en']
03-09 01:19 DEBUG  TaskList: # Running tasklist...
03-09 01:19 DEBUG  TaskList: ## Running select_target_dir...
03-09 01:19 INFO   WindowsBackend: Installing into C:\ubuntu
03-09 01:19 DEBUG  TaskList: ## Finished select_target_dir
03-09 01:19 DEBUG  TaskList: ## Running create_dir_structure...
03-09 01:19 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-09 01:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-09 01:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-09 01:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-09 01:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-09 01:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-09 01:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-09 01:19 DEBUG  TaskList: ## Finished create_dir_structure
03-09 01:19 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 01:19 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 01:19 DEBUG  TaskList: ## Running create_uninstaller...
03-09 01:19 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 01:19 DEBUG  TaskList: ## Finished create_uninstaller
03-09 01:19 DEBUG  TaskList: ## Running copy_installation_files...
03-09 01:19 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-09 01:19 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\winboot -> C:\ubuntu\winboot
03-09 01:19 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-09 01:19 DEBUG  TaskList: ## Finished copy_installation_files
03-09 01:19 DEBUG  TaskList: ## Running use_cd...
03-09 01:19 DEBUG  TaskList: New task copy_file
03-09 01:19 DEBUG  TaskList: ### Running copy_file...
03-09 01:23 DEBUG  TaskList: ### Finished copy_file
03-09 01:23 DEBUG  TaskList: New task check_iso
03-09 01:23 DEBUG  TaskList: ### Running check_iso...
03-09 01:23 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-09 01:23 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-09 01:23 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-09 01:23 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:23 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-09 01:23 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
03-09 01:23 DEBUG  TaskList: New task get_metalink
03-09 01:23 DEBUG  TaskList: #### Running get_metalink...
03-09 01:23 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink > C:\ubuntu\install
03-09 01:23 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
03-09 01:23 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.metalink > C:\ubuntu\install
03-09 01:23 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
03-09 01:23 DEBUG  TaskList: #### Finished get_metalink
03-09 01:23 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\ubuntu\install\installation.iso, ignoring
03-09 01:23 DEBUG  TaskList: ### Finished check_iso
03-09 01:23 DEBUG  TaskList: ## Finished use_cd
03-09 01:23 DEBUG  TaskList: ## Running extract_kernel...
03-09 01:23 DEBUG  CommonBackend: Copying files from CD F:\
03-09 01:24 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-09 01:24 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
03-09 01:24 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-09 01:24 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
03-09 01:24 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-09 01:24 DEBUG  TaskList: ## Finished extract_kernel
03-09 01:24 DEBUG  TaskList: ## Running create_preseed_cdboot...
03-09 01:24 DEBUG  TaskList: ## Finished create_preseed_cdboot
03-09 01:24 DEBUG  TaskList: ## Running modify_bootloader...
03-09 01:24 DEBUG  TaskList: New task modify_bcd
03-09 01:24 DEBUG  TaskList: ### Running modify_bcd...
03-09 01:24 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 207376.960938 mb free ntfs)
03-09 01:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {ce933108-7663-11df-b187-af18c7e076c4}
03-09 01:24 DEBUG  TaskList: ### Finished modify_bcd
03-09 01:24 DEBUG  TaskList: New task modify_bcd
03-09 01:24 DEBUG  TaskList: ### Running modify_bcd...
03-09 01:24 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:24 DEBUG  WindowsBackend: BCD has already been modified
03-09 01:24 DEBUG  TaskList: ### Finished modify_bcd
03-09 01:24 DEBUG  TaskList: New task modify_bcd
03-09 01:24 DEBUG  TaskList: ### Running modify_bcd...
03-09 01:24 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:24 DEBUG  WindowsBackend: BCD has already been modified
03-09 01:24 DEBUG  TaskList: ### Finished modify_bcd
03-09 01:24 DEBUG  TaskList: New task modify_bcd
03-09 01:24 DEBUG  TaskList: ### Running modify_bcd...
03-09 01:24 DEBUG  WindowsBackend: modify_bcd Drive(G: hd 69901.8398438 mb free ntfs)
03-09 01:24 DEBUG  WindowsBackend: BCD has already been modified
03-09 01:24 DEBUG  TaskList: ### Finished modify_bcd
03-09 01:24 DEBUG  TaskList: ## Finished modify_bootloader
03-09 01:24 DEBUG  TaskList: ## Running modify_grub_configuration...
03-09 01:24 DEBUG  TaskList: ## Finished modify_grub_configuration
03-09 01:24 DEBUG  TaskList: ## Running uncompress_files...
03-09 01:24 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
03-09 01:24 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
03-09 01:24 DEBUG  TaskList: ## Finished uncompress_files
03-09 01:24 DEBUG  TaskList: ## Running eject_cd...
03-09 01:24 DEBUG  TaskList: ## Finished eject_cd
03-09 01:24 DEBUG  TaskList: # Finished tasklist
03-09 01:24 INFO   root: Almost finished installing
03-09 01:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD622.tmp\translations, languages=['en_US', 'en']
03-09 01:24 INFO   root: Finished installation
03-09 01:24 INFO   root: Rebooting
03-09 01:24 DEBUG  TaskList: # Running tasklist...
03-09 01:24 DEBUG  TaskList: ## Running reboot...
03-09 01:24 DEBUG  TaskList: ## Finished reboot
03-09 01:24 DEBUG  TaskList: # Finished tasklist
03-09 01:24 DEBUG  root: application.quit
03-09 01:24 DEBUG  WindowsFrontend: frontend.quit
03-09 01:24 DEBUG  WindowsFrontend: frontend.on_quit
03-09 01:24 DEBUG  root: application.on_quit
03-09 01:24 INFO   root: sys.exit
03-09 01:44 INFO   root: === wubi 10.10 rev197 ===
03-09 01:44 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 01:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-09 01:44 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\data
03-09 01:44 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\bin\7z.exe
03-09 01:44 DEBUG  CommonBackend: Fetching basic info...
03-09 01:44 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:44 DEBUG  CommonBackend: platform=win32
03-09 01:44 DEBUG  CommonBackend: osname=nt
03-09 01:44 DEBUG  CommonBackend: language=en_US
03-09 01:44 DEBUG  CommonBackend: encoding=cp1256
03-09 01:44 DEBUG  WindowsBackend: arch=amd64
03-09 01:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\data\isolist.ini
03-09 01:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:44 DEBUG  WindowsBackend: Fetching host info...
03-09 01:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:44 DEBUG  WindowsBackend: windows version=vista
03-09 01:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:44 DEBUG  WindowsBackend: windows_sp=None
03-09 01:44 DEBUG  WindowsBackend: windows_build=7600
03-09 01:44 DEBUG  WindowsBackend: gmt=4
03-09 01:44 DEBUG  WindowsBackend: country=US
03-09 01:44 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:44 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:44 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:44 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:44 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:44 DEBUG  WindowsBackend: windows_language=English
03-09 01:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:44 DEBUG  WindowsBackend: bootloader=vista
03-09 01:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 206662.527344 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(C: hd 206662.527344 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-09 01:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-09 01:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 01:44 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:44 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:44 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 01:44 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 01:44 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:44 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:44 DEBUG  CommonBackend: Searching for local CDs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:44 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:44 INFO   root: Running the CD menu...
03-09 01:44 DEBUG  WindowsFrontend: __init__...
03-09 01:44 DEBUG  WindowsFrontend: on_init...
03-09 01:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
03-09 01:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
03-09 01:44 INFO   root: CD menu finished
03-09 01:44 INFO   root: Already installed, running the uninstaller...
03-09 01:44 INFO   root: Running the uninstaller...
03-09 01:44 INFO   CommonBackend: This is the uninstaller running
03-09 01:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
03-09 01:44 INFO   root: Received settings
03-09 01:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
03-09 01:44 DEBUG  TaskList: # Running tasklist...
03-09 01:44 DEBUG  TaskList: ## Running Backup ISO...
03-09 01:44 DEBUG  TaskList: ## Finished Backup ISO
03-09 01:44 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 01:44 DEBUG  WindowsBackend: Removing bcd entry {ce933108-7663-11df-b187-af18c7e076c4}
03-09 01:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
03-09 01:44 DEBUG  WindowsBackend: undo_bootini C:
03-09 01:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 206662.527344 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: undo_bootini D:
03-09 01:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: undo_bootini E:
03-09 01:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:44 DEBUG  WindowsBackend: undo_bootini G:
03-09 01:44 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 69901.8398438 mb free ntfs)
03-09 01:44 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 01:44 DEBUG  TaskList: ## Running Remove target dir...
03-09 01:44 DEBUG  CommonBackend: Deleting C:\ubuntu
03-09 01:44 DEBUG  TaskList: ## Finished Remove target dir
03-09 01:44 DEBUG  TaskList: ## Running Remove registry key...
03-09 01:44 DEBUG  TaskList: ## Finished Remove registry key
03-09 01:44 DEBUG  TaskList: # Finished tasklist
03-09 01:44 INFO   root: Almost finished uninstalling
03-09 01:44 INFO   root: Finished uninstallation
03-09 01:44 DEBUG  CommonBackend: Fetching basic info...
03-09 01:44 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:44 DEBUG  CommonBackend: platform=win32
03-09 01:44 DEBUG  CommonBackend: osname=nt
03-09 01:44 DEBUG  WindowsBackend: arch=amd64
03-09 01:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\data\isolist.ini
03-09 01:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:44 DEBUG  WindowsBackend: Fetching host info...
03-09 01:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:44 DEBUG  WindowsBackend: windows version=vista
03-09 01:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:44 DEBUG  WindowsBackend: windows_sp=None
03-09 01:44 DEBUG  WindowsBackend: windows_build=7600
03-09 01:44 DEBUG  WindowsBackend: gmt=4
03-09 01:44 DEBUG  WindowsBackend: country=US
03-09 01:44 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:44 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:44 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:44 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:44 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:44 DEBUG  WindowsBackend: windows_language=English
03-09 01:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:44 DEBUG  WindowsBackend: bootloader=vista
03-09 01:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207372.058594 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(C: hd 207372.058594 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:44 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 01:44 DEBUG  WindowsBackend: uninstaller_path=None
03-09 01:44 DEBUG  WindowsBackend: previous_target_dir=None
03-09 01:44 DEBUG  WindowsBackend: previous_distro_name=None
03-09 01:44 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:44 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:44 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:44 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:44 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:44 DEBUG  CommonBackend: Searching for local CDs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:44 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:44 INFO   root: Running the installer...
03-09 01:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
03-09 01:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
03-09 01:45 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-09 01:45 INFO   root: Received settings
03-09 01:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
03-09 01:45 DEBUG  TaskList: # Running tasklist...
03-09 01:45 DEBUG  TaskList: ## Running select_target_dir...
03-09 01:45 INFO   WindowsBackend: Installing into G:\ubuntu
03-09 01:45 DEBUG  TaskList: ## Finished select_target_dir
03-09 01:45 DEBUG  TaskList: ## Running create_dir_structure...
03-09 01:45 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-09 01:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-09 01:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-09 01:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-09 01:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-09 01:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-09 01:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-09 01:45 DEBUG  TaskList: ## Finished create_dir_structure
03-09 01:45 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 01:45 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 01:45 DEBUG  TaskList: ## Running create_uninstaller...
03-09 01:45 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 01:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 01:45 DEBUG  TaskList: ## Finished create_uninstaller
03-09 01:45 DEBUG  TaskList: ## Running copy_installation_files...
03-09 01:45 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-09 01:45 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\winboot -> G:\ubuntu\winboot
03-09 01:45 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC65A.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-09 01:45 DEBUG  TaskList: ## Finished copy_installation_files
03-09 01:45 DEBUG  TaskList: ## Running get_iso...
03-09 01:45 DEBUG  TaskList: New task copy_file
03-09 01:45 DEBUG  TaskList: ### Running copy_file...
03-09 01:49 DEBUG  TaskList: ### Finished copy_file
03-09 01:49 DEBUG  TaskList: New task check_iso
03-09 01:49 DEBUG  TaskList: ### Running check_iso...
03-09 01:49 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
03-09 01:49 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
03-09 01:49 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
03-09 01:49 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:49 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
03-09 01:49 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
03-09 01:49 DEBUG  TaskList: New task get_metalink
03-09 01:49 DEBUG  TaskList: #### Running get_metalink...
03-09 01:49 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink > G:\ubuntu\install
03-09 01:49 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
03-09 01:49 DEBUG  downloader: download finished (read 9071 bytes)
03-09 01:49 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > G:\ubuntu\install
03-09 01:49 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-09 01:49 DEBUG  downloader: download finished (read 488 bytes)
03-09 01:49 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > G:\ubuntu\install
03-09 01:49 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-09 01:49 DEBUG  downloader: download finished (read 198 bytes)
03-09 01:49 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 01:49 INFO   saplog: Checking block bindings..
03-09 01:49 INFO   saplog: Key verified successfully.
03-09 01:49 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-09 01:49 DEBUG  TaskList: #### Finished get_metalink
03-09 01:49 DEBUG  TaskList: New task get_file_md5
03-09 01:49 DEBUG  TaskList: #### Running get_file_md5...
03-09 01:49 DEBUG  TaskList: #### Finished get_file_md5
03-09 01:49 DEBUG  TaskList: ### Finished check_iso
03-09 01:49 DEBUG  TaskList: ## Finished get_iso
03-09 01:49 DEBUG  TaskList: ## Running extract_kernel...
03-09 01:49 DEBUG  CommonBackend: Copying files from CD F:\
03-09 01:49 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-09 01:49 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-09 01:49 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-09 01:49 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-09 01:49 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-09 01:49 DEBUG  TaskList: ## Finished extract_kernel
03-09 01:49 DEBUG  TaskList: ## Running choose_disk_sizes...
03-09 01:49 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
03-09 01:49 DEBUG  TaskList: ## Finished choose_disk_sizes
03-09 01:49 DEBUG  TaskList: ## Running create_preseed...
03-09 01:49 DEBUG  TaskList: ## Finished create_preseed
03-09 01:49 DEBUG  TaskList: ## Running modify_bootloader...
03-09 01:49 DEBUG  TaskList: New task modify_bcd
03-09 01:49 DEBUG  TaskList: ### Running modify_bcd...
03-09 01:49 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 207372.058594 mb free ntfs)
03-09 01:49 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933109-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933109-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-09 01:49 DEBUG  TaskList: # Cancelling tasklist
03-09 01:49 DEBUG  TaskList: New task modify_bcd
03-09 01:49 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933109-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce933109-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-09 01:49 DEBUG  TaskList: New task modify_bcd
03-09 01:49 DEBUG  TaskList: New task modify_bcd
03-09 01:49 DEBUG  TaskList: ## Finished modify_bootloader
03-09 01:49 DEBUG  TaskList: # Finished tasklist
03-09 01:55 INFO   root: === wubi 10.10 rev197 ===
03-09 01:55 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 01:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-09 01:55 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\data
03-09 01:55 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\bin\7z.exe
03-09 01:55 DEBUG  CommonBackend: Fetching basic info...
03-09 01:55 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:55 DEBUG  CommonBackend: platform=win32
03-09 01:55 DEBUG  CommonBackend: osname=nt
03-09 01:55 DEBUG  CommonBackend: language=en_US
03-09 01:55 DEBUG  CommonBackend: encoding=cp1256
03-09 01:55 DEBUG  WindowsBackend: arch=amd64
03-09 01:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\data\isolist.ini
03-09 01:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:55 DEBUG  WindowsBackend: Fetching host info...
03-09 01:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:55 DEBUG  WindowsBackend: windows version=vista
03-09 01:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:55 DEBUG  WindowsBackend: windows_sp=None
03-09 01:55 DEBUG  WindowsBackend: windows_build=7600
03-09 01:55 DEBUG  WindowsBackend: gmt=4
03-09 01:55 DEBUG  WindowsBackend: country=US
03-09 01:55 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:55 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:55 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:55 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:55 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:55 DEBUG  WindowsBackend: windows_language=English
03-09 01:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:55 DEBUG  WindowsBackend: bootloader=vista
03-09 01:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207366.398438 mb free ntfs)
03-09 01:55 DEBUG  WindowsBackend: drive=Drive(C: hd 207366.398438 mb free ntfs)
03-09 01:55 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:55 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:55 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:55 DEBUG  WindowsBackend: drive=Drive(G: hd 69192.0898438 mb free ntfs)
03-09 01:55 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 01:55 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 01:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 01:55 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:55 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:55 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 01:55 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 01:55 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:55 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:55 DEBUG  CommonBackend: Searching for local CDs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Ubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Ubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Ubuntu Netbook CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Kubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Kubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Kubuntu Netbook CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Xubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Xubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Mythbuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp is a valid Mythbuntu CD
03-09 01:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:55 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:55 INFO   root: Running the CD menu...
03-09 01:55 DEBUG  WindowsFrontend: __init__...
03-09 01:55 DEBUG  WindowsFrontend: on_init...
03-09 01:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\translations, languages=['en_US', 'en']
03-09 01:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD99C.tmp\translations, languages=['en_US', 'en']
03-09 01:55 INFO   root: CD menu finished
03-09 01:55 INFO   root: Rebooting
03-09 01:55 DEBUG  TaskList: # Running tasklist...
03-09 01:55 DEBUG  TaskList: ## Running reboot...
03-09 01:55 DEBUG  TaskList: ## Finished reboot
03-09 01:55 DEBUG  TaskList: # Finished tasklist
03-09 01:55 DEBUG  root: application.quit
03-09 01:55 DEBUG  WindowsFrontend: frontend.quit
03-09 01:55 DEBUG  WindowsFrontend: frontend.on_quit
03-09 01:55 DEBUG  root: application.on_quit
03-09 01:55 INFO   root: sys.exit
03-09 01:57 INFO   root: === wubi 10.10 rev197 ===
03-09 01:57 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 01:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-09 01:57 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\data
03-09 01:57 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\bin\7z.exe
03-09 01:57 DEBUG  CommonBackend: Fetching basic info...
03-09 01:57 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:57 DEBUG  CommonBackend: platform=win32
03-09 01:57 DEBUG  CommonBackend: osname=nt
03-09 01:57 DEBUG  CommonBackend: language=en_US
03-09 01:57 DEBUG  CommonBackend: encoding=cp1256
03-09 01:57 DEBUG  WindowsBackend: arch=amd64
03-09 01:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\data\isolist.ini
03-09 01:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:57 DEBUG  WindowsBackend: Fetching host info...
03-09 01:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:57 DEBUG  WindowsBackend: windows version=vista
03-09 01:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:57 DEBUG  WindowsBackend: windows_sp=None
03-09 01:57 DEBUG  WindowsBackend: windows_build=7600
03-09 01:57 DEBUG  WindowsBackend: gmt=4
03-09 01:57 DEBUG  WindowsBackend: country=US
03-09 01:57 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:57 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:57 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:57 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:57 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:57 DEBUG  WindowsBackend: windows_language=English
03-09 01:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:57 DEBUG  WindowsBackend: bootloader=vista
03-09 01:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207367.703125 mb free ntfs)
03-09 01:57 DEBUG  WindowsBackend: drive=Drive(C: hd 207367.703125 mb free ntfs)
03-09 01:57 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:57 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:57 DEBUG  WindowsBackend: drive=Drive(G: hd 69192.0898438 mb free ntfs)
03-09 01:57 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 01:57 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 01:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 01:57 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:57 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:57 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 01:57 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 01:57 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:57 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:57 DEBUG  CommonBackend: Searching for local CDs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Ubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Ubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Ubuntu Netbook CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Kubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Kubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Kubuntu Netbook CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Xubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Xubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Mythbuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp is a valid Mythbuntu CD
03-09 01:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:57 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:57 INFO   root: Running the CD menu...
03-09 01:57 DEBUG  WindowsFrontend: __init__...
03-09 01:57 DEBUG  WindowsFrontend: on_init...
03-09 01:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\translations, languages=['en_US', 'en']
03-09 01:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\translations, languages=['en_US', 'en']
03-09 01:58 INFO   root: CD menu finished
03-09 01:58 INFO   root: Already installed, running the uninstaller...
03-09 01:58 INFO   root: Running the uninstaller...
03-09 01:58 INFO   CommonBackend: This is the uninstaller running
03-09 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF6A.tmp\translations, languages=['en_US', 'en']
03-09 01:58 INFO   WindowsFrontend: Operation cancelled
03-09 01:58 DEBUG  WindowsFrontend: frontend.quit
03-09 01:58 DEBUG  WindowsFrontend: frontend.on_quit
03-09 01:58 DEBUG  root: application.on_quit
03-09 01:58 INFO   root: sys.exit
03-09 01:58 INFO   root: === wubi 10.10 rev197 ===
03-09 01:58 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 01:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-09 01:58 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\data
03-09 01:58 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\bin\7z.exe
03-09 01:58 DEBUG  CommonBackend: Fetching basic info...
03-09 01:58 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:58 DEBUG  CommonBackend: platform=win32
03-09 01:58 DEBUG  CommonBackend: osname=nt
03-09 01:58 DEBUG  CommonBackend: language=en_US
03-09 01:58 DEBUG  CommonBackend: encoding=cp1256
03-09 01:58 DEBUG  WindowsBackend: arch=amd64
03-09 01:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\data\isolist.ini
03-09 01:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:58 DEBUG  WindowsBackend: Fetching host info...
03-09 01:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:58 DEBUG  WindowsBackend: windows version=vista
03-09 01:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:58 DEBUG  WindowsBackend: windows_sp=None
03-09 01:58 DEBUG  WindowsBackend: windows_build=7600
03-09 01:58 DEBUG  WindowsBackend: gmt=4
03-09 01:58 DEBUG  WindowsBackend: country=US
03-09 01:58 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:58 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:58 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:58 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:58 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:58 DEBUG  WindowsBackend: windows_language=English
03-09 01:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:58 DEBUG  WindowsBackend: bootloader=vista
03-09 01:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207369.007813 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(C: hd 207369.007813 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(G: hd 69192.0898438 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 01:58 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 01:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 01:58 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:58 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:58 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 01:58 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 01:58 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:58 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:58 DEBUG  CommonBackend: Searching for local CDs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Ubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Kubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 01:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 01:58 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:58 INFO   root: Running the CD menu...
03-09 01:58 DEBUG  WindowsFrontend: __init__...
03-09 01:58 DEBUG  WindowsFrontend: on_init...
03-09 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 01:58 INFO   root: CD menu finished
03-09 01:58 INFO   root: Already installed, running the uninstaller...
03-09 01:58 INFO   root: Running the uninstaller...
03-09 01:58 INFO   CommonBackend: This is the uninstaller running
03-09 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 01:58 INFO   root: Received settings
03-09 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 01:58 DEBUG  TaskList: # Running tasklist...
03-09 01:58 DEBUG  TaskList: ## Running Backup ISO...
03-09 01:58 DEBUG  TaskList: ## Finished Backup ISO
03-09 01:58 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 01:58 DEBUG  WindowsBackend: Could not find bcd id
03-09 01:58 DEBUG  WindowsBackend: undo_bootini C:
03-09 01:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 207369.007813 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: undo_bootini D:
03-09 01:58 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: undo_bootini E:
03-09 01:58 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:58 DEBUG  WindowsBackend: undo_bootini G:
03-09 01:58 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 69192.0898438 mb free ntfs)
03-09 01:58 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 01:58 DEBUG  TaskList: ## Running Remove target dir...
03-09 01:58 DEBUG  CommonBackend: Deleting G:\ubuntu
03-09 01:58 DEBUG  TaskList: ## Finished Remove target dir
03-09 01:58 DEBUG  TaskList: ## Running Remove registry key...
03-09 01:58 DEBUG  TaskList: ## Finished Remove registry key
03-09 01:58 DEBUG  TaskList: # Finished tasklist
03-09 01:58 INFO   root: Almost finished uninstalling
03-09 01:58 INFO   root: Finished uninstallation
03-09 01:58 DEBUG  CommonBackend: Fetching basic info...
03-09 01:58 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 01:58 DEBUG  CommonBackend: platform=win32
03-09 01:58 DEBUG  CommonBackend: osname=nt
03-09 01:58 DEBUG  WindowsBackend: arch=amd64
03-09 01:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\data\isolist.ini
03-09 01:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 01:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 01:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 01:58 DEBUG  WindowsBackend: Fetching host info...
03-09 01:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 01:58 DEBUG  WindowsBackend: windows version=vista
03-09 01:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 01:58 DEBUG  WindowsBackend: windows_sp=None
03-09 01:58 DEBUG  WindowsBackend: windows_build=7600
03-09 01:58 DEBUG  WindowsBackend: gmt=4
03-09 01:58 DEBUG  WindowsBackend: country=US
03-09 01:58 DEBUG  WindowsBackend: timezone=America/New_York
03-09 01:58 DEBUG  WindowsBackend: windows_username=Administrator
03-09 01:58 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 01:58 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 01:58 DEBUG  WindowsBackend: windows_language_code=1033
03-09 01:58 DEBUG  WindowsBackend: windows_language=English
03-09 01:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 01:58 DEBUG  WindowsBackend: bootloader=vista
03-09 01:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207366.335938 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(C: hd 207366.335938 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 01:58 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 01:58 DEBUG  WindowsBackend: uninstaller_path=None
03-09 01:58 DEBUG  WindowsBackend: previous_target_dir=None
03-09 01:58 DEBUG  WindowsBackend: previous_distro_name=None
03-09 01:58 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 01:58 DEBUG  WindowsBackend: keyboard_layout=us
03-09 01:58 DEBUG  WindowsBackend: keyboard_variant=
03-09 01:58 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 01:58 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 01:58 DEBUG  CommonBackend: Searching for local CDs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Ubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Kubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 01:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 01:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 01:58 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 01:58 INFO   root: Running the CD boot helper...
03-09 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 01:59 INFO   root: CD boot helper confirmed
03-09 01:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 01:59 DEBUG  TaskList: # Running tasklist...
03-09 01:59 DEBUG  TaskList: ## Running select_target_dir...
03-09 01:59 INFO   WindowsBackend: Installing into C:\ubuntu
03-09 01:59 DEBUG  TaskList: ## Finished select_target_dir
03-09 01:59 DEBUG  TaskList: ## Running create_dir_structure...
03-09 01:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-09 01:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-09 01:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-09 01:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-09 01:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-09 01:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-09 01:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-09 01:59 DEBUG  TaskList: ## Finished create_dir_structure
03-09 01:59 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 01:59 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 01:59 DEBUG  TaskList: ## Running create_uninstaller...
03-09 01:59 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 01:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 01:59 DEBUG  TaskList: ## Finished create_uninstaller
03-09 01:59 DEBUG  TaskList: ## Running copy_installation_files...
03-09 01:59 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-09 01:59 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\winboot -> C:\ubuntu\winboot
03-09 01:59 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-09 01:59 DEBUG  TaskList: ## Finished copy_installation_files
03-09 01:59 DEBUG  TaskList: ## Running use_cd...
03-09 01:59 DEBUG  TaskList: New task copy_file
03-09 01:59 DEBUG  TaskList: ### Running copy_file...
03-09 02:03 DEBUG  TaskList: ### Finished copy_file
03-09 02:03 DEBUG  TaskList: New task check_iso
03-09 02:03 DEBUG  TaskList: ### Running check_iso...
03-09 02:03 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-09 02:03 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-09 02:03 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-09 02:03 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 02:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 02:03 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-09 02:03 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
03-09 02:03 DEBUG  TaskList: New task get_metalink
03-09 02:03 DEBUG  TaskList: #### Running get_metalink...
03-09 02:03 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink > C:\ubuntu\install
03-09 02:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
03-09 02:03 DEBUG  downloader: download finished (read 9071 bytes)
03-09 02:03 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > C:\ubuntu\install
03-09 02:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-09 02:03 DEBUG  downloader: download finished (read 488 bytes)
03-09 02:03 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
03-09 02:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-09 02:03 DEBUG  downloader: download finished (read 198 bytes)
03-09 02:03 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 02:03 INFO   saplog: Checking block bindings..
03-09 02:03 INFO   saplog: Key verified successfully.
03-09 02:03 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-09 02:03 DEBUG  TaskList: #### Finished get_metalink
03-09 02:03 DEBUG  TaskList: New task get_file_md5
03-09 02:03 DEBUG  TaskList: #### Running get_file_md5...
03-09 02:03 DEBUG  TaskList: #### Finished get_file_md5
03-09 02:03 DEBUG  TaskList: ### Finished check_iso
03-09 02:03 DEBUG  TaskList: ## Finished use_cd
03-09 02:03 DEBUG  TaskList: ## Running extract_kernel...
03-09 02:03 DEBUG  CommonBackend: Copying files from CD F:\
03-09 02:04 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-09 02:04 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
03-09 02:04 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-09 02:04 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
03-09 02:04 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-09 02:04 DEBUG  TaskList: ## Finished extract_kernel
03-09 02:04 DEBUG  TaskList: ## Running create_preseed_cdboot...
03-09 02:04 DEBUG  TaskList: ## Finished create_preseed_cdboot
03-09 02:04 DEBUG  TaskList: ## Running modify_bootloader...
03-09 02:04 DEBUG  TaskList: New task modify_bcd
03-09 02:04 DEBUG  TaskList: ### Running modify_bcd...
03-09 02:04 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 207366.335938 mb free ntfs)
03-09 02:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {ce93310a-7663-11df-b187-af18c7e076c4}
03-09 02:04 DEBUG  TaskList: ### Finished modify_bcd
03-09 02:04 DEBUG  TaskList: New task modify_bcd
03-09 02:04 DEBUG  TaskList: ### Running modify_bcd...
03-09 02:04 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2841.45703125 mb free ntfs)
03-09 02:04 DEBUG  WindowsBackend: BCD has already been modified
03-09 02:04 DEBUG  TaskList: ### Finished modify_bcd
03-09 02:04 DEBUG  TaskList: New task modify_bcd
03-09 02:04 DEBUG  TaskList: ### Running modify_bcd...
03-09 02:04 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 92.6884765625 mb free fat32)
03-09 02:04 DEBUG  WindowsBackend: BCD has already been modified
03-09 02:04 DEBUG  TaskList: ### Finished modify_bcd
03-09 02:04 DEBUG  TaskList: New task modify_bcd
03-09 02:04 DEBUG  TaskList: ### Running modify_bcd...
03-09 02:04 DEBUG  WindowsBackend: modify_bcd Drive(G: hd 69901.8398438 mb free ntfs)
03-09 02:04 DEBUG  WindowsBackend: BCD has already been modified
03-09 02:04 DEBUG  TaskList: ### Finished modify_bcd
03-09 02:04 DEBUG  TaskList: ## Finished modify_bootloader
03-09 02:04 DEBUG  TaskList: ## Running modify_grub_configuration...
03-09 02:04 DEBUG  TaskList: ## Finished modify_grub_configuration
03-09 02:04 DEBUG  TaskList: ## Running uncompress_files...
03-09 02:04 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
03-09 02:04 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
03-09 02:04 DEBUG  TaskList: ## Finished uncompress_files
03-09 02:04 DEBUG  TaskList: ## Running eject_cd...
03-09 02:04 DEBUG  TaskList: ## Finished eject_cd
03-09 02:04 DEBUG  TaskList: # Finished tasklist
03-09 02:04 INFO   root: Almost finished installing
03-09 02:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylCB88.tmp\translations, languages=['en_US', 'en']
03-09 02:04 INFO   root: Finished installation
03-09 02:04 INFO   root: Rebooting
03-09 02:04 DEBUG  TaskList: # Running tasklist...
03-09 02:04 DEBUG  TaskList: ## Running reboot...
03-09 02:04 DEBUG  TaskList: ## Finished reboot
03-09 02:04 DEBUG  TaskList: # Finished tasklist
03-09 02:04 DEBUG  root: application.quit
03-09 02:04 DEBUG  WindowsFrontend: frontend.quit
03-09 02:04 DEBUG  WindowsFrontend: frontend.on_quit
03-09 02:04 DEBUG  root: application.on_quit
03-09 02:04 INFO   root: sys.exit
03-09 17:33 INFO   root: === wubi 10.10 rev197 ===
03-09 17:33 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 17:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-09 17:33 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\data
03-09 17:33 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\bin\7z.exe
03-09 17:33 DEBUG  CommonBackend: Fetching basic info...
03-09 17:33 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 17:33 DEBUG  CommonBackend: platform=win32
03-09 17:33 DEBUG  CommonBackend: osname=nt
03-09 17:33 DEBUG  CommonBackend: language=en_US
03-09 17:33 DEBUG  CommonBackend: encoding=cp1256
03-09 17:33 DEBUG  WindowsBackend: arch=amd64
03-09 17:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\data\isolist.ini
03-09 17:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 17:33 DEBUG  WindowsBackend: Fetching host info...
03-09 17:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 17:33 DEBUG  WindowsBackend: windows version=vista
03-09 17:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 17:33 DEBUG  WindowsBackend: windows_sp=None
03-09 17:33 DEBUG  WindowsBackend: windows_build=7600
03-09 17:33 DEBUG  WindowsBackend: gmt=4
03-09 17:33 DEBUG  WindowsBackend: country=US
03-09 17:33 DEBUG  WindowsBackend: timezone=America/New_York
03-09 17:33 DEBUG  WindowsBackend: windows_username=Administrator
03-09 17:33 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 17:33 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 17:33 DEBUG  WindowsBackend: windows_language_code=1033
03-09 17:33 DEBUG  WindowsBackend: windows_language=English
03-09 17:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 17:33 DEBUG  WindowsBackend: bootloader=vista
03-09 17:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 209724.285156 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(C: hd 209724.285156 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-09 17:33 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-09 17:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 17:33 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 17:33 DEBUG  WindowsBackend: keyboard_layout=us
03-09 17:33 DEBUG  WindowsBackend: keyboard_variant=
03-09 17:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 17:33 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 17:33 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 17:33 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 17:33 DEBUG  CommonBackend: Searching for local CDs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Ubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Kubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 17:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 17:33 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 17:33 INFO   root: Running the CD menu...
03-09 17:33 DEBUG  WindowsFrontend: __init__...
03-09 17:33 DEBUG  WindowsFrontend: on_init...
03-09 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\translations, languages=['en_US', 'en']
03-09 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\translations, languages=['en_US', 'en']
03-09 17:33 INFO   root: CD menu finished
03-09 17:33 INFO   root: Already installed, running the uninstaller...
03-09 17:33 INFO   root: Running the uninstaller...
03-09 17:33 INFO   CommonBackend: This is the uninstaller running
03-09 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\translations, languages=['en_US', 'en']
03-09 17:33 INFO   root: Received settings
03-09 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\translations, languages=['en_US', 'en']
03-09 17:33 DEBUG  TaskList: # Running tasklist...
03-09 17:33 DEBUG  TaskList: ## Running Backup ISO...
03-09 17:33 DEBUG  TaskList: ## Finished Backup ISO
03-09 17:33 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 17:33 DEBUG  WindowsBackend: Removing bcd entry {ce93310a-7663-11df-b187-af18c7e076c4}
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
03-09 17:33 DEBUG  WindowsBackend: undo_bootini C:
03-09 17:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 209724.285156 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: undo_bootini D:
03-09 17:33 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: undo_bootini E:
03-09 17:33 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 17:33 DEBUG  WindowsBackend: undo_bootini G:
03-09 17:33 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 69901.8398438 mb free ntfs)
03-09 17:33 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 17:33 DEBUG  TaskList: ## Running Remove target dir...
03-09 17:33 DEBUG  CommonBackend: Deleting C:\ubuntu
03-09 17:33 DEBUG  TaskList: ## Finished Remove target dir
03-09 17:33 DEBUG  TaskList: ## Running Remove registry key...
03-09 17:33 DEBUG  TaskList: ## Finished Remove registry key
03-09 17:33 DEBUG  TaskList: # Finished tasklist
03-09 17:33 INFO   root: Almost finished uninstalling
03-09 17:33 INFO   root: Finished uninstallation
03-09 17:33 DEBUG  CommonBackend: Fetching basic info...
03-09 17:33 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-09 17:33 DEBUG  CommonBackend: platform=win32
03-09 17:33 DEBUG  CommonBackend: osname=nt
03-09 17:33 DEBUG  WindowsBackend: arch=amd64
03-09 17:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\data\isolist.ini
03-09 17:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 17:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 17:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 17:33 DEBUG  WindowsBackend: Fetching host info...
03-09 17:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 17:33 DEBUG  WindowsBackend: windows version=vista
03-09 17:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 17:33 DEBUG  WindowsBackend: windows_sp=None
03-09 17:33 DEBUG  WindowsBackend: windows_build=7600
03-09 17:33 DEBUG  WindowsBackend: gmt=4
03-09 17:33 DEBUG  WindowsBackend: country=US
03-09 17:33 DEBUG  WindowsBackend: timezone=America/New_York
03-09 17:33 DEBUG  WindowsBackend: windows_username=Administrator
03-09 17:33 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 17:33 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 17:33 DEBUG  WindowsBackend: windows_language_code=1033
03-09 17:33 DEBUG  WindowsBackend: windows_language=English
03-09 17:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 17:33 DEBUG  WindowsBackend: bootloader=vista
03-09 17:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210430.058594 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(C: hd 210430.058594 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 17:33 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 17:33 DEBUG  WindowsBackend: uninstaller_path=None
03-09 17:33 DEBUG  WindowsBackend: previous_target_dir=None
03-09 17:33 DEBUG  WindowsBackend: previous_distro_name=None
03-09 17:33 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 17:33 DEBUG  WindowsBackend: keyboard_layout=us
03-09 17:33 DEBUG  WindowsBackend: keyboard_variant=
03-09 17:33 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 17:33 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 17:33 DEBUG  CommonBackend: Searching for local CDs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Ubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Kubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 17:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 17:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 17:33 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-09 17:33 INFO   root: Running the installer...
03-09 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\translations, languages=['en_US', 'en']
03-09 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\translations, languages=['en_US', 'en']
03-09 17:33 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-09 17:33 INFO   root: Received settings
03-09 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\translations, languages=['en_US', 'en']
03-09 17:33 DEBUG  TaskList: # Running tasklist...
03-09 17:33 DEBUG  TaskList: ## Running select_target_dir...
03-09 17:33 INFO   WindowsBackend: Installing into G:\ubuntu
03-09 17:33 DEBUG  TaskList: ## Finished select_target_dir
03-09 17:33 DEBUG  TaskList: ## Running create_dir_structure...
03-09 17:33 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-09 17:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-09 17:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-09 17:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-09 17:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-09 17:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-09 17:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-09 17:33 DEBUG  TaskList: ## Finished create_dir_structure
03-09 17:33 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 17:33 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 17:33 DEBUG  TaskList: ## Running create_uninstaller...
03-09 17:33 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 17:33 DEBUG  TaskList: ## Finished create_uninstaller
03-09 17:33 DEBUG  TaskList: ## Running copy_installation_files...
03-09 17:33 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-09 17:33 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\winboot -> G:\ubuntu\winboot
03-09 17:33 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD4DB.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-09 17:33 DEBUG  TaskList: ## Finished copy_installation_files
03-09 17:33 DEBUG  TaskList: ## Running get_iso...
03-09 17:33 DEBUG  TaskList: New task copy_file
03-09 17:33 DEBUG  TaskList: ### Running copy_file...
03-09 17:38 DEBUG  TaskList: ### Finished copy_file
03-09 17:38 DEBUG  TaskList: New task check_iso
03-09 17:38 DEBUG  TaskList: ### Running check_iso...
03-09 17:38 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
03-09 17:38 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
03-09 17:38 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
03-09 17:38 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 17:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 17:38 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
03-09 17:38 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
03-09 17:38 DEBUG  TaskList: New task get_metalink
03-09 17:38 DEBUG  TaskList: #### Running get_metalink...
03-09 17:38 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink > G:\ubuntu\install
03-09 17:38 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
03-09 17:38 DEBUG  downloader: download finished (read 9071 bytes)
03-09 17:38 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > G:\ubuntu\install
03-09 17:38 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-09 17:38 DEBUG  downloader: download finished (read 488 bytes)
03-09 17:38 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > G:\ubuntu\install
03-09 17:38 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-09 17:38 DEBUG  downloader: download finished (read 198 bytes)
03-09 17:38 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 17:38 INFO   saplog: Checking block bindings..
03-09 17:38 INFO   saplog: Key verified successfully.
03-09 17:38 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-09 17:38 DEBUG  TaskList: #### Finished get_metalink
03-09 17:38 DEBUG  TaskList: New task get_file_md5
03-09 17:38 DEBUG  TaskList: #### Running get_file_md5...
03-09 17:38 DEBUG  TaskList: #### Finished get_file_md5
03-09 17:38 DEBUG  TaskList: ### Finished check_iso
03-09 17:38 DEBUG  TaskList: ## Finished get_iso
03-09 17:38 DEBUG  TaskList: ## Running extract_kernel...
03-09 17:38 DEBUG  CommonBackend: Copying files from CD F:\
03-09 17:38 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-09 17:38 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-09 17:38 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-09 17:38 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-09 17:38 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-09 17:38 DEBUG  TaskList: ## Finished extract_kernel
03-09 17:38 DEBUG  TaskList: ## Running choose_disk_sizes...
03-09 17:38 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
03-09 17:38 DEBUG  TaskList: ## Finished choose_disk_sizes
03-09 17:38 DEBUG  TaskList: ## Running create_preseed...
03-09 17:38 DEBUG  TaskList: ## Finished create_preseed
03-09 17:38 DEBUG  TaskList: ## Running modify_bootloader...
03-09 17:38 DEBUG  TaskList: New task modify_bcd
03-09 17:38 DEBUG  TaskList: ### Running modify_bcd...
03-09 17:38 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 210430.058594 mb free ntfs)
03-09 17:38 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce93310b-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce93310b-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-09 17:38 DEBUG  TaskList: # Cancelling tasklist
03-09 17:38 DEBUG  TaskList: New task modify_bcd
03-09 17:38 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce93310b-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ce93310b-7663-11df-b187-af18c7e076c4} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-09 17:38 DEBUG  TaskList: New task modify_bcd
03-09 17:38 DEBUG  TaskList: New task modify_bcd
03-09 17:38 DEBUG  TaskList: ## Finished modify_bootloader
03-09 17:38 DEBUG  TaskList: # Finished tasklist
03-09 18:28 INFO   root: === wubi 10.10 rev197 ===
03-09 18:28 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 18:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 18:28 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\data
03-09 18:28 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\bin\7z.exe
03-09 18:28 DEBUG  CommonBackend: Fetching basic info...
03-09 18:28 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 18:28 DEBUG  CommonBackend: platform=win32
03-09 18:28 DEBUG  CommonBackend: osname=nt
03-09 18:28 DEBUG  CommonBackend: language=en_US
03-09 18:28 DEBUG  CommonBackend: encoding=cp1256
03-09 18:28 DEBUG  WindowsBackend: arch=amd64
03-09 18:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\data\isolist.ini
03-09 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 18:28 DEBUG  WindowsBackend: Fetching host info...
03-09 18:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 18:28 DEBUG  WindowsBackend: windows version=vista
03-09 18:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 18:28 DEBUG  WindowsBackend: windows_sp=None
03-09 18:28 DEBUG  WindowsBackend: windows_build=7600
03-09 18:28 DEBUG  WindowsBackend: gmt=4
03-09 18:28 DEBUG  WindowsBackend: country=US
03-09 18:28 DEBUG  WindowsBackend: timezone=America/New_York
03-09 18:28 DEBUG  WindowsBackend: windows_username=Administrator
03-09 18:28 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 18:28 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 18:28 DEBUG  WindowsBackend: windows_language_code=1033
03-09 18:28 DEBUG  WindowsBackend: windows_language=English
03-09 18:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 18:28 DEBUG  WindowsBackend: bootloader=vista
03-09 18:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210420.195313 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(C: hd 210420.195313 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(G: hd 69192.0898438 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 18:28 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 18:28 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 18:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 18:28 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 18:28 DEBUG  WindowsBackend: keyboard_layout=us
03-09 18:28 DEBUG  WindowsBackend: keyboard_variant=
03-09 18:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 18:28 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 18:28 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 18:28 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 18:28 DEBUG  CommonBackend: Searching for local CDs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 18:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 18:28 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 18:28 INFO   root: Running the CD menu...
03-09 18:28 DEBUG  WindowsFrontend: __init__...
03-09 18:28 DEBUG  WindowsFrontend: on_init...
03-09 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\translations, languages=['en_US', 'en']
03-09 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\translations, languages=['en_US', 'en']
03-09 18:28 INFO   root: CD menu finished
03-09 18:28 INFO   root: Already installed, running the uninstaller...
03-09 18:28 INFO   root: Running the uninstaller...
03-09 18:28 INFO   CommonBackend: This is the uninstaller running
03-09 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC0FD.tmp\translations, languages=['en_US', 'en']
03-09 18:28 INFO   WindowsFrontend: Operation cancelled
03-09 18:28 DEBUG  WindowsFrontend: frontend.quit
03-09 18:28 DEBUG  WindowsFrontend: frontend.on_quit
03-09 18:28 DEBUG  root: application.on_quit
03-09 18:28 INFO   root: sys.exit
03-09 18:28 INFO   root: === wubi 10.10 rev197 ===
03-09 18:28 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 18:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 18:28 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\data
03-09 18:28 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\bin\7z.exe
03-09 18:28 DEBUG  CommonBackend: Fetching basic info...
03-09 18:28 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 18:28 DEBUG  CommonBackend: platform=win32
03-09 18:28 DEBUG  CommonBackend: osname=nt
03-09 18:28 DEBUG  CommonBackend: language=en_US
03-09 18:28 DEBUG  CommonBackend: encoding=cp1256
03-09 18:28 DEBUG  WindowsBackend: arch=amd64
03-09 18:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\data\isolist.ini
03-09 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 18:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 18:28 DEBUG  WindowsBackend: Fetching host info...
03-09 18:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 18:28 DEBUG  WindowsBackend: windows version=vista
03-09 18:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 18:28 DEBUG  WindowsBackend: windows_sp=None
03-09 18:28 DEBUG  WindowsBackend: windows_build=7600
03-09 18:28 DEBUG  WindowsBackend: gmt=4
03-09 18:28 DEBUG  WindowsBackend: country=US
03-09 18:28 DEBUG  WindowsBackend: timezone=America/New_York
03-09 18:28 DEBUG  WindowsBackend: windows_username=Administrator
03-09 18:28 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 18:28 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 18:28 DEBUG  WindowsBackend: windows_language_code=1033
03-09 18:28 DEBUG  WindowsBackend: windows_language=English
03-09 18:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 18:28 DEBUG  WindowsBackend: bootloader=vista
03-09 18:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210424.425781 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(C: hd 210424.425781 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(G: hd 69192.0898438 mb free ntfs)
03-09 18:28 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 18:28 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 18:28 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 18:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 18:28 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 18:28 DEBUG  WindowsBackend: keyboard_layout=us
03-09 18:28 DEBUG  WindowsBackend: keyboard_variant=
03-09 18:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 18:28 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 18:28 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 18:28 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 18:28 DEBUG  CommonBackend: Searching for local CDs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 18:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 18:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 18:28 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 18:28 INFO   root: Running the CD menu...
03-09 18:28 DEBUG  WindowsFrontend: __init__...
03-09 18:28 DEBUG  WindowsFrontend: on_init...
03-09 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\translations, languages=['en_US', 'en']
03-09 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl6067.tmp\translations, languages=['en_US', 'en']
03-09 18:29 DEBUG  root: application.quit
03-09 18:29 DEBUG  WindowsFrontend: frontend.quit
03-09 18:29 DEBUG  WindowsFrontend: frontend.on_quit
03-09 18:29 DEBUG  root: application.on_quit
03-09 18:29 INFO   root: sys.exit
03-09 18:29 INFO   root: === wubi 10.10 rev197 ===
03-09 18:29 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 18:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 18:29 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\data
03-09 18:29 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\bin\7z.exe
03-09 18:29 DEBUG  CommonBackend: Fetching basic info...
03-09 18:29 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 18:29 DEBUG  CommonBackend: platform=win32
03-09 18:29 DEBUG  CommonBackend: osname=nt
03-09 18:29 DEBUG  CommonBackend: language=en_US
03-09 18:29 DEBUG  CommonBackend: encoding=cp1256
03-09 18:29 DEBUG  WindowsBackend: arch=amd64
03-09 18:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\data\isolist.ini
03-09 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 18:29 DEBUG  WindowsBackend: Fetching host info...
03-09 18:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 18:29 DEBUG  WindowsBackend: windows version=vista
03-09 18:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 18:29 DEBUG  WindowsBackend: windows_sp=None
03-09 18:29 DEBUG  WindowsBackend: windows_build=7600
03-09 18:29 DEBUG  WindowsBackend: gmt=4
03-09 18:29 DEBUG  WindowsBackend: country=US
03-09 18:29 DEBUG  WindowsBackend: timezone=America/New_York
03-09 18:29 DEBUG  WindowsBackend: windows_username=Administrator
03-09 18:29 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 18:29 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 18:29 DEBUG  WindowsBackend: windows_language_code=1033
03-09 18:29 DEBUG  WindowsBackend: windows_language=English
03-09 18:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 18:29 DEBUG  WindowsBackend: bootloader=vista
03-09 18:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210421.597656 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(C: hd 210421.597656 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(G: hd 69192.0898438 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 18:29 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 18:29 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 18:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 18:29 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 18:29 DEBUG  WindowsBackend: keyboard_layout=us
03-09 18:29 DEBUG  WindowsBackend: keyboard_variant=
03-09 18:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 18:29 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 18:29 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 18:29 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 18:29 DEBUG  CommonBackend: Searching for local CDs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 18:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 18:29 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 18:29 INFO   root: Running the CD menu...
03-09 18:29 DEBUG  WindowsFrontend: __init__...
03-09 18:29 DEBUG  WindowsFrontend: on_init...
03-09 18:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\translations, languages=['en_US', 'en']
03-09 18:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\translations, languages=['en_US', 'en']
03-09 18:29 INFO   root: CD menu finished
03-09 18:29 INFO   root: Already installed, running the uninstaller...
03-09 18:29 INFO   root: Running the uninstaller...
03-09 18:29 INFO   CommonBackend: This is the uninstaller running
03-09 18:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\translations, languages=['en_US', 'en']
03-09 18:29 INFO   root: Received settings
03-09 18:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\translations, languages=['en_US', 'en']
03-09 18:29 DEBUG  TaskList: # Running tasklist...
03-09 18:29 DEBUG  TaskList: ## Running Backup ISO...
03-09 18:29 DEBUG  TaskList: ## Finished Backup ISO
03-09 18:29 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 18:29 DEBUG  WindowsBackend: Could not find bcd id
03-09 18:29 DEBUG  WindowsBackend: undo_bootini C:
03-09 18:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 210421.597656 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: undo_bootini D:
03-09 18:29 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: undo_bootini E:
03-09 18:29 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 18:29 DEBUG  WindowsBackend: undo_bootini G:
03-09 18:29 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 69192.0898438 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: undo_bootini H:
03-09 18:29 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 2988.33203125 mb free fat32)
03-09 18:29 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 18:29 DEBUG  TaskList: ## Running Remove target dir...
03-09 18:29 DEBUG  CommonBackend: Deleting G:\ubuntu
03-09 18:29 DEBUG  TaskList: ## Finished Remove target dir
03-09 18:29 DEBUG  TaskList: ## Running Remove registry key...
03-09 18:29 DEBUG  TaskList: ## Finished Remove registry key
03-09 18:29 DEBUG  TaskList: # Finished tasklist
03-09 18:29 INFO   root: Almost finished uninstalling
03-09 18:29 INFO   root: Finished uninstallation
03-09 18:29 DEBUG  CommonBackend: Fetching basic info...
03-09 18:29 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 18:29 DEBUG  CommonBackend: platform=win32
03-09 18:29 DEBUG  CommonBackend: osname=nt
03-09 18:29 DEBUG  WindowsBackend: arch=amd64
03-09 18:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\data\isolist.ini
03-09 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 18:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 18:29 DEBUG  WindowsBackend: Fetching host info...
03-09 18:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 18:29 DEBUG  WindowsBackend: windows version=vista
03-09 18:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 18:29 DEBUG  WindowsBackend: windows_sp=None
03-09 18:29 DEBUG  WindowsBackend: windows_build=7600
03-09 18:29 DEBUG  WindowsBackend: gmt=4
03-09 18:29 DEBUG  WindowsBackend: country=US
03-09 18:29 DEBUG  WindowsBackend: timezone=America/New_York
03-09 18:29 DEBUG  WindowsBackend: windows_username=Administrator
03-09 18:29 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 18:29 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 18:29 DEBUG  WindowsBackend: windows_language_code=1033
03-09 18:29 DEBUG  WindowsBackend: windows_language=English
03-09 18:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 18:29 DEBUG  WindowsBackend: bootloader=vista
03-09 18:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210421.6875 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(C: hd 210421.6875 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 18:29 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 18:29 DEBUG  WindowsBackend: uninstaller_path=None
03-09 18:29 DEBUG  WindowsBackend: previous_target_dir=None
03-09 18:29 DEBUG  WindowsBackend: previous_distro_name=None
03-09 18:29 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 18:29 DEBUG  WindowsBackend: keyboard_layout=us
03-09 18:29 DEBUG  WindowsBackend: keyboard_variant=
03-09 18:29 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 18:29 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 18:29 DEBUG  CommonBackend: Searching for local CDs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 18:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 18:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 18:29 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 18:29 INFO   root: Running the installer...
03-09 18:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\translations, languages=['en_US', 'en']
03-09 18:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\translations, languages=['en_US', 'en']
03-09 18:30 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-09 18:30 INFO   root: Received settings
03-09 18:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\translations, languages=['en_US', 'en']
03-09 18:30 DEBUG  TaskList: # Running tasklist...
03-09 18:30 DEBUG  TaskList: ## Running select_target_dir...
03-09 18:30 INFO   WindowsBackend: Installing into G:\ubuntu
03-09 18:30 DEBUG  TaskList: ## Finished select_target_dir
03-09 18:30 DEBUG  TaskList: ## Running create_dir_structure...
03-09 18:30 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-09 18:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-09 18:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-09 18:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-09 18:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-09 18:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-09 18:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-09 18:30 DEBUG  TaskList: ## Finished create_dir_structure
03-09 18:30 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 18:30 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 18:30 DEBUG  TaskList: ## Running create_uninstaller...
03-09 18:30 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 18:30 DEBUG  TaskList: ## Finished create_uninstaller
03-09 18:30 DEBUG  TaskList: ## Running copy_installation_files...
03-09 18:30 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-09 18:30 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\winboot -> G:\ubuntu\winboot
03-09 18:30 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylB07.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-09 18:30 DEBUG  TaskList: ## Finished copy_installation_files
03-09 18:30 DEBUG  TaskList: ## Running get_iso...
03-09 18:30 DEBUG  TaskList: New task copy_file
03-09 18:30 DEBUG  TaskList: ### Running copy_file...
03-09 18:38 DEBUG  TaskList: ### Finished copy_file
03-09 18:38 DEBUG  TaskList: New task check_iso
03-09 18:38 DEBUG  TaskList: ### Running check_iso...
03-09 18:38 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
03-09 18:38 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
03-09 18:38 DEBUG  Distro:     wrong size: 3868623360 > 900000000
03-09 18:38 DEBUG  TaskList: ### Finished check_iso
03-09 18:38 DEBUG  CommonBackend: Searching for local ISO
03-09 18:38 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 18:38 DEBUG  TaskList: New task get_metalink
03-09 18:38 DEBUG  TaskList: ### Running get_metalink...
03-09 18:38 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > G:\ubuntu\install
03-09 18:39 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
03-09 18:39 DEBUG  downloader: download finished (read 9135 bytes)
03-09 18:39 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > G:\ubuntu\install
03-09 18:39 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-09 18:39 DEBUG  downloader: download finished (read 488 bytes)
03-09 18:39 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > G:\ubuntu\install
03-09 18:39 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-09 18:39 DEBUG  downloader: download finished (read 198 bytes)
03-09 18:39 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 18:39 INFO   saplog: Checking block bindings..
03-09 18:39 INFO   saplog: Key verified successfully.
03-09 18:39 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-09 18:39 DEBUG  TaskList: ### Finished get_metalink
03-09 18:39 DEBUG  TaskList: New task download
03-09 18:39 DEBUG  TaskList: ### Running download...
03-09 18:39 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > G:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-09 19:49 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


03-09 19:49 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
03-09 19:49 DEBUG  TaskList: ### Finished download
03-09 19:49 ERROR  TaskList: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
03-09 19:49 DEBUG  TaskList: # Cancelling tasklist
03-09 19:49 DEBUG  TaskList: # Finished tasklist
03-09 19:49 ERROR  root: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
03-09 20:43 INFO   root: === wubi 10.10 rev197 ===
03-09 20:43 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 20:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
03-09 20:43 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\data
03-09 20:43 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\bin\7z.exe
03-09 20:43 DEBUG  CommonBackend: Fetching basic info...
03-09 20:43 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
03-09 20:43 DEBUG  CommonBackend: platform=win32
03-09 20:43 DEBUG  CommonBackend: osname=nt
03-09 20:43 DEBUG  CommonBackend: language=en_US
03-09 20:43 DEBUG  CommonBackend: encoding=cp1256
03-09 20:43 DEBUG  WindowsBackend: arch=amd64
03-09 20:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\data\isolist.ini
03-09 20:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 20:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 20:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 20:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 20:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 20:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 20:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 20:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 20:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 20:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 20:43 DEBUG  WindowsBackend: Fetching host info...
03-09 20:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 20:43 DEBUG  WindowsBackend: windows version=vista
03-09 20:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 20:43 DEBUG  WindowsBackend: windows_sp=None
03-09 20:43 DEBUG  WindowsBackend: windows_build=7600
03-09 20:43 DEBUG  WindowsBackend: gmt=4
03-09 20:43 DEBUG  WindowsBackend: country=US
03-09 20:43 DEBUG  WindowsBackend: timezone=America/New_York
03-09 20:43 DEBUG  WindowsBackend: windows_username=Administrator
03-09 20:43 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 20:43 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 20:43 DEBUG  WindowsBackend: windows_language_code=1033
03-09 20:43 DEBUG  WindowsBackend: windows_language=English
03-09 20:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 20:43 DEBUG  WindowsBackend: bootloader=vista
03-09 20:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211762.296875 mb free ntfs)
03-09 20:43 DEBUG  WindowsBackend: drive=Drive(C: hd 211762.296875 mb free ntfs)
03-09 20:43 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 20:43 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 20:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 20:43 DEBUG  WindowsBackend: drive=Drive(G: hd 66090.3242188 mb free ntfs)
03-09 20:43 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 20:43 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 20:43 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 20:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 20:43 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 20:43 DEBUG  WindowsBackend: keyboard_layout=us
03-09 20:43 DEBUG  WindowsBackend: keyboard_variant=
03-09 20:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 20:43 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 20:43 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 20:43 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 20:43 DEBUG  CommonBackend: Searching for local CDs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Ubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Kubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 20:43 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 20:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 20:43 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 20:43 INFO   root: Running the uninstaller...
03-09 20:43 INFO   CommonBackend: This is the uninstaller running
03-09 20:43 DEBUG  WindowsFrontend: __init__...
03-09 20:43 DEBUG  WindowsFrontend: on_init...
03-09 20:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5427.tmp\translations, languages=['en_US', 'en']
03-09 20:43 INFO   WindowsFrontend: Operation cancelled
03-09 20:43 DEBUG  WindowsFrontend: frontend.quit
03-09 20:43 DEBUG  WindowsFrontend: frontend.on_quit
03-09 20:43 DEBUG  root: application.on_quit
03-09 20:43 INFO   root: sys.exit
03-09 20:52 INFO   root: === wubi 10.10 rev197 ===
03-09 20:52 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 20:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 20:52 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\data
03-09 20:52 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\bin\7z.exe
03-09 20:52 DEBUG  CommonBackend: Fetching basic info...
03-09 20:52 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 20:52 DEBUG  CommonBackend: platform=win32
03-09 20:52 DEBUG  CommonBackend: osname=nt
03-09 20:52 DEBUG  CommonBackend: language=en_US
03-09 20:52 DEBUG  CommonBackend: encoding=cp1256
03-09 20:52 DEBUG  WindowsBackend: arch=amd64
03-09 20:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\data\isolist.ini
03-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 20:52 DEBUG  WindowsBackend: Fetching host info...
03-09 20:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 20:52 DEBUG  WindowsBackend: windows version=vista
03-09 20:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 20:52 DEBUG  WindowsBackend: windows_sp=None
03-09 20:52 DEBUG  WindowsBackend: windows_build=7600
03-09 20:52 DEBUG  WindowsBackend: gmt=4
03-09 20:52 DEBUG  WindowsBackend: country=US
03-09 20:52 DEBUG  WindowsBackend: timezone=America/New_York
03-09 20:52 DEBUG  WindowsBackend: windows_username=Administrator
03-09 20:52 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 20:52 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 20:52 DEBUG  WindowsBackend: windows_language_code=1033
03-09 20:52 DEBUG  WindowsBackend: windows_language=English
03-09 20:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 20:52 DEBUG  WindowsBackend: bootloader=vista
03-09 20:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211751.386719 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(C: hd 211751.382813 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(G: hd 66090.3242188 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 20:52 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 20:52 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 20:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 20:52 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 20:52 DEBUG  WindowsBackend: keyboard_layout=us
03-09 20:52 DEBUG  WindowsBackend: keyboard_variant=
03-09 20:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 20:52 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 20:52 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 20:52 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 20:52 DEBUG  CommonBackend: Searching for local CDs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 20:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 20:52 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 20:52 INFO   root: Running the CD menu...
03-09 20:52 DEBUG  WindowsFrontend: __init__...
03-09 20:52 DEBUG  WindowsFrontend: on_init...
03-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\translations, languages=['en_US', 'en']
03-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl92FB.tmp\translations, languages=['en_US', 'en']
03-09 20:52 DEBUG  root: application.quit
03-09 20:52 DEBUG  WindowsFrontend: frontend.quit
03-09 20:52 DEBUG  WindowsFrontend: frontend.on_quit
03-09 20:52 DEBUG  root: application.on_quit
03-09 20:52 INFO   root: sys.exit
03-09 20:52 INFO   root: === wubi 10.10 rev197 ===
03-09 20:52 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 20:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 20:52 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\data
03-09 20:52 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\bin\7z.exe
03-09 20:52 DEBUG  CommonBackend: Fetching basic info...
03-09 20:52 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 20:52 DEBUG  CommonBackend: platform=win32
03-09 20:52 DEBUG  CommonBackend: osname=nt
03-09 20:52 DEBUG  CommonBackend: language=en_US
03-09 20:52 DEBUG  CommonBackend: encoding=cp1256
03-09 20:52 DEBUG  WindowsBackend: arch=amd64
03-09 20:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\data\isolist.ini
03-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 20:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 20:52 DEBUG  WindowsBackend: Fetching host info...
03-09 20:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 20:52 DEBUG  WindowsBackend: windows version=vista
03-09 20:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 20:52 DEBUG  WindowsBackend: windows_sp=None
03-09 20:52 DEBUG  WindowsBackend: windows_build=7600
03-09 20:52 DEBUG  WindowsBackend: gmt=4
03-09 20:52 DEBUG  WindowsBackend: country=US
03-09 20:52 DEBUG  WindowsBackend: timezone=America/New_York
03-09 20:52 DEBUG  WindowsBackend: windows_username=Administrator
03-09 20:52 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 20:52 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 20:52 DEBUG  WindowsBackend: windows_language_code=1033
03-09 20:52 DEBUG  WindowsBackend: windows_language=English
03-09 20:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 20:52 DEBUG  WindowsBackend: bootloader=vista
03-09 20:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211750.417969 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(C: hd 211750.417969 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(G: hd 66090.3242188 mb free ntfs)
03-09 20:52 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 20:52 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 20:52 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 20:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 20:52 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 20:52 DEBUG  WindowsBackend: keyboard_layout=us
03-09 20:52 DEBUG  WindowsBackend: keyboard_variant=
03-09 20:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 20:52 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 20:52 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 20:52 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 20:52 DEBUG  CommonBackend: Searching for local CDs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 20:52 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 20:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 20:52 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 20:52 INFO   root: Running the CD menu...
03-09 20:52 DEBUG  WindowsFrontend: __init__...
03-09 20:52 DEBUG  WindowsFrontend: on_init...
03-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\translations, languages=['en_US', 'en']
03-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD854.tmp\translations, languages=['en_US', 'en']
03-09 20:53 DEBUG  root: application.quit
03-09 20:53 DEBUG  WindowsFrontend: frontend.quit
03-09 20:53 DEBUG  WindowsFrontend: frontend.on_quit
03-09 20:53 DEBUG  root: application.on_quit
03-09 20:53 INFO   root: sys.exit
03-09 20:55 INFO   root: === wubi 10.10 rev197 ===
03-09 20:55 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 20:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 20:55 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\data
03-09 20:55 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\bin\7z.exe
03-09 20:55 DEBUG  CommonBackend: Fetching basic info...
03-09 20:55 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 20:55 DEBUG  CommonBackend: platform=win32
03-09 20:55 DEBUG  CommonBackend: osname=nt
03-09 20:55 DEBUG  CommonBackend: language=en_US
03-09 20:55 DEBUG  CommonBackend: encoding=cp1256
03-09 20:55 DEBUG  WindowsBackend: arch=amd64
03-09 20:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\data\isolist.ini
03-09 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 20:55 DEBUG  WindowsBackend: Fetching host info...
03-09 20:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 20:55 DEBUG  WindowsBackend: windows version=vista
03-09 20:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 20:55 DEBUG  WindowsBackend: windows_sp=None
03-09 20:55 DEBUG  WindowsBackend: windows_build=7600
03-09 20:55 DEBUG  WindowsBackend: gmt=4
03-09 20:55 DEBUG  WindowsBackend: country=US
03-09 20:55 DEBUG  WindowsBackend: timezone=America/New_York
03-09 20:55 DEBUG  WindowsBackend: windows_username=Administrator
03-09 20:55 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 20:55 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 20:55 DEBUG  WindowsBackend: windows_language_code=1033
03-09 20:55 DEBUG  WindowsBackend: windows_language=English
03-09 20:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 20:55 DEBUG  WindowsBackend: bootloader=vista
03-09 20:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211741.820313 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(C: hd 211741.820313 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(G: hd 66090.3242188 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 20:55 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 20:55 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 20:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 20:55 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 20:55 DEBUG  WindowsBackend: keyboard_layout=us
03-09 20:55 DEBUG  WindowsBackend: keyboard_variant=
03-09 20:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 20:55 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 20:55 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 20:55 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 20:55 DEBUG  CommonBackend: Searching for local CDs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 20:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 20:55 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 20:55 INFO   root: Running the CD menu...
03-09 20:55 DEBUG  WindowsFrontend: __init__...
03-09 20:55 DEBUG  WindowsFrontend: on_init...
03-09 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\translations, languages=['en_US', 'en']
03-09 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylE7EE.tmp\translations, languages=['en_US', 'en']
03-09 20:55 INFO   WindowsFrontend: Operation cancelled
03-09 20:55 DEBUG  WindowsFrontend: frontend.quit
03-09 20:55 DEBUG  WindowsFrontend: frontend.on_quit
03-09 20:55 DEBUG  root: application.on_quit
03-09 20:55 INFO   root: sys.exit
03-09 20:55 INFO   root: === wubi 10.10 rev197 ===
03-09 20:55 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 20:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 20:55 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\data
03-09 20:55 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\bin\7z.exe
03-09 20:55 DEBUG  CommonBackend: Fetching basic info...
03-09 20:55 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 20:55 DEBUG  CommonBackend: platform=win32
03-09 20:55 DEBUG  CommonBackend: osname=nt
03-09 20:55 DEBUG  CommonBackend: language=en_US
03-09 20:55 DEBUG  CommonBackend: encoding=cp1256
03-09 20:55 DEBUG  WindowsBackend: arch=amd64
03-09 20:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\data\isolist.ini
03-09 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 20:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 20:55 DEBUG  WindowsBackend: Fetching host info...
03-09 20:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 20:55 DEBUG  WindowsBackend: windows version=vista
03-09 20:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 20:55 DEBUG  WindowsBackend: windows_sp=None
03-09 20:55 DEBUG  WindowsBackend: windows_build=7600
03-09 20:55 DEBUG  WindowsBackend: gmt=4
03-09 20:55 DEBUG  WindowsBackend: country=US
03-09 20:55 DEBUG  WindowsBackend: timezone=America/New_York
03-09 20:55 DEBUG  WindowsBackend: windows_username=Administrator
03-09 20:55 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 20:55 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 20:55 DEBUG  WindowsBackend: windows_language_code=1033
03-09 20:55 DEBUG  WindowsBackend: windows_language=English
03-09 20:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 20:55 DEBUG  WindowsBackend: bootloader=vista
03-09 20:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211740.324219 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(C: hd 211740.320313 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(G: hd 66090.3242188 mb free ntfs)
03-09 20:55 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 20:55 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 20:55 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 20:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 20:55 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 20:55 DEBUG  WindowsBackend: keyboard_layout=us
03-09 20:55 DEBUG  WindowsBackend: keyboard_variant=
03-09 20:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 20:55 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 20:55 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 20:55 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 20:55 DEBUG  CommonBackend: Searching for local CDs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 20:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 20:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 20:55 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 20:55 INFO   root: Running the CD menu...
03-09 20:55 DEBUG  WindowsFrontend: __init__...
03-09 20:55 DEBUG  WindowsFrontend: on_init...
03-09 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\translations, languages=['en_US', 'en']
03-09 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl5060.tmp\translations, languages=['en_US', 'en']
03-09 20:55 INFO   WindowsFrontend: Operation cancelled
03-09 20:55 DEBUG  WindowsFrontend: frontend.quit
03-09 20:55 DEBUG  WindowsFrontend: frontend.on_quit
03-09 20:55 DEBUG  root: application.on_quit
03-09 20:55 INFO   root: sys.exit
03-09 20:57 INFO   root: === wubi 10.10 rev197 ===
03-09 20:57 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 20:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 20:57 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\data
03-09 20:57 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\bin\7z.exe
03-09 20:57 DEBUG  CommonBackend: Fetching basic info...
03-09 20:57 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 20:57 DEBUG  CommonBackend: platform=win32
03-09 20:57 DEBUG  CommonBackend: osname=nt
03-09 20:57 DEBUG  CommonBackend: language=en_US
03-09 20:57 DEBUG  CommonBackend: encoding=cp1256
03-09 20:57 DEBUG  WindowsBackend: arch=amd64
03-09 20:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\data\isolist.ini
03-09 20:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 20:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 20:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 20:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 20:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 20:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 20:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 20:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 20:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 20:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 20:57 DEBUG  WindowsBackend: Fetching host info...
03-09 20:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 20:57 DEBUG  WindowsBackend: windows version=vista
03-09 20:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 20:57 DEBUG  WindowsBackend: windows_sp=None
03-09 20:57 DEBUG  WindowsBackend: windows_build=7600
03-09 20:57 DEBUG  WindowsBackend: gmt=4
03-09 20:57 DEBUG  WindowsBackend: country=US
03-09 20:57 DEBUG  WindowsBackend: timezone=America/New_York
03-09 20:57 DEBUG  WindowsBackend: windows_username=Administrator
03-09 20:57 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 20:57 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 20:57 DEBUG  WindowsBackend: windows_language_code=1033
03-09 20:57 DEBUG  WindowsBackend: windows_language=English
03-09 20:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 20:57 DEBUG  WindowsBackend: bootloader=vista
03-09 20:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211745.222656 mb free ntfs)
03-09 20:57 DEBUG  WindowsBackend: drive=Drive(C: hd 211745.222656 mb free ntfs)
03-09 20:57 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 20:57 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 20:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 20:57 DEBUG  WindowsBackend: drive=Drive(G: hd 66090.3242188 mb free ntfs)
03-09 20:57 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 20:57 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 20:57 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 20:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 20:57 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 20:57 DEBUG  WindowsBackend: keyboard_layout=us
03-09 20:57 DEBUG  WindowsBackend: keyboard_variant=
03-09 20:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 20:57 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 20:57 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 20:57 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 20:57 DEBUG  CommonBackend: Searching for local CDs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Ubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Kubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 20:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 20:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 20:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 20:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 20:57 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 20:57 INFO   root: Running the CD menu...
03-09 20:57 DEBUG  WindowsFrontend: __init__...
03-09 20:57 DEBUG  WindowsFrontend: on_init...
03-09 20:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\translations, languages=['en_US', 'en']
03-09 20:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylC8BA.tmp\translations, languages=['en_US', 'en']
03-09 20:57 INFO   root: CD menu finished
03-09 20:57 INFO   root: Rebooting
03-09 20:57 DEBUG  TaskList: # Running tasklist...
03-09 20:57 DEBUG  TaskList: ## Running reboot...
03-09 20:57 DEBUG  TaskList: ## Finished reboot
03-09 20:57 DEBUG  TaskList: # Finished tasklist
03-09 20:57 DEBUG  root: application.quit
03-09 20:57 DEBUG  WindowsFrontend: frontend.quit
03-09 20:57 DEBUG  WindowsFrontend: frontend.on_quit
03-09 20:57 DEBUG  root: application.on_quit
03-09 20:57 INFO   root: sys.exit
03-09 21:42 INFO   root: === wubi 10.10 rev197 ===
03-09 21:42 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 21:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-09 21:42 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\data
03-09 21:42 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\bin\7z.exe
03-09 21:42 DEBUG  CommonBackend: Fetching basic info...
03-09 21:42 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 21:42 DEBUG  CommonBackend: platform=win32
03-09 21:42 DEBUG  CommonBackend: osname=nt
03-09 21:42 DEBUG  CommonBackend: language=en_US
03-09 21:42 DEBUG  CommonBackend: encoding=cp1256
03-09 21:42 DEBUG  WindowsBackend: arch=amd64
03-09 21:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\data\isolist.ini
03-09 21:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 21:42 DEBUG  WindowsBackend: Fetching host info...
03-09 21:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 21:42 DEBUG  WindowsBackend: windows version=vista
03-09 21:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 21:42 DEBUG  WindowsBackend: windows_sp=None
03-09 21:42 DEBUG  WindowsBackend: windows_build=7600
03-09 21:42 DEBUG  WindowsBackend: gmt=4
03-09 21:42 DEBUG  WindowsBackend: country=US
03-09 21:42 DEBUG  WindowsBackend: timezone=America/New_York
03-09 21:42 DEBUG  WindowsBackend: windows_username=Administrator
03-09 21:42 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 21:42 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 21:42 DEBUG  WindowsBackend: windows_language_code=1033
03-09 21:42 DEBUG  WindowsBackend: windows_language=English
03-09 21:42 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 21:42 DEBUG  WindowsBackend: bootloader=vista
03-09 21:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211741.105469 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(C: hd 211741.105469 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(G: hd 66090.3242188 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 21:42 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 21:42 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 21:42 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 21:42 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 21:42 DEBUG  WindowsBackend: keyboard_layout=us
03-09 21:42 DEBUG  WindowsBackend: keyboard_variant=
03-09 21:42 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 21:42 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 21:42 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 21:42 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 21:42 DEBUG  CommonBackend: Searching for local CDs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 21:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 21:42 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 21:42 INFO   root: Running the CD menu...
03-09 21:42 DEBUG  WindowsFrontend: __init__...
03-09 21:42 DEBUG  WindowsFrontend: on_init...
03-09 21:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\translations, languages=['en_US', 'en']
03-09 21:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\translations, languages=['en_US', 'en']
03-09 21:42 INFO   root: CD menu finished
03-09 21:42 INFO   root: Already installed, running the uninstaller...
03-09 21:42 INFO   root: Running the uninstaller...
03-09 21:42 INFO   CommonBackend: This is the uninstaller running
03-09 21:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\translations, languages=['en_US', 'en']
03-09 21:42 INFO   root: Received settings
03-09 21:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\translations, languages=['en_US', 'en']
03-09 21:42 DEBUG  TaskList: # Running tasklist...
03-09 21:42 DEBUG  TaskList: ## Running Backup ISO...
03-09 21:42 DEBUG  TaskList: ## Finished Backup ISO
03-09 21:42 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 21:42 DEBUG  WindowsBackend: Could not find bcd id
03-09 21:42 DEBUG  WindowsBackend: undo_bootini C:
03-09 21:42 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 211741.105469 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: undo_bootini D:
03-09 21:42 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: undo_bootini E:
03-09 21:42 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 21:42 DEBUG  WindowsBackend: undo_bootini G:
03-09 21:42 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 66090.3242188 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: undo_bootini H:
03-09 21:42 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 2988.33203125 mb free fat32)
03-09 21:42 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 21:42 DEBUG  TaskList: ## Running Remove target dir...
03-09 21:42 DEBUG  CommonBackend: Deleting G:\ubuntu
03-09 21:42 DEBUG  TaskList: ## Finished Remove target dir
03-09 21:42 DEBUG  TaskList: ## Running Remove registry key...
03-09 21:42 DEBUG  TaskList: ## Finished Remove registry key
03-09 21:42 DEBUG  TaskList: # Finished tasklist
03-09 21:42 INFO   root: Almost finished uninstalling
03-09 21:42 INFO   root: Finished uninstallation
03-09 21:42 DEBUG  CommonBackend: Fetching basic info...
03-09 21:42 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-09 21:42 DEBUG  CommonBackend: platform=win32
03-09 21:42 DEBUG  CommonBackend: osname=nt
03-09 21:42 DEBUG  WindowsBackend: arch=amd64
03-09 21:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\data\isolist.ini
03-09 21:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 21:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 21:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 21:42 DEBUG  WindowsBackend: Fetching host info...
03-09 21:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 21:42 DEBUG  WindowsBackend: windows version=vista
03-09 21:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 21:42 DEBUG  WindowsBackend: windows_sp=None
03-09 21:42 DEBUG  WindowsBackend: windows_build=7600
03-09 21:42 DEBUG  WindowsBackend: gmt=4
03-09 21:42 DEBUG  WindowsBackend: country=US
03-09 21:42 DEBUG  WindowsBackend: timezone=America/New_York
03-09 21:42 DEBUG  WindowsBackend: windows_username=Administrator
03-09 21:42 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 21:42 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 21:42 DEBUG  WindowsBackend: windows_language_code=1033
03-09 21:42 DEBUG  WindowsBackend: windows_language=English
03-09 21:42 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 21:42 DEBUG  WindowsBackend: bootloader=vista
03-09 21:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211741.078125 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(C: hd 211741.078125 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 21:42 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 21:42 DEBUG  WindowsBackend: uninstaller_path=None
03-09 21:42 DEBUG  WindowsBackend: previous_target_dir=None
03-09 21:42 DEBUG  WindowsBackend: previous_distro_name=None
03-09 21:42 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 21:42 DEBUG  WindowsBackend: keyboard_layout=us
03-09 21:42 DEBUG  WindowsBackend: keyboard_variant=
03-09 21:42 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 21:42 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 21:42 DEBUG  CommonBackend: Searching for local CDs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 21:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 21:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 21:42 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 21:42 INFO   root: Running the installer...
03-09 21:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\translations, languages=['en_US', 'en']
03-09 21:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\translations, languages=['en_US', 'en']
03-09 21:43 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-09 21:43 INFO   root: Received settings
03-09 21:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\translations, languages=['en_US', 'en']
03-09 21:43 DEBUG  TaskList: # Running tasklist...
03-09 21:43 DEBUG  TaskList: ## Running select_target_dir...
03-09 21:43 INFO   WindowsBackend: Installing into G:\ubuntu
03-09 21:43 DEBUG  TaskList: ## Finished select_target_dir
03-09 21:43 DEBUG  TaskList: ## Running create_dir_structure...
03-09 21:43 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-09 21:43 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-09 21:43 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-09 21:43 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-09 21:43 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-09 21:43 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-09 21:43 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-09 21:43 DEBUG  TaskList: ## Finished create_dir_structure
03-09 21:43 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 21:43 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 21:43 DEBUG  TaskList: ## Running create_uninstaller...
03-09 21:43 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 21:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 21:43 DEBUG  TaskList: ## Finished create_uninstaller
03-09 21:43 DEBUG  TaskList: ## Running copy_installation_files...
03-09 21:43 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-09 21:43 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\winboot -> G:\ubuntu\winboot
03-09 21:43 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl8075.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-09 21:43 DEBUG  TaskList: ## Finished copy_installation_files
03-09 21:43 DEBUG  TaskList: ## Running get_iso...
03-09 21:43 DEBUG  TaskList: New task copy_file
03-09 21:43 DEBUG  TaskList: ### Running copy_file...
03-09 21:51 DEBUG  TaskList: ### Finished copy_file
03-09 21:51 DEBUG  TaskList: New task check_iso
03-09 21:51 DEBUG  TaskList: ### Running check_iso...
03-09 21:51 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
03-09 21:51 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
03-09 21:51 DEBUG  Distro:     wrong size: 3868623360 > 900000000
03-09 21:51 DEBUG  TaskList: ### Finished check_iso
03-09 21:51 DEBUG  CommonBackend: Searching for local ISO
03-09 21:51 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 21:51 DEBUG  TaskList: New task get_metalink
03-09 21:51 DEBUG  TaskList: ### Running get_metalink...
03-09 21:51 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > G:\ubuntu\install
03-09 21:51 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
03-09 21:51 DEBUG  downloader: download finished (read 9135 bytes)
03-09 21:51 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > G:\ubuntu\install
03-09 21:51 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-09 21:51 DEBUG  downloader: download finished (read 488 bytes)
03-09 21:51 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > G:\ubuntu\install
03-09 21:51 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-09 21:51 DEBUG  downloader: download finished (read 198 bytes)
03-09 21:51 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 21:51 INFO   saplog: Checking block bindings..
03-09 21:51 INFO   saplog: Key verified successfully.
03-09 21:51 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-09 21:51 DEBUG  TaskList: ### Finished get_metalink
03-09 21:51 DEBUG  TaskList: New task download
03-09 21:51 DEBUG  TaskList: ### Running download...
03-09 21:51 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > G:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-09 22:07 INFO   WindowsFrontend: Operation cancelled
03-09 22:07 DEBUG  WindowsFrontend: frontend.quit
03-09 22:07 DEBUG  WindowsFrontend: frontend.on_quit
03-09 22:07 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-09 22:07 DEBUG  TaskList: # Cancelling tasklist
03-09 22:07 DEBUG  TaskList: ### Finished download
03-09 22:07 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-09 22:07 DEBUG  root: application.on_quit
03-09 22:07 DEBUG  root: Forceful exit
03-09 22:07 INFO   root: sys.exit
03-09 22:14 INFO   root: === wubi 10.10 rev197 ===
03-09 22:14 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 22:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator.KHALILULLAH\\Downloads\\Programs\\wubi.exe"']
03-09 22:14 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\data
03-09 22:14 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\bin\7z.exe
03-09 22:14 DEBUG  CommonBackend: Fetching basic info...
03-09 22:14 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe
03-09 22:14 DEBUG  CommonBackend: platform=win32
03-09 22:14 DEBUG  CommonBackend: osname=nt
03-09 22:14 DEBUG  CommonBackend: language=en_US
03-09 22:14 DEBUG  CommonBackend: encoding=cp1256
03-09 22:14 DEBUG  WindowsBackend: arch=amd64
03-09 22:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\data\isolist.ini
03-09 22:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 22:14 DEBUG  WindowsBackend: Fetching host info...
03-09 22:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 22:14 DEBUG  WindowsBackend: windows version=vista
03-09 22:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 22:14 DEBUG  WindowsBackend: windows_sp=None
03-09 22:14 DEBUG  WindowsBackend: windows_build=7600
03-09 22:14 DEBUG  WindowsBackend: gmt=4
03-09 22:14 DEBUG  WindowsBackend: country=US
03-09 22:14 DEBUG  WindowsBackend: timezone=America/New_York
03-09 22:14 DEBUG  WindowsBackend: windows_username=Administrator
03-09 22:14 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 22:14 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 22:14 DEBUG  WindowsBackend: windows_language_code=1033
03-09 22:14 DEBUG  WindowsBackend: windows_language=English
03-09 22:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 22:14 DEBUG  WindowsBackend: bootloader=vista
03-09 22:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211744.710938 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(C: hd 211744.710938 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(G: hd 66178.3242188 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 22:14 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 22:14 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 22:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 22:14 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 22:14 DEBUG  WindowsBackend: keyboard_layout=us
03-09 22:14 DEBUG  WindowsBackend: keyboard_variant=
03-09 22:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 22:14 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 22:14 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 22:14 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 22:14 DEBUG  CommonBackend: Searching for local CDs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 22:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 22:14 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 22:14 INFO   root: Running the CD menu...
03-09 22:14 DEBUG  WindowsFrontend: __init__...
03-09 22:14 DEBUG  WindowsFrontend: on_init...
03-09 22:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\translations, languages=['en_US', 'en']
03-09 22:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\translations, languages=['en_US', 'en']
03-09 22:14 INFO   root: CD menu finished
03-09 22:14 INFO   root: Already installed, running the uninstaller...
03-09 22:14 INFO   root: Running the uninstaller...
03-09 22:14 INFO   CommonBackend: This is the uninstaller running
03-09 22:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\translations, languages=['en_US', 'en']
03-09 22:14 INFO   root: Received settings
03-09 22:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\translations, languages=['en_US', 'en']
03-09 22:14 DEBUG  TaskList: # Running tasklist...
03-09 22:14 DEBUG  TaskList: ## Running Backup ISO...
03-09 22:14 DEBUG  TaskList: ## Finished Backup ISO
03-09 22:14 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 22:14 DEBUG  WindowsBackend: Could not find bcd id
03-09 22:14 DEBUG  WindowsBackend: undo_bootini C:
03-09 22:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 211744.710938 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: undo_bootini D:
03-09 22:14 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: undo_bootini E:
03-09 22:14 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 22:14 DEBUG  WindowsBackend: undo_bootini G:
03-09 22:14 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 66178.3242188 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: undo_bootini H:
03-09 22:14 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 2988.33203125 mb free fat32)
03-09 22:14 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 22:14 DEBUG  TaskList: ## Running Remove target dir...
03-09 22:14 DEBUG  CommonBackend: Deleting G:\ubuntu
03-09 22:14 DEBUG  TaskList: ## Finished Remove target dir
03-09 22:14 DEBUG  TaskList: ## Running Remove registry key...
03-09 22:14 DEBUG  TaskList: ## Finished Remove registry key
03-09 22:14 DEBUG  TaskList: # Finished tasklist
03-09 22:14 INFO   root: Almost finished uninstalling
03-09 22:14 INFO   root: Finished uninstallation
03-09 22:14 DEBUG  CommonBackend: Fetching basic info...
03-09 22:14 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe
03-09 22:14 DEBUG  CommonBackend: platform=win32
03-09 22:14 DEBUG  CommonBackend: osname=nt
03-09 22:14 DEBUG  WindowsBackend: arch=amd64
03-09 22:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\data\isolist.ini
03-09 22:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 22:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 22:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 22:14 DEBUG  WindowsBackend: Fetching host info...
03-09 22:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 22:14 DEBUG  WindowsBackend: windows version=vista
03-09 22:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 22:14 DEBUG  WindowsBackend: windows_sp=None
03-09 22:14 DEBUG  WindowsBackend: windows_build=7600
03-09 22:14 DEBUG  WindowsBackend: gmt=4
03-09 22:14 DEBUG  WindowsBackend: country=US
03-09 22:14 DEBUG  WindowsBackend: timezone=America/New_York
03-09 22:14 DEBUG  WindowsBackend: windows_username=Administrator
03-09 22:14 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 22:14 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 22:14 DEBUG  WindowsBackend: windows_language_code=1033
03-09 22:14 DEBUG  WindowsBackend: windows_language=English
03-09 22:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 22:14 DEBUG  WindowsBackend: bootloader=vista
03-09 22:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211744.476563 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(C: hd 211744.476563 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 22:14 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 22:14 DEBUG  WindowsBackend: uninstaller_path=None
03-09 22:14 DEBUG  WindowsBackend: previous_target_dir=None
03-09 22:14 DEBUG  WindowsBackend: previous_distro_name=None
03-09 22:14 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 22:14 DEBUG  WindowsBackend: keyboard_layout=us
03-09 22:14 DEBUG  WindowsBackend: keyboard_variant=
03-09 22:14 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 22:14 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 22:14 DEBUG  CommonBackend: Searching for local CDs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 22:14 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 22:14 INFO   root: Running the installer...
03-09 22:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\translations, languages=['en_US', 'en']
03-09 22:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\translations, languages=['en_US', 'en']
03-09 22:15 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-09 22:15 INFO   root: Received settings
03-09 22:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\translations, languages=['en_US', 'en']
03-09 22:15 DEBUG  TaskList: # Running tasklist...
03-09 22:15 DEBUG  TaskList: ## Running select_target_dir...
03-09 22:15 INFO   WindowsBackend: Installing into G:\ubuntu
03-09 22:15 DEBUG  TaskList: ## Finished select_target_dir
03-09 22:15 DEBUG  TaskList: ## Running create_dir_structure...
03-09 22:15 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-09 22:15 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-09 22:15 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-09 22:15 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-09 22:15 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-09 22:15 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-09 22:15 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-09 22:15 DEBUG  TaskList: ## Finished create_dir_structure
03-09 22:15 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 22:15 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 22:15 DEBUG  TaskList: ## Running create_uninstaller...
03-09 22:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 22:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 22:15 DEBUG  TaskList: ## Finished create_uninstaller
03-09 22:15 DEBUG  TaskList: ## Running copy_installation_files...
03-09 22:15 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-09 22:15 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\winboot -> G:\ubuntu\winboot
03-09 22:15 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylF344.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-09 22:15 DEBUG  TaskList: ## Finished copy_installation_files
03-09 22:15 DEBUG  TaskList: ## Running get_iso...
03-09 22:15 DEBUG  TaskList: New task copy_file
03-09 22:15 DEBUG  TaskList: ### Running copy_file...
03-09 22:23 DEBUG  TaskList: ### Finished copy_file
03-09 22:23 DEBUG  TaskList: New task check_iso
03-09 22:23 DEBUG  TaskList: ### Running check_iso...
03-09 22:23 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
03-09 22:23 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
03-09 22:23 DEBUG  Distro:     wrong size: 3868623360 > 900000000
03-09 22:23 DEBUG  TaskList: ### Finished check_iso
03-09 22:23 DEBUG  CommonBackend: Searching for local ISO
03-09 22:23 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 22:23 DEBUG  TaskList: New task get_metalink
03-09 22:23 DEBUG  TaskList: ### Running get_metalink...
03-09 22:23 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > G:\ubuntu\install
03-09 22:24 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
03-09 22:24 DEBUG  downloader: download finished (read 9135 bytes)
03-09 22:24 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > G:\ubuntu\install
03-09 22:24 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-09 22:24 DEBUG  downloader: download finished (read 488 bytes)
03-09 22:24 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > G:\ubuntu\install
03-09 22:24 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-09 22:24 DEBUG  downloader: download finished (read 198 bytes)
03-09 22:24 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 22:24 INFO   saplog: Checking block bindings..
03-09 22:24 INFO   saplog: Key verified successfully.
03-09 22:24 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-09 22:24 DEBUG  TaskList: ### Finished get_metalink
03-09 22:24 DEBUG  TaskList: New task download
03-09 22:24 DEBUG  TaskList: ### Running download...
03-09 22:24 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > G:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-09 22:28 INFO   WindowsFrontend: Operation cancelled
03-09 22:28 DEBUG  WindowsFrontend: frontend.quit
03-09 22:28 DEBUG  WindowsFrontend: frontend.on_quit
03-09 22:28 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-09 22:28 DEBUG  TaskList: # Cancelling tasklist
03-09 22:28 DEBUG  TaskList: ### Finished download
03-09 22:28 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-09 22:28 DEBUG  root: application.on_quit
03-09 22:28 DEBUG  root: Forceful exit
03-09 22:28 INFO   root: sys.exit
03-09 22:28 INFO   root: === wubi 10.10 rev197 ===
03-09 22:28 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-09 22:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator.KHALILULLAH\\Downloads\\Programs\\wubi.exe"']
03-09 22:28 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\data
03-09 22:28 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\bin\7z.exe
03-09 22:28 DEBUG  CommonBackend: Fetching basic info...
03-09 22:28 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe
03-09 22:28 DEBUG  CommonBackend: platform=win32
03-09 22:28 DEBUG  CommonBackend: osname=nt
03-09 22:28 DEBUG  CommonBackend: language=en_US
03-09 22:28 DEBUG  CommonBackend: encoding=cp1256
03-09 22:28 DEBUG  WindowsBackend: arch=amd64
03-09 22:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\data\isolist.ini
03-09 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 22:28 DEBUG  WindowsBackend: Fetching host info...
03-09 22:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 22:28 DEBUG  WindowsBackend: windows version=vista
03-09 22:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 22:28 DEBUG  WindowsBackend: windows_sp=None
03-09 22:28 DEBUG  WindowsBackend: windows_build=7600
03-09 22:28 DEBUG  WindowsBackend: gmt=4
03-09 22:28 DEBUG  WindowsBackend: country=US
03-09 22:28 DEBUG  WindowsBackend: timezone=America/New_York
03-09 22:28 DEBUG  WindowsBackend: windows_username=Administrator
03-09 22:28 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 22:28 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 22:28 DEBUG  WindowsBackend: windows_language_code=1033
03-09 22:28 DEBUG  WindowsBackend: windows_language=English
03-09 22:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 22:28 DEBUG  WindowsBackend: bootloader=vista
03-09 22:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211743.3125 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(C: hd 211743.3125 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(G: hd 66199.8242188 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 22:28 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-09 22:28 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-09 22:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 22:28 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 22:28 DEBUG  WindowsBackend: keyboard_layout=us
03-09 22:28 DEBUG  WindowsBackend: keyboard_variant=
03-09 22:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-09 22:28 DEBUG  CommonBackend: locale=en_US.UTF-8
03-09 22:28 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 22:28 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 22:28 DEBUG  CommonBackend: Searching for local CDs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-09 22:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-09 22:28 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 22:28 INFO   root: Running the CD menu...
03-09 22:28 DEBUG  WindowsFrontend: __init__...
03-09 22:28 DEBUG  WindowsFrontend: on_init...
03-09 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\translations, languages=['en_US', 'en']
03-09 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\translations, languages=['en_US', 'en']
03-09 22:28 INFO   root: CD menu finished
03-09 22:28 INFO   root: Already installed, running the uninstaller...
03-09 22:28 INFO   root: Running the uninstaller...
03-09 22:28 INFO   CommonBackend: This is the uninstaller running
03-09 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\translations, languages=['en_US', 'en']
03-09 22:28 INFO   root: Received settings
03-09 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\translations, languages=['en_US', 'en']
03-09 22:28 DEBUG  TaskList: # Running tasklist...
03-09 22:28 DEBUG  TaskList: ## Running Backup ISO...
03-09 22:28 DEBUG  TaskList: ## Finished Backup ISO
03-09 22:28 DEBUG  TaskList: ## Running Remove bootloader entry...
03-09 22:28 DEBUG  WindowsBackend: Could not find bcd id
03-09 22:28 DEBUG  WindowsBackend: undo_bootini C:
03-09 22:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 211743.3125 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: undo_bootini D:
03-09 22:28 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: undo_bootini E:
03-09 22:28 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-09 22:28 DEBUG  WindowsBackend: undo_bootini G:
03-09 22:28 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 66199.8242188 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: undo_bootini H:
03-09 22:28 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 2988.33203125 mb free fat32)
03-09 22:28 DEBUG  TaskList: ## Finished Remove bootloader entry
03-09 22:28 DEBUG  TaskList: ## Running Remove target dir...
03-09 22:28 DEBUG  CommonBackend: Deleting G:\ubuntu
03-09 22:28 DEBUG  TaskList: ## Finished Remove target dir
03-09 22:28 DEBUG  TaskList: ## Running Remove registry key...
03-09 22:28 DEBUG  TaskList: ## Finished Remove registry key
03-09 22:28 DEBUG  TaskList: # Finished tasklist
03-09 22:28 INFO   root: Almost finished uninstalling
03-09 22:28 INFO   root: Finished uninstallation
03-09 22:28 DEBUG  CommonBackend: Fetching basic info...
03-09 22:28 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe
03-09 22:28 DEBUG  CommonBackend: platform=win32
03-09 22:28 DEBUG  CommonBackend: osname=nt
03-09 22:28 DEBUG  WindowsBackend: arch=amd64
03-09 22:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\data\isolist.ini
03-09 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 22:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-09 22:28 DEBUG  WindowsBackend: Fetching host info...
03-09 22:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 22:28 DEBUG  WindowsBackend: windows version=vista
03-09 22:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-09 22:28 DEBUG  WindowsBackend: windows_sp=None
03-09 22:28 DEBUG  WindowsBackend: windows_build=7600
03-09 22:28 DEBUG  WindowsBackend: gmt=4
03-09 22:28 DEBUG  WindowsBackend: country=US
03-09 22:28 DEBUG  WindowsBackend: timezone=America/New_York
03-09 22:28 DEBUG  WindowsBackend: windows_username=Administrator
03-09 22:28 DEBUG  WindowsBackend: user_full_name=Administrator
03-09 22:28 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-09 22:28 DEBUG  WindowsBackend: windows_language_code=1033
03-09 22:28 DEBUG  WindowsBackend: windows_language=English
03-09 22:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-09 22:28 DEBUG  WindowsBackend: bootloader=vista
03-09 22:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211743.773438 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(C: hd 211743.773438 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.8398438 mb free ntfs)
03-09 22:28 DEBUG  WindowsBackend: drive=Drive(H: removable 2988.33203125 mb free fat32)
03-09 22:28 DEBUG  WindowsBackend: uninstaller_path=None
03-09 22:28 DEBUG  WindowsBackend: previous_target_dir=None
03-09 22:28 DEBUG  WindowsBackend: previous_distro_name=None
03-09 22:28 DEBUG  WindowsBackend: keyboard_id=67699721
03-09 22:28 DEBUG  WindowsBackend: keyboard_layout=us
03-09 22:28 DEBUG  WindowsBackend: keyboard_variant=
03-09 22:28 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-09 22:28 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 22:28 DEBUG  CommonBackend: Searching for local CDs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-09 22:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-09 22:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-09 22:28 INFO   Distro: Found a valid CD for Ubuntu: H:\
03-09 22:28 INFO   root: Running the installer...
03-09 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\translations, languages=['en_US', 'en']
03-09 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\translations, languages=['en_US', 'en']
03-09 22:28 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-09 22:28 INFO   root: Received settings
03-09 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\translations, languages=['en_US', 'en']
03-09 22:28 DEBUG  TaskList: # Running tasklist...
03-09 22:28 DEBUG  TaskList: ## Running select_target_dir...
03-09 22:28 INFO   WindowsBackend: Installing into C:\ubuntu
03-09 22:28 DEBUG  TaskList: ## Finished select_target_dir
03-09 22:28 DEBUG  TaskList: ## Running create_dir_structure...
03-09 22:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-09 22:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-09 22:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-09 22:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-09 22:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-09 22:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-09 22:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-09 22:28 DEBUG  TaskList: ## Finished create_dir_structure
03-09 22:28 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 22:28 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 22:28 DEBUG  TaskList: ## Running create_uninstaller...
03-09 22:28 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 22:28 DEBUG  TaskList: ## Finished create_uninstaller
03-09 22:28 DEBUG  TaskList: ## Running copy_installation_files...
03-09 22:28 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-09 22:28 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\winboot -> C:\ubuntu\winboot
03-09 22:28 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylBB54.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-09 22:28 DEBUG  TaskList: ## Finished copy_installation_files
03-09 22:28 DEBUG  TaskList: ## Running get_iso...
03-09 22:28 DEBUG  TaskList: New task copy_file
03-09 22:28 DEBUG  TaskList: ### Running copy_file...
03-09 22:37 DEBUG  TaskList: ### Finished copy_file
03-09 22:37 DEBUG  TaskList: New task check_iso
03-09 22:37 DEBUG  TaskList: ### Running check_iso...
03-09 22:37 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-09 22:37 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-09 22:37 DEBUG  Distro:     wrong size: 3868623360 > 900000000
03-09 22:37 DEBUG  TaskList: ### Finished check_iso
03-09 22:37 DEBUG  CommonBackend: Searching for local ISO
03-09 22:37 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 22:37 DEBUG  TaskList: New task get_metalink
03-09 22:37 DEBUG  TaskList: ### Running get_metalink...
03-09 22:37 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > C:\ubuntu\install
03-09 22:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
03-09 22:37 DEBUG  downloader: download finished (read 9135 bytes)
03-09 22:37 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > C:\ubuntu\install
03-09 22:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-09 22:37 DEBUG  downloader: download finished (read 488 bytes)
03-09 22:37 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
03-09 22:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-09 22:37 DEBUG  downloader: download finished (read 198 bytes)
03-09 22:37 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 22:37 INFO   saplog: Checking block bindings..
03-09 22:37 INFO   saplog: Key verified successfully.
03-09 22:37 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-09 22:37 DEBUG  TaskList: ### Finished get_metalink
03-09 22:37 DEBUG  TaskList: New task download
03-09 22:37 DEBUG  TaskList: ### Running download...
03-09 22:37 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-10 00:22 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


03-10 00:22 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
03-10 00:22 DEBUG  TaskList: ### Finished download
03-10 00:22 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
03-10 00:22 DEBUG  TaskList: # Cancelling tasklist
03-10 00:22 DEBUG  TaskList: # Finished tasklist
03-10 00:22 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'

```

I tried to boot from CD,From USB Stick and from Wubi Windows Installer but got same error everytime.

Anybody got any idea how to ractify this problem.
Waiting diengly for a posotive response.
Thanks in advance.

---

### Post by bcbc on 2011-03-10
Likely G: is a dynamic disc - you can't install Ubuntu onto those because they're only visible to Windows.

---

### Post by CyberHax0rs on 2011-03-10
> **bcbc said:**
> Likely G: is a dynamic disc - you can't install Ubuntu onto those because they're only visible to Windows.
I already tried to install on C Drive and got same issue.
Anyother idea.

---

### Post by bcbc on 2011-03-10
> **CyberHax0rs said:**
> I already tried to install on C Drive and got same issue.
Anyother idea.

Do you have the log file from that attempt? Very often the error you see does not describe the actual cause of the problem. So it's a good idea to post the log file if it's not clear what the problem is.

---

### Post by CyberHax0rs on 2011-03-11
> **bcbc said:**
> Do you have the log file from that attempt? Very often the error you see does not describe the actual cause of the problem. So it's a good idea to post the log file if it's not clear what the problem is.


Thanks for ur reply.
This is the log file u asked for.

```
03-12 00:40 INFO   root: === wubi 10.10 rev197 ===
03-12 00:40 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-12 00:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator.KHALILULLAH\\Downloads\\Programs\\wubi.exe"']
03-12 00:40 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\data
03-12 00:40 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\bin\7z.exe
03-12 00:40 DEBUG  CommonBackend: Fetching basic info...
03-12 00:40 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe
03-12 00:40 DEBUG  CommonBackend: platform=win32
03-12 00:40 DEBUG  CommonBackend: osname=nt
03-12 00:40 DEBUG  CommonBackend: language=en_US
03-12 00:40 DEBUG  CommonBackend: encoding=cp1256
03-12 00:40 DEBUG  WindowsBackend: arch=amd64
03-12 00:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\data\isolist.ini
03-12 00:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-12 00:40 DEBUG  WindowsBackend: Fetching host info...
03-12 00:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-12 00:40 DEBUG  WindowsBackend: windows version=vista
03-12 00:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-12 00:40 DEBUG  WindowsBackend: windows_sp=None
03-12 00:40 DEBUG  WindowsBackend: windows_build=7600
03-12 00:40 DEBUG  WindowsBackend: gmt=4
03-12 00:40 DEBUG  WindowsBackend: country=US
03-12 00:40 DEBUG  WindowsBackend: timezone=America/New_York
03-12 00:40 DEBUG  WindowsBackend: windows_username=Administrator
03-12 00:40 DEBUG  WindowsBackend: user_full_name=Administrator
03-12 00:40 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-12 00:40 DEBUG  WindowsBackend: windows_language_code=1033
03-12 00:40 DEBUG  WindowsBackend: windows_language=English
03-12 00:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-12 00:40 DEBUG  WindowsBackend: bootloader=vista
03-12 00:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210653.867188 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(C: hd 210653.867188 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.84375 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-12 00:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-12 00:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-12 00:40 DEBUG  WindowsBackend: keyboard_id=67699721
03-12 00:40 DEBUG  WindowsBackend: keyboard_layout=us
03-12 00:40 DEBUG  WindowsBackend: keyboard_variant=
03-12 00:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-12 00:40 DEBUG  CommonBackend: locale=en_US.UTF-8
03-12 00:40 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-12 00:40 DEBUG  CommonBackend: Searching ISOs on USB devices
03-12 00:40 DEBUG  CommonBackend: Searching for local CDs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 INFO   root: Already installed, running the uninstaller...
03-12 00:40 INFO   root: Running the uninstaller...
03-12 00:40 INFO   CommonBackend: This is the uninstaller running
03-12 00:40 DEBUG  WindowsFrontend: __init__...
03-12 00:40 DEBUG  WindowsFrontend: on_init...
03-12 00:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\translations, languages=['en_US', 'en']
03-12 00:40 INFO   root: Received settings
03-12 00:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\translations, languages=['en_US', 'en']
03-12 00:40 DEBUG  TaskList: # Running tasklist...
03-12 00:40 DEBUG  TaskList: ## Running Backup ISO...
03-12 00:40 DEBUG  TaskList: ## Finished Backup ISO
03-12 00:40 DEBUG  TaskList: ## Running Remove bootloader entry...
03-12 00:40 DEBUG  WindowsBackend: Could not find bcd id
03-12 00:40 DEBUG  WindowsBackend: undo_bootini C:
03-12 00:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 210653.867188 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: undo_bootini D:
03-12 00:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: undo_bootini E:
03-12 00:40 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-12 00:40 DEBUG  WindowsBackend: undo_bootini G:
03-12 00:40 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 69901.84375 mb free ntfs)
03-12 00:40 DEBUG  TaskList: ## Finished Remove bootloader entry
03-12 00:40 DEBUG  TaskList: ## Running Remove target dir...
03-12 00:40 DEBUG  CommonBackend: Deleting C:\ubuntu
03-12 00:40 DEBUG  TaskList: ## Finished Remove target dir
03-12 00:40 DEBUG  TaskList: ## Running Remove registry key...
03-12 00:40 DEBUG  TaskList: ## Finished Remove registry key
03-12 00:40 DEBUG  TaskList: # Finished tasklist
03-12 00:40 INFO   root: Almost finished uninstalling
03-12 00:40 INFO   root: Finished uninstallation
03-12 00:40 DEBUG  CommonBackend: Fetching basic info...
03-12 00:40 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe
03-12 00:40 DEBUG  CommonBackend: platform=win32
03-12 00:40 DEBUG  CommonBackend: osname=nt
03-12 00:40 DEBUG  WindowsBackend: arch=amd64
03-12 00:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\data\isolist.ini
03-12 00:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-12 00:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-12 00:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-12 00:40 DEBUG  WindowsBackend: Fetching host info...
03-12 00:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-12 00:40 DEBUG  WindowsBackend: windows version=vista
03-12 00:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-12 00:40 DEBUG  WindowsBackend: windows_sp=None
03-12 00:40 DEBUG  WindowsBackend: windows_build=7600
03-12 00:40 DEBUG  WindowsBackend: gmt=4
03-12 00:40 DEBUG  WindowsBackend: country=US
03-12 00:40 DEBUG  WindowsBackend: timezone=America/New_York
03-12 00:40 DEBUG  WindowsBackend: windows_username=Administrator
03-12 00:40 DEBUG  WindowsBackend: user_full_name=Administrator
03-12 00:40 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-12 00:40 DEBUG  WindowsBackend: windows_language_code=1033
03-12 00:40 DEBUG  WindowsBackend: windows_language=English
03-12 00:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-12 00:40 DEBUG  WindowsBackend: bootloader=vista
03-12 00:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210777.902344 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(C: hd 210777.902344 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-12 00:40 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.84375 mb free ntfs)
03-12 00:40 DEBUG  WindowsBackend: uninstaller_path=None
03-12 00:40 DEBUG  WindowsBackend: previous_target_dir=None
03-12 00:40 DEBUG  WindowsBackend: previous_distro_name=None
03-12 00:40 DEBUG  WindowsBackend: keyboard_id=67699721
03-12 00:40 DEBUG  WindowsBackend: keyboard_layout=us
03-12 00:40 DEBUG  WindowsBackend: keyboard_variant=
03-12 00:40 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-12 00:40 DEBUG  CommonBackend: Searching ISOs on USB devices
03-12 00:40 DEBUG  CommonBackend: Searching for local CDs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 INFO   root: Running the installer...
03-12 00:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\translations, languages=['en_US', 'en']
03-12 00:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\translations, languages=['en_US', 'en']
03-12 00:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-12 00:40 INFO   root: Received settings
03-12 00:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\translations, languages=['en_US', 'en']
03-12 00:40 DEBUG  TaskList: # Running tasklist...
03-12 00:40 DEBUG  TaskList: ## Running select_target_dir...
03-12 00:40 INFO   WindowsBackend: Installing into C:\ubuntu
03-12 00:40 DEBUG  TaskList: ## Finished select_target_dir
03-12 00:40 DEBUG  TaskList: ## Running create_dir_structure...
03-12 00:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-12 00:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-12 00:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-12 00:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-12 00:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-12 00:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-12 00:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-12 00:40 DEBUG  TaskList: ## Finished create_dir_structure
03-12 00:40 DEBUG  TaskList: ## Running uncompress_target_dir...
03-12 00:40 DEBUG  TaskList: ## Finished uncompress_target_dir
03-12 00:40 DEBUG  TaskList: ## Running create_uninstaller...
03-12 00:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-12 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-12 00:40 DEBUG  TaskList: ## Finished create_uninstaller
03-12 00:40 DEBUG  TaskList: ## Running copy_installation_files...
03-12 00:40 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-12 00:40 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\winboot -> C:\ubuntu\winboot
03-12 00:40 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-12 00:40 DEBUG  TaskList: ## Finished copy_installation_files
03-12 00:40 DEBUG  TaskList: ## Running get_iso...
03-12 00:40 DEBUG  CommonBackend: Searching for local CD
03-12 00:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pyl2D9B.tmp\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 00:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 00:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 00:40 DEBUG  CommonBackend: Searching for local ISO
03-12 00:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-12 00:40 DEBUG  TaskList: New task get_metalink
03-12 00:40 DEBUG  TaskList: ### Running get_metalink...
03-12 00:40 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > C:\ubuntu\install
03-12 00:41 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
03-12 00:41 DEBUG  downloader: download finished (read 9135 bytes)
03-12 00:41 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > C:\ubuntu\install
03-12 00:41 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-12 00:41 DEBUG  downloader: download finished (read 488 bytes)
03-12 00:41 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
03-12 00:41 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-12 00:41 DEBUG  downloader: download finished (read 198 bytes)
03-12 00:41 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-12 00:41 INFO   saplog: Checking block bindings..
03-12 00:41 INFO   saplog: Key verified successfully.
03-12 00:41 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-12 00:41 DEBUG  TaskList: ### Finished get_metalink
03-12 00:41 DEBUG  TaskList: New task download
03-12 00:41 DEBUG  TaskList: ### Running download...
03-12 00:41 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-12 01:13 INFO   WindowsFrontend: Operation cancelled
03-12 01:13 DEBUG  WindowsFrontend: frontend.quit
03-12 01:13 DEBUG  WindowsFrontend: frontend.on_quit
03-12 01:13 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-12 01:13 DEBUG  TaskList: # Cancelling tasklist
03-12 01:13 DEBUG  TaskList: ### Finished download
03-12 01:13 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-12 01:13 DEBUG  root: application.on_quit
03-12 01:13 DEBUG  root: Forceful exit
03-12 01:13 INFO   root: sys.exit
03-12 03:00 INFO   root: === wubi 10.10 rev197 ===
03-12 03:00 DEBUG  root: Logfile is c:\users\admini~1.kha\appdata\local\temp\wubi-10.10-rev197.log
03-12 03:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator.KHALILULLAH\\Downloads\\Programs\\wubi_2.exe"']
03-12 03:00 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\data
03-12 03:00 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\bin\7z.exe
03-12 03:00 DEBUG  CommonBackend: Fetching basic info...
03-12 03:00 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi_2.exe
03-12 03:00 DEBUG  CommonBackend: platform=win32
03-12 03:00 DEBUG  CommonBackend: osname=nt
03-12 03:00 DEBUG  CommonBackend: language=en_US
03-12 03:00 DEBUG  CommonBackend: encoding=cp1256
03-12 03:00 DEBUG  WindowsBackend: arch=amd64
03-12 03:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\data\isolist.ini
03-12 03:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-12 03:00 DEBUG  WindowsBackend: Fetching host info...
03-12 03:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-12 03:00 DEBUG  WindowsBackend: windows version=vista
03-12 03:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-12 03:00 DEBUG  WindowsBackend: windows_sp=None
03-12 03:00 DEBUG  WindowsBackend: windows_build=7600
03-12 03:00 DEBUG  WindowsBackend: gmt=4
03-12 03:00 DEBUG  WindowsBackend: country=US
03-12 03:00 DEBUG  WindowsBackend: timezone=America/New_York
03-12 03:00 DEBUG  WindowsBackend: windows_username=Administrator
03-12 03:00 DEBUG  WindowsBackend: user_full_name=Administrator
03-12 03:00 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-12 03:00 DEBUG  WindowsBackend: windows_language_code=1033
03-12 03:00 DEBUG  WindowsBackend: windows_language=English
03-12 03:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-12 03:00 DEBUG  WindowsBackend: bootloader=vista
03-12 03:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210315.746094 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(C: hd 210315.746094 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.84375 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-12 03:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-12 03:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-12 03:00 DEBUG  WindowsBackend: keyboard_id=67699721
03-12 03:00 DEBUG  WindowsBackend: keyboard_layout=us
03-12 03:00 DEBUG  WindowsBackend: keyboard_variant=
03-12 03:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1256')
03-12 03:00 DEBUG  CommonBackend: locale=en_US.UTF-8
03-12 03:00 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-12 03:00 DEBUG  CommonBackend: Searching ISOs on USB devices
03-12 03:00 DEBUG  CommonBackend: Searching for local CDs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 INFO   root: Already installed, running the uninstaller...
03-12 03:00 INFO   root: Running the uninstaller...
03-12 03:00 INFO   CommonBackend: This is the uninstaller running
03-12 03:00 DEBUG  WindowsFrontend: __init__...
03-12 03:00 DEBUG  WindowsFrontend: on_init...
03-12 03:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\translations, languages=['en_US', 'en']
03-12 03:00 INFO   root: Received settings
03-12 03:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\translations, languages=['en_US', 'en']
03-12 03:00 DEBUG  TaskList: # Running tasklist...
03-12 03:00 DEBUG  TaskList: ## Running Backup ISO...
03-12 03:00 DEBUG  TaskList: ## Finished Backup ISO
03-12 03:00 DEBUG  TaskList: ## Running Remove bootloader entry...
03-12 03:00 DEBUG  WindowsBackend: Could not find bcd id
03-12 03:00 DEBUG  WindowsBackend: undo_bootini C:
03-12 03:00 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 210315.746094 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: undo_bootini D:
03-12 03:00 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2841.45703125 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: undo_bootini E:
03-12 03:00 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.6884765625 mb free fat32)
03-12 03:00 DEBUG  WindowsBackend: undo_bootini G:
03-12 03:00 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 69901.84375 mb free ntfs)
03-12 03:00 DEBUG  TaskList: ## Finished Remove bootloader entry
03-12 03:00 DEBUG  TaskList: ## Running Remove target dir...
03-12 03:00 DEBUG  CommonBackend: Deleting C:\ubuntu
03-12 03:00 DEBUG  TaskList: ## Finished Remove target dir
03-12 03:00 DEBUG  TaskList: ## Running Remove registry key...
03-12 03:00 DEBUG  TaskList: ## Finished Remove registry key
03-12 03:00 DEBUG  TaskList: # Finished tasklist
03-12 03:00 INFO   root: Almost finished uninstalling
03-12 03:00 INFO   root: Finished uninstallation
03-12 03:00 DEBUG  CommonBackend: Fetching basic info...
03-12 03:00 DEBUG  CommonBackend: original_exe=C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi_2.exe
03-12 03:00 DEBUG  CommonBackend: platform=win32
03-12 03:00 DEBUG  CommonBackend: osname=nt
03-12 03:00 DEBUG  WindowsBackend: arch=amd64
03-12 03:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\data\isolist.ini
03-12 03:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-12 03:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-12 03:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-12 03:00 DEBUG  WindowsBackend: Fetching host info...
03-12 03:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-12 03:00 DEBUG  WindowsBackend: windows version=vista
03-12 03:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-12 03:00 DEBUG  WindowsBackend: windows_sp=None
03-12 03:00 DEBUG  WindowsBackend: windows_build=7600
03-12 03:00 DEBUG  WindowsBackend: gmt=4
03-12 03:00 DEBUG  WindowsBackend: country=US
03-12 03:00 DEBUG  WindowsBackend: timezone=America/New_York
03-12 03:00 DEBUG  WindowsBackend: windows_username=Administrator
03-12 03:00 DEBUG  WindowsBackend: user_full_name=Administrator
03-12 03:00 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator.KHALILULLAH
03-12 03:00 DEBUG  WindowsBackend: windows_language_code=1033
03-12 03:00 DEBUG  WindowsBackend: windows_language=English
03-12 03:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
03-12 03:00 DEBUG  WindowsBackend: bootloader=vista
03-12 03:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210405.328125 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(C: hd 210405.328125 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(D: hd 2841.45703125 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(E: hd 92.6884765625 mb free fat32)
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-12 03:00 DEBUG  WindowsBackend: drive=Drive(G: hd 69901.84375 mb free ntfs)
03-12 03:00 DEBUG  WindowsBackend: uninstaller_path=None
03-12 03:00 DEBUG  WindowsBackend: previous_target_dir=None
03-12 03:00 DEBUG  WindowsBackend: previous_distro_name=None
03-12 03:00 DEBUG  WindowsBackend: keyboard_id=67699721
03-12 03:00 DEBUG  WindowsBackend: keyboard_layout=us
03-12 03:00 DEBUG  WindowsBackend: keyboard_variant=
03-12 03:00 DEBUG  WindowsBackend: total_memory_mb=3893.859375
03-12 03:00 DEBUG  CommonBackend: Searching ISOs on USB devices
03-12 03:00 DEBUG  CommonBackend: Searching for local CDs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 INFO   root: Running the installer...
03-12 03:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\translations, languages=['en_US', 'en']
03-12 03:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\translations, languages=['en_US', 'en']
03-12 03:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-12 03:00 INFO   root: Received settings
03-12 03:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\translations, languages=['en_US', 'en']
03-12 03:00 DEBUG  TaskList: # Running tasklist...
03-12 03:00 DEBUG  TaskList: ## Running select_target_dir...
03-12 03:00 INFO   WindowsBackend: Installing into C:\ubuntu
03-12 03:00 DEBUG  TaskList: ## Finished select_target_dir
03-12 03:00 DEBUG  TaskList: ## Running create_dir_structure...
03-12 03:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-12 03:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-12 03:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-12 03:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-12 03:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-12 03:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-12 03:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-12 03:00 DEBUG  TaskList: ## Finished create_dir_structure
03-12 03:00 DEBUG  TaskList: ## Running uncompress_target_dir...
03-12 03:00 DEBUG  TaskList: ## Finished uncompress_target_dir
03-12 03:00 DEBUG  TaskList: ## Running create_uninstaller...
03-12 03:00 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator.KHALILULLAH\Downloads\Programs\wubi_2.exe -> C:\ubuntu\uninstall-wubi.exe
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-12 03:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-12 03:00 DEBUG  TaskList: ## Finished create_uninstaller
03-12 03:00 DEBUG  TaskList: ## Running copy_installation_files...
03-12 03:00 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-12 03:00 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\winboot -> C:\ubuntu\winboot
03-12 03:00 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-12 03:00 DEBUG  TaskList: ## Finished copy_installation_files
03-12 03:00 DEBUG  TaskList: ## Running get_iso...
03-12 03:00 DEBUG  CommonBackend: Searching for local CD
03-12 03:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1.KHA\AppData\Local\Temp\pylD919.tmp\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-12 03:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-12 03:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-12 03:00 DEBUG  CommonBackend: Searching for local ISO
03-12 03:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-12 03:00 DEBUG  TaskList: New task get_metalink
03-12 03:00 DEBUG  TaskList: ### Running get_metalink...
03-12 03:00 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > C:\ubuntu\install
03-12 03:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
03-12 03:00 DEBUG  downloader: download finished (read 9135 bytes)
03-12 03:00 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > C:\ubuntu\install
03-12 03:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-12 03:00 DEBUG  downloader: download finished (read 488 bytes)
03-12 03:00 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
03-12 03:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-12 03:00 DEBUG  downloader: download finished (read 198 bytes)
03-12 03:00 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-12 03:00 INFO   saplog: Checking block bindings..
03-12 03:00 INFO   saplog: Key verified successfully.
03-12 03:00 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-12 03:00 DEBUG  TaskList: ### Finished get_metalink
03-12 03:00 DEBUG  TaskList: New task download
03-12 03:00 DEBUG  TaskList: ### Running download...
03-12 03:00 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-12 04:01 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


03-12 04:01 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
03-12 04:01 DEBUG  TaskList: ### Finished download
03-12 04:01 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
03-12 04:01 DEBUG  TaskList: # Cancelling tasklist
03-12 04:01 DEBUG  TaskList: # Finished tasklist
03-12 04:01 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'

```

Please let me know wat's wrong.
Thanks in advance.

---

### Post by bcbc on 2011-03-11
> 03-12 03:00 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-12 04:01 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Wubi tried to download the .iso and failed. Either pyrun.exe is blocked by your firewall, or something else is blocking the bittorrent download.

In your earlier attempts you had a valid CD with 32-bit Ubuntu 10.10. So either pop that back in the drive and try again, or else download and place the desktop cd iso you want in the same folder as wubi.exe and then it will find and use that.

---

### Post by CyberHax0rs on 2011-03-13
> **bcbc said:**
> Wubi tried to download the .iso and failed. Either pyrun.exe is blocked by your firewall, or something else is blocking the bittorrent download.

In your earlier attempts you had a valid CD with 32-bit Ubuntu 10.10. So either pop that back in the drive and try again, or else download and place the desktop cd iso you want in the same folder as wubi.exe and then it will find and use that.


Hey i just disabled my firewall and i was able to install Ubunutu.Thanks a lot for ur assistance :)

---

