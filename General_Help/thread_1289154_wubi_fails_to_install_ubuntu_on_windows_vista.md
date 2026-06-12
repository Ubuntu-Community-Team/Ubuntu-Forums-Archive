---
title: "wubi fails to install ubuntu on windows vista"
date: 2009-10-12
forum: General Help
---

### Post by Rodart on 2009-10-12
Hi, so i tried to install ubuntu from the cd into windows vista , with the wubi thing, the installagion starts and it gives me an error,if i select the installation lenguage as Spanish, I have a screen shot:
 
[http://img195.imageshack.us/img195/7254/ubuntuerror.jpg](http://img195.imageshack.us/img195/7254/ubuntuerror.jpg)
 
and the log:
> 10-12 06:26 INFO root: === wubi 9.04 rev128 ===
10-12 06:26 DEBUG root: Logfile is c:\users\rodro\appdata\local\temp\wubi-9.04-rev128.log
10-12 06:26 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
10-12 06:26 DEBUG CommonBackend: data_dir=C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\data
10-12 06:26 DEBUG WindowsBackend: 7z=C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\bin\7z.exe
10-12 06:26 DEBUG CommonBackend: Fetching basic info...
10-12 06:26 DEBUG CommonBackend: original_exe=D:\wubi.exe
10-12 06:26 DEBUG CommonBackend: platform=win32
10-12 06:26 DEBUG CommonBackend: osname=nt
10-12 06:26 DEBUG CommonBackend: language=en_US
10-12 06:26 DEBUG CommonBackend: encoding=cp1252
10-12 06:26 DEBUG WindowsBackend: arch=amd64
10-12 06:26 DEBUG CommonBackend: Parsing isolist=C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\data\isolist.ini
10-12 06:26 DEBUG CommonBackend: Adding distro Xubuntu-i386
10-12 06:26 DEBUG CommonBackend: Adding distro Xubuntu-amd64
10-12 06:26 DEBUG CommonBackend: Adding distro Kubuntu-amd64
10-12 06:26 DEBUG CommonBackend: Adding distro Mythbuntu-i386
10-12 06:26 DEBUG CommonBackend: Adding distro Ubuntu-amd64
10-12 06:26 DEBUG CommonBackend: Adding distro Ubuntu-i386
10-12 06:26 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
10-12 06:26 DEBUG CommonBackend: Adding distro Kubuntu-i386
10-12 06:26 DEBUG WindowsBackend: Fetching host info...
10-12 06:26 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-12 06:26 DEBUG WindowsBackend: windows version=vista
10-12 06:26 DEBUG WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
10-12 06:26 DEBUG WindowsBackend: windows_sp=Service Pack 1
10-12 06:26 DEBUG WindowsBackend: windows_build=6001
10-12 06:26 DEBUG WindowsBackend: gmt=-3
10-12 06:26 DEBUG WindowsBackend: country=US
10-12 06:26 DEBUG WindowsBackend: timezone=America/North_Dakota/Center
10-12 06:26 DEBUG WindowsBackend: windows_username=rodro
10-12 06:26 DEBUG WindowsBackend: user_full_name=rodro
10-12 06:26 DEBUG WindowsBackend: user_directory=rodro
10-12 06:26 DEBUG WindowsBackend: windows_language_code=1033
10-12 06:26 DEBUG WindowsBackend: windows_language=English
10-12 06:26 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
10-12 06:26 DEBUG WindowsBackend: bootloader=vista
10-12 06:26 DEBUG WindowsBackend: system_drive=Drive(C: hd 30567.4609375 mb free )
10-12 06:26 DEBUG WindowsBackend: drive=Drive(C: hd 30567.4609375 mb free )
10-12 06:26 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-12 06:26 DEBUG WindowsBackend: uninstaller_path=None
10-12 06:26 DEBUG WindowsBackend: previous_target_dir=None
10-12 06:26 DEBUG WindowsBackend: previous_distro_name=None
10-12 06:26 DEBUG WindowsBackend: keyboard_id=67765257
10-12 06:26 DEBUG WindowsBackend: keyboard_layout=us
10-12 06:26 DEBUG WindowsBackend: keyboard_variant=
10-12 06:26 DEBUG CommonBackend: locale=en_US.UTF-8
10-12 06:26 DEBUG WindowsBackend: total_memory_mb=2046.5703125
10-12 06:26 DEBUG CommonBackend: Searching ISOs on USB devices
10-12 06:26 DEBUG CommonBackend: Searching for local CDs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Ubuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Ubuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Kubuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Kubuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Xubuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Xubuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Mythbuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp is a valid Mythbuntu CD
10-12 06:26 DEBUG Distro: does not contain C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\casper\filesystem.squashfs
10-12 06:26 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
10-12 06:26 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-12 06:26 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-12 06:26 INFO Distro: Found a valid CD for Ubuntu: D:\
10-12 06:26 INFO root: Running the CD menu...
10-12 06:26 DEBUG WindowsFrontend: __init__...
10-12 06:26 DEBUG WindowsFrontend: on_init...
10-12 06:26 INFO root: CD menu finished
10-12 06:26 INFO root: Running the installer...
10-12 06:27 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=8000MB, distro_name=Ubuntu, language=Spanish, username=rodro
10-12 06:27 INFO root: Received settings
10-12 06:27 DEBUG TaskList: # Running tasklist...
10-12 06:27 DEBUG TaskList: ## Running select_target_dir...
10-12 06:27 INFO WindowsBackend: Installing into C:\ubuntu
10-12 06:27 DEBUG TaskList: ## Finished select_target_dir
10-12 06:27 DEBUG TaskList: ## Running create_dir_structure...
10-12 06:27 DEBUG CommonBackend: Creating dir C:\ubuntu
10-12 06:27 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
10-12 06:27 DEBUG CommonBackend: Creating dir C:\ubuntu\install
10-12 06:27 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
10-12 06:27 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
10-12 06:27 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-12 06:27 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-12 06:27 DEBUG TaskList: ## Finished create_dir_structure
10-12 06:27 DEBUG TaskList: ## Running uncompress_target_dir...
10-12 06:27 DEBUG TaskList: ## Finished uncompress_target_dir
10-12 06:27 DEBUG TaskList: ## Running create_uninstaller...
10-12 06:27 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-12 06:27 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-12 06:27 DEBUG TaskList: ## Finished create_uninstaller
10-12 06:27 DEBUG TaskList: ## Running copy_installation_files...
10-12 06:27 DEBUG WindowsBackend: Copying C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-12 06:27 DEBUG WindowsBackend: Copying C:\Users\rodro\AppData\Local\Temp\pyl4DE1.tmp\winboot -> C:\ubuntu\winboot
10-12 06:27 ERROR TaskList: writelines() argument must be a sequence of strings
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 161, in copy_installation_files
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 257, in replace_line_in_file
TypeError: writelines() argument must be a sequence of strings
10-12 06:27 DEBUG TaskList: # Cancelling tasklist
10-12 06:27 DEBUG TaskList: # Finished tasklist
10-12 06:27 ERROR root: writelines() argument must be a sequence of strings
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
TypeError: writelines() argument must be a sequence of strings

 
 
 
Thanks.
 
Rodart.

---

### Post by Rodart on 2009-10-12
yes this seems to happen only if i choose " Spanish " as the Ubuntu lenguage.

---

### Post by davidryderuk on 2009-10-12
Hello again,
I'm not sure what the problem with choosing spanish during installation is, however it should be relativly simple to install spanish after the installation (although I can't confirm this since I only speak English).

[http://ubuntuforums.org/showthread.php?t=400169](http://ubuntuforums.org/showthread.php?t=400169)

> open a terminal (Applications->Accessories->Terminal)
write:
Code:

sudo aptitude install language-pack-es

this will install Spanish language
now in the login screen you can change the language
press Ctrl-Alt-Backspace for login
select your language from the language menu

---

### Post by Rodart on 2009-10-12
> **davidryderuk said:**
> Hello again,
I'm not sure what the problem with choosing spanish during installation is, however it should be relativly simple to install spanish after the installation (although I can't confirm this since I only speak English).
 
[http://ubuntuforums.org/showthread.php?t=400169](http://ubuntuforums.org/showthread.php?t=400169)
 
 
yes, that worked out fine, Thanks :D.
 
Rodart.

---

