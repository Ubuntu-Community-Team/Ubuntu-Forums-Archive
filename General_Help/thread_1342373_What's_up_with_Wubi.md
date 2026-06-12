---
title: "What's up with Wubi?"
date: 2009-11-30
forum: General Help
---

### Post by Shibblet on 2009-11-30
**The Issue:**
Well, got a new laptop, and it comes with Windows 7.  Along with a Windows 7 recovery partition.  So, I have to use Wubi to install Kubuntu, else GRUB will take my partition loader and execute it.

**The Problem:**
So, I load Wubi off of the Kubuntu CD, and goes through the motions, then instead of running off of the CD, it starts downloading...  What?

Secondly, after the download, it crashes with some error.  So I tried running it again, and taking out of Windows Firewall, so there wouldn't be any access issues.  Same thing (45 minutes of download, 2 seconds of crash.)

Then I tried disconnecting the Wi-Fi to see if it would run off of the CD, and it crashes before the download.

**The Rant:**
Holy crap-stains on a turtle!  Why won't this work!  ;)

**The Legitimate Question:**
Does Wubi have Windows 7 issues?

---

### Post by u.b.u.n.t.u on 2009-11-30
Firstly a compliment on the structure of your situation. Makes it easy on the eyes to read and mind to comprehend.

Now to the matter of wubi. I think that software is in a word, "brilliant".

Yes it does wish to access the net and yes it may have issues if such is denied. I would give it access to the net and trust it, though I do agree that it should explain itself better.

After the typical initial install, wubi accessing the net, it then requests a reboot. Upon reboot it completes the installation process.

When you receive an error message after a crash, it is best to write such down. It may well save a lot of subsequent trial and error testing.

You say you tried the install a second time and encountered another crash. Is this identical to the first? Were the error messages the same?

Downloading for 45 minutes sounds really long, my experience is a few minutes, but speed is dependant upon many factors.

Wubi does not have Windows 7 issues as all of my wubi usage is from an installation of Windows 7.

It would be good to know what the error message states. Do allow wubi internet access. Check your internet connection. Give it another try?

---

### Post by Shibblet on 2009-12-01
This.

[ATTACH]138298[/ATTACH]

And the content of the .log

> 12-01 13:57 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-01 13:57 DEBUG  root: Logfile is c:\users\shibblet\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-01 13:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-01 13:57 DEBUG  CommonBackend: data_dir=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\data
12-01 13:57 DEBUG  WindowsBackend: 7z=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\bin\7z.exe
12-01 13:57 DEBUG  CommonBackend: Fetching basic info...
12-01 13:57 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-01 13:57 DEBUG  CommonBackend: platform=win32
12-01 13:57 DEBUG  CommonBackend: osname=nt
12-01 13:57 DEBUG  CommonBackend: language=en_US
12-01 13:57 DEBUG  CommonBackend: encoding=cp1252
12-01 13:57 DEBUG  WindowsBackend: arch=amd64
12-01 13:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\data\isolist.ini
12-01 13:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-01 13:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-01 13:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-01 13:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-01 13:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-01 13:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-01 13:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-01 13:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-01 13:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-01 13:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-01 13:57 DEBUG  WindowsBackend: Fetching host info...
12-01 13:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-01 13:57 DEBUG  WindowsBackend: windows version=vista
12-01 13:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-01 13:57 DEBUG  WindowsBackend: windows_sp=None
12-01 13:57 DEBUG  WindowsBackend: windows_build=7600
12-01 13:57 DEBUG  WindowsBackend: gmt=-9
12-01 13:57 DEBUG  WindowsBackend: country=US
12-01 13:57 DEBUG  WindowsBackend: timezone=America/Yakutat
12-01 13:57 DEBUG  WindowsBackend: windows_username=Shibblet
12-01 13:57 DEBUG  WindowsBackend: user_full_name=Shibblet
12-01 13:57 DEBUG  WindowsBackend: user_directory=C:\Users\Shibblet
12-01 13:57 DEBUG  WindowsBackend: windows_language_code=1033
12-01 13:57 DEBUG  WindowsBackend: windows_language=English
12-01 13:57 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Neo Processor MV-40
12-01 13:57 DEBUG  WindowsBackend: bootloader=vista
12-01 13:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28002.078125 mb free ntfs)
12-01 13:57 DEBUG  WindowsBackend: drive=Drive(C: hd 28002.078125 mb free ntfs)
12-01 13:57 DEBUG  WindowsBackend: drive=Drive(D: removable 1210.29296875 mb free fat32)
12-01 13:57 DEBUG  WindowsBackend: uninstaller_path=None
12-01 13:57 DEBUG  WindowsBackend: previous_target_dir=None
12-01 13:57 DEBUG  WindowsBackend: previous_distro_name=None
12-01 13:57 DEBUG  WindowsBackend: keyboard_id=67699721
12-01 13:57 DEBUG  WindowsBackend: keyboard_layout=us
12-01 13:57 DEBUG  WindowsBackend: keyboard_variant=
12-01 13:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-01 13:57 DEBUG  CommonBackend: locale=en_US.UTF-8
12-01 13:57 DEBUG  WindowsBackend: total_memory_mb=1919.3046875
12-01 13:57 DEBUG  CommonBackend: Searching ISOs on USB devices
12-01 13:57 DEBUG  CommonBackend: Searching for local CDs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Ubuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Ubuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Ubuntu Netbook Remix CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Kubuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Kubuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Kubuntu Netbook CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Xubuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Xubuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Mythbuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp is a valid Mythbuntu CD
12-01 13:57 DEBUG  Distro:     does not contain C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\casper\filesystem.squashfs
12-01 13:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-01 13:57 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-01 13:57 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-01 13:57 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
12-01 13:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-01 13:57 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
12-01 13:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-01 13:57 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
12-01 13:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-01 13:57 INFO   Distro: Found a valid CD for Kubuntu: D:\
12-01 13:57 INFO   root: Running the CD menu...
12-01 13:57 DEBUG  WindowsFrontend: __init__...
12-01 13:57 DEBUG  WindowsFrontend: on_init...
12-01 13:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\translations, languages=['en_US', 'en']
12-01 13:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\translations, languages=['en_US', 'en']
12-01 13:57 INFO   root: CD menu finished
12-01 13:57 INFO   root: Running the installer...
12-01 13:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\translations, languages=['en_US', 'en']
12-01 13:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\translations, languages=['en_US', 'en']
12-01 13:57 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=shibblet
12-01 13:57 INFO   root: Received settings
12-01 13:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\translations, languages=['en_US', 'en']
12-01 13:57 DEBUG  TaskList: # Running tasklist...
12-01 13:57 DEBUG  TaskList: ## Running select_target_dir...
12-01 13:57 INFO   WindowsBackend: Installing into C:\ubuntu
12-01 13:57 DEBUG  TaskList: ## Finished select_target_dir
12-01 13:57 DEBUG  TaskList: ## Running create_dir_structure...
12-01 13:57 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-01 13:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-01 13:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-01 13:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-01 13:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-01 13:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-01 13:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-01 13:57 DEBUG  TaskList: ## Finished create_dir_structure
12-01 13:57 DEBUG  TaskList: ## Running uncompress_target_dir...
12-01 13:57 DEBUG  TaskList: ## Finished uncompress_target_dir
12-01 13:57 DEBUG  TaskList: ## Running create_uninstaller...
12-01 13:57 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
12-01 13:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-01 13:57 DEBUG  TaskList: ## Finished create_uninstaller
12-01 13:57 DEBUG  TaskList: ## Running copy_installation_files...
12-01 13:57 DEBUG  WindowsBackend: Copying C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-01 13:57 DEBUG  WindowsBackend: Copying C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\winboot -> C:\ubuntu\winboot
12-01 13:57 DEBUG  WindowsBackend: Copying C:\Users\Shibblet\AppData\Local\Temp\pylF835.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
12-01 13:57 DEBUG  TaskList: ## Finished copy_installation_files
12-01 13:57 DEBUG  TaskList: ## Running get_iso...
12-01 13:57 DEBUG  TaskList: New task copy_file
12-01 13:57 DEBUG  TaskList: ### Running copy_file...
12-01 13:59 DEBUG  TaskList: ### Finished copy_file
12-01 13:59 DEBUG  TaskList: New task check_iso
12-01 13:59 DEBUG  TaskList: ### Running check_iso...
12-01 13:59 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
12-01 13:59 DEBUG  Distro:   checking Kubuntu ISO C:\ubuntu\install\installation.iso
12-01 13:59 DEBUG  Distro:     wrong size: 1998710784 > 900000000
12-01 13:59 DEBUG  TaskList: ### Finished check_iso
12-01 13:59 DEBUG  CommonBackend: Searching for local ISO
12-01 13:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-01 13:59 DEBUG  TaskList: New task get_metalink
12-01 13:59 DEBUG  TaskList: ### Running get_metalink...
12-01 13:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
12-01 14:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\kubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink, basename=kubuntu-9.10-desktop-i386.metalink, length=28219, text=None
12-01 14:00 DEBUG  downloader: download finished (read 28219 bytes)
12-01 14:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink) > C:\ubuntu\install
12-01 14:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=282, text=None
12-01 14:00 DEBUG  downloader: download finished (read 282 bytes)
12-01 14:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
12-01 14:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
12-01 14:00 DEBUG  downloader: download finished (read 189 bytes)
12-01 14:00 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-01 14:00 INFO   saplog: Checking block bindings..
12-01 14:00 INFO   saplog: Key verified successfully.
12-01 14:00 DEBUG  CommonBackend: metalink md5sums:
900cf707b1fd37ff8eb6f8e7c6518090  kubuntu-9.10-alternate-amd64.metalink
539eb2637eb1519f474b315af2b02fd2  kubuntu-9.10-alternate-i386.metalink
9fd91ccd34288d0f9e804eb3bd13d202  kubuntu-9.10-desktop-amd64.metalink
59f61e753d5b315befc131896d34145d  kubuntu-9.10-desktop-i386.metalink

12-01 14:00 DEBUG  TaskList: ### Finished get_metalink
12-01 14:00 DEBUG  TaskList: New task download
12-01 14:00 DEBUG  TaskList: ### Running download...
12-01 14:00 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-01 14:24 DEBUG  TaskList: ### Finished download
12-01 14:24 DEBUG  TaskList: New task check_iso
12-01 14:24 DEBUG  TaskList: ### Running check_iso...
12-01 14:24 DEBUG  CommonBackend: Checking C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-01 14:24 DEBUG  Distro:   checking Kubuntu ISO C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-01 14:24 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-01 14:24 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-01 14:24 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-01 14:24 INFO   Distro: Found a valid iso for Kubuntu: C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-01 14:24 DEBUG  CommonBackend: Using distro Kubuntu i386 instead of Kubuntu amd64
12-01 14:24 DEBUG  TaskList: New task get_metalink
12-01 14:24 DEBUG  TaskList: #### Running get_metalink...
12-01 14:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
12-01 14:24 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink) err=[Errno 9] Requested Range Not Satisfiable
12-01 14:24 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-i386.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-i386.metalink) > C:\ubuntu\install
12-01 14:24 DEBUG  downloader: Download start filename=C:\ubuntu\install\karmic-desktop-i386.metalink, url=http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-i386.metalink, basename=karmic-desktop-i386.metalink, length=1010, text=None
12-01 14:24 DEBUG  downloader: download finished (read 1010 bytes)
12-01 14:24 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink) > C:\ubuntu\install
12-01 14:24 ERROR  TaskList: [Errno 9] Requested Range Not Satisfiable
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 378, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 241, in check_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1177, in _make_request
URLGrabError: [Errno 9] Requested Range Not Satisfiable
12-01 14:24 DEBUG  TaskList: # Cancelling tasklist
12-01 14:24 ERROR  root: [Errno 9] Requested Range Not Satisfiable
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 378, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 241, in check_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1177, in _make_request
URLGrabError: [Errno 9] Requested Range Not Satisfiable
12-01 14:24 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso, ignoring
12-01 14:24 DEBUG  TaskList: ### Finished check_iso
12-01 14:24 DEBUG  TaskList: ## Finished get_iso
12-01 14:24 DEBUG  TaskList: # Finished tasklist

---

### Post by Megafag on 2009-12-01
Have you got any issue with just doing a regular, live CD/USB install?

---

### Post by Shibblet on 2009-12-01
> **Megafag said:**
> Have you got any issue with just doing a regular, live CD/USB install?

This.

> **Shibblet said:**
> **The Issue:**
Well, got a new laptop, and it comes with Windows 7.  Along with a Windows 7 recovery partition.  So, I have to use Wubi to install Kubuntu, else GRUB will take my partition loader and execute it.

---

### Post by u.b.u.n.t.u on 2009-12-01
```
12-01 14:00 DEBUG btdownloader: downloading http://releases.ubuntu.com/kubuntu/9...86.iso.torrent > C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
```

Are you able to check your download log at about the time in question to see if you have a spike of about 600-700 MB?

Did wubi torrent download the ISO? If you have the ISO already it really ought not to download it, but rather to install from it.

Is this what happened?

---

### Post by Shibblet on 2009-12-01
> **u.b.u.n.t.u said:**
> ```
12-01 14:00 DEBUG btdownloader: downloading http://releases.ubuntu.com/kubuntu/9...86.iso.torrent > C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
```

Are you able to check your download log at about the time in question to see if you have a spike of about 600-700 MB?

Did wubi torrent download the ISO? If you have the ISO already it really ought not to download it, but rather to install from it.

Is this what happened?

Yeah, it seems like that's what's going on.

I am running Wubi off of the Kubuntu CD.  So, it's all there.  Not a ISO file though.  It does the same thing if I download it and use it independently of the CD.

---

### Post by u.b.u.n.t.u on 2009-12-01
It may be worthwhile to edit your firewall and remove all references to wubi, eg:

pyrun.exe

Then closely monitor the install process and halt it at any sign of it commencing an ISO download.

I have experienced this problem with Ubuntu 9.10, but managed to get it to work.

---

### Post by Shibblet on 2009-12-01
> **u.b.u.n.t.u said:**
> It may be worthwhile to edit your firewall and remove all references to wubi, eg:

pyrun.exe

Then closely monitor the install process and halt it at any sign of it commencing an ISO download.

I have experienced this problem with Ubuntu 9.10, but managed to get it to work.

Except that when I download Wubi.exe and run it without the CD, it crashes the same way.

---

### Post by u.b.u.n.t.u on 2009-12-01
> **Shibblet said:**
> Except that when I download Wubi.exe and run it without the CD, it crashes the same way.

Wubi is on the CD itself. I run it from there. I actually run the ISO, ubuntu-9.10-desktop-amd64.iso, in a virtual drive and do it that way.

Here is a screenshot of what I see and I click wubi.exe to install Ubuntu 9.10.

[IMG]http://img690.imageshack.us/img690/9299/20091202115333.png[/IMG]

---

### Post by Shibblet on 2009-12-02
Still the same error no matter what I do.  However, I am going to give up.

I tried a standard install, side by side with Windows 7.  Fortunately it didn't ruin my recovery partition.  I can still use it.

But, once I got Kubuntu installed, the wireless doesn't work.  I start to lose patience with this kind of thing.

---

### Post by u.b.u.n.t.u on 2009-12-02
Yeah these things can be a life lesson in patience.

Rather than just give up, why not put it on the back burner, for Ubuntu is in a constant stage of development and a solution may arrive at anytime.

By the way, just off topic, I had a look Wasilla, Alaska in google and wow, just wow! 

How awesome is this!

[IMG]http://img268.imageshack.us/img268/7518/wasillaalaska.jpg[/IMG]

To be fair and open, I live in Melbourne, Australia.

---

### Post by garvinrick4 on 2009-12-02
Download new .iso copy from Ubuntu and BURN it to a CD will be about 690 meg or so.
Anything you download from Ubuntu for version of OS will be .iso file.

Takes about 12 minutes to download.  About 10 minutes to burn at slow speed 8x or so
maybe 16x but not 24x  on burn. There is an option usually in burning software.

Stick CD in tray choose WUBI  give the size you want at least 10 gig 20 or so if you want to put in music, pictures and such. Do not have to put in CD tray and then boot
off of CD anymore. Just put in tray and run software choose Wubi, that is it.


Type in password twice.

Hit go.  Takes 12 minutes and you are running.

Host is C: drive  in Ubuntu and you can drag and drop files to Ubuntu from Host/users/your
windows name

Make sure all of wubi is uninstalled from previous attempts.  If it is there will be in C:
right next to Users.   Do unintstall from WUBI folder.   If you take it out in add and remove programs you might leave in dos4grub and have to edit out. 
"bcdedit"    without qoutes in command line in Windows.   Look and make sure there is not a boot that has WUBI in it.   One instructional and Should just be the one for Windows 7,
Some have a Vista in there leave it alone it is for D:

If a Wubi in "bcdedit" post here and I will give you the one line edit to remove. No big deal.  Like  " bcdedit /delete {  a number in the grub  }"   without quotes

---

### Post by Shibblet on 2009-12-02
I'll keep plugging away.  Need to get a wireless driver for this computer.  It's an MSI 6981 Wireless card.

But to answer the Wasilla thing.  Here's a new thread.

[http://ubuntuforums.org/showthread.php?p=8425027#post8425027]("http://ubuntuforums.org/showthread.php?p=8425027#post8425027")

---

### Post by Shibblet on 2009-12-02
Can you run the ndiswrapper in Kubuntu?

---

### Post by fidamehran on 2009-12-05
> **u.b.u.n.t.u said:**
> Yeah these things can be a life lesson in patience.


Hi u.b.u.n.t.u,
It really has been life lesson. It's good to see that an experienced Ubuntu user like you is not one of the Wubi-bashers. I personally have been using Ubuntu since 7.04 and everytime through Wubi.
But I feel there is really some sort of problem in Wubi 9.10 compatibility with Windows 7. I feel it's some sort of protection that Win7 developers put to protect writing in the boot sector?!
I don't know. Because, I have been getting an error like the one the OP was getting, when I tried installing through Wubi.
I feel hopeful as I found you, as you have said you are using Windows 7 and have installed 9.10 through Wubi.

Can you tell me how?

---

### Post by u.b.u.n.t.u on 2009-12-05
I have installed Ubuntu 9.10 a number of times. Always the same set up.  From a second HDD I use daemon tools to mount the Ubuntu 9.10 ISO. I browse to the file wubi.exe and click it, and proceed as per any other windows install.

The only problem I have found is wubi thinking the ISO is missing and starting to torrent it. I repeat the start and it seems good but still demands internet access or no go.

After a few minutes, with the coffee still hot, reboot and complete the install procedure and there is Ubuntu 9.10.

Before state
HDD #1 = Windows 7 100% NTFS
HDD #2 = Data 100% NTFS (mounted Ubuntu 9.10 ISO here)

After state
HDD #1 = Windows 7 with wubi virtual Ubuntu 9.10
HDD #2 = Data 100% NTFS

I have Ubuntu 9.10 fully updated and customised the look. I require certain improvements with Ubuntu before I consider a separate partition. Ubuntu is in a permanent state of testing with me. I hate to say this, but it is not ready for deployment for my needs nor can I recommend it as an alternative to those I know who are happy to have Windows.

Areas Ubuntu needs to improve:

ESSENTIAL

1. Fully functional 3d - this is not a luxury.
2. Fully functional flash in Firefox.
3. Pre-configured GUI firewall.
4. Credible driver support, eg GUI type in driver and get a reply with a link to infor, driver download, this forum.
5. Huge warning on updates that may compromise the stability of Ubuntu.
6. GUI with guided drop down menus to edit xorg.
7. No more blank screens at boot, greater recovery features including basic VESA fallback.
8. All of the above are INCLUDED in a basic install.

DESIRABLE

1. Various two minute instruction videos, eg youtube, dealing with how to actually do things, with three levels, beginner, intermediate, advanced.

With a bit more thought I could probably add to the list.

It isn't just my usage I consider but also those whom I know who trust me regarding computers. People don't want to mess with a terminal and they don't want "stability" which really means endless breakages here and there, and they don't want to be told that it is basically their own fault for being too ignorant or stupid to switch and understand.

So you can see why I describe myself as testing Ubuntu rather than using it.

That the threads here are never ending with problems, most of which are no the fault of the user substantiates my assessment.

Ubuntu will get there, though I say give it maybe another five years. As for other distos, well forget it. The average Windows user will not switch and if that doesn't matter then what I have said above largely doesn't matter either.

Yeah I will post this now! lol :p

NB

I want Ubuntu to succeed, and I wouldn't post if I didn't have an interest in improving it. I thank Windows 7, but I want to switch.

Ubuntu is still too much of an unfinished jigsaw.

If you have a different point of view, fine. I am merely stating my position for what it is worth and not wishing to debate matters.

---

### Post by fidamehran on 2009-12-06
All thumbs up, u.b.u.n.t.u ! Although I'm not that much into the technical bit like you, but my view is pretty much similar to yours.

Thanks for the tip on the second hard disk. I didn't think of that. Daemon Tools to fire up the ISO. Cool. Although I'm not entirely clear why the ISO would require to be on a different HDD. That would be nearly synonymous to using a burned CD, right? So, I really don't get why my CD install is not working. When the WUBI install is nearly ended, it gives an error and writes the history in some rev160.log file. I can give you the details in the log file if you want.

---

### Post by u.b.u.n.t.u on 2009-12-06
> **fidamehran said:**
> Although I'm not entirely clear why the ISO would require to be on a different HDD.

That HDD is for data. I don't trust Windows enough to store anything of value on the same HDD. I keep Windows well away from my data and I image Windows for a quick few minute re-image if needed. As I do a bit of testing on Windows, a re-image of a fresh install with installed needed applications works very well.

> **fidamehran said:**
> When the WUBI install is nearly ended, it gives an error and writes the history in some rev160.log file. I can give you the details in the log file if you want.

Sure post it here or at least relevant extracts if it is too long.

---

### Post by fidamehran on 2009-12-06
Dear u.b.u.n.t.u,
Are you there? I thought your way would be the solution. I downloaded Daemon Tools Lite and installed it. Loaded the ISO and ran install. But after rebooting, when I select Ubuntu from the Windows bootloader list to complete the installation, this shows up in a black screen:
"Try (hd 0,0): NTFS5S: No wubildr"
What is that?
Sorry to other posters, as probably I'm deviating from the actual post and started posting my own problems here.

---

### Post by fidamehran on 2009-12-06
Here is the content of the "c:\users\fida\appdata\local\temp\wubi-9.10ubuntu1-rev160.log" file.

[PHP]12-06 18:50 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-06 18:50 DEBUG  root: Logfile is c:\users\fida\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-06 18:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="M:\\wubi.exe"', '--cdmenu']
12-06 18:50 DEBUG  CommonBackend: data_dir=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\data
12-06 18:50 DEBUG  WindowsBackend: 7z=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\bin\7z.exe
12-06 18:50 DEBUG  CommonBackend: Fetching basic info...
12-06 18:50 DEBUG  CommonBackend: original_exe=M:\wubi.exe
12-06 18:50 DEBUG  CommonBackend: platform=win32
12-06 18:50 DEBUG  CommonBackend: osname=nt
12-06 18:50 DEBUG  CommonBackend: language=en_US
12-06 18:50 DEBUG  CommonBackend: encoding=cp1252
12-06 18:50 DEBUG  WindowsBackend: arch=amd64
12-06 18:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\data\isolist.ini
12-06 18:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-06 18:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-06 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-06 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-06 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-06 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-06 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-06 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-06 18:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-06 18:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-06 18:50 DEBUG  WindowsBackend: Fetching host info...
12-06 18:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-06 18:50 DEBUG  WindowsBackend: windows version=vista
12-06 18:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-06 18:50 DEBUG  WindowsBackend: windows_sp=None
12-06 18:50 DEBUG  WindowsBackend: windows_build=7600
12-06 18:50 DEBUG  WindowsBackend: gmt=6
12-06 18:50 DEBUG  WindowsBackend: country=US
12-06 18:50 DEBUG  WindowsBackend: timezone=America/New_York
12-06 18:50 DEBUG  WindowsBackend: windows_username=Fida
12-06 18:50 DEBUG  WindowsBackend: user_full_name=Fida
12-06 18:50 DEBUG  WindowsBackend: user_directory=C:\Users\Fida
12-06 18:50 DEBUG  WindowsBackend: windows_language_code=1033
12-06 18:50 DEBUG  WindowsBackend: windows_language=English
12-06 18:50 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
12-06 18:50 DEBUG  WindowsBackend: bootloader=vista
12-06 18:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 302321.667969 mb free ntfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(C: hd 302321.667969 mb free ntfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(D: hd 7701.11328125 mb free ntfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(E: hd 1346.17578125 mb free ntfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(F: hd 3245.46875 mb free fat32)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(G: hd 8463.99609375 mb free ntfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(H: hd 261130.625 mb free ntfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(I: hd 302840.609375 mb free ntfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free cdfs)
12-06 18:50 DEBUG  WindowsBackend: drive=Drive(M: cd 0.0 mb free cdfs)
12-06 18:50 DEBUG  WindowsBackend: uninstaller_path=None
12-06 18:50 DEBUG  WindowsBackend: previous_target_dir=None
12-06 18:50 DEBUG  WindowsBackend: previous_distro_name=None
12-06 18:50 DEBUG  WindowsBackend: keyboard_id=67699721
12-06 18:50 DEBUG  WindowsBackend: keyboard_layout=us
12-06 18:50 DEBUG  WindowsBackend: keyboard_variant=
12-06 18:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-06 18:50 DEBUG  CommonBackend: locale=en_US.UTF-8
12-06 18:50 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-06 18:50 DEBUG  CommonBackend: Searching ISOs on USB devices
12-06 18:50 DEBUG  CommonBackend: Searching for local CDs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook Remix CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu Netbook CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-06 18:50 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-06 18:50 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
12-06 18:50 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-06 18:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-06 18:50 INFO   Distro: Found a valid CD for Ubuntu: M:\
12-06 18:50 INFO   root: Running the CD menu...
12-06 18:50 DEBUG  WindowsFrontend: __init__...
12-06 18:50 DEBUG  WindowsFrontend: on_init...
12-06 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\translations, languages=['en_US', 'en']
12-06 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\translations, languages=['en_US', 'en']
12-06 18:50 INFO   root: CD menu finished
12-06 18:50 INFO   root: Running the installer...
12-06 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\translations, languages=['en_US', 'en']
12-06 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\translations, languages=['en_US', 'en']
12-06 18:50 DEBUG  WinuiInstallationPage: target_drive=I:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=fida
12-06 18:50 INFO   root: Received settings
12-06 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\translations, languages=['en_US', 'en']
12-06 18:50 DEBUG  TaskList: # Running tasklist...
12-06 18:50 DEBUG  TaskList: ## Running select_target_dir...
12-06 18:50 INFO   WindowsBackend: Installing into I:\ubuntu
12-06 18:50 DEBUG  TaskList: ## Finished select_target_dir
12-06 18:50 DEBUG  TaskList: ## Running create_dir_structure...
12-06 18:50 DEBUG  CommonBackend: Creating dir I:\ubuntu
12-06 18:50 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
12-06 18:50 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
12-06 18:50 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
12-06 18:50 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
12-06 18:50 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
12-06 18:50 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
12-06 18:50 DEBUG  TaskList: ## Finished create_dir_structure
12-06 18:50 DEBUG  TaskList: ## Running uncompress_target_dir...
12-06 18:50 DEBUG  TaskList: ## Finished uncompress_target_dir
12-06 18:50 DEBUG  TaskList: ## Running create_uninstaller...
12-06 18:50 DEBUG  WindowsBackend: Copying uninstaller M:\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString I:\ubuntu\uninstall-wubi.exe
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir I:\ubuntu
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon I:\ubuntu\Ubuntu.ico
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-06 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-06 18:50 DEBUG  TaskList: ## Finished create_uninstaller
12-06 18:50 DEBUG  TaskList: ## Running copy_installation_files...
12-06 18:50 DEBUG  WindowsBackend: Copying C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\data\custom-installation -> I:\ubuntu\install\custom-installation
12-06 18:50 DEBUG  WindowsBackend: Copying C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\winboot -> I:\ubuntu\winboot
12-06 18:50 DEBUG  WindowsBackend: Copying C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\data\images\Ubuntu.ico -> I:\ubuntu\Ubuntu.ico
12-06 18:50 DEBUG  TaskList: ## Finished copy_installation_files
12-06 18:50 DEBUG  TaskList: ## Running get_iso...
12-06 18:50 DEBUG  TaskList: New task copy_file
12-06 18:50 DEBUG  TaskList: ### Running copy_file...
12-06 18:51 DEBUG  TaskList: ### Finished copy_file
12-06 18:51 DEBUG  TaskList: New task check_iso
12-06 18:51 DEBUG  TaskList: ### Running check_iso...
12-06 18:51 DEBUG  CommonBackend: Checking I:\ubuntu\install\installation.iso
12-06 18:51 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu\install\installation.iso
12-06 18:51 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu\install\installation.iso
12-06 18:51 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-06 18:51 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-06 18:51 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu\install\installation.iso
12-06 18:51 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
12-06 18:51 DEBUG  TaskList: New task get_metalink
12-06 18:51 DEBUG  TaskList: #### Running get_metalink...
12-06 18:51 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink > I:\ubuntu\install
12-06 18:51 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-06 18:51 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-i386.metalink > I:\ubuntu\install
12-06 18:51 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-06 18:51 DEBUG  TaskList: #### Finished get_metalink
12-06 18:51 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for I:\ubuntu\install\installation.iso, ignoring
12-06 18:51 DEBUG  TaskList: ### Finished check_iso
12-06 18:51 DEBUG  TaskList: ## Finished get_iso
12-06 18:51 DEBUG  TaskList: ## Running extract_kernel...
12-06 18:51 DEBUG  CommonBackend: Copying files from CD M:\
12-06 18:51 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
12-06 18:51 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\vmlinuz
12-06 18:51 DEBUG  CommonBackend:   I:\ubuntu\install\boot\vmlinuz md5 = 284af6e5e36cc3cd8c096b00ad4a3f96 == 284af6e5e36cc3cd8c096b00ad4a3f96
12-06 18:51 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\initrd.lz
12-06 18:51 DEBUG  CommonBackend:   I:\ubuntu\install\boot\initrd.lz md5 = f74d16c6b6e4d182e009a50898df7761 == f74d16c6b6e4d182e009a50898df7761
12-06 18:51 DEBUG  TaskList: ## Finished extract_kernel
12-06 18:51 DEBUG  TaskList: ## Running choose_disk_sizes...
12-06 18:51 DEBUG  WindowsBackend: total size=8000
  root=7744
  swap=256
  home=0
  usr=0
12-06 18:51 DEBUG  TaskList: ## Finished choose_disk_sizes
12-06 18:51 DEBUG  TaskList: ## Running create_preseed...
12-06 18:51 DEBUG  TaskList: ## Finished create_preseed
12-06 18:51 DEBUG  TaskList: ## Running modify_bootloader...
12-06 18:51 DEBUG  TaskList: New task modify_bcd
12-06 18:51 DEBUG  TaskList: ### Running modify_bcd...
12-06 18:51 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 302321.667969 mb free ntfs)
12-06 18:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {82ec0fd8-b065-11de-81d7-eaf807b62f02}
12-06 18:51 DEBUG  TaskList: ### Finished modify_bcd
12-06 18:51 DEBUG  TaskList: New task modify_bcd
12-06 18:51 DEBUG  TaskList: ### Running modify_bcd...
12-06 18:51 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 7701.11328125 mb free ntfs)
12-06 18:51 DEBUG  WindowsBackend: BCD has already been modified
12-06 18:51 DEBUG  TaskList: ### Finished modify_bcd
12-06 18:51 DEBUG  TaskList: New task modify_bcd
12-06 18:51 DEBUG  TaskList: ### Running modify_bcd...
12-06 18:51 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 1346.17578125 mb free ntfs)
12-06 18:51 DEBUG  WindowsBackend: BCD has already been modified
12-06 18:51 DEBUG  TaskList: ### Finished modify_bcd
12-06 18:51 DEBUG  TaskList: New task modify_bcd
12-06 18:51 DEBUG  TaskList: ### Running modify_bcd...
12-06 18:51 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 3245.46875 mb free fat32)
12-06 18:51 DEBUG  WindowsBackend: BCD has already been modified
12-06 18:51 DEBUG  TaskList: ### Finished modify_bcd
12-06 18:51 DEBUG  TaskList: New task modify_bcd
12-06 18:51 DEBUG  TaskList: ### Running modify_bcd...
12-06 18:51 DEBUG  WindowsBackend: modify_bcd Drive(G: hd 8463.99609375 mb free ntfs)
12-06 18:51 DEBUG  WindowsBackend: BCD has already been modified
12-06 18:51 DEBUG  TaskList: ### Finished modify_bcd
12-06 18:51 DEBUG  TaskList: New task modify_bcd
12-06 18:51 DEBUG  TaskList: ### Running modify_bcd...
12-06 18:51 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 261130.625 mb free ntfs)
12-06 18:51 DEBUG  WindowsBackend: BCD has already been modified
12-06 18:51 DEBUG  TaskList: ### Finished modify_bcd
12-06 18:51 DEBUG  TaskList: New task modify_bcd
12-06 18:51 DEBUG  TaskList: ### Running modify_bcd...
12-06 18:51 DEBUG  WindowsBackend: modify_bcd Drive(I: hd 302840.609375 mb free ntfs)
12-06 18:51 DEBUG  WindowsBackend: BCD has already been modified
12-06 18:51 DEBUG  TaskList: ### Finished modify_bcd
12-06 18:51 DEBUG  TaskList: ## Finished modify_bootloader
12-06 18:51 DEBUG  TaskList: ## Running modify_grub_configuration...
12-06 18:51 DEBUG  TaskList: ## Finished modify_grub_configuration
12-06 18:51 DEBUG  TaskList: ## Running create_virtual_disks...
12-06 18:51 DEBUG  Virtualdisk:  Creating virtual disk I:\ubuntu\disks\root.disk of 7744MB
12-06 18:51 DEBUG  Virtualdisk:  Creating virtual disk I:\ubuntu\disks\swap.disk of 256MB
12-06 18:51 DEBUG  TaskList: ## Finished create_virtual_disks
12-06 18:51 DEBUG  TaskList: ## Running uncompress_files...
12-06 18:51 DEBUG  WindowsBackend: compact I:\ubuntu\install\boot /U /A /F
12-06 18:51 DEBUG  WindowsBackend: compact I:\ubuntu\install\boot\*.* /U /A /F
12-06 18:51 DEBUG  TaskList: ## Finished uncompress_files
12-06 18:51 DEBUG  TaskList: ## Running eject_cd...
12-06 18:51 DEBUG  TaskList: ## Finished eject_cd
12-06 18:51 DEBUG  TaskList: # Finished tasklist
12-06 18:51 INFO   root: Almost finished installing
12-06 18:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Fida\AppData\Local\Temp\pylE4B3.tmp\translations, languages=['en_US', 'en']
12-06 18:51 INFO   root: Finished installation
12-06 18:51 INFO   root: Rebooting
12-06 18:51 DEBUG  TaskList: # Running tasklist...
12-06 18:51 DEBUG  TaskList: ## Running reboot...
12-06 18:51 DEBUG  TaskList: ## Finished reboot
12-06 18:51 DEBUG  TaskList: # Finished tasklist
12-06 18:51 DEBUG  root: application.quit
12-06 18:51 DEBUG  WindowsFrontend: frontend.quit
12-06 18:51 DEBUG  WindowsFrontend: frontend.on_quit
12-06 18:51 DEBUG  root: application.on_quit
12-06 18:51 INFO   root: sys.exit
[/PHP]

---

### Post by fidamehran on 2009-12-06
Sorry, double post

---

### Post by u.b.u.n.t.u on 2009-12-06
> **fidamehran said:**
> Dear u.b.u.n.t.u,
Are you there? I thought your way would be the solution. I downloaded Daemon Tools Lite and installed it. Loaded the ISO and ran install. But after rebooting, when I select Ubuntu from the Windows bootloader list to complete the installation, this shows up in a black screen:
"Try (hd 0,0): NTFS5S: No wubildr"
What is that?
Sorry to other posters, as probably I'm deviating from the actual post and started posting my own problems here.


Time zones. We are in two different time zones. It is morning here so at about the time of my last post it was well into the night.

I have looked at the log twice. I am simply reading it and cannot determine any problems related by it.

I think it best to start at the very beginning and walk through from there. That will help me to better place things in a context.

So to start, as I understand it.

Problem:

You have two HDD. You are running Windows 7 on one HDD and wish to install Ubuntu 9.10 via wubi, so a virtual install on Windows 7, is that correct?

What is the capacity of the HDDS?

What is your GPU?

How much RAM? (Running Windows 7 I would think 4GB+)

What is the source of your Ubuntu 9.10 CD?

Once this is established we can narrow down matters.

I do agree this deserves it's own thread because, although it may be similar to the OP, this is your problem and not his. It also helps anyone using the search to keep it simple as possible. Your call.

If you start a new thread, just add a link here.

---

### Post by fidamehran on 2009-12-07
Ok, here goes:
Yeah, right. I have two HDDs. One 1 TB (running Windows 7 on C: drive, has 2 more drives). The other one 80GB (where I put the Ubuntu ISO file.)

I have 3 GB of RAM, which is handling Win7 pretty well.

I have a Pentium Dual Core @1.8 GHz each processor.

My GPU is a Nvidia Geforce 8600GT with 1 GB VRAM.

I got my Ubuntu CD ISO from Ubuntu's own website from a mirror from Taiwan, I think.

By the way, I saw in another post ([http://ubuntuforums.org/showthread.php?t=1308098]("http://ubuntuforums.org/showthread.php?t=1308098")) where a person mentioned something like this:

[PHP]The general goal is to reproduce exactly what the Wubi installer would have done for Windows 7 (without it going through and making a fresh Ubuntu disk image and install... the disk image is independent of the Windows versions). I assume Ubuntu was installed in C:\ubuntu in the old OS. These same instructions will work if the target system is Vista as well.

1. Copy C:\ubuntu to C:\ubuntu from the old system to the new system.
2. Copy the two files C:\ubuntu\winboot\wubildr and C:\ubuntu\winboot\wubildr.mbr to C:\
3. Go to Start and type in cmd. Right-click cmd.exe and click Run as Administrator.
4. In the cmd window, issue the command: bcdedit /create /d "Ubuntu" /application bootsector
5. Note down the UUID identifier the command returns. Mine is {773d31e4-c3bd-11de-83ed-b036f4cbaf34} but yours will be different. You will need this identifier for the next steps.
6. Enter the command: bcdedit /set {your-identifier} device partition=C:
7. Enter the command: bcdedit /set {your-identifier} path \ubuntu\winboot\wubildr.mbr
8. Enter the command: bcdedit /displayorder {your-identifier} /addlast
9. Enter the command: bcdedit /timeout 10
10. Enter the command: fsutil fsinfo ntfsinfo C:

Note down what it says for "NTFS Volume Serial Number". Take what is after the 0x and capitalize any letters in the serial number. You should end up with something that's 16 characters long with numbers and capital letters.

11. Open C:\ubuntu\disks\boot\grub\menu.lst with a text editor that can handle UNIX newlines (like Notepad2: www.flos-freeware.ch/notepad2.html). This is your new partition UUID

12. Replace all instances of root=UUID=XXXXXXXXXXXXXXXX (where XXXXXXXXXXXXXXXX is your old partition's UUID) with the new partition UUID.

That's it. Reboot and you'll be able to select Ubuntu from the boot menu.

You can also replace C: with any other local drive letter if you put the Wubi files elsewhere. Steps 10-12 are just the extra steps for migration.[/PHP]

You think that is a proper solution? Don't know if I should mess with the BCDEDIT myself, though.

---

### Post by u.b.u.n.t.u on 2009-12-07
I cannot comment on that recommendation but if you try it, back everything up and know how to revert back to a working system.

My HDDs are seagate and I only mention this because they have a free True Image clone than images HDD. So it takes me but minutes to re-image my entire 7 Windows and settings. Perhaps have a system like that and clonezilla also has a good reputatuion.

So the 80 GB HDD with the Ubuntu 9.10 ISO, you are trying to write back onto the 80 GB HDD with an install of Ubuntu 9.10?

Have you tried the options such as:

1. ISO on Windows 7 HDD and install from there to 80 GB HDD.

2. Try the 80 GB HDD as an NTFS and Ext4 file format.

3. Burn the Ubuntu 9.10 ISO to a CD or DVD.

4. Download the ISO again but from a different source. 

5. A variation of the above.

It really is a matter of trial and error for it should work without the need to edit the boot loader.

---

### Post by fidamehran on 2009-12-07
I couldn't agree more. Why should I, an average user, go into the trouble of editing the bootloader?

As for your statements, No, I don't have any images of the HDD, or not even RAID. In fact, I don't understand the RAID thing quite. Anyway, that's not point of discussion here.

As for your next paragraph
> So the 80 GB HDD with the Ubuntu 9.10 ISO, you are trying to write back onto the 80 GB HDD with an install of Ubuntu 9.10?
No, in fact, I was trying to put the ISO on the 80GB, and install Ubuntu to the 1TB HDD. Both the drives where the ISO is and also the ones where I was trying to install Ubuntu (a drive other than the C: drive where the Win 7 is installed) are NTFS.

> 1. ISO on Windows 7 HDD and install from there to 80 GB HDD.
No, I haven't tried that. I'll definitely try it out. Thinking positively all the time. Trying not to think it'll not work.

> 2. Try the 80 GB HDD as an NTFS and Ext4 file format.
Do you mean, to keep one drive in the 80 GB as NTFS (where the ISO will be) and another drive in the 80 GB as Ext4 (where I'll install the Ubuntu)? No, I haven't tried that. And there's just another problem. I don't know how to convert drive to Ext4. Is there any way to convert a drive to Ext4 from within Windows (install gparted?)? I use Easeus Partition Manager to convert my drives (from FAT32 to NTFS that is).

> 3. Burn the Ubuntu 9.10 ISO to a CD or DVD.
I already have burnt an Ubuntu CD, installing from there doesn't even reach up to the Rebooting prompt. As I mentioned earlier, near the end of the installing, gives an error and writes a log at "wubi-9.10ubuntu1-rev160.log". [I think that log had a different content than the one I posted to you, as the posted log comes from a Wubi-ISO installation.

> 4. Download the ISO again but from a different source.
You mean, not from Ubuntu.com itself? Hmm. Really? Let me see who else has the download.

> 5. A variation of the above.
Phew! only if I knew.
:-)

Thanks for your continuous effort behind me. I guess friends are not made just through face to face introduction.

---

### Post by u.b.u.n.t.u on 2009-12-07
> **fidamehran said:**
> Do you mean, to keep one drive in the 80 GB as NTFS (where the ISO will be) and another drive in the 80 GB as Ext4 (where I'll install the Ubuntu)? 

I misunderstood. I thought you were trying to install onto the 80GB HDD. You clarified that you want to install Ubuntu onto the 1TB HDD.


> **fidamehran said:**
> I don't know how to convert drive to Ext4. Is there any way to convert a drive to Ext4 from within Windows (install gparted?)? I use Easeus Partition Manager to convert my drives (from FAT32 to NTFS that is).

No longer an issue now that I understand you wish to install Ubuntu 9.10 onto the 1TB HDD where Windows 7 currently is.

Ext4 is new and so only the latest linux releases can format a HDD to that file system.

> **fidamehran said:**
> I already have burnt an Ubuntu CD, installing from there doesn't even reach up to the Rebooting prompt. As I mentioned earlier, near the end of the installing, gives an error and writes a log at "wubi-9.10ubuntu1-rev160.log". [I think that log had a different content than the one I posted to you, as the posted log comes from a Wubi-ISO installation.

Any post install log from a failed install is worth checking. If you could post this different log it may prove useful in determining exactly what the problem is.


> **fidamehran said:**
> You mean, not from Ubuntu.com itself? Hmm. Really? Let me see who else has the download.

The thing is it is unclear why you are having this problem, and in such cases everything needs to be checked, double checked and checked again. 

Maybe the image is bad. A download from a different mirror may address that.

This is certainly a perplexing tech challenge.

At this stage:

1. Try the ISO from Windows 7.

2. Download Ubuntu 9.10 again, but from a different mirror. Rename your current ISO with a prefix or suffix "ORIGINAL_DOWNLOAD".

3. Post any install log that is different to what you have already posted.

Let us see if this advances the matter any.


UPDATE


4. Windows 7
Control Panel > Programs and Features
Do you see Ubuntu listed?

---

### Post by steveneddy on 2009-12-07
I've stated this a million times:

Wubi sucks.

Use a VM so it will work correctly.

Wubi was only designed to be used as a "try it out" option, not for a permanent install.

Use Virtualbox, you will be much happier.

---

### Post by Slim Odds on 2009-12-07
> **u.b.u.n.t.u said:**
> ...

By the way, just off topic, I had a look Wasilla, Alaska in google and wow, just wow! 

How awesome is this!

[IMG]http://img268.imageshack.us/img268/7518/wasillaalaska.jpg[/IMG]

To be fair and open, I live in Melbourne, Australia.

Beautiful, but the average high temp in July is 69F

A little cool for me.... ;)

---

### Post by u.b.u.n.t.u on 2009-12-07
> **steveneddy said:**
> I've stated this a million times:

Wubi sucks.

Use a VM so it will work correctly.

Wubi was only designed to be used as a "try it out" option, not for a permanent install.

Use Virtualbox, you will be much happier.

I note your technical assessment that wubi "sucks". I think that fidamehran is aware that wubi may not install first time every time, that alternatives exist, and maybe fidamehran doesn't want to turn back at the first sign of a technical challenge.

Maybe you missed this part:

> **fidamehran said:**
> It's good to see that an experienced Ubuntu user like you is not one of the Wubi-bashers. I personally have been using Ubuntu since 7.04 and everytime through Wubi.

---

### Post by u.b.u.n.t.u on 2009-12-07
> **Slim Odds said:**
> Beautiful, but the average high temp in July is 69F

A little cool for me.... ;)


You may wish to check this out, a dedicated thread by Shibblet.
[http://ubuntuforums.org/showthread.php?t=1343638](http://ubuntuforums.org/showthread.php?t=1343638)

---

### Post by fidamehran on 2009-12-08
Thanks u.b.u.t.u (Gee, it's tough to type your name),
I'll try out your suggestions. Not sure how soon, though. 'Cause I feel I'll become terribly busy at office the coming days [end of year.... annual report.... :-( ]
But still, I keep this page saved in the session saver, so that I can check when and what you replied.
Hope you'll still find my post (even if after a few days) with updates on what happenned.
In the mean time, start your holidays celebration and get in the mood. Wubi can wait a bit.... :-)

---

