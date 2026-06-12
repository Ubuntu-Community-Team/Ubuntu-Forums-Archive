---
title: "WUBI giving error."
date: 2011-01-20
forum: General Help
---

### Post by Blue Dolphin on 2011-01-20
Hi,
 
I downloaded wubi few days ago, and tried installing ubuntu with iyt, it woorked fine & started. But I had to stop the download for some reasons.
 
Now after that when I tried to run wubi again its giving me error. Please see screenshot of the error.
[http://ubuntuforums.org/attachment.php?attachmentid=181577&stc=1&d=1295547147](http://ubuntuforums.org/attachment.php?attachmentid=181577&stc=1&d=1295547147) 
 
This error message prompt does not disappear no matter if click Try again, Cancel, Continue & stays at the top of all the window. Even now when I am typing thsi post this error dialog box is on top. I have to forecefully end the following two processes from the task manager then this window disappears.
Screenshot of the processes: [http://ubuntuforums.org/attachment.php?attachmentid=181578&stc=1&d=1295547147](http://ubuntuforums.org/attachment.php?attachmentid=181578&stc=1&d=1295547147)
 
Besides this -
1) Why it is saying pyrun.exe in the header of error message. Shouldn't it be wubi.exe?
2) Why are there two processes, as marked in second snapshot. Should not there be one or I am guessing it wrong?
 
Please see second screenshot for processes.
 
I have downloaded the iso file manually and kept the file in the same folder as wubi is, but still the same issue.
 
Please help so that I can install ubuntu.
 
Thanks.

---

### Post by bcbc on 2011-01-20
That error is due to a problem python has with drive's that are assigned, but empty. It could be a USB card reader. Sometimes there are problems with phones or other peripherals attached. Just remove them before running.

The pyrun.exe thing is Python. Wubi is written in Python.

When you get Ubuntu installed with Wubi, it's important to avoid updates to packages grub-pc and grub-common. 
All your data will be stored on a virtual disk (a file called root.disk) and you should back it up (or the data) as it's not as stable as a true disk partition.

---

### Post by Blue Dolphin on 2011-01-21
Hi bcbc,
Thanks for responding. That error is resolved but now I am getting another error while installation.
**Error Sanpshot:** [http://ubuntuforums.org/attachment.php?attachmentid=181634&stc=1&d=1295591998](http://ubuntuforums.org/attachment.php?attachmentid=181634&stc=1&d=1295591998)
 
I am installing 10.10 version. But I guess it is looking for 10.04 version as highlighted in snapshot. Yesterday I copied 10.4 version from a CD to USB stick. But I didn't install it. Do you think it might be the reason fro this error.
 
I read error log and same thing there, 10.4 version is being looked for.
Error log file size exceeded the attachment limit, so I am pasting the text.
**Log file name was:** wubi-10.04.1-rev190.log
**Text:**
01-21 10:57 INFO   root: === wubi 10.04.1 rev190 ===
01-21 10:57 DEBUG  root: Logfile is c:\users\jaspre~1\appdata\local\temp\wubi-10.04.1-rev190.log
01-21 10:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
01-21 10:57 DEBUG  CommonBackend: data_dir=C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\data
01-21 10:57 DEBUG  WindowsBackend: 7z=C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\bin\7z.exe
01-21 10:57 DEBUG  CommonBackend: Fetching basic info...
01-21 10:57 DEBUG  CommonBackend: original_exe=C:\wubi.exe
01-21 10:57 DEBUG  CommonBackend: platform=win32
01-21 10:57 DEBUG  CommonBackend: osname=nt
01-21 10:57 DEBUG  CommonBackend: language=en_IN
01-21 10:57 DEBUG  CommonBackend: encoding=cp1252
01-21 10:57 DEBUG  WindowsBackend: arch=amd64
01-21 10:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\data\isolist.ini
01-21 10:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-21 10:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-21 10:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-21 10:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-21 10:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-21 10:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-21 10:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-21 10:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-21 10:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-21 10:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-21 10:57 DEBUG  WindowsBackend: Fetching host info...
01-21 10:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-21 10:57 DEBUG  WindowsBackend: windows version=vista
01-21 10:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
01-21 10:57 DEBUG  WindowsBackend: windows_sp=None
01-21 10:57 DEBUG  WindowsBackend: windows_build=7600
01-21 10:57 DEBUG  WindowsBackend: gmt=5
01-21 10:57 DEBUG  WindowsBackend: country=IN
01-21 10:57 DEBUG  WindowsBackend: timezone=Asia/Calcutta
01-21 10:57 DEBUG  WindowsBackend: windows_username=Jaspreet Kaur
01-21 10:57 DEBUG  WindowsBackend: user_full_name=Jaspreet Kaur
01-21 10:57 DEBUG  WindowsBackend: user_directory=C:\Users\Jaspreet Kaur
01-21 10:57 DEBUG  WindowsBackend: windows_language_code=1033
01-21 10:57 DEBUG  WindowsBackend: windows_language=English
01-21 10:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
01-21 10:57 DEBUG  WindowsBackend: bootloader=vista
01-21 10:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 248537.011719 mb free ntfs)
01-21 10:57 DEBUG  WindowsBackend: drive=Drive(C: hd 248537.011719 mb free ntfs)
01-21 10:57 DEBUG  WindowsBackend: drive=Drive(D: removable 0.0 mb free )
01-21 10:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-21 10:57 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-21 10:57 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
01-21 10:57 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-21 10:57 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
01-21 10:57 DEBUG  WindowsBackend: uninstaller_path=None
01-21 10:57 DEBUG  WindowsBackend: previous_target_dir=None
01-21 10:57 DEBUG  WindowsBackend: previous_distro_name=None
01-21 10:57 DEBUG  WindowsBackend: keyboard_id=67699721
01-21 10:57 DEBUG  WindowsBackend: keyboard_layout=us
01-21 10:57 DEBUG  WindowsBackend: keyboard_variant=
01-21 10:57 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
01-21 10:57 DEBUG  CommonBackend: locale=en_IN
01-21 10:57 DEBUG  WindowsBackend: total_memory_mb=2990.09765625
01-21 10:57 DEBUG  CommonBackend: Searching ISOs on USB devices
01-21 10:57 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
01-21 10:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
01-21 10:57 DEBUG  Distro: wrong version: 10.10 != 10.04.1
01-21 10:57 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong version: 10.10 != 10.04.1
01-21 10:57 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
01-21 10:57 DEBUG  Distro:   checking Kubuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
01-21 10:57 DEBUG  Distro:   checking Kubuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
01-21 10:57 DEBUG  Distro:   checking Kubuntu Netbook ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Kubuntu Netbook
01-21 10:57 DEBUG  Distro:   checking Xubuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
01-21 10:57 DEBUG  Distro:   checking Xubuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
01-21 10:57 DEBUG  Distro:   checking Mythbuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
01-21 10:57 DEBUG  Distro:   checking Mythbuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
01-21 10:57 DEBUG  CommonBackend: Searching for local CDs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Ubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Kubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu Netbook CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 INFO   root: Running the installer...
01-21 10:57 DEBUG  WindowsFrontend: __init__...
01-21 10:57 DEBUG  WindowsFrontend: on_init...
01-21 10:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\translations, languages=['en_IN', 'en']
01-21 10:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\translations, languages=['en_IN', 'en']
01-21 10:57 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jaspreetkaur
01-21 10:57 INFO   root: Received settings
01-21 10:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\translations, languages=['en_US', 'en']
01-21 10:57 DEBUG  TaskList: # Running tasklist...
01-21 10:57 DEBUG  TaskList: ## Running select_target_dir...
01-21 10:57 INFO   WindowsBackend: Installing into C:\ubuntu
01-21 10:57 DEBUG  TaskList: ## Finished select_target_dir
01-21 10:57 DEBUG  TaskList: ## Running create_dir_structure...
01-21 10:57 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-21 10:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-21 10:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-21 10:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-21 10:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-21 10:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-21 10:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-21 10:57 DEBUG  TaskList: ## Finished create_dir_structure
01-21 10:57 DEBUG  TaskList: ## Running uncompress_target_dir...
01-21 10:57 DEBUG  TaskList: ## Finished uncompress_target_dir
01-21 10:57 DEBUG  TaskList: ## Running create_uninstaller...
01-21 10:57 DEBUG  WindowsBackend: Copying uninstaller C:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-21 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-21 10:57 DEBUG  TaskList: ## Finished create_uninstaller
01-21 10:57 DEBUG  TaskList: ## Running copy_installation_files...
01-21 10:57 DEBUG  WindowsBackend: Copying C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-21 10:57 DEBUG  WindowsBackend: Copying C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\winboot -> C:\ubuntu\winboot
01-21 10:57 DEBUG  WindowsBackend: Copying C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-21 10:57 DEBUG  TaskList: ## Finished copy_installation_files
01-21 10:57 DEBUG  TaskList: ## Running get_iso...
01-21 10:57 DEBUG  CommonBackend: Searching for local CD
01-21 10:57 DEBUG  Distro:   checking whether C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain C:\Users\JASPRE~1\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 10:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 10:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 10:57 DEBUG  CommonBackend: Searching for local ISO
01-21 10:57 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu-10.10-desktop-amd64.iso
01-21 10:57 DEBUG  Distro: wrong version: 10.10 != 10.04.1
01-21 10:57 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-21 10:57 DEBUG  TaskList: New task get_metalink
01-21 10:57 DEBUG  TaskList: ### Running get_metalink...
01-21 10:57 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) > C:\ubuntu\install
01-21 10:57 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
01-21 10:57 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
01-21 10:57 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
01-21 10:57 DEBUG  TaskList: ### Finished get_metalink
01-21 10:57 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-21 10:57 DEBUG  TaskList: # Cancelling tasklist
01-21 10:57 DEBUG  TaskList: # Finished tasklist
01-21 10:57 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO

Thanks.

---

### Post by bcbc on 2011-01-21
The version of wubi.exe on [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) is 10.04.1
It can only install 10.04.1

If you want 10.10 get wubi.exe from here: [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

---

### Post by Blue Dolphin on 2011-01-21
Hey bcbc, 
 
Thanks for link. :)
 
In the installer window, the installation size is 17GB by default. What does intallation size mean here? Is this the space that entire ubuntu OS is going to take? Can we change it, increase it? Or should we keep it as it is? And is there any advantage/disadvantage of increasing or decreasing it?
 
Screenshot: [http://ubuntuforums.org/attachment.php?attachmentid=181636&stc=1&d=1295596120](http://ubuntuforums.org/attachment.php?attachmentid=181636&stc=1&d=1295596120)
 
Thanks.

---

### Post by Rubi1200 on 2011-01-21
What you see is the total amount of space the installation will take. You can either increase or decrease it, but I would recommend you keep the defaults.

Bigger is always better, depending on what you want to do (save files etc.).

---

### Post by Blue Dolphin on 2011-01-21
> **Rubi1200 said:**
>  Bigger is always better, depending on what you want to do (save files etc.).

Thats what I thought. I am going to increase it. How about 30GB.

Thanks.

---

### Post by Rubi1200 on 2011-01-21
30GB is perfect!

Good luck and enjoy :)

---

### Post by Blue Dolphin on 2011-01-21
> **bcbc said:**
> When you get Ubuntu installed with Wubi, it's important to avoid updates to packages grub-pc and grub-common. 
All your data will be stored on a virtual disk (a file called root.disk) and you should back it up (or the data) as it's not as stable as a true disk partition.

How do we avoid updates update to grub-pc or grub-common?

And how do we create the backup you are talking about?

---

### Post by Blue Dolphin on 2011-01-21
> **Rubi1200 said:**
> 30GB is perfect!

Good luck and enjoy :) :)

I just saw the wubi MEGATHREAD for this grub-pc, grub-common lock thingy. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Solution provided there are for 10.04, upgrade to 10.10 from 10.04. What about if we instaling 10.10 fresh, I mean not upgarding from 10.04. What steps need to be executed then?

Thanks.

---

### Post by Rubi1200 on 2011-01-21
Same procedure; lock the packages in Synaptic as mentioned there.

---

### Post by Blue Dolphin on 2011-01-21
As I read in many other threads installing ubuntu using wubi, doesnt utilize full potential of unbuntu and still is on windows File System and may cause certain problems too, so I have dropped the idea of installing it using wubi. I am going to burn a CD and then install it.

**My queries for this:**

1. Will this CD procedure install the ubuntu as an independent OS. I mean utilizing full potential and avoid those grub issues?

2. I checked unbuntu site to see the procedure of burning CD on windows7. Its says:
 			**Windows 7**

 		
 		 			
[LIST=1]
[*]Right-click on an ISO image and choose 'Burn disc image'.
[/LIST]
By saying ISO image, do they mean ISO file that I downloaded?
And when I right click on the file their is no 'Burn disc image' option? Am I doing something wrong?

3. Will this CD installation make my system Dual Boot or over ride my windows7? :( I don't want that to happen. :(

I am using windows 7 and there is only partition C: dirve, that is in use. Other Q: drive is protected window7 back up drive. So where will Ubuntu install as their is no third partition. Will installation automatically take care of it and will take free space from C: and create a partition? 

Thanks.

---

### Post by ivanovnegro on 2011-01-21
> **Blue Dolphin said:**
> As I read in many other threads installing ubuntu using wubi, doesnt utilize full potential of unbuntu and still is on windows File System and may cause certain problems too, so I have dropped the idea of installing it using wubi. I am going to burn a CD and then install it. 

I think that is the better idea, just wanted to recommend it.

> **My queries for this:**

1. Will this CD procedure install the ubuntu as an independent OS. I mean utilizing full potential and avoid those grub issues?

It will install Ubuntu as an independent OS and normally there are not issues with Grub.

2. I checked unbuntu site to see the procedure of burning CD on windows7. Its says:
             **Windows 7**

         
                      
[LIST=1]
[*]Right-click on an ISO image and choose 'Burn disc image'.
[/LIST]
By saying ISO image, do they mean ISO file that I downloaded?
And when I right click on the file their is no 'Burn disc image' option? Am I doing something wrong?

You could open the burn software you have and then make an ISO image with that ISO file you downloaded

> 3. Will this CD installation make my system Dual Boot or over ride my windows7? :( I don't want that to happen. :(

  You can choose later in the installation process how you want to install Ubuntu to your system, if dual or not. 

> I am using windows 7 and there is only partition C: dirve, that is in use. Other Q: drive is protected window7 back up drive. So where will Ubuntu install as their is no third partition. Will installation automatically take care of it and will take free space from C: and create a partition? 

You can make a new partition within Windows before or later while  installing Ubuntu using the free space on the drive and its good to  defragment the Windows partition before and important, make a backup of  all your data.

[/QUOTE]Thanks.[/QUOTE]

There is also a good documentation about the installation process on the Ubuntu homepage.
Sorry, I typed in your text, without to notice it, now its difficult to see my post, my bad.

Edit: I tried to edit my post, dont know what happened here while typing, I did not want to confuse you.

---

### Post by bcbc on 2011-01-21
> **Blue Dolphin said:**
> As I read in many other threads installing ubuntu using wubi, doesnt utilize full potential of unbuntu and still is on windows File System and may cause certain problems too, so I have dropped the idea of installing it using wubi. I am going to burn a CD and then install it.

**My queries for this:**

1. Will this CD procedure install the ubuntu as an independent OS. I mean utilizing full potential and avoid those grub issues?

2. I checked unbuntu site to see the procedure of burning CD on windows7. Its says:
 			**Windows 7**

 		
 		 			
[LIST=1]
[*]Right-click on an ISO image and choose 'Burn disc image'.
[/LIST]
By saying ISO image, do they mean ISO file that I downloaded?
And when I right click on the file their is no 'Burn disc image' option? Am I doing something wrong?

3. Will this CD installation make my system Dual Boot or over ride my windows7? :( I don't want that to happen. :(

I am using windows 7 and there is only partition C: dirve, that is in use. Other Q: drive is protected window7 back up drive. So where will Ubuntu install as their is no third partition. Will installation automatically take care of it and will take free space from C: and create a partition? 

Thanks.

A proper installation is better than Wubi. You will need to use Windows 7 to shrink the C: to create a new partition. Then install Ubuntu into that free space. You can let the installer do this as well, but 10.10 has some confusing interface/bug that has caused some to overwrite windows: [http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Also, you can only have 4 primary partitions - some computers come with 4 already used - so you should check this as well. Go to the win 7 disk utility and confirm that you have 3 or less primary partitions.

Wubi is good to try Ubuntu - if you've never used it and aren't sure whether you will keep it or are not familiar/comfortable with partitioning. Uninstalling a Wubi install is as simple as going to the control panel and removing "Ubuntu".

---

### Post by Blue Dolphin on 2011-01-21
> **ivanovnegro said:**
> 
You could open the burn software you have and then make an ISO image with that ISO file you downloaded


Hey ivanovnegro,

Thanks for resposnding. Just to be clear, making an ISO image is no different than burning ISO file to CD..or is it? I mean you write ISO file to CD and it is called ISO image...right?

Sorry if that was a dumb question. :P

Thanks.

---

### Post by ivanovnegro on 2011-01-21
> **Blue Dolphin said:**
> Hey ivanovnegro,

Thanks for resposnding. Just to be clear, making an ISO image is no different than burning ISO file to CD..or is it? I mean you write ISO file to CD and it is called ISO image...right?

Sorry if that was a dumb question. :P

Thanks.

Yes, thats it. There are no dumb questions, dont worry.

Edit: Ok, Im not an English speaker, so, I try to explain it again. You download a disc image and this image you have to burn on the CD, the CD will contain in the end all the files you need to boot/install from the CD. I dont know how it is called in the Windows software but it has to be similar. Dont make a data or multimedia CD. 
[Link on Wikipedia]("http://en.wikipedia.org/wiki/ISO_image")

---

