---
title: "WUBI Issues - Will not install (getting error message)"
date: 2011-11-02
forum: General Help
---

### Post by JPost on 2011-11-02
Hey Guys,
I'm trying to dual boot with Ubuntu and Windows XP.  I downloaded Wubi and during the install I get this error message during it (see attached image).

Does anyone know what this is?

I don't have anything plugged into my USB slots besides my wireless device that connects my keyboard and mouse.  

It seems to give the error while downloading ''ubuntu-11.10-wubi-amd64.tar.xz''.  The top of the error says pyrun.exe.

Can someone please help?

Thanks

[IMG]http://i.imgur.com/BgHqG.jpg[/IMG]

---

### Post by bcbc on 2011-11-02
pyrun.exe is the python runtime (wubi is written in python). The program is crashing - so you should [file a bug]("https://bugs.launchpad.net/wubi/+filebug"). Post the wubi-11.10-rev245.log on the bug report (it's in the %temp% directory).

You could also post the log file here if you like. Maybe look in that Microsoft error report as well - and post those on the bug report.

---

### Post by milosoftware on 2012-01-13
I got exactly the same error today. Any news?
(and it's hard to find this page because all you get when searching is that disk error which is unrelated)

Here's the log:

```
01-13 12:57 INFO   root: === wubi 11.10 rev245 ===
01-13 12:57 DEBUG  root: Logfile is c:\users\mike~1.loo\appdata\local\temp\wubi-11.10-rev245.log
01-13 12:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mike.looijmans\\Downloads\\wubi.exe"']
01-13 12:57 DEBUG  CommonBackend: data_dir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\data
01-13 12:57 DEBUG  WindowsBackend: 7z=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\bin\7z.exe
01-13 12:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 12:57 DEBUG  CommonBackend: Fetching basic info...
01-13 12:57 DEBUG  CommonBackend: original_exe=C:\Users\mike.looijmans\Downloads\wubi.exe
01-13 12:57 DEBUG  CommonBackend: platform=win32
01-13 12:57 DEBUG  CommonBackend: osname=nt
01-13 12:57 DEBUG  CommonBackend: language=nl_NL
01-13 12:57 DEBUG  CommonBackend: encoding=cp1252
01-13 12:57 DEBUG  WindowsBackend: arch=amd64
01-13 12:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\data\isolist.ini
01-13 12:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-13 12:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-13 12:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 12:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 12:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 12:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 12:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 12:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 12:57 DEBUG  WindowsBackend: Fetching host info...
01-13 12:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 12:57 DEBUG  WindowsBackend: windows version=vista
01-13 12:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-13 12:57 DEBUG  WindowsBackend: windows_sp=None
01-13 12:57 DEBUG  WindowsBackend: windows_build=7600
01-13 12:57 DEBUG  WindowsBackend: gmt=1
01-13 12:57 DEBUG  WindowsBackend: country=NL
01-13 12:57 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
01-13 12:57 DEBUG  WindowsBackend: windows_username=mike.looijmans
01-13 12:57 DEBUG  WindowsBackend: user_full_name=mike.looijmans
01-13 12:57 DEBUG  WindowsBackend: user_directory=P:\
01-13 12:57 DEBUG  WindowsBackend: windows_language_code=1043
01-13 12:57 DEBUG  WindowsBackend: windows_language=Dutch
01-13 12:57 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3550  @ 3.07GHz
01-13 12:57 DEBUG  WindowsBackend: bootloader=vista
01-13 12:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 790068.1875 mb free ntfs)
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(C: hd 790068.1875 mb free ntfs)
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(L: remote 1273507.10938 mb free ntfs)
01-13 12:57 DEBUG  WindowsBackend: drive=Drive(P: remote 1273507.10938 mb free ntfs)
01-13 12:57 DEBUG  WindowsBackend: uninstaller_path=None
01-13 12:57 DEBUG  WindowsBackend: previous_target_dir=None
01-13 12:57 DEBUG  WindowsBackend: previous_distro_name=None
01-13 12:57 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 12:57 DEBUG  WindowsBackend: keyboard_layout=us
01-13 12:57 DEBUG  WindowsBackend: keyboard_variant=
01-13 12:57 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
01-13 12:57 DEBUG  CommonBackend: locale=nl_NL.UTF-8
01-13 12:57 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-13 12:57 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 12:57 DEBUG  CommonBackend: Searching for local CDs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 12:57 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:57 INFO   root: Running the installer...
01-13 12:57 DEBUG  WindowsFrontend: __init__...
01-13 12:57 DEBUG  WindowsFrontend: on_init...
01-13 12:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\translations, languages=['nl_NL', 'nl']
01-13 12:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl8615.tmp\translations, languages=['nl_NL', 'nl']
01-13 12:58 INFO   WindowsFrontend: Operation cancelled
01-13 12:58 DEBUG  WindowsFrontend: frontend.quit
01-13 12:58 DEBUG  WindowsFrontend: frontend.on_quit
01-13 12:58 DEBUG  root: application.on_quit
01-13 12:58 INFO   root: sys.exit
01-13 12:58 INFO   root: === wubi 11.10 rev245 ===
01-13 12:58 DEBUG  root: Logfile is c:\users\mike~1.loo\appdata\local\temp\wubi-11.10-rev245.log
01-13 12:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mike.looijmans\\Downloads\\wubi.exe"']
01-13 12:58 DEBUG  CommonBackend: data_dir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\data
01-13 12:58 DEBUG  WindowsBackend: 7z=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\bin\7z.exe
01-13 12:58 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 12:58 DEBUG  CommonBackend: Fetching basic info...
01-13 12:58 DEBUG  CommonBackend: original_exe=C:\Users\mike.looijmans\Downloads\wubi.exe
01-13 12:58 DEBUG  CommonBackend: platform=win32
01-13 12:58 DEBUG  CommonBackend: osname=nt
01-13 12:58 DEBUG  CommonBackend: language=nl_NL
01-13 12:58 DEBUG  CommonBackend: encoding=cp1252
01-13 12:58 DEBUG  WindowsBackend: arch=amd64
01-13 12:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\data\isolist.ini
01-13 12:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-13 12:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-13 12:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 12:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 12:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 12:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 12:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 12:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 12:58 DEBUG  WindowsBackend: Fetching host info...
01-13 12:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 12:58 DEBUG  WindowsBackend: windows version=vista
01-13 12:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-13 12:58 DEBUG  WindowsBackend: windows_sp=None
01-13 12:58 DEBUG  WindowsBackend: windows_build=7600
01-13 12:58 DEBUG  WindowsBackend: gmt=1
01-13 12:58 DEBUG  WindowsBackend: country=NL
01-13 12:58 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
01-13 12:58 DEBUG  WindowsBackend: windows_username=mike.looijmans
01-13 12:58 DEBUG  WindowsBackend: user_full_name=mike.looijmans
01-13 12:58 DEBUG  WindowsBackend: user_directory=P:\
01-13 12:58 DEBUG  WindowsBackend: windows_language_code=1043
01-13 12:58 DEBUG  WindowsBackend: windows_language=Dutch
01-13 12:58 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3550  @ 3.07GHz
01-13 12:58 DEBUG  WindowsBackend: bootloader=vista
01-13 12:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 790067.535156 mb free ntfs)
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(C: hd 790067.535156 mb free ntfs)
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(L: remote 1273507.10938 mb free ntfs)
01-13 12:58 DEBUG  WindowsBackend: drive=Drive(P: remote 1273507.10938 mb free ntfs)
01-13 12:58 DEBUG  WindowsBackend: uninstaller_path=None
01-13 12:58 DEBUG  WindowsBackend: previous_target_dir=None
01-13 12:58 DEBUG  WindowsBackend: previous_distro_name=None
01-13 12:58 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 12:58 DEBUG  WindowsBackend: keyboard_layout=us
01-13 12:58 DEBUG  WindowsBackend: keyboard_variant=
01-13 12:58 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
01-13 12:58 DEBUG  CommonBackend: locale=nl_NL.UTF-8
01-13 12:58 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-13 12:58 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 12:58 DEBUG  CommonBackend: Searching for local CDs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 12:58 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:58 INFO   root: Running the installer...
01-13 12:58 DEBUG  WindowsFrontend: __init__...
01-13 12:58 DEBUG  WindowsFrontend: on_init...
01-13 12:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\translations, languages=['nl_NL', 'nl']
01-13 12:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\translations, languages=['nl_NL', 'nl']
01-13 12:59 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=milo
01-13 12:59 INFO   root: Received settings
01-13 12:59 DEBUG  CommonBackend: Searching for local CD
01-13 12:59 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 12:59 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 12:59 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 12:59 DEBUG  CommonBackend: Searching for local ISO
01-13 12:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl916B.tmp\translations, languages=['en_US', 'en']
01-13 12:59 DEBUG  TaskList: # Running tasklist...
01-13 12:59 DEBUG  TaskList: ## Running select_target_dir...
01-13 12:59 INFO   WindowsBackend: Installing into C:\ubuntu
01-13 12:59 DEBUG  TaskList: ## Finished select_target_dir
01-13 12:59 DEBUG  TaskList: ## Running create_dir_structure...
01-13 12:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-13 12:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-13 12:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-13 12:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-13 12:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-13 12:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-13 12:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-13 12:59 DEBUG  TaskList: ## Finished create_dir_structure
01-13 12:59 DEBUG  TaskList: ## Running create_uninstaller...
01-13 12:59 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mike.looijmans\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-13 12:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-13 12:59 DEBUG  TaskList: ## Finished create_uninstaller
01-13 12:59 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-13 12:59 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-13 12:59 DEBUG  TaskList: ## Running get_diskimage...
01-13 12:59 DEBUG  TaskList: New task download
01-13 12:59 DEBUG  TaskList: ### Running download...
01-13 12:59 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-13 12:59 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-13 13:02 INFO   root: === wubi 11.10 rev245 ===
01-13 13:02 DEBUG  root: Logfile is c:\users\mike~1.loo\appdata\local\temp\wubi-11.10-rev245.log
01-13 13:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mike.looijmans\\Downloads\\wubi.exe"']
01-13 13:02 DEBUG  CommonBackend: data_dir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\data
01-13 13:02 DEBUG  WindowsBackend: 7z=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\bin\7z.exe
01-13 13:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 13:02 DEBUG  CommonBackend: Fetching basic info...
01-13 13:02 DEBUG  CommonBackend: original_exe=C:\Users\mike.looijmans\Downloads\wubi.exe
01-13 13:02 DEBUG  CommonBackend: platform=win32
01-13 13:02 DEBUG  CommonBackend: osname=nt
01-13 13:02 DEBUG  CommonBackend: language=nl_NL
01-13 13:02 DEBUG  CommonBackend: encoding=cp1252
01-13 13:02 DEBUG  WindowsBackend: arch=amd64
01-13 13:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\data\isolist.ini
01-13 13:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-13 13:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-13 13:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 13:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 13:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 13:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 13:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 13:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 13:02 DEBUG  WindowsBackend: Fetching host info...
01-13 13:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 13:02 DEBUG  WindowsBackend: windows version=vista
01-13 13:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-13 13:02 DEBUG  WindowsBackend: windows_sp=None
01-13 13:02 DEBUG  WindowsBackend: windows_build=7600
01-13 13:02 DEBUG  WindowsBackend: gmt=1
01-13 13:02 DEBUG  WindowsBackend: country=NL
01-13 13:02 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
01-13 13:02 DEBUG  WindowsBackend: windows_username=mike.looijmans
01-13 13:02 DEBUG  WindowsBackend: user_full_name=mike.looijmans
01-13 13:02 DEBUG  WindowsBackend: user_directory=P:\
01-13 13:02 DEBUG  WindowsBackend: windows_language_code=1043
01-13 13:02 DEBUG  WindowsBackend: windows_language=Dutch
01-13 13:02 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3550  @ 3.07GHz
01-13 13:02 DEBUG  WindowsBackend: bootloader=vista
01-13 13:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 789685.851563 mb free ntfs)
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(C: hd 789685.851563 mb free ntfs)
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(L: remote 1273507.11328 mb free ntfs)
01-13 13:02 DEBUG  WindowsBackend: drive=Drive(P: remote 1273507.11328 mb free ntfs)
01-13 13:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-13 13:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-13 13:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-13 13:02 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 13:02 DEBUG  WindowsBackend: keyboard_layout=us
01-13 13:02 DEBUG  WindowsBackend: keyboard_variant=
01-13 13:02 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
01-13 13:02 DEBUG  CommonBackend: locale=nl_NL.UTF-8
01-13 13:02 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-13 13:02 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 13:02 DEBUG  CommonBackend: Searching for local CDs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:02 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:02 INFO   root: Already installed, running the uninstaller...
01-13 13:02 INFO   root: Running the uninstaller...
01-13 13:02 INFO   CommonBackend: This is the uninstaller running
01-13 13:02 DEBUG  WindowsFrontend: __init__...
01-13 13:02 DEBUG  WindowsFrontend: on_init...
01-13 13:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:03 INFO   root: Received settings
01-13 13:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:03 DEBUG  TaskList: # Running tasklist...
01-13 13:03 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
01-13 13:03 DEBUG  WindowsBackend: Could not find bcd id
01-13 13:03 DEBUG  WindowsBackend: undo_bootini C:
01-13 13:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 789685.851563 mb free ntfs)
01-13 13:03 DEBUG  WindowsBackend: undo_bootini E:
01-13 13:03 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: undo_bootini F:
01-13 13:03 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: undo_bootini G:
01-13 13:03 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: undo_bootini H:
01-13 13:03 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: undo_bootini I:
01-13 13:03 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
01-13 13:03 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
01-13 13:03 DEBUG  TaskList: ## Running Doelmap verwijderen...
01-13 13:03 DEBUG  CommonBackend: Deleting C:\ubuntu
01-13 13:03 DEBUG  TaskList: ## Finished Doelmap verwijderen
01-13 13:03 DEBUG  TaskList: ## Running Registersleutel verwijderen...
01-13 13:03 DEBUG  TaskList: ## Finished Registersleutel verwijderen
01-13 13:03 DEBUG  TaskList: # Finished tasklist
01-13 13:03 INFO   root: Almost finished uninstalling
01-13 13:03 INFO   root: Finished uninstallation
01-13 13:03 DEBUG  CommonBackend: Fetching basic info...
01-13 13:03 DEBUG  CommonBackend: original_exe=C:\Users\mike.looijmans\Downloads\wubi.exe
01-13 13:03 DEBUG  CommonBackend: platform=win32
01-13 13:03 DEBUG  CommonBackend: osname=nt
01-13 13:03 DEBUG  WindowsBackend: arch=amd64
01-13 13:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\data\isolist.ini
01-13 13:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-13 13:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-13 13:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 13:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 13:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 13:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 13:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 13:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 13:03 DEBUG  WindowsBackend: Fetching host info...
01-13 13:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 13:03 DEBUG  WindowsBackend: windows version=vista
01-13 13:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-13 13:03 DEBUG  WindowsBackend: windows_sp=None
01-13 13:03 DEBUG  WindowsBackend: windows_build=7600
01-13 13:03 DEBUG  WindowsBackend: gmt=1
01-13 13:03 DEBUG  WindowsBackend: country=NL
01-13 13:03 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
01-13 13:03 DEBUG  WindowsBackend: windows_username=mike.looijmans
01-13 13:03 DEBUG  WindowsBackend: user_full_name=mike.looijmans
01-13 13:03 DEBUG  WindowsBackend: user_directory=P:\
01-13 13:03 DEBUG  WindowsBackend: windows_language_code=1043
01-13 13:03 DEBUG  WindowsBackend: windows_language=Dutch
01-13 13:03 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3550  @ 3.07GHz
01-13 13:03 DEBUG  WindowsBackend: bootloader=vista
01-13 13:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 790064.417969 mb free ntfs)
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(C: hd 790064.417969 mb free ntfs)
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(L: remote 1273507.11328 mb free ntfs)
01-13 13:03 DEBUG  WindowsBackend: drive=Drive(P: remote 1273507.11328 mb free ntfs)
01-13 13:03 DEBUG  WindowsBackend: uninstaller_path=None
01-13 13:03 DEBUG  WindowsBackend: previous_target_dir=None
01-13 13:03 DEBUG  WindowsBackend: previous_distro_name=None
01-13 13:03 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 13:03 DEBUG  WindowsBackend: keyboard_layout=us
01-13 13:03 DEBUG  WindowsBackend: keyboard_variant=
01-13 13:03 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-13 13:03 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 13:03 DEBUG  CommonBackend: Searching for local CDs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 INFO   root: Running the installer...
01-13 13:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:03 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=milo
01-13 13:03 INFO   root: Received settings
01-13 13:03 DEBUG  CommonBackend: Searching for local CD
01-13 13:03 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:03 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:03 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:03 DEBUG  CommonBackend: Searching for local ISO
01-13 13:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pyl38C1.tmp\translations, languages=['en_US', 'en']
01-13 13:03 DEBUG  TaskList: # Running tasklist...
01-13 13:03 DEBUG  TaskList: ## Running select_target_dir...
01-13 13:03 INFO   WindowsBackend: Installing into C:\ubuntu
01-13 13:03 DEBUG  TaskList: ## Finished select_target_dir
01-13 13:03 DEBUG  TaskList: ## Running create_dir_structure...
01-13 13:03 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-13 13:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-13 13:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-13 13:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-13 13:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-13 13:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-13 13:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-13 13:03 DEBUG  TaskList: ## Finished create_dir_structure
01-13 13:03 DEBUG  TaskList: ## Running create_uninstaller...
01-13 13:03 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mike.looijmans\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-13 13:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-13 13:03 DEBUG  TaskList: ## Finished create_uninstaller
01-13 13:03 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-13 13:03 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-13 13:03 DEBUG  TaskList: ## Running get_diskimage...
01-13 13:03 DEBUG  TaskList: New task download
01-13 13:03 DEBUG  TaskList: ### Running download...
01-13 13:03 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-13 13:03 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-13 13:10 INFO   root: === wubi 11.10 rev245 ===
01-13 13:10 DEBUG  root: Logfile is c:\users\mike~1.loo\appdata\local\temp\wubi-11.10-rev245.log
01-13 13:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mike.looijmans\\Downloads\\wubi.exe"']
01-13 13:10 DEBUG  CommonBackend: data_dir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\data
01-13 13:10 DEBUG  WindowsBackend: 7z=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\bin\7z.exe
01-13 13:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-13 13:10 DEBUG  CommonBackend: Fetching basic info...
01-13 13:10 DEBUG  CommonBackend: original_exe=C:\Users\mike.looijmans\Downloads\wubi.exe
01-13 13:10 DEBUG  CommonBackend: platform=win32
01-13 13:10 DEBUG  CommonBackend: osname=nt
01-13 13:10 DEBUG  CommonBackend: language=nl_NL
01-13 13:10 DEBUG  CommonBackend: encoding=cp1252
01-13 13:10 DEBUG  WindowsBackend: arch=amd64
01-13 13:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\data\isolist.ini
01-13 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-13 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 13:10 DEBUG  WindowsBackend: Fetching host info...
01-13 13:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 13:10 DEBUG  WindowsBackend: windows version=vista
01-13 13:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-13 13:10 DEBUG  WindowsBackend: windows_sp=None
01-13 13:10 DEBUG  WindowsBackend: windows_build=7600
01-13 13:10 DEBUG  WindowsBackend: gmt=1
01-13 13:10 DEBUG  WindowsBackend: country=NL
01-13 13:10 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
01-13 13:10 DEBUG  WindowsBackend: windows_username=mike.looijmans
01-13 13:10 DEBUG  WindowsBackend: user_full_name=mike.looijmans
01-13 13:10 DEBUG  WindowsBackend: user_directory=P:\
01-13 13:10 DEBUG  WindowsBackend: windows_language_code=1043
01-13 13:10 DEBUG  WindowsBackend: windows_language=Dutch
01-13 13:10 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3550  @ 3.07GHz
01-13 13:10 DEBUG  WindowsBackend: bootloader=vista
01-13 13:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 789456.363281 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(C: hd 789456.363281 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(L: remote 1273507.11328 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(P: remote 1273507.11328 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-13 13:10 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-13 13:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-13 13:10 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 13:10 DEBUG  WindowsBackend: keyboard_layout=us
01-13 13:10 DEBUG  WindowsBackend: keyboard_variant=
01-13 13:10 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
01-13 13:10 DEBUG  CommonBackend: locale=nl_NL.UTF-8
01-13 13:10 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-13 13:10 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 13:10 DEBUG  CommonBackend: Searching for local CDs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 INFO   root: Already installed, running the uninstaller...
01-13 13:10 INFO   root: Running the uninstaller...
01-13 13:10 INFO   CommonBackend: This is the uninstaller running
01-13 13:10 DEBUG  WindowsFrontend: __init__...
01-13 13:10 DEBUG  WindowsFrontend: on_init...
01-13 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:10 INFO   root: Received settings
01-13 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:10 DEBUG  TaskList: # Running tasklist...
01-13 13:10 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
01-13 13:10 DEBUG  WindowsBackend: Could not find bcd id
01-13 13:10 DEBUG  WindowsBackend: undo_bootini C:
01-13 13:10 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 789456.363281 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: undo_bootini E:
01-13 13:10 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: undo_bootini F:
01-13 13:10 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: undo_bootini G:
01-13 13:10 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: undo_bootini H:
01-13 13:10 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: undo_bootini I:
01-13 13:10 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
01-13 13:10 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
01-13 13:10 DEBUG  TaskList: ## Running Doelmap verwijderen...
01-13 13:10 DEBUG  CommonBackend: Deleting C:\ubuntu
01-13 13:10 DEBUG  TaskList: ## Finished Doelmap verwijderen
01-13 13:10 DEBUG  TaskList: ## Running Registersleutel verwijderen...
01-13 13:10 DEBUG  TaskList: ## Finished Registersleutel verwijderen
01-13 13:10 DEBUG  TaskList: # Finished tasklist
01-13 13:10 INFO   root: Almost finished uninstalling
01-13 13:10 INFO   root: Finished uninstallation
01-13 13:10 DEBUG  CommonBackend: Fetching basic info...
01-13 13:10 DEBUG  CommonBackend: original_exe=C:\Users\mike.looijmans\Downloads\wubi.exe
01-13 13:10 DEBUG  CommonBackend: platform=win32
01-13 13:10 DEBUG  CommonBackend: osname=nt
01-13 13:10 DEBUG  WindowsBackend: arch=amd64
01-13 13:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\data\isolist.ini
01-13 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-13 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-13 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-13 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-13 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-13 13:10 DEBUG  WindowsBackend: Fetching host info...
01-13 13:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-13 13:10 DEBUG  WindowsBackend: windows version=vista
01-13 13:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-13 13:10 DEBUG  WindowsBackend: windows_sp=None
01-13 13:10 DEBUG  WindowsBackend: windows_build=7600
01-13 13:10 DEBUG  WindowsBackend: gmt=1
01-13 13:10 DEBUG  WindowsBackend: country=NL
01-13 13:10 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
01-13 13:10 DEBUG  WindowsBackend: windows_username=mike.looijmans
01-13 13:10 DEBUG  WindowsBackend: user_full_name=mike.looijmans
01-13 13:10 DEBUG  WindowsBackend: user_directory=P:\
01-13 13:10 DEBUG  WindowsBackend: windows_language_code=1043
01-13 13:10 DEBUG  WindowsBackend: windows_language=Dutch
01-13 13:10 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3550  @ 3.07GHz
01-13 13:10 DEBUG  WindowsBackend: bootloader=vista
01-13 13:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 789834.953125 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(C: hd 789834.953125 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(L: remote 1273507.11328 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: drive=Drive(P: remote 1273507.11328 mb free ntfs)
01-13 13:10 DEBUG  WindowsBackend: uninstaller_path=None
01-13 13:10 DEBUG  WindowsBackend: previous_target_dir=None
01-13 13:10 DEBUG  WindowsBackend: previous_distro_name=None
01-13 13:10 DEBUG  WindowsBackend: keyboard_id=67699721
01-13 13:10 DEBUG  WindowsBackend: keyboard_layout=us
01-13 13:10 DEBUG  WindowsBackend: keyboard_variant=
01-13 13:10 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-13 13:10 DEBUG  CommonBackend: Searching ISOs on USB devices
01-13 13:10 DEBUG  CommonBackend: Searching for local CDs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 INFO   root: Running the installer...
01-13 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\translations, languages=['nl_NL', 'nl']
01-13 13:10 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mikelooijmans
01-13 13:10 INFO   root: Received settings
01-13 13:10 DEBUG  CommonBackend: Searching for local CD
01-13 13:10 DEBUG  Distro:   checking whether C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
01-13 13:10 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
01-13 13:10 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
01-13 13:10 DEBUG  CommonBackend: Searching for local ISO
01-13 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MIKE~1.LOO\AppData\Local\Temp\pylE48A.tmp\translations, languages=['en_US', 'en']
01-13 13:10 DEBUG  TaskList: # Running tasklist...
01-13 13:10 DEBUG  TaskList: ## Running select_target_dir...
01-13 13:10 INFO   WindowsBackend: Installing into C:\ubuntu
01-13 13:10 DEBUG  TaskList: ## Finished select_target_dir
01-13 13:10 DEBUG  TaskList: ## Running create_dir_structure...
01-13 13:10 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-13 13:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-13 13:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-13 13:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-13 13:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-13 13:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-13 13:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-13 13:10 DEBUG  TaskList: ## Finished create_dir_structure
01-13 13:10 DEBUG  TaskList: ## Running create_uninstaller...
01-13 13:10 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mike.looijmans\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-13 13:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-13 13:10 DEBUG  TaskList: ## Finished create_uninstaller
01-13 13:10 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-13 13:10 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-13 13:10 DEBUG  TaskList: ## Running get_diskimage...
01-13 13:10 DEBUG  TaskList: New task download
01-13 13:10 DEBUG  TaskList: ### Running download...
01-13 13:10 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-13 13:10 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None

```

---

### Post by bcbc on 2012-01-13
When you click on the Microsoft message: to see what this data report contains [COLOR="Blue"]click here[/COLOR], can you identify the xml file location and post that as well?

Also, consider filing a bug and attaching that information.

---

