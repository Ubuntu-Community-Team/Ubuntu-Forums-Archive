---
title: "No Windows boot manager after installing Wubi"
date: 2010-07-21
forum: General Help
---

### Post by bsexton on 2010-07-21
No Windows boot manager after installing Wubi

I just picked up a Aspire one 532h-2588. Has Win7 on it.

I installed Wubi on it but after rebooting there is no new option to boot ubuntu.

I poked around the wubi folders in win7 but did not see anything.

How can I get this to boot to the wubi ubuntu install (or know why it is not)?

EDIT:
I tried copying this file and rebooting
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
but it did not help.

I do see a blip as the pc starts to boot but then it boots to windows.

---

### Post by bcbc on 2010-07-21
> **bsexton said:**
> No Windows boot manager after installing Wubi

I just picked up a Aspire one 532h-2588. Has Win7 on it.

I installed Wubi on it but after rebooting there is no new option to boot ubuntu.

I poked around the wubi folders in win7 but did not see anything.

How can I get this to boot to the wubi ubuntu install (or know why it is not)?

EDIT:
I tried copying this file and rebooting
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
but it did not help.

I do see a blip as the pc starts to boot but then it boots to windows.

It's not possible to install wubi without the boot menu, because the actual ubuntu install is only done after rebooting and selecting Ubuntu from the boot menu! So, I suspect something went wrong with the windows part of the install.

FYI the directories for ubuntu are \ubuntu (e.g. c:\ubuntu). In Add/Remove programs there should be an entry for Ubuntu.

If you try to install again, run it as an administrator. 

Also, do not use the 9.10 wubildr fix for 10.04 ubuntu - it will not work. (That link you mentioned specifically says to only use the fix if you 'installed' using 9.10).

---

### Post by bsexton on 2010-07-22
"Ubuntu" is add/remove programs.

I ran the install as admin and in XP compatibility mode(I got errors about the temp dir before I changed that).
The windows side of the install finished successfully but when I went to reboot the boot manager screen was not there.

---

### Post by bcbc on 2010-07-22
> **bsexton said:**
> "Ubuntu" is add/remove programs.

I ran the install as admin and in XP compatibility mode(I got errors about the temp dir before I changed that).
The windows side of the install finished successfully but when I went to reboot the boot manager screen was not there.

Hit the windows key, type 'msconfig' in the search programs and files box, hit enter, select the Boot tab. See if Ubuntu is in there.  Check the timeout is > 0. **EDIT:** this does NOT show the Ubuntu entry in the boot menu. You have to go to Control Panel, System, Advanced System Settings, Advanced tab, Startup and Recovery.

You'll probably need to reinstall to get it to work, but next time make sure that Ubuntu is in the menu after installing but before rebooting. 

If that's not the problem, then I'm not sure what you can do...

---

### Post by bsexton on 2010-07-23
Thanks for all you help.

Unfortunately that menu was already set to 30. 
It is windows 7 starter (not sure if it matters).

I may need to just look at booting with either a usb stick or CD.

---

### Post by bcbc on 2010-07-23
> **bsexton said:**
> Thanks for all you help.

Unfortunately that menu was already set to 30. 
It is windows 7 starter (not sure if it matters).

I may need to just look at booting with either a usb stick or CD.

Can you post the wubi log file? Maybe it has some info in it as to what the problem is. To get it, go to windows explorer and type %temp% in the address bar. Copy and paste inbetween [[SIZE="1"] [/SIZE]CODE][/CODE] tags or attach. (fyi it contains a little identifying info like your username and location).

---

### Post by bcbc on 2010-07-23
I was looking on launchpad ... there's a bug regarding win7 and failure to update the boot menu [https://bugs.launchpad.net/wubi/+bug/468664](https://bugs.launchpad.net/wubi/+bug/468664)

Maybe you're affected by this as well.

---

### Post by bsexton on 2010-07-23
I went to the wubi site and got the latest. Shouldn't the include the fix for the launchpad bug (assuming it was fixed)?


I think this is the file (only log file I see).
```
07-21 07:30 INFO   root: === wubi 10.04 rev189 ===
07-21 07:30 DEBUG  root: Logfile is c:\users\machinename\appdata\local\temp\wubi-10.04-rev189.log
07-21 07:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\machinename\\Downloads\\wubi.exe"']
07-21 07:30 DEBUG  CommonBackend: data_dir=C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\data
07-21 07:30 DEBUG  WindowsBackend: 7z=C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\bin\7z.exe
07-21 07:30 DEBUG  CommonBackend: Fetching basic info...
07-21 07:30 DEBUG  CommonBackend: original_exe=C:\Users\machinename\Downloads\wubi.exe
07-21 07:30 DEBUG  CommonBackend: platform=win32
07-21 07:30 DEBUG  CommonBackend: osname=nt
07-21 07:30 DEBUG  CommonBackend: language=en_US
07-21 07:30 DEBUG  CommonBackend: encoding=cp1252
07-21 07:30 DEBUG  WindowsBackend: arch=amd64
07-21 07:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\data\isolist.ini
07-21 07:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 07:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 07:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 07:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 07:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 07:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 07:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 07:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 07:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-21 07:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-21 07:30 DEBUG  WindowsBackend: Fetching host info...
07-21 07:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 07:30 DEBUG  WindowsBackend: windows version=vista
07-21 07:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
07-21 07:30 DEBUG  WindowsBackend: windows_sp=None
07-21 07:30 DEBUG  WindowsBackend: windows_build=7600
07-21 07:30 DEBUG  WindowsBackend: gmt=-5
07-21 07:30 DEBUG  WindowsBackend: country=US
07-21 07:30 DEBUG  WindowsBackend: timezone=America/New_York
07-21 07:30 DEBUG  WindowsBackend: windows_username=machinename
07-21 07:30 DEBUG  WindowsBackend: user_full_name=machinename
07-21 07:30 DEBUG  WindowsBackend: user_directory=C:\Users\machinename
07-21 07:30 DEBUG  WindowsBackend: windows_language_code=1033
07-21 07:30 DEBUG  WindowsBackend: windows_language=English
07-21 07:30 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
07-21 07:30 DEBUG  WindowsBackend: bootloader=vista
07-21 07:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 125524.335938 mb free ntfs)
07-21 07:30 DEBUG  WindowsBackend: drive=Drive(C: hd 125524.335938 mb free ntfs)
07-21 07:30 DEBUG  WindowsBackend: uninstaller_path=None
07-21 07:30 DEBUG  WindowsBackend: previous_target_dir=None
07-21 07:30 DEBUG  WindowsBackend: previous_distro_name=None
07-21 07:30 DEBUG  WindowsBackend: keyboard_id=67699721
07-21 07:30 DEBUG  WindowsBackend: keyboard_layout=us
07-21 07:30 DEBUG  WindowsBackend: keyboard_variant=
07-21 07:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-21 07:30 DEBUG  CommonBackend: locale=en_US.UTF-8
07-21 07:30 DEBUG  WindowsBackend: total_memory_mb=1013.1015625
07-21 07:30 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 07:30 DEBUG  CommonBackend: Searching for local CDs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Ubuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Ubuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Ubuntu Netbook CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Kubuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Kubuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Kubuntu Netbook CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Xubuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Xubuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Mythbuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Mythbuntu CD
07-21 07:30 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:30 INFO   root: Running the installer...
07-21 07:30 DEBUG  WindowsFrontend: __init__...
07-21 07:30 DEBUG  WindowsFrontend: on_init...
07-21 07:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\translations, languages=['en_US', 'en']
07-21 07:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\translations, languages=['en_US', 'en']
07-21 07:31 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=machinename
07-21 07:31 INFO   root: Received settings
07-21 07:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\translations, languages=['en_US', 'en']
07-21 07:31 DEBUG  TaskList: # Running tasklist...
07-21 07:31 DEBUG  TaskList: ## Running select_target_dir...
07-21 07:31 INFO   WindowsBackend: Installing into C:\ubuntu
07-21 07:31 DEBUG  TaskList: ## Finished select_target_dir
07-21 07:31 DEBUG  TaskList: ## Running create_dir_structure...
07-21 07:31 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-21 07:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-21 07:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-21 07:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-21 07:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-21 07:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-21 07:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-21 07:31 DEBUG  TaskList: ## Finished create_dir_structure
07-21 07:31 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 07:31 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 07:31 DEBUG  TaskList: ## Running create_uninstaller...
07-21 07:31 DEBUG  WindowsBackend: Copying uninstaller C:\Users\machinename\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-21 07:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-21 07:31 DEBUG  TaskList: ## Finished create_uninstaller
07-21 07:31 DEBUG  TaskList: ## Running copy_installation_files...
07-21 07:31 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-21 07:31 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\winboot -> C:\ubuntu\winboot
07-21 07:31 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-21 07:31 DEBUG  TaskList: ## Finished copy_installation_files
07-21 07:31 DEBUG  TaskList: ## Running get_iso...
07-21 07:31 DEBUG  CommonBackend: Searching for local CD
07-21 07:31 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp is a valid Ubuntu CD
07-21 07:31 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl62DD.tmp\casper\filesystem.squashfs
07-21 07:31 DEBUG  CommonBackend: Searching for local ISO
07-21 07:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-21 07:31 DEBUG  TaskList: New task get_metalink
07-21 07:31 DEBUG  TaskList: ### Running get_metalink...
07-21 07:31 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink > C:\ubuntu\install
07-21 07:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-21 07:31 DEBUG  downloader: download finished (read 7472 bytes)
07-21 07:31 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > C:\ubuntu\install
07-21 07:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-21 07:31 DEBUG  downloader: download finished (read 639 bytes)
07-21 07:31 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
07-21 07:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-21 07:31 DEBUG  downloader: download finished (read 189 bytes)
07-21 07:31 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-21 07:31 INFO   saplog: Checking block bindings..
07-21 07:31 INFO   saplog: Key verified successfully.
07-21 07:31 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

07-21 07:31 DEBUG  TaskList: ### Finished get_metalink
07-21 07:31 DEBUG  TaskList: New task download
07-21 07:31 DEBUG  TaskList: ### Running download...
07-21 07:31 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 07:54 ERROR  TaskList: Couldn't listen - (10013, 'Permission denied')
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 242, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Couldn't listen - (10013, 'Permission denied')
07-21 07:54 ERROR  TaskList: Non fatal error Couldn't listen - (10013, 'Permission denied') in task download
07-21 07:54 DEBUG  TaskList: ### Finished download
07-21 07:54 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-21 07:54 DEBUG  TaskList: # Cancelling tasklist
07-21 07:54 DEBUG  TaskList: # Finished tasklist
07-21 07:54 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-21 07:55 INFO   root: === wubi 10.04 rev189 ===
07-21 07:55 DEBUG  root: Logfile is c:\users\machinename\appdata\local\temp\wubi-10.04-rev189.log
07-21 07:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\machinename\\Downloads\\wubi.exe"']
07-21 07:55 DEBUG  CommonBackend: data_dir=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\data
07-21 07:55 DEBUG  WindowsBackend: 7z=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\bin\7z.exe
07-21 07:55 DEBUG  CommonBackend: Fetching basic info...
07-21 07:55 DEBUG  CommonBackend: original_exe=C:\Users\machinename\Downloads\wubi.exe
07-21 07:55 DEBUG  CommonBackend: platform=win32
07-21 07:55 DEBUG  CommonBackend: osname=nt
07-21 07:55 DEBUG  CommonBackend: language=en_US
07-21 07:55 DEBUG  CommonBackend: encoding=cp1252
07-21 07:55 DEBUG  WindowsBackend: arch=amd64
07-21 07:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\data\isolist.ini
07-21 07:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-21 07:55 DEBUG  WindowsBackend: Fetching host info...
07-21 07:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 07:55 DEBUG  WindowsBackend: windows version=vista
07-21 07:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
07-21 07:55 DEBUG  WindowsBackend: windows_sp=None
07-21 07:55 DEBUG  WindowsBackend: windows_build=7600
07-21 07:55 DEBUG  WindowsBackend: gmt=-5
07-21 07:55 DEBUG  WindowsBackend: country=US
07-21 07:55 DEBUG  WindowsBackend: timezone=America/New_York
07-21 07:55 DEBUG  WindowsBackend: windows_username=machinename
07-21 07:55 DEBUG  WindowsBackend: user_full_name=machinename
07-21 07:55 DEBUG  WindowsBackend: user_directory=C:\Users\machinename
07-21 07:55 DEBUG  WindowsBackend: windows_language_code=1033
07-21 07:55 DEBUG  WindowsBackend: windows_language=English
07-21 07:55 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
07-21 07:55 DEBUG  WindowsBackend: bootloader=vista
07-21 07:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 125125.886719 mb free ntfs)
07-21 07:55 DEBUG  WindowsBackend: drive=Drive(C: hd 125125.886719 mb free ntfs)
07-21 07:55 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-21 07:55 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-21 07:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 07:55 DEBUG  WindowsBackend: keyboard_id=67699721
07-21 07:55 DEBUG  WindowsBackend: keyboard_layout=us
07-21 07:55 DEBUG  WindowsBackend: keyboard_variant=
07-21 07:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-21 07:55 DEBUG  CommonBackend: locale=en_US.UTF-8
07-21 07:55 DEBUG  WindowsBackend: total_memory_mb=1013.1015625
07-21 07:55 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 07:55 DEBUG  CommonBackend: Searching for local CDs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Ubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Ubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Ubuntu Netbook CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Kubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Kubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Kubuntu Netbook CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Xubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Xubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Mythbuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Mythbuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 INFO   root: Already installed, running the uninstaller...
07-21 07:55 INFO   root: Running the uninstaller...
07-21 07:55 INFO   CommonBackend: This is the uninstaller running
07-21 07:55 DEBUG  WindowsFrontend: __init__...
07-21 07:55 DEBUG  WindowsFrontend: on_init...
07-21 07:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\translations, languages=['en_US', 'en']
07-21 07:55 INFO   root: Received settings
07-21 07:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\translations, languages=['en_US', 'en']
07-21 07:55 DEBUG  TaskList: # Running tasklist...
07-21 07:55 DEBUG  TaskList: ## Running Backup ISO...
07-21 07:55 DEBUG  TaskList: ## Finished Backup ISO
07-21 07:55 DEBUG  TaskList: ## Running Remove bootloader entry...
07-21 07:55 DEBUG  WindowsBackend: Could not find bcd id
07-21 07:55 DEBUG  WindowsBackend: undo_bootini C:
07-21 07:55 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 125125.886719 mb free ntfs)
07-21 07:55 DEBUG  TaskList: ## Finished Remove bootloader entry
07-21 07:55 DEBUG  TaskList: ## Running Remove target dir...
07-21 07:55 DEBUG  CommonBackend: Deleting C:\ubuntu
07-21 07:55 DEBUG  TaskList: ## Finished Remove target dir
07-21 07:55 DEBUG  TaskList: ## Running Remove registry key...
07-21 07:55 DEBUG  TaskList: ## Finished Remove registry key
07-21 07:55 DEBUG  TaskList: # Finished tasklist
07-21 07:55 INFO   root: Almost finished uninstalling
07-21 07:55 INFO   root: Finished uninstallation
07-21 07:55 DEBUG  CommonBackend: Fetching basic info...
07-21 07:55 DEBUG  CommonBackend: original_exe=C:\Users\machinename\Downloads\wubi.exe
07-21 07:55 DEBUG  CommonBackend: platform=win32
07-21 07:55 DEBUG  CommonBackend: osname=nt
07-21 07:55 DEBUG  WindowsBackend: arch=amd64
07-21 07:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\data\isolist.ini
07-21 07:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 07:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-21 07:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-21 07:55 DEBUG  WindowsBackend: Fetching host info...
07-21 07:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 07:55 DEBUG  WindowsBackend: windows version=vista
07-21 07:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
07-21 07:55 DEBUG  WindowsBackend: windows_sp=None
07-21 07:55 DEBUG  WindowsBackend: windows_build=7600
07-21 07:55 DEBUG  WindowsBackend: gmt=-5
07-21 07:55 DEBUG  WindowsBackend: country=US
07-21 07:55 DEBUG  WindowsBackend: timezone=America/New_York
07-21 07:55 DEBUG  WindowsBackend: windows_username=machinename
07-21 07:55 DEBUG  WindowsBackend: user_full_name=machinename
07-21 07:55 DEBUG  WindowsBackend: user_directory=C:\Users\machinename
07-21 07:55 DEBUG  WindowsBackend: windows_language_code=1033
07-21 07:55 DEBUG  WindowsBackend: windows_language=English
07-21 07:55 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
07-21 07:55 DEBUG  WindowsBackend: bootloader=vista
07-21 07:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 125127.40625 mb free ntfs)
07-21 07:55 DEBUG  WindowsBackend: drive=Drive(C: hd 125127.40625 mb free ntfs)
07-21 07:55 DEBUG  WindowsBackend: uninstaller_path=None
07-21 07:55 DEBUG  WindowsBackend: previous_target_dir=None
07-21 07:55 DEBUG  WindowsBackend: previous_distro_name=None
07-21 07:55 DEBUG  WindowsBackend: keyboard_id=67699721
07-21 07:55 DEBUG  WindowsBackend: keyboard_layout=us
07-21 07:55 DEBUG  WindowsBackend: keyboard_variant=
07-21 07:55 DEBUG  WindowsBackend: total_memory_mb=1013.1015625
07-21 07:55 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 07:55 DEBUG  CommonBackend: Searching for local CDs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Ubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Ubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Ubuntu Netbook CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Kubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Kubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Kubuntu Netbook CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Xubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Xubuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Mythbuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Mythbuntu CD
07-21 07:55 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 07:55 INFO   root: Running the installer...
07-21 07:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\translations, languages=['en_US', 'en']
07-21 07:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\translations, languages=['en_US', 'en']
07-21 08:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=machinename
07-21 08:02 INFO   root: Received settings
07-21 08:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\translations, languages=['en_US', 'en']
07-21 08:02 DEBUG  TaskList: # Running tasklist...
07-21 08:02 DEBUG  TaskList: ## Running select_target_dir...
07-21 08:02 INFO   WindowsBackend: Installing into C:\ubuntu
07-21 08:02 DEBUG  TaskList: ## Finished select_target_dir
07-21 08:02 DEBUG  TaskList: ## Running create_dir_structure...
07-21 08:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-21 08:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-21 08:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-21 08:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-21 08:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-21 08:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-21 08:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-21 08:02 DEBUG  TaskList: ## Finished create_dir_structure
07-21 08:02 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 08:02 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 08:02 DEBUG  TaskList: ## Running create_uninstaller...
07-21 08:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\machinename\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-21 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-21 08:02 DEBUG  TaskList: ## Finished create_uninstaller
07-21 08:02 DEBUG  TaskList: ## Running copy_installation_files...
07-21 08:02 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-21 08:02 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\winboot -> C:\ubuntu\winboot
07-21 08:02 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-21 08:02 DEBUG  TaskList: ## Finished copy_installation_files
07-21 08:02 DEBUG  TaskList: ## Running get_iso...
07-21 08:02 DEBUG  CommonBackend: Searching for local CD
07-21 08:02 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp is a valid Ubuntu CD
07-21 08:02 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl5037.tmp\casper\filesystem.squashfs
07-21 08:02 DEBUG  CommonBackend: Searching for local ISO
07-21 08:02 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-21 08:02 DEBUG  TaskList: New task get_metalink
07-21 08:02 DEBUG  TaskList: ### Running get_metalink...
07-21 08:02 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink > C:\ubuntu\install
07-21 08:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-21 08:02 DEBUG  downloader: download finished (read 7472 bytes)
07-21 08:02 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > C:\ubuntu\install
07-21 08:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-21 08:02 DEBUG  downloader: download finished (read 639 bytes)
07-21 08:02 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
07-21 08:02 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-21 08:02 DEBUG  downloader: download finished (read 189 bytes)
07-21 08:02 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-21 08:02 INFO   saplog: Checking block bindings..
07-21 08:02 INFO   saplog: Key verified successfully.
07-21 08:02 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

07-21 08:02 DEBUG  TaskList: ### Finished get_metalink
07-21 08:02 DEBUG  TaskList: New task download
07-21 08:02 DEBUG  TaskList: ### Running download...
07-21 08:02 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 08:14 ERROR  TaskList: Couldn't listen - (10013, 'Permission denied')
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 242, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Couldn't listen - (10013, 'Permission denied')
07-21 08:14 ERROR  TaskList: Non fatal error Couldn't listen - (10013, 'Permission denied') in task download
07-21 08:14 DEBUG  TaskList: ### Finished download
07-21 08:14 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-21 08:14 DEBUG  TaskList: # Cancelling tasklist
07-21 08:14 DEBUG  TaskList: # Finished tasklist
07-21 08:14 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-21 10:14 INFO   root: === wubi 10.04 rev189 ===
07-21 10:14 DEBUG  root: Logfile is c:\users\machinename\appdata\local\temp\wubi-10.04-rev189.log
07-21 10:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\machinename\\Downloads\\wubi.exe"']
07-21 10:14 DEBUG  CommonBackend: data_dir=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\data
07-21 10:14 DEBUG  WindowsBackend: 7z=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\bin\7z.exe
07-21 10:14 DEBUG  CommonBackend: Fetching basic info...
07-21 10:14 DEBUG  CommonBackend: original_exe=C:\Users\machinename\Downloads\wubi.exe
07-21 10:14 DEBUG  CommonBackend: platform=win32
07-21 10:14 DEBUG  CommonBackend: osname=nt
07-21 10:14 DEBUG  CommonBackend: language=en_US
07-21 10:14 DEBUG  CommonBackend: encoding=cp1252
07-21 10:14 DEBUG  WindowsBackend: arch=amd64
07-21 10:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\data\isolist.ini
07-21 10:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 10:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 10:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 10:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 10:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 10:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 10:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 10:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 10:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-21 10:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-21 10:14 DEBUG  WindowsBackend: Fetching host info...
07-21 10:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 10:14 DEBUG  WindowsBackend: windows version=xp
07-21 10:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-21 10:14 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-21 10:14 DEBUG  WindowsBackend: windows_build=2600
07-21 10:14 DEBUG  WindowsBackend: gmt=-5
07-21 10:14 DEBUG  WindowsBackend: country=US
07-21 10:14 DEBUG  WindowsBackend: timezone=America/New_York
07-21 10:14 DEBUG  WindowsBackend: windows_username=machinename
07-21 10:14 DEBUG  WindowsBackend: user_full_name=machinename
07-21 10:14 DEBUG  WindowsBackend: user_directory=C:\Users\machinename
07-21 10:14 DEBUG  WindowsBackend: windows_language_code=1033
07-21 10:14 DEBUG  WindowsBackend: windows_language=English
07-21 10:14 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
07-21 10:14 DEBUG  WindowsBackend: bootloader=xp
07-21 10:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 124418.675781 mb free ntfs)
07-21 10:14 DEBUG  WindowsBackend: drive=Drive(C: hd 124418.675781 mb free ntfs)
07-21 10:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-21 10:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-21 10:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 10:14 DEBUG  WindowsBackend: keyboard_id=67699721
07-21 10:14 DEBUG  WindowsBackend: keyboard_layout=us
07-21 10:14 DEBUG  WindowsBackend: keyboard_variant=
07-21 10:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-21 10:14 DEBUG  CommonBackend: locale=en_US.UTF-8
07-21 10:14 DEBUG  WindowsBackend: total_memory_mb=1013.1015625
07-21 10:14 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 10:14 DEBUG  CommonBackend: Searching for local CDs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Ubuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Ubuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Ubuntu Netbook CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Kubuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Kubuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Kubuntu Netbook CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Xubuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Xubuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Mythbuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Mythbuntu CD
07-21 10:14 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:14 INFO   root: Already installed, running the uninstaller...
07-21 10:14 INFO   root: Running the uninstaller...
07-21 10:14 INFO   CommonBackend: This is the uninstaller running
07-21 10:14 DEBUG  WindowsFrontend: __init__...
07-21 10:14 DEBUG  WindowsFrontend: on_init...
07-21 10:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\translations, languages=['en_US', 'en']
07-21 10:16 INFO   root: Received settings
07-21 10:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\translations, languages=['en_US', 'en']
07-21 10:16 DEBUG  TaskList: # Running tasklist...
07-21 10:16 DEBUG  TaskList: ## Running Backup ISO...
07-21 10:16 DEBUG  TaskList: ## Finished Backup ISO
07-21 10:16 DEBUG  TaskList: ## Running Remove bootloader entry...
07-21 10:16 DEBUG  WindowsBackend: Could not find bcd id
07-21 10:16 DEBUG  WindowsBackend: undo_bootini C:
07-21 10:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 124418.675781 mb free ntfs)
07-21 10:16 DEBUG  TaskList: ## Finished Remove bootloader entry
07-21 10:16 DEBUG  TaskList: ## Running Remove target dir...
07-21 10:16 DEBUG  CommonBackend: Deleting C:\ubuntu
07-21 10:16 DEBUG  TaskList: ## Finished Remove target dir
07-21 10:16 DEBUG  TaskList: ## Running Remove registry key...
07-21 10:16 DEBUG  TaskList: ## Finished Remove registry key
07-21 10:16 DEBUG  TaskList: # Finished tasklist
07-21 10:16 INFO   root: Almost finished uninstalling
07-21 10:16 INFO   root: Finished uninstallation
07-21 10:16 DEBUG  CommonBackend: Fetching basic info...
07-21 10:16 DEBUG  CommonBackend: original_exe=C:\Users\machinename\Downloads\wubi.exe
07-21 10:16 DEBUG  CommonBackend: platform=win32
07-21 10:16 DEBUG  CommonBackend: osname=nt
07-21 10:16 DEBUG  WindowsBackend: arch=amd64
07-21 10:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\data\isolist.ini
07-21 10:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 10:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 10:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 10:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 10:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 10:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 10:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 10:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 10:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-21 10:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-21 10:16 DEBUG  WindowsBackend: Fetching host info...
07-21 10:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 10:16 DEBUG  WindowsBackend: windows version=xp
07-21 10:16 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-21 10:16 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-21 10:16 DEBUG  WindowsBackend: windows_build=2600
07-21 10:16 DEBUG  WindowsBackend: gmt=-5
07-21 10:16 DEBUG  WindowsBackend: country=US
07-21 10:16 DEBUG  WindowsBackend: timezone=America/New_York
07-21 10:16 DEBUG  WindowsBackend: windows_username=machinename
07-21 10:16 DEBUG  WindowsBackend: user_full_name=machinename
07-21 10:16 DEBUG  WindowsBackend: user_directory=C:\Users\machinename
07-21 10:16 DEBUG  WindowsBackend: windows_language_code=1033
07-21 10:16 DEBUG  WindowsBackend: windows_language=English
07-21 10:16 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
07-21 10:16 DEBUG  WindowsBackend: bootloader=xp
07-21 10:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 124418.488281 mb free ntfs)
07-21 10:16 DEBUG  WindowsBackend: drive=Drive(C: hd 124418.488281 mb free ntfs)
07-21 10:16 DEBUG  WindowsBackend: uninstaller_path=None
07-21 10:16 DEBUG  WindowsBackend: previous_target_dir=None
07-21 10:16 DEBUG  WindowsBackend: previous_distro_name=None
07-21 10:16 DEBUG  WindowsBackend: keyboard_id=67699721
07-21 10:16 DEBUG  WindowsBackend: keyboard_layout=us
07-21 10:16 DEBUG  WindowsBackend: keyboard_variant=
07-21 10:16 DEBUG  WindowsBackend: total_memory_mb=1013.1015625
07-21 10:16 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 10:16 DEBUG  CommonBackend: Searching for local CDs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Ubuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Ubuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Ubuntu Netbook CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Kubuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Kubuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Kubuntu Netbook CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Xubuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Xubuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Mythbuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Mythbuntu CD
07-21 10:16 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:16 INFO   root: Running the installer...
07-21 10:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\translations, languages=['en_US', 'en']
07-21 10:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\translations, languages=['en_US', 'en']
07-21 10:17 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=machinename
07-21 10:17 INFO   root: Received settings
07-21 10:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\translations, languages=['en_US', 'en']
07-21 10:17 DEBUG  TaskList: # Running tasklist...
07-21 10:17 DEBUG  TaskList: ## Running select_target_dir...
07-21 10:17 INFO   WindowsBackend: Installing into C:\ubuntu
07-21 10:17 DEBUG  TaskList: ## Finished select_target_dir
07-21 10:17 DEBUG  TaskList: ## Running create_dir_structure...
07-21 10:17 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-21 10:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-21 10:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-21 10:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-21 10:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-21 10:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-21 10:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-21 10:17 DEBUG  TaskList: ## Finished create_dir_structure
07-21 10:17 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 10:17 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 10:17 DEBUG  TaskList: ## Running create_uninstaller...
07-21 10:17 DEBUG  WindowsBackend: Copying uninstaller C:\Users\machinename\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-21 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-21 10:17 DEBUG  TaskList: ## Finished create_uninstaller
07-21 10:17 DEBUG  TaskList: ## Running copy_installation_files...
07-21 10:17 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-21 10:17 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\winboot -> C:\ubuntu\winboot
07-21 10:17 DEBUG  WindowsBackend: Copying C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-21 10:17 DEBUG  TaskList: ## Finished copy_installation_files
07-21 10:17 DEBUG  TaskList: ## Running get_iso...
07-21 10:17 DEBUG  CommonBackend: Searching for local CD
07-21 10:17 DEBUG  Distro:   checking whether C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp is a valid Ubuntu CD
07-21 10:17 DEBUG  Distro:     does not contain C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\casper\filesystem.squashfs
07-21 10:17 DEBUG  CommonBackend: Searching for local ISO
07-21 10:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-21 10:17 DEBUG  TaskList: New task get_metalink
07-21 10:17 DEBUG  TaskList: ### Running get_metalink...
07-21 10:17 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink > C:\ubuntu\install
07-21 10:17 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-21 10:18 DEBUG  downloader: download finished (read 7472 bytes)
07-21 10:18 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > C:\ubuntu\install
07-21 10:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-21 10:18 DEBUG  downloader: download finished (read 639 bytes)
07-21 10:18 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
07-21 10:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-21 10:18 DEBUG  downloader: download finished (read 189 bytes)
07-21 10:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-21 10:18 INFO   saplog: Checking block bindings..
07-21 10:18 INFO   saplog: Key verified successfully.
07-21 10:18 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

07-21 10:18 DEBUG  TaskList: ### Finished get_metalink
07-21 10:18 DEBUG  TaskList: New task download
07-21 10:18 DEBUG  TaskList: ### Running download...
07-21 10:18 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:30 DEBUG  TaskList: ### Finished download
07-21 11:30 DEBUG  TaskList: New task check_iso
07-21 11:30 DEBUG  TaskList: ### Running check_iso...
07-21 11:30 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:30 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:30 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release amd64 (20100429)
07-21 11:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
07-21 11:30 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:30 DEBUG  TaskList: New task get_file_md5
07-21 11:30 DEBUG  TaskList: #### Running get_file_md5...
07-21 11:31 DEBUG  TaskList: #### Finished get_file_md5
07-21 11:31 DEBUG  TaskList: ### Finished check_iso
07-21 11:31 DEBUG  TaskList: ## Finished get_iso
07-21 11:31 DEBUG  TaskList: ## Running extract_kernel...
07-21 11:31 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:31 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:31 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:31 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 11:31 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-21 11:31 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
07-21 11:31 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 135737a6c8608631a2cde5a8aad7995c == 135737a6c8608631a2cde5a8aad7995c
07-21 11:31 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
07-21 11:31 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4c67c0bd8c44ecca988e71e7631ed0aa == 4c67c0bd8c44ecca988e71e7631ed0aa
07-21 11:31 DEBUG  TaskList: ## Finished extract_kernel
07-21 11:31 DEBUG  TaskList: ## Running choose_disk_sizes...
07-21 11:31 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
07-21 11:31 DEBUG  TaskList: ## Finished choose_disk_sizes
07-21 11:31 DEBUG  TaskList: ## Running create_preseed...
07-21 11:31 DEBUG  TaskList: ## Finished create_preseed
07-21 11:31 DEBUG  TaskList: ## Running modify_bootloader...
07-21 11:31 DEBUG  TaskList: New task modify_bootini
07-21 11:31 DEBUG  TaskList: ### Running modify_bootini...
07-21 11:31 DEBUG  WindowsBackend: modify_bootini C:
07-21 11:31 DEBUG  WindowsBackend: Could not find boot.ini C:\boot.ini
07-21 11:31 DEBUG  TaskList: ### Finished modify_bootini
07-21 11:31 DEBUG  TaskList: ## Finished modify_bootloader
07-21 11:31 DEBUG  TaskList: ## Running modify_grub_configuration...
07-21 11:31 DEBUG  TaskList: ## Finished modify_grub_configuration
07-21 11:31 DEBUG  TaskList: ## Running create_virtual_disks...
07-21 11:31 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
07-21 11:31 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
07-21 11:31 DEBUG  TaskList: ## Finished create_virtual_disks
07-21 11:31 DEBUG  TaskList: ## Running uncompress_files...
07-21 11:31 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
07-21 11:31 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
07-21 11:31 DEBUG  TaskList: ## Finished uncompress_files
07-21 11:31 DEBUG  TaskList: ## Running eject_cd...
07-21 11:31 DEBUG  TaskList: ## Finished eject_cd
07-21 11:31 DEBUG  TaskList: # Finished tasklist
07-21 11:31 INFO   root: Almost finished installing
07-21 11:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\machinename\AppData\Local\Temp\pyl95F9.tmp\translations, languages=['en_US', 'en']
07-21 12:42 INFO   root: Finished installation
07-21 12:42 INFO   root: Rebooting
07-21 12:42 DEBUG  TaskList: # Running tasklist...
07-21 12:42 DEBUG  TaskList: ## Running reboot...
07-21 12:42 DEBUG  TaskList: ## Finished reboot
07-21 12:42 DEBUG  TaskList: # Finished tasklist
07-21 12:42 DEBUG  root: application.quit
07-21 12:42 DEBUG  WindowsFrontend: frontend.quit
07-21 12:42 DEBUG  WindowsFrontend: frontend.on_quit
07-21 12:42 DEBUG  root: application.on_quit
07-21 12:42 INFO   root: sys.exit

```

---

### Post by bcbc on 2010-07-23
> **bsexton said:**
> I went to the wubi site and got the latest. Shouldn't the include the fix for the launchpad bug (assuming it was fixed)?


The bug was not fixed, but that is not your problem anyway. This is > 07-21 08:02 DEBUG  TaskList: ### Running download...
07-21 08:02 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-21 08:14 ERROR  TaskList: Couldn't listen - (10013, 'Permission denied')

It is trying to download the amd64 version of ubuntu using bit torrent and getting permission denied. It might be the windows firewall or perhaps a router issue. (did you get a popup asking you to allow firewall access to pyrun.exe?)

What I recommend is that you download the image yourself separately. Then place wubi.exe and the image in the same folder and wubi will find it and use it. It has many additional advantages, you can use the image to create a live USB (bootable USB stick with the image) and also if you reinstall wubi you don't have to download it each time.

Note - wubi has decided to use the 64bit ubuntu, based on your computer being 64bit (it says amd but it's just the 64 bit version and works on intel). If you want to install the 32 bit version you can but you might need to supply the --32bit command line parameter.

---

### Post by bsexton on 2010-07-23
Now that you mention it I hadn't even thought about the processor.

This thing has an Atom processor. Do I need to do something special for that (I have no idea)?

Also, I may tried to change network setting and download elsewhere.

---

### Post by bcbc on 2010-07-23
> **bsexton said:**
> Now that you mention it I hadn't even thought about the processor.

This thing has an Atom processor. Do I need to do something special for that (I have no idea)?

Also, I may tried to change network setting and download elsewhere.

If it's a netbook consider downloading the Ubuntu Netbook Edition. [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

That page doesn't mention the wubi option, but just put it in the same folder as wubi.exe and run it. Make sure you select the netbook from the wubi drop down box, otherwise it will download the version you select (i.e. don't select Ubuntu, select Ubuntu Netbook).

If you have a usb stick you can install on that (as per instructions in the link) and boot it in 'Live' mode (i.e. 'try without installing'). That's a good way to see if it works and importantly gives you a rescue medium if something goes wrong.

It's also a good idea to create a Windows USB recovery (returns it to factory installed state) and/or a rescue USB to repair(I think this requires some workarounds, but there are links on the web that describe it) if you haven't already.

---

### Post by bcbc on 2010-07-23
PS my comment earlier about msconfig is not accurate. The Ubuntu entry does not show up after I installed the netbook version, but it is in the windows boot menu.

I placed wubi.exe and the downloaded Ubuntu Netbook Edition .iso, and it installed without problems.

---

