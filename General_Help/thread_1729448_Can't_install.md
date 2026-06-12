---
title: "Can't install"
date: 2011-04-14
forum: General Help
---

### Post by Dualshotty on 2011-04-14
Well I'm trying to install Ubuntu. I've never had it as my OS before but I'm excited to use it. Unfortunately, when I used the Windows Installer file I always get the same error when I get to the end for some reason, heres a picture of the error.

[IMG]http://i.imgur.com/DMxHK.png[/IMG]

Well I went to the log and heres what it said (I tried installing like 5 times, so you may see some repeats). As far as I can tell it can't access the file, its getting a "404 Error". But I'm a noob and could be totally wrong.

```
04-14 18:34 INFO   root: === wubi 10.04.1 rev190 ===
04-14 18:34 DEBUG  root: Logfile is c:\users\brandon\appdata\local\temp\wubi-10.04.1-rev190.log
04-14 18:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brandon\\Downloads\\wubi.exe"']
04-14 18:34 DEBUG  CommonBackend: data_dir=C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\data
04-14 18:34 DEBUG  WindowsBackend: 7z=C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\bin\7z.exe
04-14 18:34 DEBUG  CommonBackend: Fetching basic info...
04-14 18:34 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 18:34 DEBUG  CommonBackend: platform=win32
04-14 18:34 DEBUG  CommonBackend: osname=nt
04-14 18:34 DEBUG  CommonBackend: language=en_US
04-14 18:34 DEBUG  CommonBackend: encoding=cp1252
04-14 18:34 DEBUG  WindowsBackend: arch=amd64
04-14 18:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\data\isolist.ini
04-14 18:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 18:34 DEBUG  WindowsBackend: Fetching host info...
04-14 18:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 18:34 DEBUG  WindowsBackend: windows version=vista
04-14 18:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 18:34 DEBUG  WindowsBackend: windows_sp=None
04-14 18:34 DEBUG  WindowsBackend: windows_build=7600
04-14 18:34 DEBUG  WindowsBackend: gmt=-7
04-14 18:34 DEBUG  WindowsBackend: country=US
04-14 18:34 DEBUG  WindowsBackend: timezone=America/Denver
04-14 18:34 DEBUG  WindowsBackend: windows_username=Brandon
04-14 18:34 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 18:34 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 18:34 DEBUG  WindowsBackend: windows_language_code=1033
04-14 18:34 DEBUG  WindowsBackend: windows_language=English
04-14 18:34 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 18:34 DEBUG  WindowsBackend: bootloader=vista
04-14 18:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195247.648438 mb free ntfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(C: hd 195247.648438 mb free ntfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 18:34 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-14 18:34 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-14 18:34 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-14 18:34 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 18:34 DEBUG  WindowsBackend: keyboard_layout=us
04-14 18:34 DEBUG  WindowsBackend: keyboard_variant=
04-14 18:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-14 18:34 DEBUG  CommonBackend: locale=en_US.UTF-8
04-14 18:34 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 18:34 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 18:34 DEBUG  CommonBackend: Searching for local CDs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl82E8.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 INFO   root: Already installed, running the uninstaller...
04-14 18:34 INFO   root: Running the uninstaller...
04-14 18:34 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
04-14 18:34 DEBUG  root: application.quit
04-14 18:34 DEBUG  root: application.on_quit
04-14 18:34 INFO   root: sys.exit
04-14 18:34 INFO   root: Quitting application
04-14 18:34 INFO   root: === wubi 10.04.1 rev190 ===
04-14 18:34 DEBUG  root: Logfile is c:\users\brandon\appdata\local\temp\wubi-10.04.1-rev190.log
04-14 18:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brandon\\Downloads\\wubi.exe"']
04-14 18:34 DEBUG  CommonBackend: data_dir=C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\data
04-14 18:34 DEBUG  WindowsBackend: 7z=C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\bin\7z.exe
04-14 18:34 DEBUG  CommonBackend: Fetching basic info...
04-14 18:34 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 18:34 DEBUG  CommonBackend: platform=win32
04-14 18:34 DEBUG  CommonBackend: osname=nt
04-14 18:34 DEBUG  CommonBackend: language=en_US
04-14 18:34 DEBUG  CommonBackend: encoding=cp1252
04-14 18:34 DEBUG  WindowsBackend: arch=amd64
04-14 18:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\data\isolist.ini
04-14 18:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 18:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 18:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 18:34 DEBUG  WindowsBackend: Fetching host info...
04-14 18:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 18:34 DEBUG  WindowsBackend: windows version=vista
04-14 18:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 18:34 DEBUG  WindowsBackend: windows_sp=None
04-14 18:34 DEBUG  WindowsBackend: windows_build=7600
04-14 18:34 DEBUG  WindowsBackend: gmt=-7
04-14 18:34 DEBUG  WindowsBackend: country=US
04-14 18:34 DEBUG  WindowsBackend: timezone=America/Denver
04-14 18:34 DEBUG  WindowsBackend: windows_username=Brandon
04-14 18:34 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 18:34 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 18:34 DEBUG  WindowsBackend: windows_language_code=1033
04-14 18:34 DEBUG  WindowsBackend: windows_language=English
04-14 18:34 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 18:34 DEBUG  WindowsBackend: bootloader=vista
04-14 18:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195955.84375 mb free ntfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(C: hd 195955.84375 mb free ntfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 18:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 18:34 DEBUG  WindowsBackend: uninstaller_path=None
04-14 18:34 DEBUG  WindowsBackend: previous_target_dir=None
04-14 18:34 DEBUG  WindowsBackend: previous_distro_name=None
04-14 18:34 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 18:34 DEBUG  WindowsBackend: keyboard_layout=us
04-14 18:34 DEBUG  WindowsBackend: keyboard_variant=
04-14 18:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-14 18:34 DEBUG  CommonBackend: locale=en_US.UTF-8
04-14 18:34 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 18:34 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 18:34 DEBUG  CommonBackend: Searching for local CDs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:34 INFO   root: Running the installer...
04-14 18:34 DEBUG  WindowsFrontend: __init__...
04-14 18:34 DEBUG  WindowsFrontend: on_init...
04-14 18:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\translations, languages=['en_US', 'en']
04-14 18:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\translations, languages=['en_US', 'en']
04-14 18:36 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brandon
04-14 18:36 INFO   root: Received settings
04-14 18:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\translations, languages=['en_US', 'en']
04-14 18:36 DEBUG  TaskList: # Running tasklist...
04-14 18:36 DEBUG  TaskList: ## Running select_target_dir...
04-14 18:36 INFO   WindowsBackend: Installing into C:\ubuntu
04-14 18:36 DEBUG  TaskList: ## Finished select_target_dir
04-14 18:36 DEBUG  TaskList: ## Running create_dir_structure...
04-14 18:36 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-14 18:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-14 18:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-14 18:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-14 18:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-14 18:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-14 18:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-14 18:36 DEBUG  TaskList: ## Finished create_dir_structure
04-14 18:36 DEBUG  TaskList: ## Running uncompress_target_dir...
04-14 18:36 DEBUG  TaskList: ## Finished uncompress_target_dir
04-14 18:36 DEBUG  TaskList: ## Running create_uninstaller...
04-14 18:36 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brandon\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-14 18:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-14 18:36 DEBUG  TaskList: ## Finished create_uninstaller
04-14 18:36 DEBUG  TaskList: ## Running copy_installation_files...
04-14 18:36 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-14 18:36 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\winboot -> C:\ubuntu\winboot
04-14 18:36 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-14 18:36 DEBUG  TaskList: ## Finished copy_installation_files
04-14 18:36 DEBUG  TaskList: ## Running get_iso...
04-14 18:36 DEBUG  CommonBackend: Searching for local CD
04-14 18:36 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp is a valid Ubuntu CD
04-14 18:36 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4AE7.tmp\casper\filesystem.squashfs
04-14 18:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:36 DEBUG  CommonBackend: Searching for local ISO
04-14 18:36 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 18:36 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 18:36 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
04-14 18:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
04-14 18:36 DEBUG  Distro: wrong version: 10.10 != 10.04.1
04-14 18:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-14 18:36 DEBUG  TaskList: New task get_metalink
04-14 18:36 DEBUG  TaskList: ### Running get_metalink...
04-14 18:36 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink > C:\ubuntu\install
04-14 18:36 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
04-14 18:36 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink > C:\ubuntu\install
04-14 18:36 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink, basename=lucid-desktop-amd64.metalink, length=1010, text=None
04-14 18:36 DEBUG  downloader: download finished (read 1010 bytes)
04-14 18:36 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink > C:\ubuntu\install
04-14 18:36 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=257, text=None
04-14 18:36 DEBUG  downloader: download finished (read 257 bytes)
04-14 18:36 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-14 18:36 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-14 18:36 DEBUG  downloader: download finished (read 198 bytes)
04-14 18:36 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-14 18:36 INFO   saplog: Checking block bindings..
04-14 18:36 INFO   saplog: Key verified successfully.
04-14 18:36 DEBUG  CommonBackend: metalink md5sums:
cda012b82a15cb5bbd6c44f1920dfd1c  natty-desktop-amd64+mac.metalink
968f50ad56a3255b13dab817133b26aa  natty-desktop-amd64.metalink
a3d5d97d438ca4e3b4080cb5181890f4  natty-desktop-i386.metalink
668910f8d3467dfc0c87f96b77ee8f74  natty-desktop-powerpc.metalink

04-14 18:36 ERROR  CommonBackend: The md5 of the metalink does match
04-14 18:36 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
04-14 18:36 DEBUG  TaskList: ### Finished get_metalink
04-14 18:36 DEBUG  TaskList: New task download
04-14 18:36 DEBUG  TaskList: ### Running download...
04-14 18:36 DEBUG  btdownloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso.torrent > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 18:36 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
04-14 18:36 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
04-14 18:36 DEBUG  TaskList: ### Finished download
04-14 18:36 DEBUG  TaskList: New task download
04-14 18:36 DEBUG  TaskList: ### Running download...
04-14 18:36 DEBUG  downloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 18:36 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso, basename=lucid-desktop-amd64.iso, length=721129472, text=None
04-14 18:54 DEBUG  TaskList: ### Finished download
04-14 18:54 DEBUG  downloader: download finished (read 721129472 bytes)
04-14 18:54 DEBUG  TaskList: New task check_iso
04-14 18:54 DEBUG  TaskList: ### Running check_iso...
04-14 18:54 DEBUG  CommonBackend: Checking C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 18:54 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 18:54 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 18:54 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
04-14 18:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
04-14 18:54 DEBUG  Distro: wrong version: 10.04.2 != 10.04.1
04-14 18:54 DEBUG  TaskList: ### Finished check_iso
04-14 18:54 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-14 18:54 DEBUG  TaskList: # Cancelling tasklist
04-14 18:54 DEBUG  TaskList: # Finished tasklist
04-14 18:54 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-14 18:54 INFO   root: === wubi 10.04.1 rev190 ===
04-14 18:54 DEBUG  root: Logfile is c:\users\brandon\appdata\local\temp\wubi-10.04.1-rev190.log
04-14 18:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brandon\\Downloads\\wubi.exe"']
04-14 18:54 DEBUG  CommonBackend: data_dir=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\data
04-14 18:54 DEBUG  WindowsBackend: 7z=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\bin\7z.exe
04-14 18:54 DEBUG  CommonBackend: Fetching basic info...
04-14 18:54 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 18:54 DEBUG  CommonBackend: platform=win32
04-14 18:54 DEBUG  CommonBackend: osname=nt
04-14 18:54 DEBUG  CommonBackend: language=en_US
04-14 18:54 DEBUG  CommonBackend: encoding=cp1252
04-14 18:54 DEBUG  WindowsBackend: arch=amd64
04-14 18:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\data\isolist.ini
04-14 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 18:54 DEBUG  WindowsBackend: Fetching host info...
04-14 18:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 18:54 DEBUG  WindowsBackend: windows version=vista
04-14 18:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 18:54 DEBUG  WindowsBackend: windows_sp=None
04-14 18:54 DEBUG  WindowsBackend: windows_build=7600
04-14 18:54 DEBUG  WindowsBackend: gmt=-7
04-14 18:54 DEBUG  WindowsBackend: country=US
04-14 18:54 DEBUG  WindowsBackend: timezone=America/Denver
04-14 18:54 DEBUG  WindowsBackend: windows_username=Brandon
04-14 18:54 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 18:54 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 18:54 DEBUG  WindowsBackend: windows_language_code=1033
04-14 18:54 DEBUG  WindowsBackend: windows_language=English
04-14 18:54 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 18:54 DEBUG  WindowsBackend: bootloader=vista
04-14 18:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195949.390625 mb free ntfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(C: hd 195949.390625 mb free ntfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 18:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-14 18:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-14 18:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-14 18:54 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 18:54 DEBUG  WindowsBackend: keyboard_layout=us
04-14 18:54 DEBUG  WindowsBackend: keyboard_variant=
04-14 18:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-14 18:54 DEBUG  CommonBackend: locale=en_US.UTF-8
04-14 18:54 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 18:54 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 18:54 DEBUG  CommonBackend: Searching for local CDs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 INFO   root: Already installed, running the uninstaller...
04-14 18:54 INFO   root: Running the uninstaller...
04-14 18:54 INFO   CommonBackend: This is the uninstaller running
04-14 18:54 DEBUG  WindowsFrontend: __init__...
04-14 18:54 DEBUG  WindowsFrontend: on_init...
04-14 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\translations, languages=['en_US', 'en']
04-14 18:54 INFO   root: Received settings
04-14 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\translations, languages=['en_US', 'en']
04-14 18:54 DEBUG  TaskList: # Running tasklist...
04-14 18:54 DEBUG  TaskList: ## Running Backup ISO...
04-14 18:54 DEBUG  TaskList: ## Finished Backup ISO
04-14 18:54 DEBUG  TaskList: ## Running Remove bootloader entry...
04-14 18:54 DEBUG  WindowsBackend: Could not find bcd id
04-14 18:54 DEBUG  WindowsBackend: undo_bootini C:
04-14 18:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195949.390625 mb free ntfs)
04-14 18:54 DEBUG  WindowsBackend: undo_bootini D:
04-14 18:54 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2072.0234375 mb free ntfs)
04-14 18:54 DEBUG  TaskList: ## Finished Remove bootloader entry
04-14 18:54 DEBUG  TaskList: ## Running Remove target dir...
04-14 18:54 DEBUG  CommonBackend: Deleting C:\ubuntu
04-14 18:54 DEBUG  TaskList: ## Finished Remove target dir
04-14 18:54 DEBUG  TaskList: ## Running Remove registry key...
04-14 18:54 DEBUG  TaskList: ## Finished Remove registry key
04-14 18:54 DEBUG  TaskList: # Finished tasklist
04-14 18:54 INFO   root: Almost finished uninstalling
04-14 18:54 INFO   root: Finished uninstallation
04-14 18:54 DEBUG  CommonBackend: Fetching basic info...
04-14 18:54 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 18:54 DEBUG  CommonBackend: platform=win32
04-14 18:54 DEBUG  CommonBackend: osname=nt
04-14 18:54 DEBUG  WindowsBackend: arch=amd64
04-14 18:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\data\isolist.ini
04-14 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 18:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 18:54 DEBUG  WindowsBackend: Fetching host info...
04-14 18:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 18:54 DEBUG  WindowsBackend: windows version=vista
04-14 18:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 18:54 DEBUG  WindowsBackend: windows_sp=None
04-14 18:54 DEBUG  WindowsBackend: windows_build=7600
04-14 18:54 DEBUG  WindowsBackend: gmt=-7
04-14 18:54 DEBUG  WindowsBackend: country=US
04-14 18:54 DEBUG  WindowsBackend: timezone=America/Denver
04-14 18:54 DEBUG  WindowsBackend: windows_username=Brandon
04-14 18:54 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 18:54 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 18:54 DEBUG  WindowsBackend: windows_language_code=1033
04-14 18:54 DEBUG  WindowsBackend: windows_language=English
04-14 18:54 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 18:54 DEBUG  WindowsBackend: bootloader=vista
04-14 18:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195950.910156 mb free ntfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(C: hd 195950.910156 mb free ntfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 18:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 18:54 DEBUG  WindowsBackend: uninstaller_path=None
04-14 18:54 DEBUG  WindowsBackend: previous_target_dir=None
04-14 18:54 DEBUG  WindowsBackend: previous_distro_name=None
04-14 18:54 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 18:54 DEBUG  WindowsBackend: keyboard_layout=us
04-14 18:54 DEBUG  WindowsBackend: keyboard_variant=
04-14 18:54 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 18:54 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 18:54 DEBUG  CommonBackend: Searching for local CDs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 18:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:54 INFO   root: Running the installer...
04-14 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\translations, languages=['en_US', 'en']
04-14 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\translations, languages=['en_US', 'en']
04-14 18:55 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brandon
04-14 18:55 INFO   root: Received settings
04-14 18:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\translations, languages=['en_US', 'en']
04-14 18:55 DEBUG  TaskList: # Running tasklist...
04-14 18:55 DEBUG  TaskList: ## Running select_target_dir...
04-14 18:55 INFO   WindowsBackend: Installing into C:\ubuntu
04-14 18:55 DEBUG  TaskList: ## Finished select_target_dir
04-14 18:55 DEBUG  TaskList: ## Running create_dir_structure...
04-14 18:55 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-14 18:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-14 18:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-14 18:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-14 18:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-14 18:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-14 18:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-14 18:55 DEBUG  TaskList: ## Finished create_dir_structure
04-14 18:55 DEBUG  TaskList: ## Running uncompress_target_dir...
04-14 18:55 DEBUG  TaskList: ## Finished uncompress_target_dir
04-14 18:55 DEBUG  TaskList: ## Running create_uninstaller...
04-14 18:55 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brandon\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-14 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-14 18:55 DEBUG  TaskList: ## Finished create_uninstaller
04-14 18:55 DEBUG  TaskList: ## Running copy_installation_files...
04-14 18:55 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-14 18:55 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\winboot -> C:\ubuntu\winboot
04-14 18:55 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-14 18:55 DEBUG  TaskList: ## Finished copy_installation_files
04-14 18:55 DEBUG  TaskList: ## Running get_iso...
04-14 18:55 DEBUG  CommonBackend: Searching for local CD
04-14 18:55 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp is a valid Ubuntu CD
04-14 18:55 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl11DE.tmp\casper\filesystem.squashfs
04-14 18:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 18:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 18:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 18:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 18:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 18:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 18:55 DEBUG  CommonBackend: Searching for local ISO
04-14 18:55 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 18:55 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 18:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
04-14 18:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
04-14 18:55 DEBUG  Distro: wrong version: 10.10 != 10.04.1
04-14 18:55 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-14 18:55 DEBUG  TaskList: New task get_metalink
04-14 18:55 DEBUG  TaskList: ### Running get_metalink...
04-14 18:55 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink > C:\ubuntu\install
04-14 18:55 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
04-14 18:55 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink > C:\ubuntu\install
04-14 18:55 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink, basename=lucid-desktop-amd64.metalink, length=1010, text=None
04-14 18:55 DEBUG  downloader: download finished (read 1010 bytes)
04-14 18:55 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink > C:\ubuntu\install
04-14 18:55 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=257, text=None
04-14 18:55 DEBUG  downloader: download finished (read 257 bytes)
04-14 18:55 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-14 18:55 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-14 18:55 DEBUG  downloader: download finished (read 198 bytes)
04-14 18:55 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-14 18:55 INFO   saplog: Checking block bindings..
04-14 18:55 INFO   saplog: Key verified successfully.
04-14 18:55 DEBUG  CommonBackend: metalink md5sums:
cda012b82a15cb5bbd6c44f1920dfd1c  natty-desktop-amd64+mac.metalink
968f50ad56a3255b13dab817133b26aa  natty-desktop-amd64.metalink
a3d5d97d438ca4e3b4080cb5181890f4  natty-desktop-i386.metalink
668910f8d3467dfc0c87f96b77ee8f74  natty-desktop-powerpc.metalink

04-14 18:55 ERROR  CommonBackend: The md5 of the metalink does match
04-14 18:55 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
04-14 18:55 DEBUG  TaskList: ### Finished get_metalink
04-14 18:55 DEBUG  TaskList: New task download
04-14 18:55 DEBUG  TaskList: ### Running download...
04-14 18:55 DEBUG  btdownloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso.torrent > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 18:55 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
04-14 18:55 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
04-14 18:55 DEBUG  TaskList: ### Finished download
04-14 18:55 DEBUG  TaskList: New task download
04-14 18:55 DEBUG  TaskList: ### Running download...
04-14 18:55 DEBUG  downloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 18:55 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso, basename=lucid-desktop-amd64.iso, length=721129472, text=None
04-14 19:26 INFO   WindowsFrontend: Operation cancelled
04-14 19:26 DEBUG  WindowsFrontend: frontend.quit
04-14 19:26 DEBUG  WindowsFrontend: frontend.on_quit
04-14 19:26 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-14 19:26 DEBUG  TaskList: # Cancelling tasklist
04-14 19:26 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-14 19:26 DEBUG  root: application.on_quit
04-14 19:26 DEBUG  root: Forceful exit
04-14 19:26 INFO   root: sys.exit
04-14 19:26 INFO   root: === wubi 10.04.1 rev190 ===
04-14 19:26 DEBUG  root: Logfile is c:\users\brandon\appdata\local\temp\wubi-10.04.1-rev190.log
04-14 19:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brandon\\Downloads\\wubi.exe"']
04-14 19:26 DEBUG  CommonBackend: data_dir=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\data
04-14 19:26 DEBUG  WindowsBackend: 7z=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\bin\7z.exe
04-14 19:26 DEBUG  CommonBackend: Fetching basic info...
04-14 19:26 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 19:26 DEBUG  CommonBackend: platform=win32
04-14 19:26 DEBUG  CommonBackend: osname=nt
04-14 19:26 DEBUG  CommonBackend: language=en_US
04-14 19:26 DEBUG  CommonBackend: encoding=cp1252
04-14 19:26 DEBUG  WindowsBackend: arch=amd64
04-14 19:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\data\isolist.ini
04-14 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 19:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 19:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 19:26 DEBUG  WindowsBackend: Fetching host info...
04-14 19:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 19:26 DEBUG  WindowsBackend: windows version=vista
04-14 19:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 19:26 DEBUG  WindowsBackend: windows_sp=None
04-14 19:26 DEBUG  WindowsBackend: windows_build=7600
04-14 19:26 DEBUG  WindowsBackend: gmt=-7
04-14 19:26 DEBUG  WindowsBackend: country=US
04-14 19:26 DEBUG  WindowsBackend: timezone=America/Denver
04-14 19:26 DEBUG  WindowsBackend: windows_username=Brandon
04-14 19:26 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 19:26 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 19:26 DEBUG  WindowsBackend: windows_language_code=1033
04-14 19:26 DEBUG  WindowsBackend: windows_language=English
04-14 19:26 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 19:26 DEBUG  WindowsBackend: bootloader=vista
04-14 19:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195239.980469 mb free ntfs)
04-14 19:26 DEBUG  WindowsBackend: drive=Drive(C: hd 195239.980469 mb free ntfs)
04-14 19:26 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 19:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 19:26 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 19:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-14 19:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-14 19:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-14 19:26 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 19:26 DEBUG  WindowsBackend: keyboard_layout=us
04-14 19:26 DEBUG  WindowsBackend: keyboard_variant=
04-14 19:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-14 19:26 DEBUG  CommonBackend: locale=en_US.UTF-8
04-14 19:26 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 19:26 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 19:26 DEBUG  CommonBackend: Searching for local CDs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Ubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Kubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:26 INFO   root: Already installed, running the uninstaller...
04-14 19:26 INFO   root: Running the uninstaller...
04-14 19:26 INFO   CommonBackend: This is the uninstaller running
04-14 19:26 DEBUG  WindowsFrontend: __init__...
04-14 19:26 DEBUG  WindowsFrontend: on_init...
04-14 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\translations, languages=['en_US', 'en']
04-14 19:27 INFO   root: Received settings
04-14 19:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\translations, languages=['en_US', 'en']
04-14 19:27 DEBUG  TaskList: # Running tasklist...
04-14 19:27 DEBUG  TaskList: ## Running Backup ISO...
04-14 19:27 DEBUG  TaskList: ## Finished Backup ISO
04-14 19:27 DEBUG  TaskList: ## Running Remove bootloader entry...
04-14 19:27 DEBUG  WindowsBackend: Could not find bcd id
04-14 19:27 DEBUG  WindowsBackend: undo_bootini C:
04-14 19:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195239.980469 mb free ntfs)
04-14 19:27 DEBUG  WindowsBackend: undo_bootini D:
04-14 19:27 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2072.0234375 mb free ntfs)
04-14 19:27 DEBUG  TaskList: ## Finished Remove bootloader entry
04-14 19:27 DEBUG  TaskList: ## Running Remove target dir...
04-14 19:27 DEBUG  CommonBackend: Deleting C:\ubuntu
04-14 19:27 DEBUG  TaskList: ## Finished Remove target dir
04-14 19:27 DEBUG  TaskList: ## Running Remove registry key...
04-14 19:27 DEBUG  TaskList: ## Finished Remove registry key
04-14 19:27 DEBUG  TaskList: # Finished tasklist
04-14 19:27 INFO   root: Almost finished uninstalling
04-14 19:27 INFO   root: Finished uninstallation
04-14 19:27 DEBUG  CommonBackend: Fetching basic info...
04-14 19:27 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 19:27 DEBUG  CommonBackend: platform=win32
04-14 19:27 DEBUG  CommonBackend: osname=nt
04-14 19:27 DEBUG  WindowsBackend: arch=amd64
04-14 19:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\data\isolist.ini
04-14 19:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 19:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 19:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 19:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 19:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 19:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 19:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 19:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 19:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 19:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 19:27 DEBUG  WindowsBackend: Fetching host info...
04-14 19:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 19:27 DEBUG  WindowsBackend: windows version=vista
04-14 19:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 19:27 DEBUG  WindowsBackend: windows_sp=None
04-14 19:27 DEBUG  WindowsBackend: windows_build=7600
04-14 19:27 DEBUG  WindowsBackend: gmt=-7
04-14 19:27 DEBUG  WindowsBackend: country=US
04-14 19:27 DEBUG  WindowsBackend: timezone=America/Denver
04-14 19:27 DEBUG  WindowsBackend: windows_username=Brandon
04-14 19:27 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 19:27 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 19:27 DEBUG  WindowsBackend: windows_language_code=1033
04-14 19:27 DEBUG  WindowsBackend: windows_language=English
04-14 19:27 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 19:27 DEBUG  WindowsBackend: bootloader=vista
04-14 19:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195929.15625 mb free ntfs)
04-14 19:27 DEBUG  WindowsBackend: drive=Drive(C: hd 195929.15625 mb free ntfs)
04-14 19:27 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 19:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 19:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 19:27 DEBUG  WindowsBackend: uninstaller_path=None
04-14 19:27 DEBUG  WindowsBackend: previous_target_dir=None
04-14 19:27 DEBUG  WindowsBackend: previous_distro_name=None
04-14 19:27 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 19:27 DEBUG  WindowsBackend: keyboard_layout=us
04-14 19:27 DEBUG  WindowsBackend: keyboard_variant=
04-14 19:27 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 19:27 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 19:27 DEBUG  CommonBackend: Searching for local CDs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Ubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Kubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 INFO   root: Running the installer...
04-14 19:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\translations, languages=['en_US', 'en']
04-14 19:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\translations, languages=['en_US', 'en']
04-14 19:27 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brandon
04-14 19:27 INFO   root: Received settings
04-14 19:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\translations, languages=['en_US', 'en']
04-14 19:27 DEBUG  TaskList: # Running tasklist...
04-14 19:27 DEBUG  TaskList: ## Running select_target_dir...
04-14 19:27 INFO   WindowsBackend: Installing into C:\ubuntu
04-14 19:27 DEBUG  TaskList: ## Finished select_target_dir
04-14 19:27 DEBUG  TaskList: ## Running create_dir_structure...
04-14 19:27 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-14 19:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-14 19:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-14 19:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-14 19:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-14 19:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-14 19:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-14 19:27 DEBUG  TaskList: ## Finished create_dir_structure
04-14 19:27 DEBUG  TaskList: ## Running uncompress_target_dir...
04-14 19:27 DEBUG  TaskList: ## Finished uncompress_target_dir
04-14 19:27 DEBUG  TaskList: ## Running create_uninstaller...
04-14 19:27 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brandon\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-14 19:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-14 19:27 DEBUG  TaskList: ## Finished create_uninstaller
04-14 19:27 DEBUG  TaskList: ## Running copy_installation_files...
04-14 19:27 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-14 19:27 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\winboot -> C:\ubuntu\winboot
04-14 19:27 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-14 19:27 DEBUG  TaskList: ## Finished copy_installation_files
04-14 19:27 DEBUG  TaskList: ## Running get_iso...
04-14 19:27 DEBUG  CommonBackend: Searching for local CD
04-14 19:27 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pylAB50.tmp\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:27 DEBUG  CommonBackend: Searching for local ISO
04-14 19:27 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 19:27 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 19:27 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
04-14 19:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
04-14 19:27 DEBUG  Distro: wrong version: 10.10 != 10.04.1
04-14 19:27 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-14 19:27 DEBUG  TaskList: New task get_metalink
04-14 19:27 DEBUG  TaskList: ### Running get_metalink...
04-14 19:27 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink > C:\ubuntu\install
04-14 19:27 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
04-14 19:27 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink > C:\ubuntu\install
04-14 19:27 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink, basename=lucid-desktop-amd64.metalink, length=1010, text=None
04-14 19:27 DEBUG  downloader: download finished (read 1010 bytes)
04-14 19:27 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink > C:\ubuntu\install
04-14 19:27 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=257, text=None
04-14 19:27 DEBUG  downloader: download finished (read 257 bytes)
04-14 19:27 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-14 19:27 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-14 19:27 DEBUG  downloader: download finished (read 198 bytes)
04-14 19:27 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-14 19:27 INFO   saplog: Checking block bindings..
04-14 19:27 INFO   saplog: Key verified successfully.
04-14 19:27 DEBUG  CommonBackend: metalink md5sums:
cda012b82a15cb5bbd6c44f1920dfd1c  natty-desktop-amd64+mac.metalink
968f50ad56a3255b13dab817133b26aa  natty-desktop-amd64.metalink
a3d5d97d438ca4e3b4080cb5181890f4  natty-desktop-i386.metalink
668910f8d3467dfc0c87f96b77ee8f74  natty-desktop-powerpc.metalink

04-14 19:27 ERROR  CommonBackend: The md5 of the metalink does match
04-14 19:27 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
04-14 19:27 DEBUG  TaskList: ### Finished get_metalink
04-14 19:27 DEBUG  TaskList: New task download
04-14 19:27 DEBUG  TaskList: ### Running download...
04-14 19:27 DEBUG  btdownloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso.torrent > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 19:27 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
04-14 19:27 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
04-14 19:27 DEBUG  TaskList: ### Finished download
04-14 19:27 DEBUG  TaskList: New task download
04-14 19:27 DEBUG  TaskList: ### Running download...
04-14 19:27 DEBUG  downloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 19:27 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso, basename=lucid-desktop-amd64.iso, length=721129472, text=None
04-14 19:47 DEBUG  TaskList: ### Finished download
04-14 19:47 DEBUG  downloader: download finished (read 721129472 bytes)
04-14 19:47 DEBUG  TaskList: New task check_iso
04-14 19:47 DEBUG  TaskList: ### Running check_iso...
04-14 19:47 DEBUG  CommonBackend: Checking C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 19:47 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 19:47 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 19:47 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
04-14 19:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
04-14 19:47 DEBUG  Distro: wrong version: 10.04.2 != 10.04.1
04-14 19:47 DEBUG  TaskList: ### Finished check_iso
04-14 19:47 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-14 19:47 DEBUG  TaskList: # Cancelling tasklist
04-14 19:47 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-14 19:47 DEBUG  TaskList: # Finished tasklist
04-14 19:59 INFO   root: === wubi 10.04.1 rev190 ===
04-14 19:59 DEBUG  root: Logfile is c:\users\brandon\appdata\local\temp\wubi-10.04.1-rev190.log
04-14 19:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brandon\\Downloads\\wubi.exe"']
04-14 19:59 DEBUG  CommonBackend: data_dir=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\data
04-14 19:59 DEBUG  WindowsBackend: 7z=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\bin\7z.exe
04-14 19:59 DEBUG  CommonBackend: Fetching basic info...
04-14 19:59 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 19:59 DEBUG  CommonBackend: platform=win32
04-14 19:59 DEBUG  CommonBackend: osname=nt
04-14 19:59 DEBUG  CommonBackend: language=en_US
04-14 19:59 DEBUG  CommonBackend: encoding=cp1252
04-14 19:59 DEBUG  WindowsBackend: arch=amd64
04-14 19:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\data\isolist.ini
04-14 19:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 19:59 DEBUG  WindowsBackend: Fetching host info...
04-14 19:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 19:59 DEBUG  WindowsBackend: windows version=vista
04-14 19:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 19:59 DEBUG  WindowsBackend: windows_sp=None
04-14 19:59 DEBUG  WindowsBackend: windows_build=7600
04-14 19:59 DEBUG  WindowsBackend: gmt=-7
04-14 19:59 DEBUG  WindowsBackend: country=US
04-14 19:59 DEBUG  WindowsBackend: timezone=America/Denver
04-14 19:59 DEBUG  WindowsBackend: windows_username=Brandon
04-14 19:59 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 19:59 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 19:59 DEBUG  WindowsBackend: windows_language_code=1033
04-14 19:59 DEBUG  WindowsBackend: windows_language=English
04-14 19:59 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 19:59 DEBUG  WindowsBackend: bootloader=vista
04-14 19:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195927.136719 mb free ntfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(C: hd 195927.136719 mb free ntfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 19:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-14 19:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-14 19:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-14 19:59 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 19:59 DEBUG  WindowsBackend: keyboard_layout=us
04-14 19:59 DEBUG  WindowsBackend: keyboard_variant=
04-14 19:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-14 19:59 DEBUG  CommonBackend: locale=en_US.UTF-8
04-14 19:59 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 19:59 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 19:59 DEBUG  CommonBackend: Searching for local CDs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 INFO   root: Already installed, running the uninstaller...
04-14 19:59 INFO   root: Running the uninstaller...
04-14 19:59 INFO   CommonBackend: This is the uninstaller running
04-14 19:59 DEBUG  WindowsFrontend: __init__...
04-14 19:59 DEBUG  WindowsFrontend: on_init...
04-14 19:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\translations, languages=['en_US', 'en']
04-14 19:59 INFO   root: Received settings
04-14 19:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\translations, languages=['en_US', 'en']
04-14 19:59 DEBUG  TaskList: # Running tasklist...
04-14 19:59 DEBUG  TaskList: ## Running Backup ISO...
04-14 19:59 DEBUG  TaskList: ## Finished Backup ISO
04-14 19:59 DEBUG  TaskList: ## Running Remove bootloader entry...
04-14 19:59 DEBUG  WindowsBackend: Could not find bcd id
04-14 19:59 DEBUG  WindowsBackend: undo_bootini C:
04-14 19:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195927.136719 mb free ntfs)
04-14 19:59 DEBUG  WindowsBackend: undo_bootini D:
04-14 19:59 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2072.0234375 mb free ntfs)
04-14 19:59 DEBUG  TaskList: ## Finished Remove bootloader entry
04-14 19:59 DEBUG  TaskList: ## Running Remove target dir...
04-14 19:59 DEBUG  CommonBackend: Deleting C:\ubuntu
04-14 19:59 DEBUG  TaskList: ## Finished Remove target dir
04-14 19:59 DEBUG  TaskList: ## Running Remove registry key...
04-14 19:59 DEBUG  TaskList: ## Finished Remove registry key
04-14 19:59 DEBUG  TaskList: # Finished tasklist
04-14 19:59 INFO   root: Almost finished uninstalling
04-14 19:59 INFO   root: Finished uninstallation
04-14 19:59 DEBUG  CommonBackend: Fetching basic info...
04-14 19:59 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 19:59 DEBUG  CommonBackend: platform=win32
04-14 19:59 DEBUG  CommonBackend: osname=nt
04-14 19:59 DEBUG  WindowsBackend: arch=amd64
04-14 19:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\data\isolist.ini
04-14 19:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 19:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 19:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 19:59 DEBUG  WindowsBackend: Fetching host info...
04-14 19:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 19:59 DEBUG  WindowsBackend: windows version=vista
04-14 19:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 19:59 DEBUG  WindowsBackend: windows_sp=None
04-14 19:59 DEBUG  WindowsBackend: windows_build=7600
04-14 19:59 DEBUG  WindowsBackend: gmt=-7
04-14 19:59 DEBUG  WindowsBackend: country=US
04-14 19:59 DEBUG  WindowsBackend: timezone=America/Denver
04-14 19:59 DEBUG  WindowsBackend: windows_username=Brandon
04-14 19:59 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 19:59 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 19:59 DEBUG  WindowsBackend: windows_language_code=1033
04-14 19:59 DEBUG  WindowsBackend: windows_language=English
04-14 19:59 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 19:59 DEBUG  WindowsBackend: bootloader=vista
04-14 19:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195928.667969 mb free ntfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(C: hd 195928.667969 mb free ntfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 19:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 19:59 DEBUG  WindowsBackend: uninstaller_path=None
04-14 19:59 DEBUG  WindowsBackend: previous_target_dir=None
04-14 19:59 DEBUG  WindowsBackend: previous_distro_name=None
04-14 19:59 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 19:59 DEBUG  WindowsBackend: keyboard_layout=us
04-14 19:59 DEBUG  WindowsBackend: keyboard_variant=
04-14 19:59 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 19:59 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 19:59 DEBUG  CommonBackend: Searching for local CDs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 INFO   root: Running the installer...
04-14 19:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\translations, languages=['en_US', 'en']
04-14 19:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\translations, languages=['en_US', 'en']
04-14 19:59 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brandon
04-14 19:59 INFO   root: Received settings
04-14 19:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\translations, languages=['en_US', 'en']
04-14 19:59 DEBUG  TaskList: # Running tasklist...
04-14 19:59 DEBUG  TaskList: ## Running select_target_dir...
04-14 19:59 INFO   WindowsBackend: Installing into C:\ubuntu
04-14 19:59 DEBUG  TaskList: ## Finished select_target_dir
04-14 19:59 DEBUG  TaskList: ## Running create_dir_structure...
04-14 19:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-14 19:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-14 19:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-14 19:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-14 19:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-14 19:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-14 19:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-14 19:59 DEBUG  TaskList: ## Finished create_dir_structure
04-14 19:59 DEBUG  TaskList: ## Running uncompress_target_dir...
04-14 19:59 DEBUG  TaskList: ## Finished uncompress_target_dir
04-14 19:59 DEBUG  TaskList: ## Running create_uninstaller...
04-14 19:59 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brandon\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-14 19:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-14 19:59 DEBUG  TaskList: ## Finished create_uninstaller
04-14 19:59 DEBUG  TaskList: ## Running copy_installation_files...
04-14 19:59 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-14 19:59 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\winboot -> C:\ubuntu\winboot
04-14 19:59 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-14 19:59 DEBUG  TaskList: ## Finished copy_installation_files
04-14 19:59 DEBUG  TaskList: ## Running get_iso...
04-14 19:59 DEBUG  CommonBackend: Searching for local CD
04-14 19:59 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl4F8B.tmp\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 19:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 19:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 19:59 DEBUG  CommonBackend: Searching for local ISO
04-14 19:59 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 19:59 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 19:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
04-14 19:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
04-14 19:59 DEBUG  Distro: wrong version: 10.10 != 10.04.1
04-14 19:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-14 19:59 DEBUG  TaskList: New task get_metalink
04-14 19:59 DEBUG  TaskList: ### Running get_metalink...
04-14 19:59 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink > C:\ubuntu\install
04-14 19:59 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
04-14 19:59 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink > C:\ubuntu\install
04-14 19:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink, basename=lucid-desktop-amd64.metalink, length=1010, text=None
04-14 19:59 DEBUG  downloader: download finished (read 1010 bytes)
04-14 19:59 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink > C:\ubuntu\install
04-14 19:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=257, text=None
04-14 19:59 DEBUG  downloader: download finished (read 257 bytes)
04-14 19:59 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-14 19:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-14 19:59 DEBUG  downloader: download finished (read 198 bytes)
04-14 19:59 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-14 19:59 INFO   saplog: Checking block bindings..
04-14 19:59 INFO   saplog: Key verified successfully.
04-14 19:59 DEBUG  CommonBackend: metalink md5sums:
cda012b82a15cb5bbd6c44f1920dfd1c  natty-desktop-amd64+mac.metalink
968f50ad56a3255b13dab817133b26aa  natty-desktop-amd64.metalink
a3d5d97d438ca4e3b4080cb5181890f4  natty-desktop-i386.metalink
668910f8d3467dfc0c87f96b77ee8f74  natty-desktop-powerpc.metalink

04-14 19:59 ERROR  CommonBackend: The md5 of the metalink does match
04-14 19:59 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
04-14 19:59 DEBUG  TaskList: ### Finished get_metalink
04-14 19:59 DEBUG  TaskList: New task download
04-14 19:59 DEBUG  TaskList: ### Running download...
04-14 19:59 DEBUG  btdownloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso.torrent > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 19:59 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
04-14 19:59 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
04-14 19:59 DEBUG  TaskList: ### Finished download
04-14 19:59 DEBUG  TaskList: New task download
04-14 19:59 DEBUG  TaskList: ### Running download...
04-14 19:59 DEBUG  downloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 19:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso, basename=lucid-desktop-amd64.iso, length=721129472, text=None
04-14 20:19 DEBUG  TaskList: ### Finished download
04-14 20:19 DEBUG  downloader: download finished (read 721129472 bytes)
04-14 20:19 DEBUG  TaskList: New task check_iso
04-14 20:19 DEBUG  TaskList: ### Running check_iso...
04-14 20:19 DEBUG  CommonBackend: Checking C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:19 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:19 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:19 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
04-14 20:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
04-14 20:19 DEBUG  Distro: wrong version: 10.04.2 != 10.04.1
04-14 20:19 DEBUG  TaskList: ### Finished check_iso
04-14 20:19 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-14 20:19 DEBUG  TaskList: # Cancelling tasklist
04-14 20:19 DEBUG  TaskList: # Finished tasklist
04-14 20:19 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-14 20:29 INFO   root: === wubi 10.04.1 rev190 ===
04-14 20:29 DEBUG  root: Logfile is c:\users\brandon\appdata\local\temp\wubi-10.04.1-rev190.log
04-14 20:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brandon\\Downloads\\wubi.exe"']
04-14 20:29 DEBUG  CommonBackend: data_dir=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\data
04-14 20:29 DEBUG  WindowsBackend: 7z=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\bin\7z.exe
04-14 20:29 DEBUG  CommonBackend: Fetching basic info...
04-14 20:29 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 20:29 DEBUG  CommonBackend: platform=win32
04-14 20:29 DEBUG  CommonBackend: osname=nt
04-14 20:29 DEBUG  CommonBackend: language=en_US
04-14 20:29 DEBUG  CommonBackend: encoding=cp1252
04-14 20:29 DEBUG  WindowsBackend: arch=amd64
04-14 20:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\data\isolist.ini
04-14 20:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 20:29 DEBUG  WindowsBackend: Fetching host info...
04-14 20:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 20:29 DEBUG  WindowsBackend: windows version=vista
04-14 20:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 20:29 DEBUG  WindowsBackend: windows_sp=None
04-14 20:29 DEBUG  WindowsBackend: windows_build=7600
04-14 20:29 DEBUG  WindowsBackend: gmt=-7
04-14 20:29 DEBUG  WindowsBackend: country=US
04-14 20:29 DEBUG  WindowsBackend: timezone=America/Denver
04-14 20:29 DEBUG  WindowsBackend: windows_username=Brandon
04-14 20:29 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 20:29 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 20:29 DEBUG  WindowsBackend: windows_language_code=1033
04-14 20:29 DEBUG  WindowsBackend: windows_language=English
04-14 20:29 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 20:29 DEBUG  WindowsBackend: bootloader=vista
04-14 20:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195998.0 mb free ntfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(C: hd 195998.0 mb free ntfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 20:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-14 20:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-14 20:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-14 20:29 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 20:29 DEBUG  WindowsBackend: keyboard_layout=us
04-14 20:29 DEBUG  WindowsBackend: keyboard_variant=
04-14 20:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-14 20:29 DEBUG  CommonBackend: locale=en_US.UTF-8
04-14 20:29 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 20:29 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 20:29 DEBUG  CommonBackend: Searching for local CDs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 INFO   root: Already installed, running the uninstaller...
04-14 20:29 INFO   root: Running the uninstaller...
04-14 20:29 INFO   CommonBackend: This is the uninstaller running
04-14 20:29 DEBUG  WindowsFrontend: __init__...
04-14 20:29 DEBUG  WindowsFrontend: on_init...
04-14 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\translations, languages=['en_US', 'en']
04-14 20:29 INFO   root: Received settings
04-14 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\translations, languages=['en_US', 'en']
04-14 20:29 DEBUG  TaskList: # Running tasklist...
04-14 20:29 DEBUG  TaskList: ## Running Backup ISO...
04-14 20:29 DEBUG  TaskList: ## Finished Backup ISO
04-14 20:29 DEBUG  TaskList: ## Running Remove bootloader entry...
04-14 20:29 DEBUG  WindowsBackend: Could not find bcd id
04-14 20:29 DEBUG  WindowsBackend: undo_bootini C:
04-14 20:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195998.0 mb free ntfs)
04-14 20:29 DEBUG  WindowsBackend: undo_bootini D:
04-14 20:29 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2072.0234375 mb free ntfs)
04-14 20:29 DEBUG  TaskList: ## Finished Remove bootloader entry
04-14 20:29 DEBUG  TaskList: ## Running Remove target dir...
04-14 20:29 DEBUG  CommonBackend: Deleting C:\ubuntu
04-14 20:29 DEBUG  TaskList: ## Finished Remove target dir
04-14 20:29 DEBUG  TaskList: ## Running Remove registry key...
04-14 20:29 DEBUG  TaskList: ## Finished Remove registry key
04-14 20:29 DEBUG  TaskList: # Finished tasklist
04-14 20:29 INFO   root: Almost finished uninstalling
04-14 20:29 INFO   root: Finished uninstallation
04-14 20:29 DEBUG  CommonBackend: Fetching basic info...
04-14 20:29 DEBUG  CommonBackend: original_exe=C:\Users\Brandon\Downloads\wubi.exe
04-14 20:29 DEBUG  CommonBackend: platform=win32
04-14 20:29 DEBUG  CommonBackend: osname=nt
04-14 20:29 DEBUG  WindowsBackend: arch=amd64
04-14 20:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\data\isolist.ini
04-14 20:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-14 20:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-14 20:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-14 20:29 DEBUG  WindowsBackend: Fetching host info...
04-14 20:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-14 20:29 DEBUG  WindowsBackend: windows version=vista
04-14 20:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-14 20:29 DEBUG  WindowsBackend: windows_sp=None
04-14 20:29 DEBUG  WindowsBackend: windows_build=7600
04-14 20:29 DEBUG  WindowsBackend: gmt=-7
04-14 20:29 DEBUG  WindowsBackend: country=US
04-14 20:29 DEBUG  WindowsBackend: timezone=America/Denver
04-14 20:29 DEBUG  WindowsBackend: windows_username=Brandon
04-14 20:29 DEBUG  WindowsBackend: user_full_name=Brandon
04-14 20:29 DEBUG  WindowsBackend: user_directory=C:\Users\Brandon
04-14 20:29 DEBUG  WindowsBackend: windows_language_code=1033
04-14 20:29 DEBUG  WindowsBackend: windows_language=English
04-14 20:29 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II X2 215 Processor
04-14 20:29 DEBUG  WindowsBackend: bootloader=vista
04-14 20:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195993.082031 mb free ntfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(C: hd 195993.082031 mb free ntfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2072.0234375 mb free ntfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-14 20:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-14 20:29 DEBUG  WindowsBackend: uninstaller_path=None
04-14 20:29 DEBUG  WindowsBackend: previous_target_dir=None
04-14 20:29 DEBUG  WindowsBackend: previous_distro_name=None
04-14 20:29 DEBUG  WindowsBackend: keyboard_id=67699721
04-14 20:29 DEBUG  WindowsBackend: keyboard_layout=us
04-14 20:29 DEBUG  WindowsBackend: keyboard_variant=
04-14 20:29 DEBUG  WindowsBackend: total_memory_mb=2942.4921875
04-14 20:29 DEBUG  CommonBackend: Searching ISOs on USB devices
04-14 20:29 DEBUG  CommonBackend: Searching for local CDs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 INFO   root: Running the installer...
04-14 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\translations, languages=['en_US', 'en']
04-14 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\translations, languages=['en_US', 'en']
04-14 20:29 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brandon
04-14 20:29 INFO   root: Received settings
04-14 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\translations, languages=['en_US', 'en']
04-14 20:29 DEBUG  TaskList: # Running tasklist...
04-14 20:29 DEBUG  TaskList: ## Running select_target_dir...
04-14 20:29 INFO   WindowsBackend: Installing into C:\ubuntu
04-14 20:29 DEBUG  TaskList: ## Finished select_target_dir
04-14 20:29 DEBUG  TaskList: ## Running create_dir_structure...
04-14 20:29 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-14 20:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-14 20:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-14 20:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-14 20:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-14 20:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-14 20:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-14 20:29 DEBUG  TaskList: ## Finished create_dir_structure
04-14 20:29 DEBUG  TaskList: ## Running uncompress_target_dir...
04-14 20:29 DEBUG  TaskList: ## Finished uncompress_target_dir
04-14 20:29 DEBUG  TaskList: ## Running create_uninstaller...
04-14 20:29 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brandon\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-14 20:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-14 20:29 DEBUG  TaskList: ## Finished create_uninstaller
04-14 20:29 DEBUG  TaskList: ## Running copy_installation_files...
04-14 20:29 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-14 20:29 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\winboot -> C:\ubuntu\winboot
04-14 20:29 DEBUG  WindowsBackend: Copying C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-14 20:29 DEBUG  TaskList: ## Finished copy_installation_files
04-14 20:29 DEBUG  TaskList: ## Running get_iso...
04-14 20:29 DEBUG  CommonBackend: Searching for local CD
04-14 20:29 DEBUG  Distro:   checking whether C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain C:\Users\Brandon\AppData\Local\Temp\pyl534D.tmp\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-14 20:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-14 20:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-14 20:29 DEBUG  CommonBackend: Searching for local ISO
04-14 20:29 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 20:29 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Brandon\Downloads\ubuntu-10.10-desktop-amd64.iso
04-14 20:29 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
04-14 20:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
04-14 20:29 DEBUG  Distro: wrong version: 10.10 != 10.04.1
04-14 20:29 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-14 20:29 DEBUG  TaskList: New task get_metalink
04-14 20:29 DEBUG  TaskList: ### Running get_metalink...
04-14 20:29 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink > C:\ubuntu\install
04-14 20:29 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
04-14 20:29 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink > C:\ubuntu\install
04-14 20:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink, basename=lucid-desktop-amd64.metalink, length=1010, text=None
04-14 20:29 DEBUG  downloader: download finished (read 1010 bytes)
04-14 20:29 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink > C:\ubuntu\install
04-14 20:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=257, text=None
04-14 20:29 DEBUG  downloader: download finished (read 257 bytes)
04-14 20:29 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-14 20:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-14 20:29 DEBUG  downloader: download finished (read 198 bytes)
04-14 20:29 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-14 20:29 INFO   saplog: Checking block bindings..
04-14 20:29 INFO   saplog: Key verified successfully.
04-14 20:29 DEBUG  CommonBackend: metalink md5sums:
cda012b82a15cb5bbd6c44f1920dfd1c  natty-desktop-amd64+mac.metalink
968f50ad56a3255b13dab817133b26aa  natty-desktop-amd64.metalink
a3d5d97d438ca4e3b4080cb5181890f4  natty-desktop-i386.metalink
668910f8d3467dfc0c87f96b77ee8f74  natty-desktop-powerpc.metalink

04-14 20:29 ERROR  CommonBackend: The md5 of the metalink does match
04-14 20:29 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
04-14 20:29 DEBUG  TaskList: ### Finished get_metalink
04-14 20:29 DEBUG  TaskList: New task download
04-14 20:29 DEBUG  TaskList: ### Running download...
04-14 20:29 DEBUG  btdownloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso.torrent > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:29 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
04-14 20:29 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
04-14 20:29 DEBUG  TaskList: ### Finished download
04-14 20:29 DEBUG  TaskList: New task download
04-14 20:29 DEBUG  TaskList: ### Running download...
04-14 20:29 DEBUG  downloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso > C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso, basename=lucid-desktop-amd64.iso, length=721129472, text=None
04-14 20:56 DEBUG  TaskList: ### Finished download
04-14 20:56 DEBUG  downloader: download finished (read 721129472 bytes)
04-14 20:56 DEBUG  TaskList: New task check_iso
04-14 20:56 DEBUG  TaskList: ### Running check_iso...
04-14 20:56 DEBUG  CommonBackend: Checking C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:56 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:56 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\lucid-desktop-amd64.iso
04-14 20:56 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
04-14 20:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
04-14 20:56 DEBUG  Distro: wrong version: 10.04.2 != 10.04.1
04-14 20:56 DEBUG  TaskList: ### Finished check_iso
04-14 20:56 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
04-14 20:56 DEBUG  TaskList: # Cancelling tasklist
04-14 20:56 DEBUG  TaskList: # Finished tasklist
04-14 20:56 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
```

Any help is greatly appreciated! I'm really anxious to try this out!

---

### Post by 3rdalbum on 2011-04-15
The Wubi program is trying to find "Lucid Daily Live", which would be a daily build of Ubuntu 10.04 (an old version).

A better idea would be to download the ISO disc image from the Ubuntu website, and burn it to CD using the "Burn image to disc" function of your burning software. Then run the Wubi program *that's in the topmost directory of the CD* or, if you want to have Ubuntu on your computer as an independent operating system, boot up your computer from the CD and follow the prompts.

---

### Post by bcbc on 2011-04-15
The 10.04.1 wubi.exe doesn't work anymore. If you got it from releases.ubuntu.com/lucid there has been a bug registered to get that wubi.exe updated to 10.04.2 - yet to be fixed.

The workaround is to do as suggested by 3rdalbum. Or you could download a 10.04.2 version from [http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe)

---

### Post by Dualshotty on 2011-04-15
> **bcbc said:**
> The 10.04.1 wubi.exe doesn't work anymore. If you got it from releases.ubuntu.com/lucid there has been a bug registered to get that wubi.exe updated to 10.04.2 - yet to be fixed.

The workaround is to do as suggested by 3rdalbum. Or you could download a 10.04.2 version from [http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe)

Okay! I'm trying the 10.04.2 version you gave me. Thanks to both of you for all the help! :)

---

### Post by DarrenJParker on 2011-04-15
Hey

I am in a similar situation to DualShotty, in that I am a beginner trying to install ubuntu with wubi.exe.

I first tried this with 10.04.1 wubi.exe, and it did not work so I tried the 10.04.2 version from the link provided by bcbc.

Unfortunately this did not work either as I got an error message saying i was denied permission and the following log file

```

04-15 14:32 INFO   root: === wubi 10.04.2 rev191 ===
04-15 14:32 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-10.04.2-rev191.log
04-15 14:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Darren\\Downloads\\wubi-r191.exe"']
04-15 14:32 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\data
04-15 14:32 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\bin\7z.exe
04-15 14:32 DEBUG  CommonBackend: Fetching basic info...
04-15 14:32 DEBUG  CommonBackend: original_exe=C:\Users\Darren\Downloads\wubi-r191.exe
04-15 14:32 DEBUG  CommonBackend: platform=win32
04-15 14:32 DEBUG  CommonBackend: osname=nt
04-15 14:32 DEBUG  CommonBackend: language=en_GB
04-15 14:32 DEBUG  CommonBackend: encoding=cp1252
04-15 14:32 DEBUG  WindowsBackend: arch=amd64
04-15 14:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\data\isolist.ini
04-15 14:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-15 14:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-15 14:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-15 14:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-15 14:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-15 14:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-15 14:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-15 14:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-15 14:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-15 14:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-15 14:32 DEBUG  WindowsBackend: Fetching host info...
04-15 14:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-15 14:32 DEBUG  WindowsBackend: windows version=vista
04-15 14:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-15 14:32 DEBUG  WindowsBackend: windows_sp=None
04-15 14:32 DEBUG  WindowsBackend: windows_build=7600
04-15 14:32 DEBUG  WindowsBackend: gmt=0
04-15 14:32 DEBUG  WindowsBackend: country=GB
04-15 14:32 DEBUG  WindowsBackend: timezone=Europe/London
04-15 14:32 DEBUG  WindowsBackend: windows_username=Darren
04-15 14:32 DEBUG  WindowsBackend: user_full_name=Darren
04-15 14:32 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-15 14:32 DEBUG  WindowsBackend: windows_language_code=1033
04-15 14:32 DEBUG  WindowsBackend: windows_language=English
04-15 14:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
04-15 14:32 DEBUG  WindowsBackend: bootloader=vista
04-15 14:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 377694.226563 mb free ntfs)
04-15 14:32 DEBUG  WindowsBackend: drive=Drive(C: hd 377694.226563 mb free ntfs)
04-15 14:32 DEBUG  WindowsBackend: drive=Drive(D: hd 2821.15625 mb free ntfs)
04-15 14:32 DEBUG  WindowsBackend: drive=Drive(E: hd 92.435546875 mb free fat32)
04-15 14:32 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-15 14:32 DEBUG  WindowsBackend: uninstaller_path=None
04-15 14:32 DEBUG  WindowsBackend: previous_target_dir=None
04-15 14:32 DEBUG  WindowsBackend: previous_distro_name=None
04-15 14:32 DEBUG  WindowsBackend: keyboard_id=-268367863
04-15 14:32 DEBUG  WindowsBackend: keyboard_layout=gb
04-15 14:32 DEBUG  WindowsBackend: keyboard_variant=
04-15 14:32 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
04-15 14:32 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-15 14:32 DEBUG  WindowsBackend: total_memory_mb=3894.8671875
04-15 14:32 DEBUG  CommonBackend: Searching ISOs on USB devices
04-15 14:32 DEBUG  CommonBackend: Searching for local CDs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Ubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Kubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF872.tmp is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:32 INFO   root: Running the installer...
04-15 14:32 DEBUG  WindowsFrontend: __init__...
04-15 14:32 DEBUG  WindowsFrontend: on_init...
04-15 14:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\translations, languages=['en_GB', 'en']
04-15 14:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\translations, languages=['en_GB', 'en']
04-15 14:32 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=darren
04-15 14:32 INFO   root: Received settings
04-15 14:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylF872.tmp\translations, languages=['en_GB', 'en']
04-15 14:32 DEBUG  TaskList: # Running tasklist...
04-15 14:32 DEBUG  TaskList: ## Running select_target_dir...
04-15 14:32 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-15 14:32 DEBUG  TaskList: # Cancelling tasklist
04-15 14:32 DEBUG  TaskList: # Finished tasklist
04-15 14:32 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-15 14:33 INFO   root: === wubi 10.04.2 rev191 ===
04-15 14:33 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-10.04.2-rev191.log
04-15 14:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Darren\\Downloads\\wubi-r191.exe"']
04-15 14:33 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\data
04-15 14:33 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\bin\7z.exe
04-15 14:33 DEBUG  CommonBackend: Fetching basic info...
04-15 14:33 DEBUG  CommonBackend: original_exe=C:\Users\Darren\Downloads\wubi-r191.exe
04-15 14:33 DEBUG  CommonBackend: platform=win32
04-15 14:33 DEBUG  CommonBackend: osname=nt
04-15 14:33 DEBUG  CommonBackend: language=en_GB
04-15 14:33 DEBUG  CommonBackend: encoding=cp1252
04-15 14:33 DEBUG  WindowsBackend: arch=amd64
04-15 14:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\data\isolist.ini
04-15 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-15 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-15 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-15 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-15 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-15 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-15 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-15 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-15 14:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-15 14:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-15 14:33 DEBUG  WindowsBackend: Fetching host info...
04-15 14:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-15 14:33 DEBUG  WindowsBackend: windows version=vista
04-15 14:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-15 14:33 DEBUG  WindowsBackend: windows_sp=None
04-15 14:33 DEBUG  WindowsBackend: windows_build=7600
04-15 14:33 DEBUG  WindowsBackend: gmt=0
04-15 14:33 DEBUG  WindowsBackend: country=GB
04-15 14:33 DEBUG  WindowsBackend: timezone=Europe/London
04-15 14:33 DEBUG  WindowsBackend: windows_username=Darren
04-15 14:33 DEBUG  WindowsBackend: user_full_name=Darren
04-15 14:33 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-15 14:33 DEBUG  WindowsBackend: windows_language_code=1033
04-15 14:33 DEBUG  WindowsBackend: windows_language=English
04-15 14:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
04-15 14:33 DEBUG  WindowsBackend: bootloader=vista
04-15 14:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 377694.109375 mb free ntfs)
04-15 14:33 DEBUG  WindowsBackend: drive=Drive(C: hd 377694.109375 mb free ntfs)
04-15 14:33 DEBUG  WindowsBackend: drive=Drive(D: hd 2821.15625 mb free ntfs)
04-15 14:33 DEBUG  WindowsBackend: drive=Drive(E: hd 92.435546875 mb free fat32)
04-15 14:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-15 14:33 DEBUG  WindowsBackend: uninstaller_path=None
04-15 14:33 DEBUG  WindowsBackend: previous_target_dir=None
04-15 14:33 DEBUG  WindowsBackend: previous_distro_name=None
04-15 14:33 DEBUG  WindowsBackend: keyboard_id=-268367863
04-15 14:33 DEBUG  WindowsBackend: keyboard_layout=gb
04-15 14:33 DEBUG  WindowsBackend: keyboard_variant=
04-15 14:33 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
04-15 14:33 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-15 14:33 DEBUG  WindowsBackend: total_memory_mb=3894.8671875
04-15 14:33 DEBUG  CommonBackend: Searching ISOs on USB devices
04-15 14:33 DEBUG  CommonBackend: Searching for local CDs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Ubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Kubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl954.tmp is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:33 INFO   root: Running the installer...
04-15 14:33 DEBUG  WindowsFrontend: __init__...
04-15 14:33 DEBUG  WindowsFrontend: on_init...
04-15 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\translations, languages=['en_GB', 'en']
04-15 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\translations, languages=['en_GB', 'en']
04-15 14:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=darren
04-15 14:33 INFO   root: Received settings
04-15 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl954.tmp\translations, languages=['en_GB', 'en']
04-15 14:33 DEBUG  TaskList: # Running tasklist...
04-15 14:33 DEBUG  TaskList: ## Running select_target_dir...
04-15 14:33 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-15 14:33 DEBUG  TaskList: # Cancelling tasklist
04-15 14:33 DEBUG  TaskList: # Finished tasklist
04-15 14:33 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-15 14:41 INFO   root: === wubi 10.04.2 rev191 ===
04-15 14:41 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-10.04.2-rev191.log
04-15 14:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Darren\\Downloads\\wubi-r191.exe"']
04-15 14:41 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\data
04-15 14:41 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\bin\7z.exe
04-15 14:41 DEBUG  CommonBackend: Fetching basic info...
04-15 14:41 DEBUG  CommonBackend: original_exe=C:\Users\Darren\Downloads\wubi-r191.exe
04-15 14:41 DEBUG  CommonBackend: platform=win32
04-15 14:41 DEBUG  CommonBackend: osname=nt
04-15 14:41 DEBUG  CommonBackend: language=en_GB
04-15 14:41 DEBUG  CommonBackend: encoding=cp1252
04-15 14:41 DEBUG  WindowsBackend: arch=amd64
04-15 14:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\data\isolist.ini
04-15 14:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-15 14:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-15 14:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-15 14:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-15 14:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-15 14:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-15 14:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-15 14:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-15 14:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-15 14:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-15 14:41 DEBUG  WindowsBackend: Fetching host info...
04-15 14:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-15 14:41 DEBUG  WindowsBackend: windows version=vista
04-15 14:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-15 14:41 DEBUG  WindowsBackend: windows_sp=None
04-15 14:41 DEBUG  WindowsBackend: windows_build=7600
04-15 14:41 DEBUG  WindowsBackend: gmt=0
04-15 14:41 DEBUG  WindowsBackend: country=GB
04-15 14:41 DEBUG  WindowsBackend: timezone=Europe/London
04-15 14:41 DEBUG  WindowsBackend: windows_username=Darren
04-15 14:41 DEBUG  WindowsBackend: user_full_name=Darren
04-15 14:41 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-15 14:41 DEBUG  WindowsBackend: windows_language_code=1033
04-15 14:41 DEBUG  WindowsBackend: windows_language=English
04-15 14:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
04-15 14:41 DEBUG  WindowsBackend: bootloader=vista
04-15 14:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 377711.308594 mb free ntfs)
04-15 14:41 DEBUG  WindowsBackend: drive=Drive(C: hd 377711.308594 mb free ntfs)
04-15 14:41 DEBUG  WindowsBackend: drive=Drive(D: hd 2821.15625 mb free ntfs)
04-15 14:41 DEBUG  WindowsBackend: drive=Drive(E: hd 92.435546875 mb free fat32)
04-15 14:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-15 14:41 DEBUG  WindowsBackend: uninstaller_path=None
04-15 14:41 DEBUG  WindowsBackend: previous_target_dir=None
04-15 14:41 DEBUG  WindowsBackend: previous_distro_name=None
04-15 14:41 DEBUG  WindowsBackend: keyboard_id=-268367863
04-15 14:41 DEBUG  WindowsBackend: keyboard_layout=gb
04-15 14:41 DEBUG  WindowsBackend: keyboard_variant=
04-15 14:41 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
04-15 14:41 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-15 14:41 DEBUG  WindowsBackend: total_memory_mb=3894.8671875
04-15 14:41 DEBUG  CommonBackend: Searching ISOs on USB devices
04-15 14:41 DEBUG  CommonBackend: Searching for local CDs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Ubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Kubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:41 INFO   root: Running the installer...
04-15 14:41 DEBUG  WindowsFrontend: __init__...
04-15 14:41 DEBUG  WindowsFrontend: on_init...
04-15 14:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\translations, languages=['en_GB', 'en']
04-15 14:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\translations, languages=['en_GB', 'en']
04-15 14:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=darren
04-15 14:42 INFO   root: Received settings
04-15 14:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylF2A7.tmp\translations, languages=['en_GB', 'en']
04-15 14:42 DEBUG  TaskList: # Running tasklist...
04-15 14:42 DEBUG  TaskList: ## Running select_target_dir...
04-15 14:42 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-15 14:42 DEBUG  TaskList: # Cancelling tasklist
04-15 14:42 DEBUG  TaskList: # Finished tasklist
04-15 14:42 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-15 14:44 INFO   root: === wubi 10.04.2 rev191 ===
04-15 14:44 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-10.04.2-rev191.log
04-15 14:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Darren\\Downloads\\wubi-r191.exe"']
04-15 14:44 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\data
04-15 14:44 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\bin\7z.exe
04-15 14:44 DEBUG  CommonBackend: Fetching basic info...
04-15 14:44 DEBUG  CommonBackend: original_exe=C:\Users\Darren\Downloads\wubi-r191.exe
04-15 14:44 DEBUG  CommonBackend: platform=win32
04-15 14:44 DEBUG  CommonBackend: osname=nt
04-15 14:44 DEBUG  CommonBackend: language=en_GB
04-15 14:44 DEBUG  CommonBackend: encoding=cp1252
04-15 14:44 DEBUG  WindowsBackend: arch=amd64
04-15 14:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\data\isolist.ini
04-15 14:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-15 14:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-15 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-15 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-15 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-15 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-15 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-15 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-15 14:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-15 14:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-15 14:44 DEBUG  WindowsBackend: Fetching host info...
04-15 14:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-15 14:44 DEBUG  WindowsBackend: windows version=vista
04-15 14:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-15 14:44 DEBUG  WindowsBackend: windows_sp=None
04-15 14:44 DEBUG  WindowsBackend: windows_build=7600
04-15 14:44 DEBUG  WindowsBackend: gmt=0
04-15 14:44 DEBUG  WindowsBackend: country=GB
04-15 14:44 DEBUG  WindowsBackend: timezone=Europe/London
04-15 14:44 DEBUG  WindowsBackend: windows_username=Darren
04-15 14:44 DEBUG  WindowsBackend: user_full_name=Darren
04-15 14:44 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-15 14:44 DEBUG  WindowsBackend: windows_language_code=1033
04-15 14:44 DEBUG  WindowsBackend: windows_language=English
04-15 14:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
04-15 14:44 DEBUG  WindowsBackend: bootloader=vista
04-15 14:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 377710.976563 mb free ntfs)
04-15 14:44 DEBUG  WindowsBackend: drive=Drive(C: hd 377710.976563 mb free ntfs)
04-15 14:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2821.15625 mb free ntfs)
04-15 14:44 DEBUG  WindowsBackend: drive=Drive(E: hd 92.435546875 mb free fat32)
04-15 14:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-15 14:44 DEBUG  WindowsBackend: uninstaller_path=None
04-15 14:44 DEBUG  WindowsBackend: previous_target_dir=None
04-15 14:44 DEBUG  WindowsBackend: previous_distro_name=None
04-15 14:44 DEBUG  WindowsBackend: keyboard_id=-268367863
04-15 14:44 DEBUG  WindowsBackend: keyboard_layout=gb
04-15 14:44 DEBUG  WindowsBackend: keyboard_variant=
04-15 14:44 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
04-15 14:44 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-15 14:44 DEBUG  WindowsBackend: total_memory_mb=3894.8671875
04-15 14:44 DEBUG  CommonBackend: Searching ISOs on USB devices
04-15 14:44 DEBUG  CommonBackend: Searching for local CDs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Ubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Kubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 INFO   root: Running the installer...
04-15 14:44 DEBUG  WindowsFrontend: __init__...
04-15 14:44 DEBUG  WindowsFrontend: on_init...
04-15 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\translations, languages=['en_GB', 'en']
04-15 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\translations, languages=['en_GB', 'en']
04-15 14:44 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=darren
04-15 14:44 INFO   root: Received settings
04-15 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\translations, languages=['en_GB', 'en']
04-15 14:44 DEBUG  TaskList: # Running tasklist...
04-15 14:44 DEBUG  TaskList: ## Running select_target_dir...
04-15 14:44 INFO   WindowsBackend: Installing into C:\ubuntu
04-15 14:44 DEBUG  TaskList: ## Finished select_target_dir
04-15 14:44 DEBUG  TaskList: ## Running create_dir_structure...
04-15 14:44 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-15 14:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-15 14:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-15 14:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-15 14:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-15 14:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-15 14:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-15 14:44 DEBUG  TaskList: ## Finished create_dir_structure
04-15 14:44 DEBUG  TaskList: ## Running uncompress_target_dir...
04-15 14:44 DEBUG  TaskList: ## Finished uncompress_target_dir
04-15 14:44 DEBUG  TaskList: ## Running create_uninstaller...
04-15 14:44 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Darren\Downloads\wubi-r191.exe -> C:\ubuntu\uninstall-wubi.exe
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-15 14:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-15 14:44 DEBUG  TaskList: ## Finished create_uninstaller
04-15 14:44 DEBUG  TaskList: ## Running copy_installation_files...
04-15 14:44 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-15 14:44 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\winboot -> C:\ubuntu\winboot
04-15 14:44 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-15 14:44 DEBUG  TaskList: ## Finished copy_installation_files
04-15 14:44 DEBUG  TaskList: ## Running get_iso...
04-15 14:44 DEBUG  CommonBackend: Searching for local CD
04-15 14:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC36D.tmp\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 14:44 DEBUG  CommonBackend: Searching for local ISO
04-15 14:44 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-15 14:44 DEBUG  TaskList: New task get_metalink
04-15 14:44 DEBUG  TaskList: ### Running get_metalink...
04-15 14:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > C:\ubuntu\install
04-15 14:44 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
04-15 14:44 DEBUG  downloader: download finished (read 39020 bytes)
04-15 14:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > C:\ubuntu\install
04-15 14:44 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
04-15 14:44 DEBUG  downloader: download finished (read 651 bytes)
04-15 14:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-15 14:44 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-15 14:44 DEBUG  downloader: download finished (read 198 bytes)
04-15 14:44 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-15 14:44 INFO   saplog: Checking block bindings..
04-15 14:44 INFO   saplog: Key verified successfully.
04-15 14:44 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink

04-15 14:44 DEBUG  TaskList: ### Finished get_metalink
04-15 14:44 DEBUG  TaskList: New task download
04-15 14:44 DEBUG  TaskList: ### Running download...
04-15 14:44 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.iso
04-15 15:45 ERROR  TaskList: Traceback (most recent call last):
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


04-15 15:45 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
04-15 15:45 DEBUG  TaskList: ### Finished download
04-15 15:45 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
04-15 15:45 DEBUG  TaskList: # Cancelling tasklist
04-15 15:45 DEBUG  TaskList: # Finished tasklist
04-15 15:45 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
04-15 15:46 INFO   root: === wubi 10.04.2 rev191 ===
04-15 15:46 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-10.04.2-rev191.log
04-15 15:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-15 15:46 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\data
04-15 15:46 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\bin\7z.exe
04-15 15:46 DEBUG  CommonBackend: Fetching basic info...
04-15 15:46 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-15 15:46 DEBUG  CommonBackend: platform=win32
04-15 15:46 DEBUG  CommonBackend: osname=nt
04-15 15:46 DEBUG  CommonBackend: language=en_GB
04-15 15:46 DEBUG  CommonBackend: encoding=cp1252
04-15 15:46 DEBUG  WindowsBackend: arch=amd64
04-15 15:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\data\isolist.ini
04-15 15:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-15 15:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-15 15:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-15 15:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-15 15:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-15 15:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-15 15:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-15 15:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-15 15:46 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-15 15:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-15 15:46 DEBUG  WindowsBackend: Fetching host info...
04-15 15:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-15 15:46 DEBUG  WindowsBackend: windows version=vista
04-15 15:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-15 15:46 DEBUG  WindowsBackend: windows_sp=None
04-15 15:46 DEBUG  WindowsBackend: windows_build=7600
04-15 15:46 DEBUG  WindowsBackend: gmt=0
04-15 15:46 DEBUG  WindowsBackend: country=GB
04-15 15:46 DEBUG  WindowsBackend: timezone=Europe/London
04-15 15:46 DEBUG  WindowsBackend: windows_username=Darren
04-15 15:46 DEBUG  WindowsBackend: user_full_name=Darren
04-15 15:46 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-15 15:46 DEBUG  WindowsBackend: windows_language_code=1033
04-15 15:46 DEBUG  WindowsBackend: windows_language=English
04-15 15:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
04-15 15:46 DEBUG  WindowsBackend: bootloader=vista
04-15 15:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 377514.625 mb free ntfs)
04-15 15:46 DEBUG  WindowsBackend: drive=Drive(C: hd 377514.625 mb free ntfs)
04-15 15:46 DEBUG  WindowsBackend: drive=Drive(D: hd 2821.15625 mb free ntfs)
04-15 15:46 DEBUG  WindowsBackend: drive=Drive(E: hd 92.435546875 mb free fat32)
04-15 15:46 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-15 15:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-15 15:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-15 15:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-15 15:46 DEBUG  WindowsBackend: keyboard_id=-268367863
04-15 15:46 DEBUG  WindowsBackend: keyboard_layout=gb
04-15 15:46 DEBUG  WindowsBackend: keyboard_variant=
04-15 15:46 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
04-15 15:46 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-15 15:46 DEBUG  WindowsBackend: total_memory_mb=3894.8671875
04-15 15:46 DEBUG  CommonBackend: Searching ISOs on USB devices
04-15 15:46 DEBUG  CommonBackend: Searching for local CDs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Ubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Kubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 15:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:46 INFO   root: Running the uninstaller...
04-15 15:46 INFO   CommonBackend: This is the uninstaller running
04-15 15:46 DEBUG  WindowsFrontend: __init__...
04-15 15:46 DEBUG  WindowsFrontend: on_init...
04-15 15:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylA38F.tmp\translations, languages=['en_GB', 'en']
04-15 15:47 INFO   WindowsFrontend: Operation cancelled
04-15 15:47 DEBUG  WindowsFrontend: frontend.quit
04-15 15:47 DEBUG  WindowsFrontend: frontend.on_quit
04-15 15:47 DEBUG  root: application.on_quit
04-15 15:47 INFO   root: sys.exit
04-15 15:47 INFO   root: === wubi 10.04.2 rev191 ===
04-15 15:47 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-10.04.2-rev191.log
04-15 15:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-15 15:47 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\data
04-15 15:47 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\bin\7z.exe
04-15 15:47 DEBUG  CommonBackend: Fetching basic info...
04-15 15:47 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-15 15:47 DEBUG  CommonBackend: platform=win32
04-15 15:47 DEBUG  CommonBackend: osname=nt
04-15 15:47 DEBUG  CommonBackend: language=en_GB
04-15 15:47 DEBUG  CommonBackend: encoding=cp1252
04-15 15:47 DEBUG  WindowsBackend: arch=amd64
04-15 15:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\data\isolist.ini
04-15 15:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-15 15:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-15 15:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-15 15:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-15 15:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-15 15:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-15 15:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-15 15:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-15 15:47 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-15 15:47 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-15 15:47 DEBUG  WindowsBackend: Fetching host info...
04-15 15:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-15 15:47 DEBUG  WindowsBackend: windows version=vista
04-15 15:47 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
04-15 15:47 DEBUG  WindowsBackend: windows_sp=None
04-15 15:47 DEBUG  WindowsBackend: windows_build=6000
04-15 15:47 DEBUG  WindowsBackend: gmt=0
04-15 15:47 DEBUG  WindowsBackend: country=GB
04-15 15:47 DEBUG  WindowsBackend: timezone=Europe/London
04-15 15:47 DEBUG  WindowsBackend: windows_username=Darren
04-15 15:47 DEBUG  WindowsBackend: user_full_name=Darren
04-15 15:47 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-15 15:47 DEBUG  WindowsBackend: windows_language_code=1033
04-15 15:47 DEBUG  WindowsBackend: windows_language=English
04-15 15:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
04-15 15:47 DEBUG  WindowsBackend: bootloader=vista
04-15 15:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 377514.042969 mb free ntfs)
04-15 15:47 DEBUG  WindowsBackend: drive=Drive(C: hd 377514.042969 mb free ntfs)
04-15 15:47 DEBUG  WindowsBackend: drive=Drive(D: hd 2821.15625 mb free ntfs)
04-15 15:47 DEBUG  WindowsBackend: drive=Drive(E: hd 92.435546875 mb free fat32)
04-15 15:47 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-15 15:47 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-15 15:47 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-15 15:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-15 15:47 DEBUG  WindowsBackend: keyboard_id=-268367863
04-15 15:47 DEBUG  WindowsBackend: keyboard_layout=gb
04-15 15:47 DEBUG  WindowsBackend: keyboard_variant=
04-15 15:47 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
04-15 15:47 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-15 15:47 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
04-15 15:47 DEBUG  CommonBackend: Searching ISOs on USB devices
04-15 15:47 DEBUG  CommonBackend: Searching for local CDs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Ubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Kubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:47 INFO   root: Running the uninstaller...
04-15 15:47 INFO   CommonBackend: This is the uninstaller running
04-15 15:47 DEBUG  WindowsFrontend: __init__...
04-15 15:47 DEBUG  WindowsFrontend: on_init...
04-15 15:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\translations, languages=['en_GB', 'en']
04-15 15:47 INFO   root: Received settings
04-15 15:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\translations, languages=['en_GB', 'en']
04-15 15:47 DEBUG  TaskList: # Running tasklist...
04-15 15:47 DEBUG  TaskList: ## Running Backup ISO...
04-15 15:47 DEBUG  TaskList: ## Finished Backup ISO
04-15 15:47 DEBUG  TaskList: ## Running Remove bootloader entry....
04-15 15:47 DEBUG  WindowsBackend: Could not find bcd id
04-15 15:47 DEBUG  WindowsBackend: undo_bootini C:
04-15 15:47 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 377514.042969 mb free ntfs)
04-15 15:47 DEBUG  WindowsBackend: undo_bootini D:
04-15 15:47 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2821.15625 mb free ntfs)
04-15 15:47 DEBUG  WindowsBackend: undo_bootini E:
04-15 15:47 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.435546875 mb free fat32)
04-15 15:47 DEBUG  TaskList: ## Finished Remove bootloader entry.
04-15 15:47 DEBUG  TaskList: ## Running Remove target dir....
04-15 15:47 DEBUG  CommonBackend: Deleting C:\ubuntu
04-15 15:47 DEBUG  TaskList: ## Finished Remove target dir.
04-15 15:47 DEBUG  TaskList: ## Running Remove registry key....
04-15 15:47 DEBUG  TaskList: ## Finished Remove registry key.
04-15 15:47 DEBUG  TaskList: # Finished tasklist
04-15 15:47 INFO   root: Almost finished uninstalling
04-15 15:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl67C8.tmp\translations, languages=['en_GB', 'en']
04-15 15:47 INFO   root: Finished uninstallation
04-15 15:47 DEBUG  root: application.quit
04-15 15:47 DEBUG  WindowsFrontend: frontend.quit
04-15 15:47 DEBUG  WindowsFrontend: frontend.on_quit
04-15 15:47 DEBUG  root: application.on_quit
04-15 15:47 INFO   root: sys.exit
04-15 15:53 INFO   root: === wubi 10.04.2 rev191 ===
04-15 15:53 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-10.04.2-rev191.log
04-15 15:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Darren\\Downloads\\wubi-r191 (2).exe"']
04-15 15:53 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\data
04-15 15:53 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\bin\7z.exe
04-15 15:53 DEBUG  CommonBackend: Fetching basic info...
04-15 15:53 DEBUG  CommonBackend: original_exe=C:\Users\Darren\Downloads\wubi-r191 (2).exe
04-15 15:53 DEBUG  CommonBackend: platform=win32
04-15 15:53 DEBUG  CommonBackend: osname=nt
04-15 15:53 DEBUG  CommonBackend: language=en_GB
04-15 15:53 DEBUG  CommonBackend: encoding=cp1252
04-15 15:53 DEBUG  WindowsBackend: arch=amd64
04-15 15:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\data\isolist.ini
04-15 15:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-15 15:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-15 15:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-15 15:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-15 15:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-15 15:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-15 15:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-15 15:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-15 15:53 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-15 15:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-15 15:53 DEBUG  WindowsBackend: Fetching host info...
04-15 15:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-15 15:53 DEBUG  WindowsBackend: windows version=vista
04-15 15:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-15 15:53 DEBUG  WindowsBackend: windows_sp=None
04-15 15:53 DEBUG  WindowsBackend: windows_build=7600
04-15 15:53 DEBUG  WindowsBackend: gmt=0
04-15 15:53 DEBUG  WindowsBackend: country=GB
04-15 15:53 DEBUG  WindowsBackend: timezone=Europe/London
04-15 15:53 DEBUG  WindowsBackend: windows_username=Darren
04-15 15:53 DEBUG  WindowsBackend: user_full_name=Darren
04-15 15:53 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-15 15:53 DEBUG  WindowsBackend: windows_language_code=1033
04-15 15:53 DEBUG  WindowsBackend: windows_language=English
04-15 15:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
04-15 15:53 DEBUG  WindowsBackend: bootloader=vista
04-15 15:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 377711.292969 mb free ntfs)
04-15 15:53 DEBUG  WindowsBackend: drive=Drive(C: hd 377711.292969 mb free ntfs)
04-15 15:53 DEBUG  WindowsBackend: drive=Drive(D: hd 2821.15625 mb free ntfs)
04-15 15:53 DEBUG  WindowsBackend: drive=Drive(E: hd 92.435546875 mb free fat32)
04-15 15:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-15 15:53 DEBUG  WindowsBackend: uninstaller_path=None
04-15 15:53 DEBUG  WindowsBackend: previous_target_dir=None
04-15 15:53 DEBUG  WindowsBackend: previous_distro_name=None
04-15 15:53 DEBUG  WindowsBackend: keyboard_id=-268367863
04-15 15:53 DEBUG  WindowsBackend: keyboard_layout=gb
04-15 15:53 DEBUG  WindowsBackend: keyboard_variant=
04-15 15:53 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
04-15 15:53 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-15 15:53 DEBUG  WindowsBackend: total_memory_mb=3894.8671875
04-15 15:53 DEBUG  CommonBackend: Searching ISOs on USB devices
04-15 15:53 DEBUG  CommonBackend: Searching for local CDs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Ubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Kubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 INFO   root: Running the installer...
04-15 15:53 DEBUG  WindowsFrontend: __init__...
04-15 15:53 DEBUG  WindowsFrontend: on_init...
04-15 15:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\translations, languages=['en_GB', 'en']
04-15 15:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\translations, languages=['en_GB', 'en']
04-15 15:53 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=darren
04-15 15:53 INFO   root: Received settings
04-15 15:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\translations, languages=['en_GB', 'en']
04-15 15:53 DEBUG  TaskList: # Running tasklist...
04-15 15:53 DEBUG  TaskList: ## Running select_target_dir...
04-15 15:53 INFO   WindowsBackend: Installing into C:\ubuntu
04-15 15:53 DEBUG  TaskList: ## Finished select_target_dir
04-15 15:53 DEBUG  TaskList: ## Running create_dir_structure...
04-15 15:53 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-15 15:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-15 15:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-15 15:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-15 15:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-15 15:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-15 15:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-15 15:53 DEBUG  TaskList: ## Finished create_dir_structure
04-15 15:53 DEBUG  TaskList: ## Running uncompress_target_dir...
04-15 15:53 DEBUG  TaskList: ## Finished uncompress_target_dir
04-15 15:53 DEBUG  TaskList: ## Running create_uninstaller...
04-15 15:53 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Darren\Downloads\wubi-r191 (2).exe -> C:\ubuntu\uninstall-wubi.exe
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-15 15:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-15 15:53 DEBUG  TaskList: ## Finished create_uninstaller
04-15 15:53 DEBUG  TaskList: ## Running copy_installation_files...
04-15 15:53 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-15 15:53 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\winboot -> C:\ubuntu\winboot
04-15 15:53 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-15 15:53 DEBUG  TaskList: ## Finished copy_installation_files
04-15 15:53 DEBUG  TaskList: ## Running get_iso...
04-15 15:53 DEBUG  CommonBackend: Searching for local CD
04-15 15:53 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl6162.tmp\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-15 15:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-15 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-15 15:53 DEBUG  CommonBackend: Searching for local ISO
04-15 15:53 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-15 15:53 DEBUG  TaskList: New task get_metalink
04-15 15:53 DEBUG  TaskList: ### Running get_metalink...
04-15 15:53 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > C:\ubuntu\install
04-15 15:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
04-15 15:53 DEBUG  downloader: download finished (read 39020 bytes)
04-15 15:53 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > C:\ubuntu\install
04-15 15:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
04-15 15:53 DEBUG  downloader: download finished (read 651 bytes)
04-15 15:53 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-15 15:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-15 15:53 DEBUG  downloader: download finished (read 198 bytes)
04-15 15:53 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-15 15:53 INFO   saplog: Checking block bindings..
04-15 15:53 INFO   saplog: Key verified successfully.
04-15 15:53 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink

04-15 15:53 DEBUG  TaskList: ### Finished get_metalink
04-15 15:53 DEBUG  TaskList: New task download
04-15 15:53 DEBUG  TaskList: ### Running download...
04-15 15:53 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.iso
04-15 16:53 ERROR  TaskList: Traceback (most recent call last):
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


04-15 16:53 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
04-15 16:53 DEBUG  TaskList: ### Finished download
04-15 16:53 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
04-15 16:53 DEBUG  TaskList: # Cancelling tasklist
04-15 16:53 DEBUG  TaskList: # Finished tasklist
04-15 16:53 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04.2-desktop-amd64.iso'
 
``` 
Any ideas?

Thanks

D

---

### Post by bcbc on 2011-04-15
@DarrenJParker:

This is the first problem:> 04-15 14:32 ERROR TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.

This is another (allowing pyrun.exe access to your firewall usually fixes this):
> 04-15 15:53 DEBUG btdownloader: downloading [http://releases.ubuntu.com/10.04.2/u...64.iso.torrent](http://releases.ubuntu.com/10.04.2/u...64.iso.torrent) > C:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.iso
04-15 16:53 ERROR TaskList: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Wubi.exe uses a bittorrent client to download the actual Desktop ISO - and often this is a point of failure, probably due to firewall software. You can get around it by allowing pyrun.exe access to the firewall (it should prompt you for this automatically)... or you can download the desktop CD ISO yourself, place it in the same folder as Wubi.exe, and run wubi from there - and in this case it finds and uses the ISO.

Or as stated earlier in the thread - burn it to CD and run it from there.

PS please edit your above post and add [CODE[SIZE="1"] [/SIZE]] at the front and [/CODE] at the back.

---

### Post by DarrenJParker on 2011-04-15
Okay Thanks I shall give that a go.

I have edited my previous post - thanks for the tip.

D

---

### Post by 3rdalbum on 2011-04-16
Do as I suggested: Try downloading the ISO, burning it to CD, and then running Wubi from the CD; or boot your computer from the CD and do a real dual-boot installation.

---

### Post by DarrenJParker on 2011-04-18
Hey

I managed to get it to work by downloading the ISO manually and then using Wubi.exe. 

Thanks for all your help!

D

---

