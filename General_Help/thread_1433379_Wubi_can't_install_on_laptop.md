---
title: "Wubi can't install on laptop"
date: 2010-03-19
forum: General Help
---

### Post by razorseal on 2010-03-19
eta: ok, the problem is wubi can't retrieve the netbook versions... any fix for this? I really don't want to use anything else but wubi. I used it on my desktop, and it was straightforward and I really prefer it (it's pretty much the only reason i'm putting linux on here lol)

I'm getting an error, it says

an error occured: Cannot download the metalink and therefore the ISO

I'll post the portion of the log which I think is giving me the prob

```
03-19 00:01 DEBUG  TaskList: New task get_metalink
03-19 00:01 DEBUG  TaskList: ### Running get_metalink...
03-19 00:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink) > C:\ubuntu\install
03-19 00:01 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
03-19 00:01 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink](http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink) > C:\ubuntu\install
03-19 00:01 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink](http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/karmic-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
03-19 00:01 DEBUG  TaskList: ### Finished get_metalink
03-19 00:01 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-19 00:01 DEBUG  TaskList: # Cancelling tasklist
03-19 00:01 DEBUG  TaskList: # Finished tasklist
03-19 00:01 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
```

---

### Post by razorseal on 2010-03-19
ok that was quick.... I'm trying to download it for my laptop and the problem is none of the network versions are downloadable right now =/

any idea how I can do this? really don't wanna download an iso and all... main reason i'm putting it on the laptop is because wubi is just so awesome lol

---

### Post by razorseal on 2010-03-19
anyone? any ideas?

---

### Post by kundan1221 on 2011-06-25
hey i m getting error in installing ubuntu in windows wista.
 code is
06-25 14:03 INFO   root: === wubi 11.04 rev211 ===
06-25 14:03 DEBUG  root: Logfile is c:\users\kundan\appdata\local\temp\wubi-11.04-rev211.log
06-25 14:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
06-25 14:03 DEBUG  CommonBackend: data_dir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\data
06-25 14:03 DEBUG  WindowsBackend: 7z=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\bin\7z.exe
06-25 14:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-25 14:03 DEBUG  CommonBackend: Fetching basic info...
06-25 14:03 DEBUG  CommonBackend: original_exe=G:\wubi.exe
06-25 14:03 DEBUG  CommonBackend: platform=win32
06-25 14:03 DEBUG  CommonBackend: osname=nt
06-25 14:03 DEBUG  CommonBackend: language=en_IN
06-25 14:03 DEBUG  CommonBackend: encoding=cp1252
06-25 14:03 DEBUG  WindowsBackend: arch=amd64
06-25 14:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\data\isolist.ini
06-25 14:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-25 14:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-25 14:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-25 14:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-25 14:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-25 14:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-25 14:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-25 14:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-25 14:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-25 14:03 DEBUG  WindowsBackend: Fetching host info...
06-25 14:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-25 14:03 DEBUG  WindowsBackend: windows version=vista
06-25 14:03 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-25 14:03 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-25 14:03 DEBUG  WindowsBackend: windows_build=6002
06-25 14:03 DEBUG  WindowsBackend: gmt=5
06-25 14:03 DEBUG  WindowsBackend: country=IN
06-25 14:03 DEBUG  WindowsBackend: timezone=Asia/Calcutta
06-25 14:03 DEBUG  WindowsBackend: windows_username=Kundan
06-25 14:03 DEBUG  WindowsBackend: user_full_name=Kundan
06-25 14:03 DEBUG  WindowsBackend: user_directory=C:\Users\Kundan
06-25 14:03 DEBUG  WindowsBackend: windows_language_code=1033
06-25 14:03 DEBUG  WindowsBackend: windows_language=English
06-25 14:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz
06-25 14:03 DEBUG  WindowsBackend: bootloader=vista
06-25 14:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139674.292969 mb free ntfs)
06-25 14:03 DEBUG  WindowsBackend: drive=Drive(C: hd 139674.292969 mb free ntfs)
06-25 14:03 DEBUG  WindowsBackend: drive=Drive(D: hd 3852.9609375 mb free ntfs)
06-25 14:03 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-25 14:03 DEBUG  WindowsBackend: drive=Drive(G: removable 3153.6875 mb free fat32)
06-25 14:03 DEBUG  WindowsBackend: drive=Drive(O: hd 7712.3359375 mb free ntfs)
06-25 14:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-25 14:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-25 14:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-25 14:03 DEBUG  WindowsBackend: keyboard_id=67699721
06-25 14:03 DEBUG  WindowsBackend: keyboard_layout=us
06-25 14:03 DEBUG  WindowsBackend: keyboard_variant=
06-25 14:03 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
06-25 14:03 DEBUG  CommonBackend: locale=en_IN
06-25 14:03 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
06-25 14:03 DEBUG  CommonBackend: Searching ISOs on USB devices
06-25 14:03 DEBUG  CommonBackend: Searching for local CDs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Ubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Ubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Ubuntu Netbook CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Kubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Kubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Xubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Xubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Mythbuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Mythbuntu CD
06-25 14:03 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-25 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-25 14:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-25 14:03 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
06-25 14:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
06-25 14:03 INFO   Distro: Found a valid CD for Ubuntu: G:\
06-25 14:03 INFO   root: Running the CD menu...
06-25 14:03 DEBUG  WindowsFrontend: __init__...
06-25 14:03 DEBUG  WindowsFrontend: on_init...
06-25 14:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\translations, languages=['en_IN', 'en']
06-25 14:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\translations, languages=['en_IN', 'en']
06-25 14:03 INFO   root: CD menu finished
06-25 14:03 INFO   root: Already installed, running the uninstaller...
06-25 14:03 INFO   root: Running the uninstaller...
06-25 14:03 INFO   CommonBackend: This is the uninstaller running
06-25 14:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\translations, languages=['en_IN', 'en']
06-25 14:04 INFO   root: Received settings
06-25 14:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\translations, languages=['en_IN', 'en']
06-25 14:04 DEBUG  TaskList: # Running tasklist...
06-25 14:04 DEBUG  TaskList: ## Running Backup ISO...
06-25 14:04 DEBUG  TaskList: ## Finished Backup ISO
06-25 14:04 DEBUG  TaskList: ## Running Remove bootloader entry...
06-25 14:04 DEBUG  WindowsBackend: Could not find bcd id
06-25 14:04 DEBUG  WindowsBackend: undo_bootini C:
06-25 14:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 139674.292969 mb free ntfs)
06-25 14:04 DEBUG  WindowsBackend: undo_bootini D:
06-25 14:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 3852.9609375 mb free ntfs)
06-25 14:04 DEBUG  WindowsBackend: undo_bootini G:
06-25 14:04 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 3153.6875 mb free fat32)
06-25 14:04 DEBUG  WindowsBackend: undo_bootini O:
06-25 14:04 DEBUG  WindowsBackend: undo_configsys Drive(O: hd 7712.3359375 mb free ntfs)
06-25 14:04 DEBUG  TaskList: ## Finished Remove bootloader entry
06-25 14:04 DEBUG  TaskList: ## Running Remove target dir...
06-25 14:04 DEBUG  CommonBackend: Deleting C:\ubuntu
06-25 14:04 DEBUG  TaskList: ## Finished Remove target dir
06-25 14:04 DEBUG  TaskList: ## Running Remove registry key...
06-25 14:04 DEBUG  TaskList: ## Finished Remove registry key
06-25 14:04 DEBUG  TaskList: # Finished tasklist
06-25 14:04 INFO   root: Almost finished uninstalling
06-25 14:04 INFO   root: Finished uninstallation
06-25 14:04 DEBUG  CommonBackend: Fetching basic info...
06-25 14:04 DEBUG  CommonBackend: original_exe=G:\wubi.exe
06-25 14:04 DEBUG  CommonBackend: platform=win32
06-25 14:04 DEBUG  CommonBackend: osname=nt
06-25 14:04 DEBUG  WindowsBackend: arch=amd64
06-25 14:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\data\isolist.ini
06-25 14:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-25 14:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-25 14:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-25 14:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-25 14:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-25 14:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-25 14:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-25 14:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-25 14:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-25 14:04 DEBUG  WindowsBackend: Fetching host info...
06-25 14:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-25 14:04 DEBUG  WindowsBackend: windows version=vista
06-25 14:04 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-25 14:04 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-25 14:04 DEBUG  WindowsBackend: windows_build=6002
06-25 14:04 DEBUG  WindowsBackend: gmt=5
06-25 14:04 DEBUG  WindowsBackend: country=IN
06-25 14:04 DEBUG  WindowsBackend: timezone=Asia/Calcutta
06-25 14:04 DEBUG  WindowsBackend: windows_username=Kundan
06-25 14:04 DEBUG  WindowsBackend: user_full_name=Kundan
06-25 14:04 DEBUG  WindowsBackend: user_directory=C:\Users\Kundan
06-25 14:04 DEBUG  WindowsBackend: windows_language_code=1033
06-25 14:04 DEBUG  WindowsBackend: windows_language=English
06-25 14:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz
06-25 14:04 DEBUG  WindowsBackend: bootloader=vista
06-25 14:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 143545.058594 mb free ntfs)
06-25 14:04 DEBUG  WindowsBackend: drive=Drive(C: hd 143545.058594 mb free ntfs)
06-25 14:04 DEBUG  WindowsBackend: drive=Drive(D: hd 3852.9609375 mb free ntfs)
06-25 14:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-25 14:04 DEBUG  WindowsBackend: drive=Drive(G: removable 3153.6875 mb free fat32)
06-25 14:04 DEBUG  WindowsBackend: drive=Drive(O: hd 7712.3359375 mb free ntfs)
06-25 14:04 DEBUG  WindowsBackend: uninstaller_path=None
06-25 14:04 DEBUG  WindowsBackend: previous_target_dir=None
06-25 14:04 DEBUG  WindowsBackend: previous_distro_name=None
06-25 14:04 DEBUG  WindowsBackend: keyboard_id=67699721
06-25 14:04 DEBUG  WindowsBackend: keyboard_layout=us
06-25 14:04 DEBUG  WindowsBackend: keyboard_variant=
06-25 14:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
06-25 14:04 DEBUG  CommonBackend: Searching ISOs on USB devices
06-25 14:04 DEBUG  CommonBackend: Searching for local CDs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Ubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Ubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Ubuntu Netbook CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Kubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Kubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Xubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Xubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Mythbuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp is a valid Mythbuntu CD
06-25 14:04 DEBUG  Distro:     does not contain C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-25 14:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-25 14:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-25 14:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-25 14:04 INFO   Distro: Found a valid CD for Ubuntu: G:\
06-25 14:04 INFO   root: Running the installer...
06-25 14:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\translations, languages=['en_IN', 'en']
06-25 14:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\translations, languages=['en_IN', 'en']
06-25 14:04 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=kundan
06-25 14:04 INFO   root: Received settings
06-25 14:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\translations, languages=['en_US', 'en']
06-25 14:04 DEBUG  TaskList: # Running tasklist...
06-25 14:04 DEBUG  TaskList: ## Running select_target_dir...
06-25 14:04 INFO   WindowsBackend: Installing into C:\ubuntu
06-25 14:04 DEBUG  TaskList: ## Finished select_target_dir
06-25 14:04 DEBUG  TaskList: ## Running create_dir_structure...
06-25 14:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-25 14:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-25 14:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-25 14:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-25 14:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-25 14:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-25 14:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-25 14:04 DEBUG  TaskList: ## Finished create_dir_structure
06-25 14:04 DEBUG  TaskList: ## Running uncompress_target_dir...
06-25 14:04 DEBUG  TaskList: ## Finished uncompress_target_dir
06-25 14:04 DEBUG  TaskList: ## Running create_uninstaller...
06-25 14:04 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-25 14:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-25 14:04 DEBUG  TaskList: ## Finished create_uninstaller
06-25 14:04 DEBUG  TaskList: ## Running copy_installation_files...
06-25 14:04 DEBUG  WindowsBackend: Copying C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-25 14:04 DEBUG  WindowsBackend: Copying C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\winboot -> C:\ubuntu\winboot
06-25 14:04 DEBUG  WindowsBackend: Copying C:\Users\Kundan\AppData\Local\Temp\pyl2606.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-25 14:04 DEBUG  TaskList: ## Finished copy_installation_files
06-25 14:04 DEBUG  TaskList: ## Running get_iso...
06-25 14:04 DEBUG  TaskList: New task copy_file
06-25 14:04 DEBUG  TaskList: ### Running copy_file...
06-25 14:12 DEBUG  TaskList: ### Finished copy_file
06-25 14:12 DEBUG  TaskList: New task check_iso
06-25 14:12 DEBUG  TaskList: ### Running check_iso...
06-25 14:12 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
06-25 14:12 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
06-25 14:12 DEBUG  Distro:     wrong size: 4051681280 > 900000000
06-25 14:12 DEBUG  TaskList: ### Finished check_iso
06-25 14:12 DEBUG  CommonBackend: Searching for local ISO
06-25 14:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-25 14:12 DEBUG  TaskList: New task get_metalink
06-25 14:12 DEBUG  TaskList: ### Running get_metalink...
06-25 14:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
06-25 14:12 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) err=[Errno 14] HTTP Error 403: Webcat Access denied
06-25 14:12 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink) > C:\ubuntu\install
06-25 14:12 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink) err=[Errno 14] HTTP Error 403: Webcat Access denied
06-25 14:12 DEBUG  TaskList: ### Finished get_metalink
06-25 14:12 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-25 14:12 DEBUG  TaskList: # Cancelling tasklist
06-25 14:12 DEBUG  TaskList: # Finished tasklist
06-25 14:12 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO

---

### Post by sanderd17 on 2011-06-25
@kundan: please don't bump an old thread.

Are you sure you have the same problem? There has been a lot of changes in the last year. The netbook version has been merged with the desktop version, so there is no netbook version anymore.

EDIT: you have posted your output, but please put it in CODE tags (select the code and click on the #-symbol in the edit bar).

---

### Post by bcbc on 2011-06-25
+1 kundan1221, please don't post to old threads (and also do this more than once.)

You're running wubi off a USB stick (not possible when it's 4GB.) You should use the methods described in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#Installation")

---

