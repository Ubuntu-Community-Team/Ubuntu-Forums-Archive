---
title: "Not able to install ubuntu"
date: 2010-06-04
forum: General Help
---

### Post by vibhor on 2010-06-04
[FONT=Arial Narrow][SIZE=3][B]hello all.
I am just new for ubuntu.
As i made a bootable Cd of Ubuntu the i just rebooted my pc
then Cd booted and a screen came

After few seconds is give an error CANNOT BOOT CD REBOOT IT.
Everytime its giving this error to me. as i can boot other cds on it.

When i try to install it inside my window then again at the last moment error occurs i am giving a screen shot of error comes..

is there any hardware requirement to install it???

[IMG]http://i50.tinypic.com/2ypi72h.jpg[/IMG]

Here is the logfile details

```

06-04 11:20 INFO   root: === wubi 10.04 rev189 ===
06-04 11:20 DEBUG  root: Logfile is c:\docume~1\moni\locals~1\temp\wubi-10.04-rev189.log
06-04 11:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
06-04 11:20 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\data
06-04 11:20 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
06-04 11:20 DEBUG  CommonBackend: Fetching basic info...
06-04 11:20 DEBUG  CommonBackend: original_exe=G:\wubi.exe
06-04 11:20 DEBUG  CommonBackend: platform=win32
06-04 11:20 DEBUG  CommonBackend: osname=nt
06-04 11:20 DEBUG  CommonBackend: language=en_US
06-04 11:20 DEBUG  CommonBackend: encoding=cp1252
06-04 11:20 DEBUG  WindowsBackend: arch=amd64
06-04 11:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
06-04 11:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-04 11:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-04 11:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-04 11:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-04 11:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-04 11:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-04 11:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-04 11:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-04 11:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-04 11:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-04 11:20 DEBUG  WindowsBackend: Fetching host info...
06-04 11:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-04 11:20 DEBUG  WindowsBackend: windows version=xp
06-04 11:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-04 11:20 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-04 11:20 DEBUG  WindowsBackend: windows_build=2600
06-04 11:20 DEBUG  WindowsBackend: gmt=5
06-04 11:20 DEBUG  WindowsBackend: country=US
06-04 11:20 DEBUG  WindowsBackend: timezone=America/New_York
06-04 11:20 DEBUG  WindowsBackend: windows_username=Moni
06-04 11:20 DEBUG  WindowsBackend: user_full_name=Moni
06-04 11:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Moni
06-04 11:20 DEBUG  WindowsBackend: windows_language_code=1033
06-04 11:20 DEBUG  WindowsBackend: windows_language=English
06-04 11:20 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) D CPU 2.80GHz
06-04 11:20 DEBUG  WindowsBackend: bootloader=xp
06-04 11:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33577.0078125 mb free ntfs)
06-04 11:20 DEBUG  WindowsBackend: drive=Drive(C: hd 33577.0078125 mb free ntfs)
06-04 11:20 DEBUG  WindowsBackend: drive=Drive(D: hd 36853.5507813 mb free ntfs)
06-04 11:20 DEBUG  WindowsBackend: drive=Drive(E: hd 39267.3242188 mb free ntfs)
06-04 11:20 DEBUG  WindowsBackend: drive=Drive(F: hd 33187.3007813 mb free ntfs)
06-04 11:20 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
06-04 11:20 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
06-04 11:20 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
06-04 11:20 DEBUG  WindowsBackend: uninstaller_path=None
06-04 11:20 DEBUG  WindowsBackend: previous_target_dir=None
06-04 11:20 DEBUG  WindowsBackend: previous_distro_name=None
06-04 11:20 DEBUG  WindowsBackend: keyboard_id=67699721
06-04 11:20 DEBUG  WindowsBackend: keyboard_layout=us
06-04 11:20 DEBUG  WindowsBackend: keyboard_variant=
06-04 11:20 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-04 11:20 DEBUG  CommonBackend: locale=en_US.UTF-8
06-04 11:20 DEBUG  WindowsBackend: total_memory_mb=2037.41796875
06-04 11:20 DEBUG  CommonBackend: Searching ISOs on USB devices
06-04 11:20 DEBUG  CommonBackend: Searching for local CDs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-04 11:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-04 11:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-04 11:20 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
06-04 11:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-04 11:20 INFO   Distro: Found a valid CD for Ubuntu: G:\
06-04 11:20 INFO   root: Running the CD menu...
06-04 11:20 DEBUG  WindowsFrontend: __init__...
06-04 11:20 DEBUG  WindowsFrontend: on_init...
06-04 11:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-04 11:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-04 11:20 INFO   root: CD menu finished
06-04 11:20 INFO   root: Running the installer...
06-04 11:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-04 11:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-04 11:21 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=moni
06-04 11:21 INFO   root: Received settings
06-04 11:21 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-04 11:21 DEBUG  TaskList: # Running tasklist...
06-04 11:21 DEBUG  TaskList: ## Running select_target_dir...
06-04 11:21 INFO   WindowsBackend: Installing into C:\ubuntu
06-04 11:21 DEBUG  TaskList: ## Finished select_target_dir
06-04 11:21 DEBUG  TaskList: ## Running create_dir_structure...
06-04 11:21 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-04 11:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-04 11:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-04 11:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-04 11:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-04 11:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-04 11:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-04 11:21 DEBUG  TaskList: ## Finished create_dir_structure
06-04 11:21 DEBUG  TaskList: ## Running uncompress_target_dir...
06-04 11:21 DEBUG  TaskList: ## Finished uncompress_target_dir
06-04 11:21 DEBUG  TaskList: ## Running create_uninstaller...
06-04 11:21 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
06-04 11:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
06-04 11:21 DEBUG  TaskList: ## Finished create_uninstaller
06-04 11:21 DEBUG  TaskList: ## Running copy_installation_files...
06-04 11:21 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-04 11:21 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\winboot -> C:\ubuntu\winboot
06-04 11:21 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Moni\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-04 11:21 DEBUG  TaskList: ## Finished copy_installation_files
06-04 11:21 DEBUG  TaskList: ## Running get_iso...
06-04 11:21 DEBUG  TaskList: New task copy_file
06-04 11:21 DEBUG  TaskList: ### Running copy_file...
06-04 11:31 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-04 11:31 DEBUG  TaskList: # Cancelling tasklist
06-04 11:31 DEBUG  TaskList: New task check_iso
06-04 11:31 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-04 11:31 DEBUG  CommonBackend: Searching for local ISO
06-04 11:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-04 11:31 DEBUG  TaskList: New task get_metalink
06-04 11:31 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-04 11:31 DEBUG  TaskList: # Cancelling tasklist
06-04 11:31 DEBUG  TaskList: # Finished tasklist


```

Hope i will get some solution soon :guitar:
[/B][/SIZE][/FONT]

---

### Post by davidmohammed on 2010-06-04
have you got administrator rights on your windows PC?  If not, install as administrator.

---

### Post by julio_cortez on 2010-06-04
> **davidmohammed said:**
> have you got administrator rights on your windows PC?  If not, install as administrator.
Well, if he loads the CD at boot time (thing that he tried) no Windows administrative rights are asked because Windows hasn't started yet (remember he's booting from CD and not from HD).

To me, the fact that both CD boot and Wubi (I guess) install return errors means that probably either the CD has errors or the image is broken.
Probably another CD is needed (it will also be useful to check the md5 of the image to be sure it's not broken, before burning it again).

---

### Post by olig1905 on 2010-06-04
Sounds like you have a dodgy cd.

Which best advice is to burn it at a slow speed, often high speed drives write the iso images badly.

So when your using your cd burning software there will be an option to set burn speed. Just choose the slowest, probably 4x.

You can then check the md5 but chances are with this method it wont be necessary

---

### Post by mick222 on 2010-06-04
Have you checked the CD see this thread [http://ubuntuforums.org/showthread.php?t=1426779](http://ubuntuforums.org/showthread.php?t=1426779) It might also be useful to list your hardware especially your Graphics card. If the cd does not get to the screen with try ubuntu and install Ubuntu it could be a bad burn so burn it at a lower speed. 
    Wubi does not need a cd if you go to [http://wubi-installer.org/](http://wubi-installer.org/) it should install inside windows but is not as good as a full install but maybe worth a try to start with you can uninstall it like a Window program from add remove when you feel able to go for a full install.

---

