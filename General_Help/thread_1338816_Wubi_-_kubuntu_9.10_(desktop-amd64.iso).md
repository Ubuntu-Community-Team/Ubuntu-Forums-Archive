---
title: "Wubi - kubuntu 9.10 (desktop-amd64.iso)"
date: 2009-11-26
forum: General Help
---

### Post by daok on 2009-11-26
Hello,

I have downloaded "kubuntu-9.10-desktop-amd64.iso" and I have mounted it on my Windows Vista 64 bits Ultimate.

I have downloaded wubi 9.10.

The problem is when installing it crash after few time.

Here is the log file:

```

11-26 21:07 INFO   root: === wubi 9.10ubuntu1 rev160 ===
11-26 21:07 DEBUG  root: Logfile is c:\users\patrick\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
11-26 21:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="Z:\\wubi.exe"']
11-26 21:07 DEBUG  CommonBackend: data_dir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\data
11-26 21:07 DEBUG  WindowsBackend: 7z=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\bin\7z.exe
11-26 21:07 DEBUG  CommonBackend: Fetching basic info...
11-26 21:07 DEBUG  CommonBackend: original_exe=Z:\wubi.exe
11-26 21:07 DEBUG  CommonBackend: platform=win32
11-26 21:07 DEBUG  CommonBackend: osname=nt
11-26 21:07 DEBUG  CommonBackend: language=fr_CA
11-26 21:07 DEBUG  CommonBackend: encoding=cp1252
11-26 21:07 DEBUG  WindowsBackend: arch=amd64
11-26 21:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\data\isolist.ini
11-26 21:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
11-26 21:07 DEBUG  WindowsBackend: Fetching host info...
11-26 21:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-26 21:07 DEBUG  WindowsBackend: windows version=vista
11-26 21:07 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Ultimate
11-26 21:07 DEBUG  WindowsBackend: windows_sp=None
11-26 21:07 DEBUG  WindowsBackend: windows_build=6002
11-26 21:07 DEBUG  WindowsBackend: gmt=-5
11-26 21:07 DEBUG  WindowsBackend: country=CA
11-26 21:07 DEBUG  WindowsBackend: timezone=America/Montreal
11-26 21:07 DEBUG  WindowsBackend: windows_username=Patrick
11-26 21:07 DEBUG  WindowsBackend: user_full_name=Patrick
11-26 21:07 DEBUG  WindowsBackend: user_directory=C:\Users\Patrick
11-26 21:07 DEBUG  WindowsBackend: windows_language_code=1036
11-26 21:07 DEBUG  WindowsBackend: windows_language=French
11-26 21:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
11-26 21:07 DEBUG  WindowsBackend: bootloader=vista
11-26 21:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 239816.335938 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(C: hd 239816.335938 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(E: hd 483619.367188 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(G: hd 84606.9375 mb free fat32)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(Z: cd 0.0 mb free cdfs)
11-26 21:07 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-26 21:07 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-26 21:07 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-26 21:07 DEBUG  WindowsBackend: keyboard_id=269029385
11-26 21:07 DEBUG  WindowsBackend: keyboard_layout=ca
11-26 21:07 DEBUG  WindowsBackend: keyboard_variant=
11-26 21:07 DEBUG  CommonBackend: python locale=('fr_CA', 'cp1252')
11-26 21:07 DEBUG  CommonBackend: locale=fr_CA.UTF-8
11-26 21:07 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
11-26 21:07 DEBUG  CommonBackend: Searching ISOs on USB devices
11-26 21:07 DEBUG  CommonBackend: Searching for local CDs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
11-26 21:07 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
11-26 21:07 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
11-26 21:07 INFO   Distro: Found a valid CD for Kubuntu: Z:\
11-26 21:07 INFO   root: Running the CD menu...
11-26 21:07 DEBUG  WindowsFrontend: __init__...
11-26 21:07 DEBUG  WindowsFrontend: on_init...
11-26 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\translations, languages=['fr_CA', 'fr']
11-26 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\translations, languages=['fr_CA', 'fr']
11-26 21:07 INFO   root: CD menu finished
11-26 21:07 INFO   root: Already installed, running the uninstaller...
11-26 21:07 INFO   root: Running the uninstaller...
11-26 21:07 INFO   CommonBackend: This is the uninstaller running
11-26 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\translations, languages=['fr_CA', 'fr']
11-26 21:07 INFO   root: Received settings
11-26 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\translations, languages=['fr_CA', 'fr']
11-26 21:07 DEBUG  TaskList: # Running tasklist...
11-26 21:07 DEBUG  TaskList: ## Running Sauvegarder l'ISO...
11-26 21:07 DEBUG  TaskList: ## Finished Sauvegarder l'ISO
11-26 21:07 DEBUG  TaskList: ## Running Supprimer l'entrée pour le programme d'amorçage...
11-26 21:07 DEBUG  WindowsBackend: Could not find bcd id
11-26 21:07 DEBUG  WindowsBackend: undo_bootini C:
11-26 21:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 239816.335938 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: undo_bootini E:
11-26 21:07 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 483619.367188 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: undo_bootini G:
11-26 21:07 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 84606.9375 mb free fat32)
11-26 21:07 DEBUG  TaskList: ## Finished Supprimer l'entrée pour le programme d'amorçage
11-26 21:07 DEBUG  TaskList: ## Running Supprimer le répertoire cible...
11-26 21:07 DEBUG  CommonBackend: Deleting C:\ubuntu
11-26 21:07 DEBUG  TaskList: ## Finished Supprimer le répertoire cible
11-26 21:07 DEBUG  TaskList: ## Running Supprimer la clé du registre...
11-26 21:07 DEBUG  TaskList: ## Finished Supprimer la clé du registre
11-26 21:07 DEBUG  TaskList: # Finished tasklist
11-26 21:07 INFO   root: Almost finished uninstalling
11-26 21:07 INFO   root: Finished uninstallation
11-26 21:07 DEBUG  CommonBackend: Fetching basic info...
11-26 21:07 DEBUG  CommonBackend: original_exe=Z:\wubi.exe
11-26 21:07 DEBUG  CommonBackend: platform=win32
11-26 21:07 DEBUG  CommonBackend: osname=nt
11-26 21:07 DEBUG  WindowsBackend: arch=amd64
11-26 21:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\data\isolist.ini
11-26 21:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-26 21:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-26 21:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
11-26 21:07 DEBUG  WindowsBackend: Fetching host info...
11-26 21:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-26 21:07 DEBUG  WindowsBackend: windows version=vista
11-26 21:07 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Ultimate
11-26 21:07 DEBUG  WindowsBackend: windows_sp=None
11-26 21:07 DEBUG  WindowsBackend: windows_build=6002
11-26 21:07 DEBUG  WindowsBackend: gmt=-5
11-26 21:07 DEBUG  WindowsBackend: country=CA
11-26 21:07 DEBUG  WindowsBackend: timezone=America/Montreal
11-26 21:07 DEBUG  WindowsBackend: windows_username=Patrick
11-26 21:07 DEBUG  WindowsBackend: user_full_name=Patrick
11-26 21:07 DEBUG  WindowsBackend: user_directory=C:\Users\Patrick
11-26 21:07 DEBUG  WindowsBackend: windows_language_code=1036
11-26 21:07 DEBUG  WindowsBackend: windows_language=French
11-26 21:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
11-26 21:07 DEBUG  WindowsBackend: bootloader=vista
11-26 21:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 240512.851563 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(C: hd 240512.851563 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(E: hd 483523.867188 mb free ntfs)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(G: hd 84445.65625 mb free fat32)
11-26 21:07 DEBUG  WindowsBackend: drive=Drive(Z: cd 0.0 mb free cdfs)
11-26 21:07 DEBUG  WindowsBackend: uninstaller_path=None
11-26 21:07 DEBUG  WindowsBackend: previous_target_dir=None
11-26 21:07 DEBUG  WindowsBackend: previous_distro_name=None
11-26 21:07 DEBUG  WindowsBackend: keyboard_id=269029385
11-26 21:07 DEBUG  WindowsBackend: keyboard_layout=ca
11-26 21:07 DEBUG  WindowsBackend: keyboard_variant=
11-26 21:07 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
11-26 21:07 DEBUG  CommonBackend: Searching ISOs on USB devices
11-26 21:07 DEBUG  CommonBackend: Searching for local CDs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-26 21:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
11-26 21:07 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu Netbook Remix CD
11-26 21:07 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
11-26 21:07 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
11-26 21:07 INFO   Distro: Found a valid CD for Kubuntu: Z:\
11-26 21:07 INFO   root: Running the installer...
11-26 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\translations, languages=['fr_CA', 'fr']
11-26 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\translations, languages=['fr_CA', 'fr']
11-26 21:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=patrick
11-26 21:07 INFO   root: Received settings
11-26 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\translations, languages=['en_US', 'en']
11-26 21:07 DEBUG  TaskList: # Running tasklist...
11-26 21:07 DEBUG  TaskList: ## Running select_target_dir...
11-26 21:07 INFO   WindowsBackend: Installing into C:\ubuntu
11-26 21:07 DEBUG  TaskList: ## Finished select_target_dir
11-26 21:07 DEBUG  TaskList: ## Running create_dir_structure...
11-26 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-26 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-26 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-26 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-26 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-26 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-26 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-26 21:07 DEBUG  TaskList: ## Finished create_dir_structure
11-26 21:07 DEBUG  TaskList: ## Running uncompress_target_dir...
11-26 21:07 DEBUG  TaskList: ## Finished uncompress_target_dir
11-26 21:07 DEBUG  TaskList: ## Running create_uninstaller...
11-26 21:07 DEBUG  WindowsBackend: Copying uninstaller Z:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.kubuntu.org
11-26 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-26 21:07 DEBUG  TaskList: ## Finished create_uninstaller
11-26 21:07 DEBUG  TaskList: ## Running copy_installation_files...
11-26 21:07 DEBUG  WindowsBackend: Copying C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-26 21:07 DEBUG  WindowsBackend: Copying C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\winboot -> C:\ubuntu\winboot
11-26 21:07 DEBUG  WindowsBackend: Copying C:\Users\Patrick\AppData\Local\Temp\pyl5A09.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
11-26 21:07 DEBUG  TaskList: ## Finished copy_installation_files
11-26 21:07 DEBUG  TaskList: ## Running get_iso...
11-26 21:07 DEBUG  TaskList: New task copy_file
11-26 21:07 DEBUG  TaskList: ### Running copy_file...
11-26 21:09 DEBUG  TaskList: ### Finished copy_file
11-26 21:09 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-26 21:09 DEBUG  TaskList: # Cancelling tasklist
11-26 21:09 DEBUG  TaskList: New task check_iso
11-26 21:09 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-26 21:09 DEBUG  CommonBackend: Searching for local ISO
11-26 21:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-26 21:09 DEBUG  TaskList: New task get_metalink
11-26 21:09 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-26 21:09 DEBUG  TaskList: # Cancelling tasklist
11-26 21:09 DEBUG  TaskList: # Finished tasklist


```Any idea?

---

### Post by daok on 2009-11-26
I have noticed in the installation that a file called isolist.ini contain a wrong value for metalink here is what it has:

> 
[Kubuntu-amd64]
arch=amd64
name=Kubuntu
packages=kubuntu-desktop
metalink=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink
#metalink=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-beta-desktop-amd64.metalink
metalink2=http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-amd64.metalink
website=http://www.kubuntu.org
ordering=3


Here is the new value:

> 
As you can see the 
[Kubuntu-amd64]
arch=amd64
name=Kubuntu
packages=kubuntu-desktop
metalink=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-amd64.metalink
#metalink=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-beta-desktop-amd64.metalink
metalink2=http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-amd64.metalink
website=http://www.kubuntu.org
ordering=3


But it still doesn't work!!! :(

I have try to like Linux 4 years ago, I thought it was too hard... I have a very weird taste again now if the installation just do not work... any body can fix that?

---

