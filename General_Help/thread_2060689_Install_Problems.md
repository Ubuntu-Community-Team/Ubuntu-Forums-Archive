---
title: "Install Problems"
date: 2012-09-20
forum: General Help
---

### Post by JXR on 2012-09-20
Why is it still such a hassle installing Linux? The best thing about Linux, in my experience thus far, has been the incredible support of the Linux Forum community. I'm still waiting for the experience called "Linux".
 
I've succeeded (after repeatedly checksumming] in burning a dvd with ubuntustudio-12.04-dvd-i386.iso.
 
I insert the dvd into my high powered Lenovo PC and, after filling in the initial splash screen (username/password) IMMEDIATELY get a Ubuntu Installer window saying:
 
An error occurred:
Could not retrieve the required disk image files
 
For more information, please see the log file: c:\docume~1\ann\locals~1\temp\wubi-12.04-rev265.log
 
I conduct a search of the complete C drive for wubi*.log and the computer returns no hits.
 
I don't know what to do. The checksum was successful; the burn was successful; the install program came up as expected. The program returned an error logged in a file I could not locate.
 
What now!

---

### Post by JXR on 2012-09-20
I found the log file!!
 
> 09-19 21:27 INFO root: === wubi 12.04 rev265 ===
09-19 21:27 DEBUG root: Logfile is c:\docume~1\ann\locals~1\temp\wubi-12.04-rev265.log
09-19 21:27 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-19 21:27 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\data
09-19 21:27 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
09-19 21:27 DEBUG WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-19 21:27 DEBUG CommonBackend: Fetching basic info...
09-19 21:27 DEBUG CommonBackend: original_exe=D:\wubi.exe
09-19 21:27 DEBUG CommonBackend: platform=win32
09-19 21:27 DEBUG CommonBackend: osname=nt
09-19 21:27 DEBUG CommonBackend: language=en_US
09-19 21:27 DEBUG CommonBackend: encoding=cp1252
09-19 21:27 DEBUG WindowsBackend: arch=amd64
09-19 21:27 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
09-19 21:27 DEBUG CommonBackend: Adding distro Xubuntu-i386
09-19 21:27 DEBUG CommonBackend: Adding distro Edubuntu-i386
09-19 21:27 DEBUG CommonBackend: Adding distro Xubuntu-amd64
09-19 21:27 DEBUG CommonBackend: Adding distro Kubuntu-amd64
09-19 21:27 DEBUG CommonBackend: Adding distro Mythbuntu-i386
09-19 21:27 DEBUG CommonBackend: Adding distro Edubuntu-amd64
09-19 21:27 DEBUG CommonBackend: Adding distro Ubuntu-amd64
09-19 21:27 DEBUG CommonBackend: Adding distro Lubuntu-i386
09-19 21:27 DEBUG CommonBackend: Adding distro Ubuntu-i386
09-19 21:27 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
09-19 21:27 DEBUG CommonBackend: Adding distro Kubuntu-i386
09-19 21:27 DEBUG CommonBackend: Adding distro Lubuntu-amd64
09-19 21:27 DEBUG WindowsBackend: Fetching host info...
09-19 21:27 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 21:27 DEBUG WindowsBackend: windows version=xp
09-19 21:27 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
09-19 21:27 DEBUG WindowsBackend: windows_sp=Service Pack 3
09-19 21:27 DEBUG WindowsBackend: windows_build=2600
09-19 21:27 DEBUG WindowsBackend: gmt=-8
09-19 21:27 DEBUG WindowsBackend: country=US
09-19 21:27 DEBUG WindowsBackend: timezone=America/Los_Angeles
09-19 21:27 DEBUG WindowsBackend: windows_username=Ann
09-19 21:27 DEBUG WindowsBackend: user_full_name=Ann
09-19 21:27 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Ann
09-19 21:27 DEBUG WindowsBackend: windows_language_code=1033
09-19 21:27 DEBUG WindowsBackend: windows_language=English
09-19 21:27 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz
09-19 21:27 DEBUG WindowsBackend: bootloader=xp
09-19 21:27 DEBUG WindowsBackend: system_drive=Drive(C: hd 77502.6328125 mb free ntfs)
09-19 21:27 DEBUG WindowsBackend: drive=Drive(C: hd 77502.6328125 mb free ntfs)
09-19 21:27 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-19 21:27 DEBUG WindowsBackend: uninstaller_path=None
09-19 21:27 DEBUG WindowsBackend: previous_target_dir=None
09-19 21:27 DEBUG WindowsBackend: previous_distro_name=None
09-19 21:27 DEBUG WindowsBackend: keyboard_id=67699721
09-19 21:27 DEBUG WindowsBackend: keyboard_layout=us
09-19 21:27 DEBUG WindowsBackend: keyboard_variant=
09-19 21:27 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
09-19 21:27 DEBUG CommonBackend: locale=en_US.UTF-8
09-19 21:27 DEBUG WindowsBackend: total_memory_mb=2039.23046875
09-19 21:27 DEBUG CommonBackend: Searching ISOs on USB devices
09-19 21:27 DEBUG CommonBackend: Searching for local CDs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Edubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Edubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Lubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Lubuntu CD
09-19 21:27 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-19 21:27 DEBUG Distro: parsing info from str=Ubuntu-Studio 12.04 "Precise Pangolin" - Release i386 (20120423)
09-19 21:27 DEBUG Distro: parsed info={'name': 'Ubuntu-Studio', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-19 21:27 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-19 21:27 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-19 21:27 INFO root: Running the installer...
09-19 21:27 DEBUG WindowsFrontend: __init__...
09-19 21:27 DEBUG WindowsFrontend: on_init...
09-19 21:27 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
09-19 21:27 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
09-19 21:45 INFO WindowsFrontend: Operation cancelled
09-19 21:45 DEBUG WindowsFrontend: frontend.quit
09-19 21:45 DEBUG WindowsFrontend: frontend.on_quit
09-19 21:45 DEBUG root: application.on_quit
09-19 21:45 INFO root: sys.exit
09-19 21:47 INFO root: === wubi 12.04 rev265 ===
09-19 21:47 DEBUG root: Logfile is c:\docume~1\ann\locals~1\temp\wubi-12.04-rev265.log
09-19 21:47 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-19 21:47 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\data
09-19 21:47 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
09-19 21:47 DEBUG WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-19 21:47 DEBUG CommonBackend: Fetching basic info...
09-19 21:47 DEBUG CommonBackend: original_exe=D:\wubi.exe
09-19 21:47 DEBUG CommonBackend: platform=win32
09-19 21:47 DEBUG CommonBackend: osname=nt
09-19 21:47 DEBUG CommonBackend: language=en_US
09-19 21:47 DEBUG CommonBackend: encoding=cp1252
09-19 21:47 DEBUG WindowsBackend: arch=amd64
09-19 21:47 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
09-19 21:47 DEBUG CommonBackend: Adding distro Xubuntu-i386
09-19 21:47 DEBUG CommonBackend: Adding distro Edubuntu-i386
09-19 21:47 DEBUG CommonBackend: Adding distro Xubuntu-amd64
09-19 21:47 DEBUG CommonBackend: Adding distro Kubuntu-amd64
09-19 21:47 DEBUG CommonBackend: Adding distro Mythbuntu-i386
09-19 21:47 DEBUG CommonBackend: Adding distro Edubuntu-amd64
09-19 21:47 DEBUG CommonBackend: Adding distro Ubuntu-amd64
09-19 21:47 DEBUG CommonBackend: Adding distro Lubuntu-i386
09-19 21:47 DEBUG CommonBackend: Adding distro Ubuntu-i386
09-19 21:47 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
09-19 21:47 DEBUG CommonBackend: Adding distro Kubuntu-i386
09-19 21:47 DEBUG CommonBackend: Adding distro Lubuntu-amd64
09-19 21:47 DEBUG WindowsBackend: Fetching host info...
09-19 21:47 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 21:47 DEBUG WindowsBackend: windows version=xp
09-19 21:47 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
09-19 21:47 DEBUG WindowsBackend: windows_sp=Service Pack 3
09-19 21:47 DEBUG WindowsBackend: windows_build=2600
09-19 21:47 DEBUG WindowsBackend: gmt=-8
09-19 21:47 DEBUG WindowsBackend: country=US
09-19 21:47 DEBUG WindowsBackend: timezone=America/Los_Angeles
09-19 21:47 DEBUG WindowsBackend: windows_username=Ann
09-19 21:47 DEBUG WindowsBackend: user_full_name=Ann
09-19 21:47 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Ann
09-19 21:47 DEBUG WindowsBackend: windows_language_code=1033
09-19 21:47 DEBUG WindowsBackend: windows_language=English
09-19 21:47 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz
09-19 21:47 DEBUG WindowsBackend: bootloader=xp
09-19 21:47 DEBUG WindowsBackend: system_drive=Drive(C: hd 77502.6445313 mb free ntfs)
09-19 21:47 DEBUG WindowsBackend: drive=Drive(C: hd 77502.6445313 mb free ntfs)
09-19 21:47 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-19 21:47 DEBUG WindowsBackend: uninstaller_path=None
09-19 21:47 DEBUG WindowsBackend: previous_target_dir=None
09-19 21:47 DEBUG WindowsBackend: previous_distro_name=None
09-19 21:47 DEBUG WindowsBackend: keyboard_id=67699721
09-19 21:47 DEBUG WindowsBackend: keyboard_layout=us
09-19 21:47 DEBUG WindowsBackend: keyboard_variant=
09-19 21:47 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
09-19 21:47 DEBUG CommonBackend: locale=en_US.UTF-8
09-19 21:47 DEBUG WindowsBackend: total_memory_mb=2039.23046875
09-19 21:47 DEBUG CommonBackend: Searching ISOs on USB devices
09-19 21:47 DEBUG CommonBackend: Searching for local CDs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Edubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Edubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Lubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp is a valid Lubuntu CD
09-19 21:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-19 21:47 DEBUG Distro: parsing info from str=Ubuntu-Studio 12.04 "Precise Pangolin" - Release i386 (20120423)
09-19 21:47 DEBUG Distro: parsed info={'name': 'Ubuntu-Studio', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-19 21:47 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-19 21:47 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-19 21:47 INFO root: Running the installer...
09-19 21:47 DEBUG WindowsFrontend: __init__...
09-19 21:47 DEBUG WindowsFrontend: on_init...
09-19 21:47 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
09-19 21:47 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
09-20 14:36 INFO root: === wubi 12.04 rev265 ===
09-20 14:36 DEBUG root: Logfile is c:\docume~1\ann\locals~1\temp\wubi-12.04-rev265.log
09-20 14:36 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-20 14:36 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\data
09-20 14:36 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
09-20 14:36 DEBUG WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-20 14:36 DEBUG CommonBackend: Fetching basic info...
09-20 14:36 DEBUG CommonBackend: original_exe=D:\wubi.exe
09-20 14:36 DEBUG CommonBackend: platform=win32
09-20 14:36 DEBUG CommonBackend: osname=nt
09-20 14:36 DEBUG CommonBackend: language=en_US
09-20 14:36 DEBUG CommonBackend: encoding=cp1252
09-20 14:36 DEBUG WindowsBackend: arch=amd64
09-20 14:36 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
09-20 14:36 DEBUG CommonBackend: Adding distro Xubuntu-i386
09-20 14:36 DEBUG CommonBackend: Adding distro Edubuntu-i386
09-20 14:36 DEBUG CommonBackend: Adding distro Xubuntu-amd64
09-20 14:36 DEBUG CommonBackend: Adding distro Kubuntu-amd64
09-20 14:36 DEBUG CommonBackend: Adding distro Mythbuntu-i386
09-20 14:36 DEBUG CommonBackend: Adding distro Edubuntu-amd64
09-20 14:36 DEBUG CommonBackend: Adding distro Ubuntu-amd64
09-20 14:36 DEBUG CommonBackend: Adding distro Lubuntu-i386
09-20 14:36 DEBUG CommonBackend: Adding distro Ubuntu-i386
09-20 14:36 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
09-20 14:36 DEBUG CommonBackend: Adding distro Kubuntu-i386
09-20 14:36 DEBUG CommonBackend: Adding distro Lubuntu-amd64
09-20 14:36 DEBUG WindowsBackend: Fetching host info...
09-20 14:36 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-20 14:36 DEBUG WindowsBackend: windows version=xp
09-20 14:36 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
09-20 14:36 DEBUG WindowsBackend: windows_sp=Service Pack 3
09-20 14:36 DEBUG WindowsBackend: windows_build=2600
09-20 14:36 DEBUG WindowsBackend: gmt=-8
09-20 14:36 DEBUG WindowsBackend: country=US
09-20 14:36 DEBUG WindowsBackend: timezone=America/Los_Angeles
09-20 14:36 DEBUG WindowsBackend: windows_username=Ann
09-20 14:36 DEBUG WindowsBackend: user_full_name=Ann
09-20 14:36 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Ann
09-20 14:36 DEBUG WindowsBackend: windows_language_code=1033
09-20 14:36 DEBUG WindowsBackend: windows_language=English
09-20 14:36 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz
09-20 14:36 DEBUG WindowsBackend: bootloader=xp
09-20 14:36 DEBUG WindowsBackend: system_drive=Drive(C: hd 77462.2265625 mb free ntfs)
09-20 14:36 DEBUG WindowsBackend: drive=Drive(C: hd 77462.2265625 mb free ntfs)
09-20 14:36 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-20 14:36 DEBUG WindowsBackend: uninstaller_path=None
09-20 14:36 DEBUG WindowsBackend: previous_target_dir=None
09-20 14:36 DEBUG WindowsBackend: previous_distro_name=None
09-20 14:36 DEBUG WindowsBackend: keyboard_id=67699721
09-20 14:36 DEBUG WindowsBackend: keyboard_layout=us
09-20 14:36 DEBUG WindowsBackend: keyboard_variant=
09-20 14:36 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
09-20 14:36 DEBUG CommonBackend: locale=en_US.UTF-8
09-20 14:36 DEBUG WindowsBackend: total_memory_mb=2039.23046875
09-20 14:36 DEBUG CommonBackend: Searching ISOs on USB devices
09-20 14:36 DEBUG CommonBackend: Searching for local CDs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Edubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Edubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Lubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Lubuntu CD
09-20 14:36 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:36 DEBUG Distro: parsing info from str=Ubuntu-Studio 12.04 "Precise Pangolin" - Release i386 (20120423)
09-20 14:36 DEBUG Distro: parsed info={'name': 'Ubuntu-Studio', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-20 14:36 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-20 14:36 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-20 14:36 INFO root: Running the installer...
09-20 14:36 DEBUG WindowsFrontend: __init__...
09-20 14:36 DEBUG WindowsFrontend: on_init...
09-20 14:36 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
09-20 14:36 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
09-20 14:47 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joost
09-20 14:47 INFO root: Received settings
09-20 14:47 DEBUG CommonBackend: Searching for local CD
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:47 DEBUG CommonBackend: Searching for local ISO
09-20 14:47 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
09-20 14:47 DEBUG TaskList: # Running tasklist...
09-20 14:47 DEBUG TaskList: ## Running select_target_dir...
09-20 14:47 INFO WindowsBackend: Installing into C:\ubuntu
09-20 14:47 DEBUG TaskList: ## Finished select_target_dir
09-20 14:47 DEBUG TaskList: ## Running create_dir_structure...
09-20 14:47 DEBUG CommonBackend: Creating dir C:\ubuntu
09-20 14:47 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
09-20 14:47 DEBUG CommonBackend: Creating dir C:\ubuntu\install
09-20 14:47 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
09-20 14:47 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
09-20 14:47 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-20 14:47 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-20 14:47 DEBUG TaskList: ## Finished create_dir_structure
09-20 14:47 DEBUG TaskList: ## Running create_uninstaller...
09-20 14:47 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-20 14:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-20 14:47 DEBUG TaskList: ## Finished create_uninstaller
09-20 14:47 DEBUG TaskList: ## Running create_preseed_diskimage...
09-20 14:47 DEBUG TaskList: ## Finished create_preseed_diskimage
09-20 14:47 DEBUG TaskList: ## Running get_diskimage...
09-20 14:47 DEBUG TaskList: New task download
09-20 14:47 DEBUG TaskList: ### Running download...
09-20 14:47 DEBUG downloader: downloading [http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz
09-20 14:47 ERROR TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\downloader.py", line 77, in download
File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
File "\lib\urlgrabber\grabber.py", line 845, in _retry
File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
File "\lib\urlgrabber\grabber.py", line 1001, in __init__
File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-20 14:47 ERROR TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
09-20 14:47 DEBUG TaskList: ### Finished download
09-20 14:47 DEBUG TaskList: New task download
09-20 14:47 DEBUG TaskList: ### Running download...
09-20 14:47 DEBUG downloader: downloading [http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz) > C:\ubuntu\disks\amd64.tar.xz
09-20 14:47 ERROR TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\downloader.py", line 77, in download
File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
File "\lib\urlgrabber\grabber.py", line 845, in _retry
File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
File "\lib\urlgrabber\grabber.py", line 1001, in __init__
File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-20 14:47 ERROR TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
09-20 14:47 DEBUG TaskList: ### Finished download
09-20 14:47 ERROR TaskList: Could not retrieve the required disk image files
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
09-20 14:47 DEBUG TaskList: # Cancelling tasklist
09-20 14:47 DEBUG TaskList: # Finished tasklist
09-20 14:47 ERROR root: Could not retrieve the required disk image files
Traceback (most recent call last):
File "\lib\wubi\application.py", line 58, in run
File "\lib\wubi\application.py", line 132, in select_task
File "\lib\wubi\application.py", line 158, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
09-20 14:47 INFO root: === wubi 12.04 rev265 ===
09-20 14:47 DEBUG root: Logfile is c:\docume~1\ann\locals~1\temp\wubi-12.04-rev265.log
09-20 14:47 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-20 14:47 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\data
09-20 14:47 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
09-20 14:47 DEBUG WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-20 14:47 DEBUG CommonBackend: Fetching basic info...
09-20 14:47 DEBUG CommonBackend: original_exe=D:\wubi.exe
09-20 14:47 DEBUG CommonBackend: platform=win32
09-20 14:47 DEBUG CommonBackend: osname=nt
09-20 14:47 DEBUG CommonBackend: language=en_US
09-20 14:47 DEBUG CommonBackend: encoding=cp1252
09-20 14:47 DEBUG WindowsBackend: arch=amd64
09-20 14:47 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
09-20 14:47 DEBUG CommonBackend: Adding distro Xubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Edubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Xubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Kubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Mythbuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Edubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Ubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Lubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Ubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Kubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Lubuntu-amd64
09-20 14:47 DEBUG WindowsBackend: Fetching host info...
09-20 14:47 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-20 14:47 DEBUG WindowsBackend: windows version=xp
09-20 14:47 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
09-20 14:47 DEBUG WindowsBackend: windows_sp=Service Pack 3
09-20 14:47 DEBUG WindowsBackend: windows_build=2600
09-20 14:47 DEBUG WindowsBackend: gmt=-8
09-20 14:47 DEBUG WindowsBackend: country=US
09-20 14:47 DEBUG WindowsBackend: timezone=America/Los_Angeles
09-20 14:47 DEBUG WindowsBackend: windows_username=Ann
09-20 14:47 DEBUG WindowsBackend: user_full_name=Ann
09-20 14:47 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Ann
09-20 14:47 DEBUG WindowsBackend: windows_language_code=1033
09-20 14:47 DEBUG WindowsBackend: windows_language=English
09-20 14:47 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz
09-20 14:47 DEBUG WindowsBackend: bootloader=xp
09-20 14:47 DEBUG WindowsBackend: system_drive=Drive(C: hd 77459.7460938 mb free ntfs)
09-20 14:47 DEBUG WindowsBackend: drive=Drive(C: hd 77459.7460938 mb free ntfs)
09-20 14:47 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-20 14:47 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-20 14:47 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
09-20 14:47 DEBUG WindowsBackend: previous_distro_name=Ubuntu
09-20 14:47 DEBUG WindowsBackend: keyboard_id=67699721
09-20 14:47 DEBUG WindowsBackend: keyboard_layout=us
09-20 14:47 DEBUG WindowsBackend: keyboard_variant=
09-20 14:47 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
09-20 14:47 DEBUG CommonBackend: locale=en_US.UTF-8
09-20 14:47 DEBUG WindowsBackend: total_memory_mb=2039.23046875
09-20 14:47 DEBUG CommonBackend: Searching ISOs on USB devices
09-20 14:47 DEBUG CommonBackend: Searching for local CDs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: parsing info from str=Ubuntu-Studio 12.04 "Precise Pangolin" - Release i386 (20120423)
09-20 14:47 DEBUG Distro: parsed info={'name': 'Ubuntu-Studio', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-20 14:47 INFO root: Already installed, running the uninstaller...
09-20 14:47 INFO root: Running the uninstaller...
09-20 14:47 INFO CommonBackend: This is the uninstaller running
09-20 14:47 DEBUG WindowsFrontend: __init__...
09-20 14:47 DEBUG WindowsFrontend: on_init...
09-20 14:47 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
09-20 14:47 INFO root: Received settings
09-20 14:47 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
09-20 14:47 DEBUG TaskList: # Running tasklist...
09-20 14:47 DEBUG TaskList: ## Running Remove bootloader entry...
09-20 14:47 ERROR WindowsBackend: Cannot find bcdedit
09-20 14:47 DEBUG WindowsBackend: undo_bootini C:
09-20 14:47 DEBUG WindowsBackend: undo_configsys Drive(C: hd 77459.7460938 mb free ntfs)
09-20 14:47 DEBUG TaskList: ## Finished Remove bootloader entry
09-20 14:47 DEBUG TaskList: ## Running Remove target dir...
09-20 14:47 DEBUG CommonBackend: Deleting C:\ubuntu
09-20 14:47 DEBUG TaskList: ## Finished Remove target dir
09-20 14:47 DEBUG TaskList: ## Running Remove registry key...
09-20 14:47 DEBUG TaskList: ## Finished Remove registry key
09-20 14:47 DEBUG TaskList: # Finished tasklist
09-20 14:47 INFO root: Almost finished uninstalling
09-20 14:47 INFO root: Finished uninstallation
09-20 14:47 DEBUG CommonBackend: Fetching basic info...
09-20 14:47 DEBUG CommonBackend: original_exe=D:\wubi.exe
09-20 14:47 DEBUG CommonBackend: platform=win32
09-20 14:47 DEBUG CommonBackend: osname=nt
09-20 14:47 DEBUG WindowsBackend: arch=amd64
09-20 14:47 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
09-20 14:47 DEBUG CommonBackend: Adding distro Xubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Edubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Xubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Kubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Mythbuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Edubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Ubuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Lubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Ubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
09-20 14:47 DEBUG CommonBackend: Adding distro Kubuntu-i386
09-20 14:47 DEBUG CommonBackend: Adding distro Lubuntu-amd64
09-20 14:47 DEBUG WindowsBackend: Fetching host info...
09-20 14:47 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-20 14:47 DEBUG WindowsBackend: windows version=xp
09-20 14:47 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
09-20 14:47 DEBUG WindowsBackend: windows_sp=Service Pack 3
09-20 14:47 DEBUG WindowsBackend: windows_build=2600
09-20 14:47 DEBUG WindowsBackend: gmt=-8
09-20 14:47 DEBUG WindowsBackend: country=US
09-20 14:47 DEBUG WindowsBackend: timezone=America/Los_Angeles
09-20 14:47 DEBUG WindowsBackend: windows_username=Ann
09-20 14:47 DEBUG WindowsBackend: user_full_name=Ann
09-20 14:47 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Ann
09-20 14:47 DEBUG WindowsBackend: windows_language_code=1033
09-20 14:47 DEBUG WindowsBackend: windows_language=English
09-20 14:47 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz
09-20 14:47 DEBUG WindowsBackend: bootloader=xp
09-20 14:47 DEBUG WindowsBackend: system_drive=Drive(C: hd 77462.09375 mb free ntfs)
09-20 14:47 DEBUG WindowsBackend: drive=Drive(C: hd 77462.09375 mb free ntfs)
09-20 14:47 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-20 14:47 DEBUG WindowsBackend: uninstaller_path=None
09-20 14:47 DEBUG WindowsBackend: previous_target_dir=None
09-20 14:47 DEBUG WindowsBackend: previous_distro_name=None
09-20 14:47 DEBUG WindowsBackend: keyboard_id=67699721
09-20 14:47 DEBUG WindowsBackend: keyboard_layout=us
09-20 14:47 DEBUG WindowsBackend: keyboard_variant=
09-20 14:47 DEBUG WindowsBackend: total_memory_mb=2039.23046875
09-20 14:47 DEBUG CommonBackend: Searching ISOs on USB devices
09-20 14:47 DEBUG CommonBackend: Searching for local CDs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Kubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Xubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Mythbuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Edubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-20 14:47 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD
09-20 14:47 DEBUG Distro: wrong name: Ubuntu Studio != Lubuntu
09-20 14:47 INFO root: Running the installer...
09-20 14:47 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
09-20 14:47 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
09-20 14:48 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ann
09-20 14:48 INFO root: Received settings
09-20 14:48 DEBUG CommonBackend: Searching for local CD
09-20 14:48 DEBUG Distro: checking whether C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
09-20 14:48 DEBUG Distro: does not contain C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
09-20 14:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
09-20 14:48 DEBUG Distro: wrong name: Ubuntu Studio != Ubuntu
09-20 14:48 DEBUG CommonBackend: Searching for local ISO
09-20 14:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ann\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
09-20 14:48 DEBUG TaskList: # Running tasklist...
09-20 14:48 DEBUG TaskList: ## Running select_target_dir...
09-20 14:48 INFO WindowsBackend: Installing into C:\ubuntu
09-20 14:48 DEBUG TaskList: ## Finished select_target_dir
09-20 14:48 DEBUG TaskList: ## Running create_dir_structure...
09-20 14:48 DEBUG CommonBackend: Creating dir C:\ubuntu
09-20 14:48 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
09-20 14:48 DEBUG CommonBackend: Creating dir C:\ubuntu\install
09-20 14:48 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
09-20 14:48 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
09-20 14:48 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-20 14:48 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-20 14:48 DEBUG TaskList: ## Finished create_dir_structure
09-20 14:48 DEBUG TaskList: ## Running create_uninstaller...
09-20 14:48 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Maicrosoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVearsion\Uninstall\Wubi DisplayVersion 12.04-rev265
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-20 14:48 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-20 14:48 DEBUG TaskList: ## Finished create_uninstaller
09-20 14:48 DEBUG TaskList: ## Running create_preseed_diskimage...
09-20 14:48 DEBUG TaskList: ## Finished create_preseed_diskimage
09-20 14:48 DEBUG TaskList: ## Running get_diskimage...
09-20 14:48 DEBUG TaskList: New task download
09-20 14:48 DEBUG TaskList: ### Running download...
09-20 14:48 DEBUG downloader: downloading [http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz
09-20 14:48 ERROR TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\downloader.py", line 77, in download
File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
File "\lib\urlgrabber\grabber.py", line 845, in _retry
File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
File "\lib\urlgrabber\grabber.py", line 1001, in __init__
File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-20 14:48 ERROR TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
09-20 14:48 DEBUG TaskList: ### Finished download
09-20 14:48 DEBUG TaskList: New task download
09-20 14:48 DEBUG TaskList: ### Running download...
09-20 14:48 DEBUG downloader: downloading [http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz) > C:\ubuntu\disks\amd64.tar.xz
09-20 14:48 ERROR TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\downloader.py", line 77, in download
File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
File "\lib\urlgrabber\grabber.py", line 845, in _retry
File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
File "\lib\urlgrabber\grabber.py", line 1001, in __init__
File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-20 14:48 ERROR TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
09-20 14:48 DEBUG TaskList: ### Finished download
09-20 14:48 ERROR TaskList: Could not retrieve the required disk image files
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
09-20 14:48 DEBUG TaskList: # Cancelling tasklist
09-20 14:48 DEBUG TaskList: # Finished tasklist
09-20 14:48 ERROR root: Could not retrieve the required disk image files
Traceback (most recent call last):
File "\lib\wubi\application.py", line 58, in run
File "\lib\wubi\application.py", line 132, in select_task
File "\lib\wubi\application.py", line 158, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
 
Given the log file, what do I do now?
 
Thanks

---

### Post by bcbc on 2012-09-20
Firstly, you can't install Ubuntu Studio using Wubi (the windows installer). You need to boot from the DVD and install it to a prepared partition (or let the installer create some partitions for you).

Secondly, you selected "Ubuntu" from the Wubi install window and the version of Wubi you are running (12.04) does not have the correct link to the latest version of Ubuntu (12.04.1). But that's probably a good thing or else it would have installed Ubuntu, not Ubuntu studio.

If you have any questions, let me know.

---

### Post by JXR on 2012-09-21
It worked! (I can't believe it!) Thanks for your help.
 
I was going to go whole-hog and replace the existing OS (Win XP) with Studio but decided to take the cautious route and let Ubuntu mount itself side-by-side the existing XP System (In doing so I also decided to let it establish how much disk space it was going to give itself, namely: 118 Gb Filesystem)
 
So I have one more question:
 
If I decide to make this an all-Linux machine...
 
After backing up files I might want to keep to another computer....
 
**If I reboot with the DVD-installer I used and instruct it to reinstall UbuntuStudio and not keep Win XP--will it overwrite everything and make the machine a dedicated UbuntuStudio machine?**
 
(or do I need to uninstall the current UbuntuStudio, etc.)
 
Thanks

---

### Post by bcbc on 2012-09-21
Great!

When you install the next time, you'll see an option, something like: **Erase and use the entire disk**

That'll be what you want, otherwise it will try to add another install.

---

