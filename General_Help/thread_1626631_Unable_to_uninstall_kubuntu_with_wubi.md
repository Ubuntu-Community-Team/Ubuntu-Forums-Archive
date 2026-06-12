---
title: "Unable to uninstall kubuntu with wubi"
date: 2010-11-20
forum: General Help
---

### Post by maddmoh on 2010-11-20
I got this error: [http://i.imgur.com/UcDZX.png](http://i.imgur.com/UcDZX.png)

This is the contents of the log file it points too:

```
11-15 22:06 INFO   root: === wubi 10.04.1 rev190 ===
11-15 22:06 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-15 22:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mike\\Documents\\setups\\wubi.exe"']
11-15 22:06 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\data
11-15 22:06 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\bin\7z.exe
11-15 22:06 DEBUG  CommonBackend: Fetching basic info...
11-15 22:06 DEBUG  CommonBackend: original_exe=C:\Users\mike\Documents\setups\wubi.exe
11-15 22:06 DEBUG  CommonBackend: platform=win32
11-15 22:06 DEBUG  CommonBackend: osname=nt
11-15 22:06 DEBUG  CommonBackend: language=en_GB
11-15 22:06 DEBUG  CommonBackend: encoding=cp1252
11-15 22:06 DEBUG  WindowsBackend: arch=amd64
11-15 22:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\data\isolist.ini
11-15 22:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-15 22:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-15 22:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-15 22:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-15 22:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-15 22:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-15 22:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-15 22:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-15 22:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-15 22:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-15 22:06 DEBUG  WindowsBackend: Fetching host info...
11-15 22:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-15 22:06 DEBUG  WindowsBackend: windows version=vista
11-15 22:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-15 22:06 DEBUG  WindowsBackend: windows_sp=None
11-15 22:06 DEBUG  WindowsBackend: windows_build=7600
11-15 22:06 DEBUG  WindowsBackend: gmt=0
11-15 22:06 DEBUG  WindowsBackend: country=GB
11-15 22:06 DEBUG  WindowsBackend: timezone=Europe/London
11-15 22:06 DEBUG  WindowsBackend: windows_username=mike
11-15 22:06 DEBUG  WindowsBackend: user_full_name=mike
11-15 22:06 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-15 22:06 DEBUG  WindowsBackend: windows_language_code=1033
11-15 22:06 DEBUG  WindowsBackend: windows_language=English
11-15 22:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-15 22:06 DEBUG  WindowsBackend: bootloader=vista
11-15 22:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 103634.492188 mb free ntfs)
11-15 22:06 DEBUG  WindowsBackend: drive=Drive(C: hd 103634.492188 mb free ntfs)
11-15 22:06 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-15 22:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-15 22:06 DEBUG  WindowsBackend: drive=Drive(F: removable 3088.125 mb free fat32)
11-15 22:06 DEBUG  WindowsBackend: uninstaller_path=None
11-15 22:06 DEBUG  WindowsBackend: previous_target_dir=None
11-15 22:06 DEBUG  WindowsBackend: previous_distro_name=None
11-15 22:06 DEBUG  WindowsBackend: keyboard_id=-268367863
11-15 22:06 DEBUG  WindowsBackend: keyboard_layout=gb
11-15 22:06 DEBUG  WindowsBackend: keyboard_variant=
11-15 22:06 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-15 22:06 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-15 22:06 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-15 22:06 DEBUG  CommonBackend: Searching ISOs on USB devices
11-15 22:06 DEBUG  CommonBackend: Searching for local CDs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Ubuntu Netbook CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Kubuntu Netbook CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro:   parsing info from str=Kubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-15 22:06 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro: wrong version: 10.10 != 10.04.1
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro: wrong version: 10.10 != 10.04.1
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Kubuntu Netbook
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Xubuntu
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Xubuntu
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Mythbuntu
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-15 22:06 DEBUG  Distro: wrong name: Kubuntu != Mythbuntu
11-15 22:06 INFO   root: Running the installer...
11-15 22:06 DEBUG  WindowsFrontend: __init__...
11-15 22:06 DEBUG  WindowsFrontend: on_init...
11-15 22:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\translations, languages=['en_GB', 'en']
11-15 22:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\translations, languages=['en_GB', 'en']
11-15 22:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Kubuntu, language=en_GB, locale=en_GB.UTF-8, username=mike
11-15 22:06 INFO   root: Received settings
11-15 22:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\translations, languages=['en_GB', 'en']
11-15 22:06 DEBUG  TaskList: # Running tasklist...
11-15 22:06 DEBUG  TaskList: ## Running select_target_dir...
11-15 22:06 INFO   WindowsBackend: Installing into C:\ubuntu
11-15 22:06 DEBUG  TaskList: ## Finished select_target_dir
11-15 22:06 DEBUG  TaskList: ## Running create_dir_structure...
11-15 22:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-15 22:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-15 22:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-15 22:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-15 22:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-15 22:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-15 22:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-15 22:06 DEBUG  TaskList: ## Finished create_dir_structure
11-15 22:06 DEBUG  TaskList: ## Running uncompress_target_dir...
11-15 22:06 DEBUG  TaskList: ## Finished uncompress_target_dir
11-15 22:06 DEBUG  TaskList: ## Running create_uninstaller...
11-15 22:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mike\Documents\setups\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.kubuntu.org
11-15 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-15 22:06 DEBUG  TaskList: ## Finished create_uninstaller
11-15 22:06 DEBUG  TaskList: ## Running copy_installation_files...
11-15 22:06 DEBUG  WindowsBackend: Copying C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-15 22:06 DEBUG  WindowsBackend: Copying C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\winboot -> C:\ubuntu\winboot
11-15 22:06 DEBUG  WindowsBackend: Copying C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
11-15 22:06 DEBUG  TaskList: ## Finished copy_installation_files
11-15 22:06 DEBUG  TaskList: ## Running get_iso...
11-15 22:06 DEBUG  CommonBackend: Searching for local CD
11-15 22:06 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-15 22:06 DEBUG  Distro: wrong version: 10.10 != 10.04.1
11-15 22:06 DEBUG  CommonBackend: Searching for local ISO
11-15 22:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-15 22:06 DEBUG  TaskList: New task get_metalink
11-15 22:06 DEBUG  TaskList: ### Running get_metalink...
11-15 22:06 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/10.04.1/kubuntu-10.04.1-desktop-amd64.metalink > C:\ubuntu\install
11-15 22:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.metalink, url=http://releases.ubuntu.com/kubuntu/10.04.1/kubuntu-10.04.1-desktop-amd64.metalink, basename=kubuntu-10.04.1-desktop-amd64.metalink, length=39193, text=None
11-15 22:06 DEBUG  downloader: download finished (read 39193 bytes)
11-15 22:06 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/10.04.1/MD5SUMS-metalink > C:\ubuntu\install
11-15 22:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/kubuntu/10.04.1/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=366, text=None
11-15 22:06 DEBUG  downloader: download finished (read 366 bytes)
11-15 22:06 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/10.04.1/MD5SUMS-metalink.gpg > C:\ubuntu\install
11-15 22:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/kubuntu/10.04.1/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
11-15 22:06 DEBUG  downloader: download finished (read 189 bytes)
11-15 22:06 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-15 22:06 INFO   saplog: Checking block bindings..
11-15 22:06 INFO   saplog: Key verified successfully.
11-15 22:06 DEBUG  CommonBackend: metalink md5sums:
da8bea1073b3cb08fe133205fdd6aed4  kubuntu-10.04.1-alternate-amd64.metalink
3fa35489918ddf656a4b506ebcb5524c  kubuntu-10.04.1-alternate-i386.metalink
9fd0fb1206863dac6939a762be69d95a  kubuntu-10.04.1-desktop-amd64.metalink
6d21e4a06ec8cf5000c491a6a79d9b25  kubuntu-10.04.1-desktop-i386.metalink
a5819d217a4e300d37b67cfd3c83da3e  kubuntu-10.04.1-netbook-i386.metalink

11-15 22:06 DEBUG  TaskList: ### Finished get_metalink
11-15 22:06 DEBUG  TaskList: New task download
11-15 22:06 DEBUG  TaskList: ### Running download...
11-15 22:06 DEBUG  btdownloader: downloading http://releases.ubuntu.com/kubuntu/10.04.1/kubuntu-10.04.1-desktop-amd64.iso.torrent > C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  TaskList: ### Finished download
11-15 22:28 DEBUG  TaskList: New task check_iso
11-15 22:28 DEBUG  TaskList: ### Running check_iso...
11-15 22:28 DEBUG  CommonBackend: Checking C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  Distro:   checking Kubuntu ISO C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  Distro:   parsing info from str=Kubuntu 10.04.1 LTS "Lucid Lynx" - Release amd64 (20100816.2)
11-15 22:28 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.2', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
11-15 22:28 INFO   Distro: Found a valid iso for Kubuntu: C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  TaskList: New task get_file_md5
11-15 22:28 DEBUG  TaskList: #### Running get_file_md5...
11-15 22:28 DEBUG  TaskList: #### Finished get_file_md5
11-15 22:28 DEBUG  TaskList: ### Finished check_iso
11-15 22:28 DEBUG  TaskList: ## Finished get_iso
11-15 22:28 DEBUG  TaskList: ## Running extract_kernel...
11-15 22:28 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\kubuntu-10.04.1-desktop-amd64.iso
11-15 22:28 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-15 22:28 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
11-15 22:28 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 3c758a2db6d6909eac17cb173fe2fae7 == 3c758a2db6d6909eac17cb173fe2fae7
11-15 22:28 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
11-15 22:28 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 921c5b8e6cbdfd600fe7388ef9a4afb0 == 921c5b8e6cbdfd600fe7388ef9a4afb0
11-15 22:28 DEBUG  TaskList: ## Finished extract_kernel
11-15 22:28 DEBUG  TaskList: ## Running choose_disk_sizes...
11-15 22:28 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
11-15 22:28 DEBUG  TaskList: ## Finished choose_disk_sizes
11-15 22:28 DEBUG  TaskList: ## Running create_preseed...
11-15 22:28 DEBUG  TaskList: ## Finished create_preseed
11-15 22:28 DEBUG  TaskList: ## Running modify_bootloader...
11-15 22:28 DEBUG  TaskList: New task modify_bcd
11-15 22:28 DEBUG  TaskList: ### Running modify_bcd...
11-15 22:28 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 103634.492188 mb free ntfs)
11-15 22:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {75765724-1d6f-11df-a5b0-834ac72df2d6}
11-15 22:28 DEBUG  TaskList: ### Finished modify_bcd
11-15 22:28 DEBUG  TaskList: New task modify_bcd
11-15 22:28 DEBUG  TaskList: ### Running modify_bcd...
11-15 22:28 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 3088.125 mb free fat32)
11-15 22:28 DEBUG  WindowsBackend: BCD has already been modified
11-15 22:28 DEBUG  TaskList: ### Finished modify_bcd
11-15 22:28 DEBUG  TaskList: ## Finished modify_bootloader
11-15 22:28 DEBUG  TaskList: ## Running modify_grub_configuration...
11-15 22:28 DEBUG  TaskList: ## Finished modify_grub_configuration
11-15 22:28 DEBUG  TaskList: ## Running create_virtual_disks...
11-15 22:28 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 19744MB
11-15 22:28 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
11-15 22:28 DEBUG  TaskList: ## Finished create_virtual_disks
11-15 22:28 DEBUG  TaskList: ## Running uncompress_files...
11-15 22:28 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
11-15 22:28 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
11-15 22:28 DEBUG  TaskList: ## Finished uncompress_files
11-15 22:28 DEBUG  TaskList: ## Running eject_cd...
11-15 22:28 DEBUG  TaskList: ## Finished eject_cd
11-15 22:28 DEBUG  TaskList: # Finished tasklist
11-15 22:28 INFO   root: Almost finished installing
11-15 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl9E70.tmp\translations, languages=['en_GB', 'en']
11-15 22:41 INFO   root: Finished installation
11-15 22:41 INFO   root: Rebooting
11-15 22:41 DEBUG  TaskList: # Running tasklist...
11-15 22:41 DEBUG  TaskList: ## Running reboot...
11-15 22:41 DEBUG  TaskList: ## Finished reboot
11-15 22:41 DEBUG  TaskList: # Finished tasklist
11-15 22:41 DEBUG  root: application.quit
11-15 22:41 DEBUG  WindowsFrontend: frontend.quit
11-15 22:41 DEBUG  WindowsFrontend: frontend.on_quit
11-15 22:41 DEBUG  root: application.on_quit
11-15 22:41 INFO   root: sys.exit
11-15 22:48 INFO   root: === wubi 10.04.1 rev190 ===
11-15 22:48 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-15 22:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mike\\Documents\\setups\\wubi.exe"']
11-15 22:48 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\data
11-15 22:48 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\bin\7z.exe
11-15 22:48 DEBUG  CommonBackend: Fetching basic info...
11-15 22:48 DEBUG  CommonBackend: original_exe=C:\Users\mike\Documents\setups\wubi.exe
11-15 22:48 DEBUG  CommonBackend: platform=win32
11-15 22:48 DEBUG  CommonBackend: osname=nt
11-15 22:48 DEBUG  CommonBackend: language=en_GB
11-15 22:48 DEBUG  CommonBackend: encoding=cp1252
11-15 22:48 DEBUG  WindowsBackend: arch=amd64
11-15 22:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\data\isolist.ini
11-15 22:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-15 22:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-15 22:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-15 22:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-15 22:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-15 22:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-15 22:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-15 22:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-15 22:48 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-15 22:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-15 22:48 DEBUG  WindowsBackend: Fetching host info...
11-15 22:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-15 22:48 DEBUG  WindowsBackend: windows version=vista
11-15 22:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-15 22:48 DEBUG  WindowsBackend: windows_sp=None
11-15 22:48 DEBUG  WindowsBackend: windows_build=7600
11-15 22:48 DEBUG  WindowsBackend: gmt=0
11-15 22:48 DEBUG  WindowsBackend: country=GB
11-15 22:48 DEBUG  WindowsBackend: timezone=Europe/London
11-15 22:48 DEBUG  WindowsBackend: windows_username=mike
11-15 22:48 DEBUG  WindowsBackend: user_full_name=mike
11-15 22:48 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-15 22:48 DEBUG  WindowsBackend: windows_language_code=1033
11-15 22:48 DEBUG  WindowsBackend: windows_language=English
11-15 22:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-15 22:48 DEBUG  WindowsBackend: bootloader=vista
11-15 22:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 82936.1757813 mb free ntfs)
11-15 22:48 DEBUG  WindowsBackend: drive=Drive(C: hd 82936.1757813 mb free ntfs)
11-15 22:48 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-15 22:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-15 22:48 DEBUG  WindowsBackend: drive=Drive(F: removable 3088.125 mb free fat32)
11-15 22:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-15 22:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-15 22:48 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-15 22:48 DEBUG  WindowsBackend: keyboard_id=-268367863
11-15 22:48 DEBUG  WindowsBackend: keyboard_layout=gb
11-15 22:48 DEBUG  WindowsBackend: keyboard_variant=
11-15 22:48 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-15 22:48 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-15 22:48 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-15 22:48 DEBUG  CommonBackend: Searching ISOs on USB devices
11-15 22:48 DEBUG  CommonBackend: Searching for local CDs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Ubuntu Netbook CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Kubuntu Netbook CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl314C.tmp is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro:   parsing info from str=Kubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-15 22:48 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro: wrong version: 10.10 != 10.04.1
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-15 22:48 DEBUG  Distro: wrong version: 10.10 != 10.04.1
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Kubuntu Netbook
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Xubuntu
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Xubuntu
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Mythbuntu
11-15 22:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-15 22:48 DEBUG  Distro: wrong name: Kubuntu != Mythbuntu
11-15 22:48 INFO   root: Already installed, running the uninstaller...
11-15 22:48 INFO   root: Running the uninstaller...
11-15 22:48 INFO   CommonBackend: This is the uninstaller running
11-15 22:48 DEBUG  WindowsFrontend: __init__...
11-15 22:48 DEBUG  WindowsFrontend: on_init...
11-15 22:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl314C.tmp\translations, languages=['en_GB', 'en']
11-15 22:48 INFO   WindowsFrontend: Operation cancelled
11-15 22:48 DEBUG  WindowsFrontend: frontend.quit
11-15 22:48 DEBUG  WindowsFrontend: frontend.on_quit
11-15 22:48 DEBUG  root: application.on_quit
11-15 22:48 INFO   root: sys.exit
11-18 20:00 INFO   root: === wubi 10.04.1 rev190 ===
11-18 20:00 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-18 20:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-18 20:00 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\data
11-18 20:00 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\bin\7z.exe
11-18 20:00 DEBUG  CommonBackend: Fetching basic info...
11-18 20:00 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-18 20:00 DEBUG  CommonBackend: platform=win32
11-18 20:00 DEBUG  CommonBackend: osname=nt
11-18 20:00 DEBUG  CommonBackend: language=en_GB
11-18 20:00 DEBUG  CommonBackend: encoding=cp1252
11-18 20:00 DEBUG  WindowsBackend: arch=amd64
11-18 20:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\data\isolist.ini
11-18 20:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-18 20:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-18 20:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-18 20:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-18 20:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-18 20:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-18 20:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-18 20:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-18 20:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-18 20:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-18 20:00 DEBUG  WindowsBackend: Fetching host info...
11-18 20:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-18 20:00 DEBUG  WindowsBackend: windows version=vista
11-18 20:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-18 20:00 DEBUG  WindowsBackend: windows_sp=None
11-18 20:00 DEBUG  WindowsBackend: windows_build=7600
11-18 20:00 DEBUG  WindowsBackend: gmt=0
11-18 20:00 DEBUG  WindowsBackend: country=GB
11-18 20:00 DEBUG  WindowsBackend: timezone=Europe/London
11-18 20:00 DEBUG  WindowsBackend: windows_username=mike
11-18 20:00 DEBUG  WindowsBackend: user_full_name=mike
11-18 20:00 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-18 20:00 DEBUG  WindowsBackend: windows_language_code=1033
11-18 20:00 DEBUG  WindowsBackend: windows_language=English
11-18 20:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-18 20:00 DEBUG  WindowsBackend: bootloader=vista
11-18 20:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71948.0820313 mb free ntfs)
11-18 20:00 DEBUG  WindowsBackend: drive=Drive(C: hd 71948.078125 mb free ntfs)
11-18 20:00 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-18 20:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-18 20:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-18 20:00 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-18 20:00 DEBUG  WindowsBackend: keyboard_id=-268367863
11-18 20:00 DEBUG  WindowsBackend: keyboard_layout=gb
11-18 20:00 DEBUG  WindowsBackend: keyboard_variant=
11-18 20:00 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-18 20:00 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-18 20:00 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-18 20:00 DEBUG  CommonBackend: Searching ISOs on USB devices
11-18 20:00 DEBUG  CommonBackend: Searching for local CDs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Ubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Ubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Ubuntu Netbook CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Kubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Kubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Kubuntu Netbook CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Xubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Xubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Mythbuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl201D.tmp is a valid Mythbuntu CD
11-18 20:00 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:00 INFO   root: Running the uninstaller...
11-18 20:00 INFO   CommonBackend: This is the uninstaller running
11-18 20:00 DEBUG  WindowsFrontend: __init__...
11-18 20:00 DEBUG  WindowsFrontend: on_init...
11-18 20:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl201D.tmp\translations, languages=['en_GB', 'en']
11-18 20:00 INFO   WindowsFrontend: Operation cancelled
11-18 20:00 DEBUG  WindowsFrontend: frontend.quit
11-18 20:00 DEBUG  WindowsFrontend: frontend.on_quit
11-18 20:00 DEBUG  root: application.on_quit
11-18 20:00 INFO   root: sys.exit
11-18 20:04 INFO   root: === wubi 10.04.1 rev190 ===
11-18 20:04 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-18 20:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mike\\Desktop\\wubi.exe"']
11-18 20:04 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\data
11-18 20:04 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\bin\7z.exe
11-18 20:04 DEBUG  CommonBackend: Fetching basic info...
11-18 20:04 DEBUG  CommonBackend: original_exe=C:\Users\mike\Desktop\wubi.exe
11-18 20:04 DEBUG  CommonBackend: platform=win32
11-18 20:04 DEBUG  CommonBackend: osname=nt
11-18 20:04 DEBUG  CommonBackend: language=en_GB
11-18 20:04 DEBUG  CommonBackend: encoding=cp1252
11-18 20:04 DEBUG  WindowsBackend: arch=amd64
11-18 20:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\data\isolist.ini
11-18 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-18 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-18 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-18 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-18 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-18 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-18 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-18 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-18 20:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-18 20:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-18 20:04 DEBUG  WindowsBackend: Fetching host info...
11-18 20:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-18 20:04 DEBUG  WindowsBackend: windows version=vista
11-18 20:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-18 20:04 DEBUG  WindowsBackend: windows_sp=None
11-18 20:04 DEBUG  WindowsBackend: windows_build=7600
11-18 20:04 DEBUG  WindowsBackend: gmt=0
11-18 20:04 DEBUG  WindowsBackend: country=GB
11-18 20:04 DEBUG  WindowsBackend: timezone=Europe/London
11-18 20:04 DEBUG  WindowsBackend: windows_username=mike
11-18 20:04 DEBUG  WindowsBackend: user_full_name=mike
11-18 20:04 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-18 20:04 DEBUG  WindowsBackend: windows_language_code=1033
11-18 20:04 DEBUG  WindowsBackend: windows_language=English
11-18 20:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-18 20:04 DEBUG  WindowsBackend: bootloader=vista
11-18 20:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71938.8007813 mb free ntfs)
11-18 20:04 DEBUG  WindowsBackend: drive=Drive(C: hd 71938.8007813 mb free ntfs)
11-18 20:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-18 20:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-18 20:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-18 20:04 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-18 20:04 DEBUG  WindowsBackend: keyboard_id=-268367863
11-18 20:04 DEBUG  WindowsBackend: keyboard_layout=gb
11-18 20:04 DEBUG  WindowsBackend: keyboard_variant=
11-18 20:04 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-18 20:04 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-18 20:04 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-18 20:04 DEBUG  CommonBackend: Searching ISOs on USB devices
11-18 20:04 DEBUG  CommonBackend: Searching for local CDs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Ubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Ubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Ubuntu Netbook CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Kubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Kubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Kubuntu Netbook CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Xubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Xubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Mythbuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp is a valid Mythbuntu CD
11-18 20:04 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:04 INFO   root: Already installed, running the uninstaller...
11-18 20:04 INFO   root: Running the uninstaller...
11-18 20:04 INFO   CommonBackend: This is the uninstaller running
11-18 20:04 DEBUG  WindowsFrontend: __init__...
11-18 20:04 DEBUG  WindowsFrontend: on_init...
11-18 20:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl69F8.tmp\translations, languages=['en_GB', 'en']
11-18 20:04 INFO   WindowsFrontend: Operation cancelled
11-18 20:04 DEBUG  WindowsFrontend: frontend.quit
11-18 20:04 DEBUG  WindowsFrontend: frontend.on_quit
11-18 20:04 DEBUG  root: application.on_quit
11-18 20:04 INFO   root: sys.exit
11-18 20:16 INFO   root: === wubi 10.04.1 rev190 ===
11-18 20:16 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-18 20:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-18 20:16 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\data
11-18 20:16 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\bin\7z.exe
11-18 20:16 DEBUG  CommonBackend: Fetching basic info...
11-18 20:16 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-18 20:16 DEBUG  CommonBackend: platform=win32
11-18 20:16 DEBUG  CommonBackend: osname=nt
11-18 20:16 DEBUG  CommonBackend: language=en_GB
11-18 20:16 DEBUG  CommonBackend: encoding=cp1252
11-18 20:16 DEBUG  WindowsBackend: arch=amd64
11-18 20:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\data\isolist.ini
11-18 20:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-18 20:16 DEBUG  WindowsBackend: Fetching host info...
11-18 20:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-18 20:16 DEBUG  WindowsBackend: windows version=vista
11-18 20:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-18 20:16 DEBUG  WindowsBackend: windows_sp=None
11-18 20:16 DEBUG  WindowsBackend: windows_build=7600
11-18 20:16 DEBUG  WindowsBackend: gmt=0
11-18 20:16 DEBUG  WindowsBackend: country=GB
11-18 20:16 DEBUG  WindowsBackend: timezone=Europe/London
11-18 20:16 DEBUG  WindowsBackend: windows_username=mike
11-18 20:16 DEBUG  WindowsBackend: user_full_name=mike
11-18 20:16 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-18 20:16 DEBUG  WindowsBackend: windows_language_code=1033
11-18 20:16 DEBUG  WindowsBackend: windows_language=English
11-18 20:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-18 20:16 DEBUG  WindowsBackend: bootloader=vista
11-18 20:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72008.3164063 mb free ntfs)
11-18 20:16 DEBUG  WindowsBackend: drive=Drive(C: hd 72008.3164063 mb free ntfs)
11-18 20:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-18 20:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-18 20:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-18 20:16 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-18 20:16 DEBUG  WindowsBackend: keyboard_id=-268367863
11-18 20:16 DEBUG  WindowsBackend: keyboard_layout=gb
11-18 20:16 DEBUG  WindowsBackend: keyboard_variant=
11-18 20:16 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-18 20:16 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-18 20:16 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-18 20:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-18 20:16 DEBUG  CommonBackend: Searching for local CDs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Ubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Kubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 INFO   root: Running the uninstaller...
11-18 20:16 INFO   CommonBackend: This is the uninstaller running
11-18 20:16 DEBUG  WindowsFrontend: __init__...
11-18 20:16 DEBUG  WindowsFrontend: on_init...
11-18 20:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\translations, languages=['en_GB', 'en']
11-18 20:16 INFO   root: Received settings
11-18 20:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl6C87.tmp\translations, languages=['en_GB', 'en']
11-18 20:16 DEBUG  TaskList: # Running tasklist...
11-18 20:16 DEBUG  TaskList: ## Running Backup ISO...
11-18 20:16 DEBUG  TaskList: ## Finished Backup ISO
11-18 20:16 DEBUG  TaskList: ## Running Remove bootloader entry....
11-18 20:16 DEBUG  WindowsBackend: Removing bcd entry {75765724-1d6f-11df-a5b0-834ac72df2d6}
11-18 20:16 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-18 20:16 DEBUG  TaskList: # Cancelling tasklist
11-18 20:16 DEBUG  TaskList: # Finished tasklist
11-18 20:16 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-18 20:16 INFO   root: === wubi 10.04.1 rev190 ===
11-18 20:16 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-18 20:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-18 20:16 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\data
11-18 20:16 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\bin\7z.exe
11-18 20:16 DEBUG  CommonBackend: Fetching basic info...
11-18 20:16 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-18 20:16 DEBUG  CommonBackend: platform=win32
11-18 20:16 DEBUG  CommonBackend: osname=nt
11-18 20:16 DEBUG  CommonBackend: language=en_GB
11-18 20:16 DEBUG  CommonBackend: encoding=cp1252
11-18 20:16 DEBUG  WindowsBackend: arch=amd64
11-18 20:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\data\isolist.ini
11-18 20:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-18 20:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-18 20:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-18 20:16 DEBUG  WindowsBackend: Fetching host info...
11-18 20:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-18 20:16 DEBUG  WindowsBackend: windows version=vista
11-18 20:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-18 20:16 DEBUG  WindowsBackend: windows_sp=None
11-18 20:16 DEBUG  WindowsBackend: windows_build=7600
11-18 20:16 DEBUG  WindowsBackend: gmt=0
11-18 20:16 DEBUG  WindowsBackend: country=GB
11-18 20:16 DEBUG  WindowsBackend: timezone=Europe/London
11-18 20:16 DEBUG  WindowsBackend: windows_username=mike
11-18 20:16 DEBUG  WindowsBackend: user_full_name=mike
11-18 20:16 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-18 20:16 DEBUG  WindowsBackend: windows_language_code=1033
11-18 20:16 DEBUG  WindowsBackend: windows_language=English
11-18 20:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-18 20:16 DEBUG  WindowsBackend: bootloader=vista
11-18 20:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72008.2148438 mb free ntfs)
11-18 20:16 DEBUG  WindowsBackend: drive=Drive(C: hd 72008.2148438 mb free ntfs)
11-18 20:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-18 20:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-18 20:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-18 20:16 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-18 20:16 DEBUG  WindowsBackend: keyboard_id=-268367863
11-18 20:16 DEBUG  WindowsBackend: keyboard_layout=gb
11-18 20:16 DEBUG  WindowsBackend: keyboard_variant=
11-18 20:16 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-18 20:16 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-18 20:16 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-18 20:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-18 20:16 DEBUG  CommonBackend: Searching for local CDs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Ubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Kubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:16 INFO   root: Running the uninstaller...
11-18 20:16 INFO   CommonBackend: This is the uninstaller running
11-18 20:16 DEBUG  WindowsFrontend: __init__...
11-18 20:16 DEBUG  WindowsFrontend: on_init...
11-18 20:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\translations, languages=['en_GB', 'en']
11-18 20:16 INFO   root: Received settings
11-18 20:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pylAD6D.tmp\translations, languages=['en_GB', 'en']
11-18 20:16 DEBUG  TaskList: # Running tasklist...
11-18 20:16 DEBUG  TaskList: ## Running Backup ISO...
11-18 20:16 DEBUG  TaskList: ## Finished Backup ISO
11-18 20:16 DEBUG  TaskList: ## Running Remove bootloader entry....
11-18 20:16 DEBUG  WindowsBackend: Removing bcd entry {75765724-1d6f-11df-a5b0-834ac72df2d6}
11-18 20:16 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-18 20:16 DEBUG  TaskList: # Cancelling tasklist
11-18 20:16 DEBUG  TaskList: # Finished tasklist
11-18 20:16 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-18 20:17 INFO   root: === wubi 10.04.1 rev190 ===
11-18 20:17 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-18 20:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-18 20:17 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\data
11-18 20:17 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\bin\7z.exe
11-18 20:17 DEBUG  CommonBackend: Fetching basic info...
11-18 20:17 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-18 20:17 DEBUG  CommonBackend: platform=win32
11-18 20:17 DEBUG  CommonBackend: osname=nt
11-18 20:17 DEBUG  CommonBackend: language=en_GB
11-18 20:17 DEBUG  CommonBackend: encoding=cp1252
11-18 20:17 DEBUG  WindowsBackend: arch=amd64
11-18 20:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\data\isolist.ini
11-18 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-18 20:17 DEBUG  WindowsBackend: Fetching host info...
11-18 20:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-18 20:17 DEBUG  WindowsBackend: windows version=vista
11-18 20:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-18 20:17 DEBUG  WindowsBackend: windows_sp=None
11-18 20:17 DEBUG  WindowsBackend: windows_build=7600
11-18 20:17 DEBUG  WindowsBackend: gmt=0
11-18 20:17 DEBUG  WindowsBackend: country=GB
11-18 20:17 DEBUG  WindowsBackend: timezone=Europe/London
11-18 20:17 DEBUG  WindowsBackend: windows_username=mike
11-18 20:17 DEBUG  WindowsBackend: user_full_name=mike
11-18 20:17 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-18 20:17 DEBUG  WindowsBackend: windows_language_code=1033
11-18 20:17 DEBUG  WindowsBackend: windows_language=English
11-18 20:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-18 20:17 DEBUG  WindowsBackend: bootloader=vista
11-18 20:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72005.3710938 mb free ntfs)
11-18 20:17 DEBUG  WindowsBackend: drive=Drive(C: hd 72005.3671875 mb free ntfs)
11-18 20:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-18 20:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-18 20:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-18 20:17 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-18 20:17 DEBUG  WindowsBackend: keyboard_id=-268367863
11-18 20:17 DEBUG  WindowsBackend: keyboard_layout=gb
11-18 20:17 DEBUG  WindowsBackend: keyboard_variant=
11-18 20:17 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-18 20:17 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-18 20:17 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-18 20:17 DEBUG  CommonBackend: Searching ISOs on USB devices
11-18 20:17 DEBUG  CommonBackend: Searching for local CDs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Ubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Kubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 INFO   root: Running the uninstaller...
11-18 20:17 INFO   CommonBackend: This is the uninstaller running
11-18 20:17 DEBUG  WindowsFrontend: __init__...
11-18 20:17 DEBUG  WindowsFrontend: on_init...
11-18 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\translations, languages=['en_GB', 'en']
11-18 20:17 INFO   root: Received settings
11-18 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl65F3.tmp\translations, languages=['en_GB', 'en']
11-18 20:17 DEBUG  TaskList: # Running tasklist...
11-18 20:17 DEBUG  TaskList: ## Running Backup ISO...
11-18 20:17 DEBUG  TaskList: ## Finished Backup ISO
11-18 20:17 DEBUG  TaskList: ## Running Remove bootloader entry....
11-18 20:17 DEBUG  WindowsBackend: Removing bcd entry {75765724-1d6f-11df-a5b0-834ac72df2d6}
11-18 20:17 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-18 20:17 DEBUG  TaskList: # Cancelling tasklist
11-18 20:17 DEBUG  TaskList: # Finished tasklist
11-18 20:17 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-18 20:17 INFO   root: === wubi 10.04.1 rev190 ===
11-18 20:17 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-18 20:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-18 20:17 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\data
11-18 20:17 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\bin\7z.exe
11-18 20:17 DEBUG  CommonBackend: Fetching basic info...
11-18 20:17 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-18 20:17 DEBUG  CommonBackend: platform=win32
11-18 20:17 DEBUG  CommonBackend: osname=nt
11-18 20:17 DEBUG  CommonBackend: language=en_GB
11-18 20:17 DEBUG  CommonBackend: encoding=cp1252
11-18 20:17 DEBUG  WindowsBackend: arch=amd64
11-18 20:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\data\isolist.ini
11-18 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-18 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-18 20:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-18 20:17 DEBUG  WindowsBackend: Fetching host info...
11-18 20:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-18 20:17 DEBUG  WindowsBackend: windows version=vista
11-18 20:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-18 20:17 DEBUG  WindowsBackend: windows_sp=None
11-18 20:17 DEBUG  WindowsBackend: windows_build=7600
11-18 20:17 DEBUG  WindowsBackend: gmt=0
11-18 20:17 DEBUG  WindowsBackend: country=GB
11-18 20:17 DEBUG  WindowsBackend: timezone=Europe/London
11-18 20:17 DEBUG  WindowsBackend: windows_username=mike
11-18 20:17 DEBUG  WindowsBackend: user_full_name=mike
11-18 20:17 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-18 20:17 DEBUG  WindowsBackend: windows_language_code=1033
11-18 20:17 DEBUG  WindowsBackend: windows_language=English
11-18 20:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-18 20:17 DEBUG  WindowsBackend: bootloader=vista
11-18 20:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72003.3398438 mb free ntfs)
11-18 20:17 DEBUG  WindowsBackend: drive=Drive(C: hd 72003.3398438 mb free ntfs)
11-18 20:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-18 20:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-18 20:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-18 20:17 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-18 20:17 DEBUG  WindowsBackend: keyboard_id=-268367863
11-18 20:17 DEBUG  WindowsBackend: keyboard_layout=gb
11-18 20:17 DEBUG  WindowsBackend: keyboard_variant=
11-18 20:17 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-18 20:17 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-18 20:17 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-18 20:17 DEBUG  CommonBackend: Searching ISOs on USB devices
11-18 20:17 DEBUG  CommonBackend: Searching for local CDs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Ubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Kubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-18 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-18 20:17 INFO   root: Running the uninstaller...
11-18 20:17 INFO   CommonBackend: This is the uninstaller running
11-18 20:17 DEBUG  WindowsFrontend: __init__...
11-18 20:17 DEBUG  WindowsFrontend: on_init...
11-18 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\translations, languages=['en_GB', 'en']
11-18 20:17 INFO   root: Received settings
11-18 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl99AF.tmp\translations, languages=['en_GB', 'en']
11-18 20:17 DEBUG  TaskList: # Running tasklist...
11-18 20:17 DEBUG  TaskList: ## Running Backup ISO...
11-18 20:17 DEBUG  TaskList: ## Finished Backup ISO
11-18 20:17 DEBUG  TaskList: ## Running Remove bootloader entry....
11-18 20:17 DEBUG  WindowsBackend: Removing bcd entry {75765724-1d6f-11df-a5b0-834ac72df2d6}
11-18 20:17 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-18 20:17 DEBUG  TaskList: # Cancelling tasklist
11-18 20:17 DEBUG  TaskList: # Finished tasklist
11-18 20:17 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-20 18:46 INFO   root: === wubi 10.04.1 rev190 ===
11-20 18:46 DEBUG  root: Logfile is c:\users\mike\appdata\local\temp\wubi-10.04.1-rev190.log
11-20 18:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-20 18:46 DEBUG  CommonBackend: data_dir=C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\data
11-20 18:46 DEBUG  WindowsBackend: 7z=C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\bin\7z.exe
11-20 18:46 DEBUG  CommonBackend: Fetching basic info...
11-20 18:46 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-20 18:46 DEBUG  CommonBackend: platform=win32
11-20 18:46 DEBUG  CommonBackend: osname=nt
11-20 18:46 DEBUG  CommonBackend: language=en_GB
11-20 18:46 DEBUG  CommonBackend: encoding=cp1252
11-20 18:46 DEBUG  WindowsBackend: arch=amd64
11-20 18:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\data\isolist.ini
11-20 18:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 18:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 18:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 18:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 18:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 18:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 18:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 18:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 18:46 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-20 18:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-20 18:46 DEBUG  WindowsBackend: Fetching host info...
11-20 18:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 18:46 DEBUG  WindowsBackend: windows version=vista
11-20 18:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 18:46 DEBUG  WindowsBackend: windows_sp=None
11-20 18:46 DEBUG  WindowsBackend: windows_build=7600
11-20 18:46 DEBUG  WindowsBackend: gmt=0
11-20 18:46 DEBUG  WindowsBackend: country=GB
11-20 18:46 DEBUG  WindowsBackend: timezone=Europe/London
11-20 18:46 DEBUG  WindowsBackend: windows_username=mike
11-20 18:46 DEBUG  WindowsBackend: user_full_name=mike
11-20 18:46 DEBUG  WindowsBackend: user_directory=C:\Users\mike
11-20 18:46 DEBUG  WindowsBackend: windows_language_code=1033
11-20 18:46 DEBUG  WindowsBackend: windows_language=English
11-20 18:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
11-20 18:46 DEBUG  WindowsBackend: bootloader=vista
11-20 18:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59778.3320313 mb free ntfs)
11-20 18:46 DEBUG  WindowsBackend: drive=Drive(C: hd 59778.3320313 mb free ntfs)
11-20 18:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 18:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-20 18:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-20 18:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-20 18:46 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-20 18:46 DEBUG  WindowsBackend: keyboard_id=-268367863
11-20 18:46 DEBUG  WindowsBackend: keyboard_layout=gb
11-20 18:46 DEBUG  WindowsBackend: keyboard_variant=
11-20 18:46 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
11-20 18:46 DEBUG  CommonBackend: locale=en_GB.UTF-8
11-20 18:46 DEBUG  WindowsBackend: total_memory_mb=4063.1875
11-20 18:46 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 18:46 DEBUG  CommonBackend: Searching for local CDs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Ubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Ubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Ubuntu Netbook CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Kubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Kubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Kubuntu Netbook CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Xubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Xubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Mythbuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether C:\Users\mike\AppData\Local\Temp\pyl7468.tmp is a valid Mythbuntu CD
11-20 18:46 DEBUG  Distro:     does not contain C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 18:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 18:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 18:46 INFO   root: Running the uninstaller...
11-20 18:46 INFO   CommonBackend: This is the uninstaller running
11-20 18:46 DEBUG  WindowsFrontend: __init__...
11-20 18:46 DEBUG  WindowsFrontend: on_init...
11-20 18:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\translations, languages=['en_GB', 'en']
11-20 18:46 INFO   root: Received settings
11-20 18:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mike\AppData\Local\Temp\pyl7468.tmp\translations, languages=['en_GB', 'en']
11-20 18:46 DEBUG  TaskList: # Running tasklist...
11-20 18:46 DEBUG  TaskList: ## Running Backup ISO...
11-20 18:46 DEBUG  TaskList: ## Finished Backup ISO
11-20 18:46 DEBUG  TaskList: ## Running Remove bootloader entry....
11-20 18:46 DEBUG  WindowsBackend: Removing bcd entry {75765724-1d6f-11df-a5b0-834ac72df2d6}
11-20 18:46 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
11-20 18:46 DEBUG  TaskList: # Cancelling tasklist
11-20 18:46 DEBUG  TaskList: # Finished tasklist
11-20 18:46 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {75765724-1d6f-11df-a5b0-834ac72df2d6} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
```

---

### Post by bcbc on 2010-11-20
It looks like you're running a 10.04.1 version of wubi.exe and have 10.10 kubuntu downloaded. Despite that it seems to have downloaded and installed Kubuntu - but subsequently trying to uninstall and reinstall it's left bits of itself around - and when it tries to remove Kubuntu from the boot manager it is failing and kicking out an error.

So, manually clean up Kubuntu using the manual uninstall instructions from the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?").
Then download the 10.10 version of Wubi from [here]("http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/") or run Wubi from the Kubuntu CD itself (F: drive?).


Regarding the first 'successful' install of Kubuntu - sometimes when Ubuntu is added to the boot manager it leaves the timeout value set to 0, so it doesn't prompt you to choose and instead boots directly into Windows. You should check this the next time it appears to successfully install.

> The Startup and recovery dialog box enables you to select the default
operating system to start if you have multiple operating systems
installed on your computer. You can also change the time-out value.
These settings are located on the Advanced tab in the System Properties
dialog box.

---

