---
title: "Can't uninstall wubi / odd error"
date: 2011-09-03
forum: General Help
---

### Post by beseiker on 2011-09-03
Hello all,

I made the mistake of hard shutting down ubuntu on the boot screen, 
then another mistake when I hard shut it down on the grub rescue prompt. 

Now it boots straight into windows without any options to boot into ubuntu. 

When I tried to replace wubi 9.10 and install wubi 10.04.3, it gave me this error,

Error executing command

>>retval =1
>>stderr = an error occurred while attempting to delete the specified entry.
The system cannot find the file path specified.

>>stdout= 

for more information, please see the log file:
c:\users\benjam~1\appdata\local\temp\wubi=10.04.3-rev128.log

the contents of that log file are below. What did I do, and how do I fix it?

08-30 19:28 INFO   root: === wubi 10.04.3 rev192 ===
08-30 19:28 DEBUG  root: Logfile is c:\users\benjam~1\appdata\local\temp\wubi-10.04.3-rev192.log
08-30 19:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\BENJAM~1\\AppData\\Local\\Temp\\Rar$EX84.976\\wubi.exe"']
08-30 19:28 DEBUG  CommonBackend: data_dir=C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\data
08-30 19:28 DEBUG  WindowsBackend: 7z=C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\bin\7z.exe
08-30 19:28 DEBUG  CommonBackend: Fetching basic info...
08-30 19:28 DEBUG  CommonBackend: original_exe=C:\Users\BENJAM~1\AppData\Local\Temp\Rar$EX84.976\wubi.exe
08-30 19:28 DEBUG  CommonBackend: platform=win32
08-30 19:28 DEBUG  CommonBackend: osname=nt
08-30 19:28 DEBUG  CommonBackend: language=en_US
08-30 19:28 DEBUG  CommonBackend: encoding=cp1252
08-30 19:28 DEBUG  WindowsBackend: arch=amd64
08-30 19:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\data\isolist.ini
08-30 19:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-30 19:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-30 19:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-30 19:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-30 19:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-30 19:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-30 19:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-30 19:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-30 19:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-30 19:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-30 19:28 DEBUG  WindowsBackend: Fetching host info...
08-30 19:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-30 19:28 DEBUG  WindowsBackend: windows version=vista
08-30 19:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-30 19:28 DEBUG  WindowsBackend: windows_sp=None
08-30 19:28 DEBUG  WindowsBackend: windows_build=7600
08-30 19:28 DEBUG  WindowsBackend: gmt=-6
08-30 19:28 DEBUG  WindowsBackend: country=US
08-30 19:28 DEBUG  WindowsBackend: timezone=America/Chicago
08-30 19:28 DEBUG  WindowsBackend: windows_username=Benjammin
08-30 19:28 DEBUG  WindowsBackend: user_full_name=Benjammin
08-30 19:28 DEBUG  WindowsBackend: user_directory=C:\Users\Benjammin
08-30 19:28 DEBUG  WindowsBackend: windows_language_code=1033
08-30 19:28 DEBUG  WindowsBackend: windows_language=English
08-30 19:28 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II N640 Dual-Core Processor
08-30 19:28 DEBUG  WindowsBackend: bootloader=vista
08-30 19:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 225663.089844 mb free ntfs)
08-30 19:28 DEBUG  WindowsBackend: drive=Drive(B: hd 161347.300781 mb free ntfs)
08-30 19:28 DEBUG  WindowsBackend: drive=Drive(C: hd 225663.089844 mb free ntfs)
08-30 19:28 DEBUG  WindowsBackend: drive=Drive(D: cd 3700.65625 mb free udf)
08-30 19:28 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
08-30 19:28 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
08-30 19:28 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
08-30 19:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-30 19:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-30 19:28 DEBUG  WindowsBackend: keyboard_layout=us
08-30 19:28 DEBUG  WindowsBackend: keyboard_variant=
08-30 19:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-30 19:28 DEBUG  CommonBackend: locale=en_US.UTF-8
08-30 19:28 DEBUG  WindowsBackend: total_memory_mb=3835.68359375
08-30 19:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-30 19:28 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-10.04.3-desktop-amd64.iso
08-30 19:28 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-10.04.3-desktop-amd64.iso
08-30 19:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
08-30 19:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
08-30 19:28 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-10.04.3-desktop-amd64.iso
08-30 19:28 DEBUG  CommonBackend: Searching for local CDs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Ubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Kubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pylA939.tmp\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu Netbook CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
08-30 19:28 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-30 19:28 INFO   root: Already installed, running the uninstaller...
08-30 19:28 INFO   root: Running the uninstaller...
08-30 19:28 INFO   CommonBackend: Launching previous uninestaller B:\ubuntu\uninstall-wubi.exe
08-30 19:28 DEBUG  root: application.quit
08-30 19:28 DEBUG  root: application.on_quit
08-30 19:28 INFO   root: sys.exit
08-30 19:28 INFO   root: Quitting application
09-03 15:35 INFO   root: === wubi 10.04.3 rev192 ===
09-03 15:35 DEBUG  root: Logfile is c:\users\benjam~1\appdata\local\temp\wubi-10.04.3-rev192.log
09-03 15:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
09-03 15:35 DEBUG  CommonBackend: data_dir=C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\data
09-03 15:35 DEBUG  WindowsBackend: 7z=C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\bin\7z.exe
09-03 15:35 DEBUG  CommonBackend: Fetching basic info...
09-03 15:35 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-03 15:35 DEBUG  CommonBackend: platform=win32
09-03 15:35 DEBUG  CommonBackend: osname=nt
09-03 15:35 DEBUG  CommonBackend: language=en_US
09-03 15:35 DEBUG  CommonBackend: encoding=cp1252
09-03 15:35 DEBUG  WindowsBackend: arch=amd64
09-03 15:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\data\isolist.ini
09-03 15:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-03 15:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-03 15:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-03 15:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-03 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-03 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-03 15:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-03 15:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-03 15:35 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-03 15:35 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-03 15:35 DEBUG  WindowsBackend: Fetching host info...
09-03 15:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-03 15:35 DEBUG  WindowsBackend: windows version=vista
09-03 15:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-03 15:35 DEBUG  WindowsBackend: windows_sp=None
09-03 15:35 DEBUG  WindowsBackend: windows_build=7600
09-03 15:35 DEBUG  WindowsBackend: gmt=-6
09-03 15:35 DEBUG  WindowsBackend: country=US
09-03 15:35 DEBUG  WindowsBackend: timezone=America/Chicago
09-03 15:35 DEBUG  WindowsBackend: windows_username=Benjammin
09-03 15:35 DEBUG  WindowsBackend: user_full_name=Benjammin
09-03 15:35 DEBUG  WindowsBackend: user_directory=C:\Users\Benjammin
09-03 15:35 DEBUG  WindowsBackend: windows_language_code=1033
09-03 15:35 DEBUG  WindowsBackend: windows_language=English
09-03 15:35 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II N640 Dual-Core Processor
09-03 15:35 DEBUG  WindowsBackend: bootloader=vista
09-03 15:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 224155.210938 mb free ntfs)
09-03 15:35 DEBUG  WindowsBackend: drive=Drive(B: hd 161345.730469 mb free ntfs)
09-03 15:35 DEBUG  WindowsBackend: drive=Drive(C: hd 224155.210938 mb free ntfs)
09-03 15:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-03 15:35 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-03 15:35 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
09-03 15:35 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
09-03 15:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-03 15:35 DEBUG  WindowsBackend: keyboard_id=67699721
09-03 15:35 DEBUG  WindowsBackend: keyboard_layout=us
09-03 15:35 DEBUG  WindowsBackend: keyboard_variant=
09-03 15:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-03 15:35 DEBUG  CommonBackend: locale=en_US.UTF-8
09-03 15:35 DEBUG  WindowsBackend: total_memory_mb=3835.68359375
09-03 15:35 DEBUG  CommonBackend: Searching ISOs on USB devices
09-03 15:35 DEBUG  CommonBackend: Searching for local CDs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
09-03 15:35 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Ubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Ubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Ubuntu Netbook CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Kubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Kubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Kubuntu Netbook CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Xubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Xubuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Mythbuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp is a valid Mythbuntu CD
09-03 15:35 DEBUG  Distro:     does not contain C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\casper\filesystem.squashfs
09-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-03 15:35 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
09-03 15:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
09-03 15:35 INFO   Distro: Found a valid CD for Ubuntu: D:\
09-03 15:35 INFO   root: Running the CD menu...
09-03 15:35 DEBUG  WindowsFrontend: __init__...
09-03 15:35 DEBUG  WindowsFrontend: on_init...
09-03 15:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\translations, languages=['en_US', 'en']
09-03 15:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BENJAM~1\AppData\Local\Temp\pyl8B00.tmp\translations, languages=['en_US', 'en']
09-03 15:35 INFO   root: CD menu finished
09-03 15:35 INFO   root: Already installed, running the uninstaller...
09-03 15:35 INFO   root: Running the uninstaller...
09-03 15:35 INFO   CommonBackend: Launching previous uninestaller B:\ubuntu\uninstall-wubi.exe
09-03 15:35 DEBUG  root: application.quit
09-03 15:35 DEBUG  WindowsFrontend: frontend.quit
09-03 15:35 DEBUG  WindowsFrontend: frontend.on_quit
09-03 15:35 DEBUG  root: application.on_quit
09-03 15:35 INFO   root: sys.exit

---

### Post by hhh on 2011-09-03
Try Uninstall_Ubuntu.exe or the manual uninstall method, both described here...
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

