---
title: "Unable to install Ubuntu with Wubi on Win7 64-bit"
date: 2012-09-25
forum: General Help
---

### Post by DarthTurducken on 2012-09-25
First time poster here.  I am trying to run Ubuntu on Windows 7 64-bit using Wubi. On my first couple of tries it gave me the "Extraction failed with code: 2". Then I manually downloaded the iso ubuntu-12.04.1-desktop-i386.iso (choosing the  64-bit version from the dropdown) to my desktop where the wubi.exe is. I'm still having the same issue. It ignores the ISO and tries to download the ubuntu-12.04.1-wubi-amd64.tar.xz file. Thanks for any help you can offer.

Here's the contents of the wubi-12.04-rev269.log:

 09-24 22:45 INFO   root: === wubi 12.04 rev269 === 09-24 22:45 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log 09-24 22:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Downloads\\wubi.exe"'] 09-24 22:45 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\data 09-24 22:45 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\bin\7z.exe 09-24 22:45 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup 09-24 22:45 DEBUG  CommonBackend: Fetching basic info... 09-24 22:45 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Downloads\wubi.exe 09-24 22:45 DEBUG  CommonBackend: platform=win32 09-24 22:45 DEBUG  CommonBackend: osname=nt 09-24 22:45 DEBUG  CommonBackend: language=en_US 09-24 22:45 DEBUG  CommonBackend: encoding=cp1252 09-24 22:45 DEBUG  WindowsBackend: arch=amd64 09-24 22:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\data\isolist.ini 09-24 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-24 22:45 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-24 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-24 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-24 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-24 22:45 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-24 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-24 22:45 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-24 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-24 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-24 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-24 22:45 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-24 22:45 DEBUG  WindowsBackend: Fetching host info... 09-24 22:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-24 22:45 DEBUG  WindowsBackend: windows version=vista 09-24 22:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-24 22:45 DEBUG  WindowsBackend: windows_sp=None 09-24 22:45 DEBUG  WindowsBackend: windows_build=7601 09-24 22:45 DEBUG  WindowsBackend: gmt=-6 09-24 22:45 DEBUG  WindowsBackend: country=US 09-24 22:45 DEBUG  WindowsBackend: timezone=America/Chicago 09-24 22:45 DEBUG  WindowsBackend: windows_username=Marc 09-24 22:45 DEBUG  WindowsBackend: user_full_name=Marc 09-24 22:45 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-24 22:45 DEBUG  WindowsBackend: windows_language_code=1033 09-24 22:45 DEBUG  WindowsBackend: windows_language=English 09-24 22:45 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-24 22:45 DEBUG  WindowsBackend: bootloader=vista 09-24 22:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 269536.660156 mb free ntfs) 09-24 22:45 DEBUG  WindowsBackend: drive=Drive(C: hd 269536.660156 mb free ntfs) 09-24 22:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-24 22:45 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-24 22:45 DEBUG  WindowsBackend: uninstaller_path=None 09-24 22:45 DEBUG  WindowsBackend: previous_target_dir=None 09-24 22:45 DEBUG  WindowsBackend: previous_distro_name=None 09-24 22:45 DEBUG  WindowsBackend: keyboard_id=67699721 09-24 22:45 DEBUG  WindowsBackend: keyboard_layout=us 09-24 22:45 DEBUG  WindowsBackend: keyboard_variant= 09-24 22:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252') 09-24 22:45 DEBUG  CommonBackend: locale=en_US.UTF-8 09-24 22:45 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-24 22:45 DEBUG  CommonBackend: Searching ISOs on USB devices 09-24 22:45 DEBUG  CommonBackend: Searching for local CDs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Ubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Ubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Kubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Kubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Xubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Xubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Mythbuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Mythbuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Edubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Edubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Lubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Lubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:45 INFO   root: Running the installer... 09-24 22:45 DEBUG  WindowsFrontend: __init__... 09-24 22:45 DEBUG  WindowsFrontend: on_init... 09-24 22:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\translations, languages=['en_US', 'en'] 09-24 22:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\translations, languages=['en_US', 'en'] 09-24 22:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc 09-24 22:46 INFO   root: Received settings 09-24 22:46 DEBUG  CommonBackend: Searching for local CD 09-24 22:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Ubuntu CD 09-24 22:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs 09-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:46 DEBUG  CommonBackend: Searching for local ISO 09-24 22:46 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Downloads\Windows 7 32-bit Repair Disc.iso 09-24 22:46 DEBUG  Distro:     does not contain casper\filesystem.squashfs 09-24 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\translations, languages=['en_US', 'en'] 09-24 22:46 DEBUG  TaskList: # Running tasklist... 09-24 22:46 DEBUG  TaskList: ## Running select_target_dir... 09-24 22:46 INFO   WindowsBackend: Installing into C:\ubuntu 09-24 22:46 DEBUG  TaskList: ## Finished select_target_dir 09-24 22:46 DEBUG  TaskList: ## Running create_dir_structure... 09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu 09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks 09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install 09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot 09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot 09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub 09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub 09-24 22:46 DEBUG  TaskList: ## Finished create_dir_structure 09-24 22:46 DEBUG  TaskList: ## Running create_uninstaller... 09-24 22:46 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com) 09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support) 09-24 22:46 DEBUG  TaskList: ## Finished create_uninstaller 09-24 22:46 DEBUG  TaskList: ## Running create_preseed_diskimage... 09-24 22:46 DEBUG  TaskList: ## Finished create_preseed_diskimage 09-24 22:46 DEBUG  TaskList: ## Running get_diskimage... 09-24 22:46 DEBUG  TaskList: New task download 09-24 22:46 DEBUG  TaskList: ### Running download... 09-24 22:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz 09-24 22:46 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None 09-24 22:49 DEBUG  downloader: download finished (read 506056432 bytes) 09-24 22:49 DEBUG  TaskList: ### Finished download 09-24 22:49 DEBUG  TaskList: ## Finished get_diskimage 09-24 22:49 DEBUG  TaskList: ## Running extract_diskimage... 09-24 22:49 ERROR  TaskList: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2 09-24 22:49 DEBUG  TaskList: # Cancelling tasklist 09-24 22:49 DEBUG  TaskList: # Finished tasklist 09-24 22:49 ERROR  root: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\application.py", line 58, in run   File "\lib\wubi\application.py", line 132, in select_task   File "\lib\wubi\application.py", line 158, in run_installer   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2 09-24 22:50 INFO   root: === wubi 12.04 rev269 === 09-24 22:50 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log 09-24 22:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"'] 09-24 22:50 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\data 09-24 22:50 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\bin\7z.exe 09-24 22:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup 09-24 22:50 DEBUG  CommonBackend: Fetching basic info... 09-24 22:50 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe 09-24 22:50 DEBUG  CommonBackend: platform=win32 09-24 22:50 DEBUG  CommonBackend: osname=nt 09-24 22:50 DEBUG  CommonBackend: language=en_US 09-24 22:50 DEBUG  CommonBackend: encoding=cp1252 09-24 22:50 DEBUG  WindowsBackend: arch=amd64 09-24 22:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\data\isolist.ini 09-24 22:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-24 22:50 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-24 22:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-24 22:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-24 22:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-24 22:50 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-24 22:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-24 22:50 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-24 22:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-24 22:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-24 22:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-24 22:50 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-24 22:50 DEBUG  WindowsBackend: Fetching host info... 09-24 22:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-24 22:50 DEBUG  WindowsBackend: windows version=vista 09-24 22:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-24 22:50 DEBUG  WindowsBackend: windows_sp=None 09-24 22:50 DEBUG  WindowsBackend: windows_build=7601 09-24 22:50 DEBUG  WindowsBackend: gmt=-6 09-24 22:50 DEBUG  WindowsBackend: country=US 09-24 22:50 DEBUG  WindowsBackend: timezone=America/Chicago 09-24 22:50 DEBUG  WindowsBackend: windows_username=Marc 09-24 22:50 DEBUG  WindowsBackend: user_full_name=Marc 09-24 22:50 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-24 22:50 DEBUG  WindowsBackend: windows_language_code=1033 09-24 22:50 DEBUG  WindowsBackend: windows_language=English 09-24 22:50 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-24 22:50 DEBUG  WindowsBackend: bootloader=vista 09-24 22:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268553.949219 mb free ntfs) 09-24 22:50 DEBUG  WindowsBackend: drive=Drive(C: hd 268553.949219 mb free ntfs) 09-24 22:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-24 22:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-24 22:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe 09-24 22:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu 09-24 22:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu 09-24 22:50 DEBUG  WindowsBackend: keyboard_id=67699721 09-24 22:50 DEBUG  WindowsBackend: keyboard_layout=us 09-24 22:50 DEBUG  WindowsBackend: keyboard_variant= 09-24 22:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252') 09-24 22:50 DEBUG  CommonBackend: locale=en_US.UTF-8 09-24 22:50 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-24 22:50 DEBUG  CommonBackend: Searching ISOs on USB devices 09-24 22:50 DEBUG  CommonBackend: Searching for local CDs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:50 INFO   root: Already installed, running the uninstaller... 09-24 22:50 INFO   root: Running the uninstaller... 09-24 22:50 INFO   CommonBackend: This is the uninstaller running 09-24 22:50 DEBUG  WindowsFrontend: __init__... 09-24 22:50 DEBUG  WindowsFrontend: on_init... 09-24 22:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en'] 09-24 22:50 INFO   root: Received settings 09-24 22:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en'] 09-24 22:50 DEBUG  TaskList: # Running tasklist... 09-24 22:50 DEBUG  TaskList: ## Running Remove bootloader entry... 09-24 22:50 DEBUG  WindowsBackend: Could not find bcd id 09-24 22:50 DEBUG  WindowsBackend: undo_bootini C: 09-24 22:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 268553.949219 mb free ntfs) 09-24 22:51 DEBUG  TaskList: ## Finished Remove bootloader entry 09-24 22:51 DEBUG  TaskList: ## Running Remove target dir... 09-24 22:51 DEBUG  CommonBackend: Deleting C:\ubuntu 09-24 22:51 DEBUG  TaskList: ## Finished Remove target dir 09-24 22:51 DEBUG  TaskList: ## Running Remove registry key... 09-24 22:51 DEBUG  TaskList: ## Finished Remove registry key 09-24 22:51 DEBUG  TaskList: # Finished tasklist 09-24 22:51 INFO   root: Almost finished uninstalling 09-24 22:51 INFO   root: Finished uninstallation 09-24 22:51 DEBUG  CommonBackend: Fetching basic info... 09-24 22:51 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe 09-24 22:51 DEBUG  CommonBackend: platform=win32 09-24 22:51 DEBUG  CommonBackend: osname=nt 09-24 22:51 DEBUG  WindowsBackend: arch=amd64 09-24 22:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\data\isolist.ini 09-24 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-24 22:51 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-24 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-24 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-24 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-24 22:51 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-24 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-24 22:51 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-24 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-24 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-24 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-24 22:51 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-24 22:51 DEBUG  WindowsBackend: Fetching host info... 09-24 22:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-24 22:51 DEBUG  WindowsBackend: windows version=vista 09-24 22:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-24 22:51 DEBUG  WindowsBackend: windows_sp=None 09-24 22:51 DEBUG  WindowsBackend: windows_build=7601 09-24 22:51 DEBUG  WindowsBackend: gmt=-6 09-24 22:51 DEBUG  WindowsBackend: country=US 09-24 22:51 DEBUG  WindowsBackend: timezone=America/Chicago 09-24 22:51 DEBUG  WindowsBackend: windows_username=Marc 09-24 22:51 DEBUG  WindowsBackend: user_full_name=Marc 09-24 22:51 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-24 22:51 DEBUG  WindowsBackend: windows_language_code=1033 09-24 22:51 DEBUG  WindowsBackend: windows_language=English 09-24 22:51 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-24 22:51 DEBUG  WindowsBackend: bootloader=vista 09-24 22:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 269185.140625 mb free ntfs) 09-24 22:51 DEBUG  WindowsBackend: drive=Drive(C: hd 269185.140625 mb free ntfs) 09-24 22:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-24 22:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-24 22:51 DEBUG  WindowsBackend: uninstaller_path=None 09-24 22:51 DEBUG  WindowsBackend: previous_target_dir=None 09-24 22:51 DEBUG  WindowsBackend: previous_distro_name=None 09-24 22:51 DEBUG  WindowsBackend: keyboard_id=67699721 09-24 22:51 DEBUG  WindowsBackend: keyboard_layout=us 09-24 22:51 DEBUG  WindowsBackend: keyboard_variant= 09-24 22:51 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-24 22:51 DEBUG  CommonBackend: Searching ISOs on USB devices 09-24 22:51 DEBUG  CommonBackend: Searching for local CDs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 INFO   root: Running the installer... 09-24 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en'] 09-24 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en'] 09-24 22:51 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc 09-24 22:51 INFO   root: Received settings 09-24 22:51 DEBUG  CommonBackend: Searching for local CD 09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-24 22:51 DEBUG  CommonBackend: Searching for local ISO 09-24 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en'] 09-24 22:51 DEBUG  TaskList: # Running tasklist... 09-24 22:51 DEBUG  TaskList: ## Running select_target_dir... 09-24 22:51 INFO   WindowsBackend: Installing into C:\ubuntu 09-24 22:51 DEBUG  TaskList: ## Finished select_target_dir 09-24 22:51 DEBUG  TaskList: ## Running create_dir_structure... 09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu 09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks 09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install 09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot 09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot 09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub 09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub 09-24 22:51 DEBUG  TaskList: ## Finished create_dir_structure 09-24 22:51 DEBUG  TaskList: ## Running create_uninstaller... 09-24 22:51 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com) 09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support) 09-24 22:51 DEBUG  TaskList: ## Finished create_uninstaller 09-24 22:51 DEBUG  TaskList: ## Running create_preseed_diskimage... 09-24 22:51 DEBUG  TaskList: ## Finished create_preseed_diskimage 09-24 22:51 DEBUG  TaskList: ## Running get_diskimage... 09-24 22:51 DEBUG  TaskList: New task download 09-24 22:51 DEBUG  TaskList: ### Running download... 09-24 22:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz 09-24 22:51 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None 09-24 22:54 DEBUG  downloader: download finished (read 506065192 bytes) 09-24 22:54 DEBUG  TaskList: ### Finished download 09-24 22:54 DEBUG  TaskList: ## Finished get_diskimage 09-24 22:54 DEBUG  TaskList: ## Running extract_diskimage... 09-24 22:54 ERROR  TaskList: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2 09-24 22:54 DEBUG  TaskList: # Cancelling tasklist 09-24 22:54 DEBUG  TaskList: # Finished tasklist 09-24 22:54 ERROR  root: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\application.py", line 58, in run   File "\lib\wubi\application.py", line 132, in select_task   File "\lib\wubi\application.py", line 158, in run_installer   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2 09-25 07:35 INFO   root: === wubi 12.04 rev269 === 09-25 07:35 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log 09-25 07:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"'] 09-25 07:35 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\data 09-25 07:35 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\bin\7z.exe 09-25 07:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup 09-25 07:35 DEBUG  CommonBackend: Fetching basic info... 09-25 07:35 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe 09-25 07:35 DEBUG  CommonBackend: platform=win32 09-25 07:35 DEBUG  CommonBackend: osname=nt 09-25 07:35 DEBUG  CommonBackend: language=en_US 09-25 07:35 DEBUG  CommonBackend: encoding=cp1252 09-25 07:35 DEBUG  WindowsBackend: arch=amd64 09-25 07:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\data\isolist.ini 09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-25 07:35 DEBUG  WindowsBackend: Fetching host info... 09-25 07:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-25 07:35 DEBUG  WindowsBackend: windows version=vista 09-25 07:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-25 07:35 DEBUG  WindowsBackend: windows_sp=None 09-25 07:35 DEBUG  WindowsBackend: windows_build=7601 09-25 07:35 DEBUG  WindowsBackend: gmt=-6 09-25 07:35 DEBUG  WindowsBackend: country=US 09-25 07:35 DEBUG  WindowsBackend: timezone=America/Chicago 09-25 07:35 DEBUG  WindowsBackend: windows_username=Marc 09-25 07:35 DEBUG  WindowsBackend: user_full_name=Marc 09-25 07:35 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-25 07:35 DEBUG  WindowsBackend: windows_language_code=1033 09-25 07:35 DEBUG  WindowsBackend: windows_language=English 09-25 07:35 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-25 07:35 DEBUG  WindowsBackend: bootloader=vista 09-25 07:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 267718.109375 mb free ntfs) 09-25 07:35 DEBUG  WindowsBackend: drive=Drive(C: hd 267718.109375 mb free ntfs) 09-25 07:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-25 07:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-25 07:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe 09-25 07:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu 09-25 07:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu 09-25 07:35 DEBUG  WindowsBackend: keyboard_id=67699721 09-25 07:35 DEBUG  WindowsBackend: keyboard_layout=us 09-25 07:35 DEBUG  WindowsBackend: keyboard_variant= 09-25 07:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252') 09-25 07:35 DEBUG  CommonBackend: locale=en_US.UTF-8 09-25 07:35 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-25 07:35 DEBUG  CommonBackend: Searching ISOs on USB devices 09-25 07:35 DEBUG  CommonBackend: Searching for local CDs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 INFO   root: Already installed, running the uninstaller... 09-25 07:35 INFO   root: Running the uninstaller... 09-25 07:35 INFO   CommonBackend: This is the uninstaller running 09-25 07:35 DEBUG  WindowsFrontend: __init__... 09-25 07:35 DEBUG  WindowsFrontend: on_init... 09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en'] 09-25 07:35 INFO   root: Received settings 09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en'] 09-25 07:35 DEBUG  TaskList: # Running tasklist... 09-25 07:35 DEBUG  TaskList: ## Running Remove bootloader entry... 09-25 07:35 DEBUG  WindowsBackend: Could not find bcd id 09-25 07:35 DEBUG  WindowsBackend: undo_bootini C: 09-25 07:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 267718.109375 mb free ntfs) 09-25 07:35 DEBUG  TaskList: ## Finished Remove bootloader entry 09-25 07:35 DEBUG  TaskList: ## Running Remove target dir... 09-25 07:35 DEBUG  CommonBackend: Deleting C:\ubuntu 09-25 07:35 DEBUG  TaskList: ## Finished Remove target dir 09-25 07:35 DEBUG  TaskList: ## Running Remove registry key... 09-25 07:35 DEBUG  TaskList: ## Finished Remove registry key 09-25 07:35 DEBUG  TaskList: # Finished tasklist 09-25 07:35 INFO   root: Almost finished uninstalling 09-25 07:35 INFO   root: Finished uninstallation 09-25 07:35 DEBUG  CommonBackend: Fetching basic info... 09-25 07:35 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe 09-25 07:35 DEBUG  CommonBackend: platform=win32 09-25 07:35 DEBUG  CommonBackend: osname=nt 09-25 07:35 DEBUG  WindowsBackend: arch=amd64 09-25 07:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\data\isolist.ini 09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-25 07:35 DEBUG  WindowsBackend: Fetching host info... 09-25 07:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-25 07:35 DEBUG  WindowsBackend: windows version=vista 09-25 07:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-25 07:35 DEBUG  WindowsBackend: windows_sp=None 09-25 07:35 DEBUG  WindowsBackend: windows_build=7601 09-25 07:35 DEBUG  WindowsBackend: gmt=-6 09-25 07:35 DEBUG  WindowsBackend: country=US 09-25 07:35 DEBUG  WindowsBackend: timezone=America/Chicago 09-25 07:35 DEBUG  WindowsBackend: windows_username=Marc 09-25 07:35 DEBUG  WindowsBackend: user_full_name=Marc 09-25 07:35 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-25 07:35 DEBUG  WindowsBackend: windows_language_code=1033 09-25 07:35 DEBUG  WindowsBackend: windows_language=English 09-25 07:35 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-25 07:35 DEBUG  WindowsBackend: bootloader=vista 09-25 07:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268327.511719 mb free ntfs) 09-25 07:35 DEBUG  WindowsBackend: drive=Drive(C: hd 268327.511719 mb free ntfs) 09-25 07:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-25 07:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-25 07:35 DEBUG  WindowsBackend: uninstaller_path=None 09-25 07:35 DEBUG  WindowsBackend: previous_target_dir=None 09-25 07:35 DEBUG  WindowsBackend: previous_distro_name=None 09-25 07:35 DEBUG  WindowsBackend: keyboard_id=67699721 09-25 07:35 DEBUG  WindowsBackend: keyboard_layout=us 09-25 07:35 DEBUG  WindowsBackend: keyboard_variant= 09-25 07:35 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-25 07:35 DEBUG  CommonBackend: Searching ISOs on USB devices 09-25 07:35 DEBUG  CommonBackend: Searching for local CDs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:35 INFO   root: Running the installer... 09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en'] 09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en'] 09-25 07:36 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marcnm 09-25 07:36 INFO   root: Received settings 09-25 07:36 DEBUG  CommonBackend: Searching for local CD 09-25 07:36 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD 09-25 07:36 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs 09-25 07:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:36 DEBUG  CommonBackend: Searching for local ISO 09-25 07:36 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso 09-25 07:36 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso 09-25 07:36 DEBUG  Distro:   parsing info from str=                                                                  09-25 07:36 ERROR  Distro: 'NoneType' object has no attribute 'group' 09-25 07:36 DEBUG  Distro: could not get info None 09-25 07:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en'] 09-25 07:36 DEBUG  TaskList: # Running tasklist... 09-25 07:36 DEBUG  TaskList: ## Running select_target_dir... 09-25 07:36 INFO   WindowsBackend: Installing into C:\ubuntu 09-25 07:36 DEBUG  TaskList: ## Finished select_target_dir 09-25 07:36 DEBUG  TaskList: ## Running create_dir_structure... 09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu 09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks 09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install 09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot 09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot 09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub 09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub 09-25 07:36 DEBUG  TaskList: ## Finished create_dir_structure 09-25 07:36 DEBUG  TaskList: ## Running create_uninstaller... 09-25 07:36 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com) 09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support) 09-25 07:36 DEBUG  TaskList: ## Finished create_uninstaller 09-25 07:36 DEBUG  TaskList: ## Running create_preseed_diskimage... 09-25 07:36 DEBUG  TaskList: ## Finished create_preseed_diskimage 09-25 07:36 DEBUG  TaskList: ## Running get_diskimage... 09-25 07:36 DEBUG  TaskList: New task download 09-25 07:36 DEBUG  TaskList: ### Running download... 09-25 07:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz 09-25 07:36 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None 09-25 07:39 DEBUG  downloader: download finished (read 506060812 bytes) 09-25 07:39 DEBUG  TaskList: ### Finished download 09-25 07:39 DEBUG  TaskList: ## Finished get_diskimage 09-25 07:39 DEBUG  TaskList: ## Running extract_diskimage... 09-25 07:39 ERROR  TaskList: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2 09-25 07:39 DEBUG  TaskList: # Cancelling tasklist 09-25 07:39 DEBUG  TaskList: # Finished tasklist 09-25 07:39 ERROR  root: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\application.py", line 58, in run   File "\lib\wubi\application.py", line 132, in select_task   File "\lib\wubi\application.py", line 158, in run_installer   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2 09-25 07:39 INFO   root: === wubi 12.04 rev269 === 09-25 07:39 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log 09-25 07:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"'] 09-25 07:39 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\data 09-25 07:39 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\bin\7z.exe 09-25 07:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup 09-25 07:39 DEBUG  CommonBackend: Fetching basic info... 09-25 07:39 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe 09-25 07:39 DEBUG  CommonBackend: platform=win32 09-25 07:39 DEBUG  CommonBackend: osname=nt 09-25 07:39 DEBUG  CommonBackend: language=en_US 09-25 07:39 DEBUG  CommonBackend: encoding=cp1252 09-25 07:39 DEBUG  WindowsBackend: arch=amd64 09-25 07:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\data\isolist.ini 09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-25 07:39 DEBUG  WindowsBackend: Fetching host info... 09-25 07:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-25 07:39 DEBUG  WindowsBackend: windows version=vista 09-25 07:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-25 07:39 DEBUG  WindowsBackend: windows_sp=None 09-25 07:39 DEBUG  WindowsBackend: windows_build=7601 09-25 07:39 DEBUG  WindowsBackend: gmt=-6 09-25 07:39 DEBUG  WindowsBackend: country=US 09-25 07:39 DEBUG  WindowsBackend: timezone=America/Chicago 09-25 07:39 DEBUG  WindowsBackend: windows_username=Marc 09-25 07:39 DEBUG  WindowsBackend: user_full_name=Marc 09-25 07:39 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-25 07:39 DEBUG  WindowsBackend: windows_language_code=1033 09-25 07:39 DEBUG  WindowsBackend: windows_language=English 09-25 07:39 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-25 07:39 DEBUG  WindowsBackend: bootloader=vista 09-25 07:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 267677.550781 mb free ntfs) 09-25 07:39 DEBUG  WindowsBackend: drive=Drive(C: hd 267677.550781 mb free ntfs) 09-25 07:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-25 07:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-25 07:39 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe 09-25 07:39 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu 09-25 07:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu 09-25 07:39 DEBUG  WindowsBackend: keyboard_id=67699721 09-25 07:39 DEBUG  WindowsBackend: keyboard_layout=us 09-25 07:39 DEBUG  WindowsBackend: keyboard_variant= 09-25 07:39 DEBUG  CommonBackend: python locale=('en_US', 'cp1252') 09-25 07:39 DEBUG  CommonBackend: locale=en_US.UTF-8 09-25 07:39 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-25 07:39 DEBUG  CommonBackend: Searching ISOs on USB devices 09-25 07:39 DEBUG  CommonBackend: Searching for local CDs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 INFO   root: Already installed, running the uninstaller... 09-25 07:39 INFO   root: Running the uninstaller... 09-25 07:39 INFO   CommonBackend: This is the uninstaller running 09-25 07:39 DEBUG  WindowsFrontend: __init__... 09-25 07:39 DEBUG  WindowsFrontend: on_init... 09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en'] 09-25 07:39 INFO   root: Received settings 09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en'] 09-25 07:39 DEBUG  TaskList: # Running tasklist... 09-25 07:39 DEBUG  TaskList: ## Running Remove bootloader entry... 09-25 07:39 DEBUG  WindowsBackend: Could not find bcd id 09-25 07:39 DEBUG  WindowsBackend: undo_bootini C: 09-25 07:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 267677.550781 mb free ntfs) 09-25 07:39 DEBUG  TaskList: ## Finished Remove bootloader entry 09-25 07:39 DEBUG  TaskList: ## Running Remove target dir... 09-25 07:39 DEBUG  CommonBackend: Deleting C:\ubuntu 09-25 07:39 DEBUG  TaskList: ## Finished Remove target dir 09-25 07:39 DEBUG  TaskList: ## Running Remove registry key... 09-25 07:39 DEBUG  TaskList: ## Finished Remove registry key 09-25 07:39 DEBUG  TaskList: # Finished tasklist 09-25 07:39 INFO   root: Almost finished uninstalling 09-25 07:39 INFO   root: Finished uninstallation 09-25 07:39 DEBUG  CommonBackend: Fetching basic info... 09-25 07:39 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe 09-25 07:39 DEBUG  CommonBackend: platform=win32 09-25 07:39 DEBUG  CommonBackend: osname=nt 09-25 07:39 DEBUG  WindowsBackend: arch=amd64 09-25 07:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\data\isolist.ini 09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-25 07:39 DEBUG  WindowsBackend: Fetching host info... 09-25 07:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-25 07:39 DEBUG  WindowsBackend: windows version=vista 09-25 07:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-25 07:39 DEBUG  WindowsBackend: windows_sp=None 09-25 07:39 DEBUG  WindowsBackend: windows_build=7601 09-25 07:39 DEBUG  WindowsBackend: gmt=-6 09-25 07:39 DEBUG  WindowsBackend: country=US 09-25 07:39 DEBUG  WindowsBackend: timezone=America/Chicago 09-25 07:39 DEBUG  WindowsBackend: windows_username=Marc 09-25 07:39 DEBUG  WindowsBackend: user_full_name=Marc 09-25 07:39 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-25 07:39 DEBUG  WindowsBackend: windows_language_code=1033 09-25 07:39 DEBUG  WindowsBackend: windows_language=English 09-25 07:39 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-25 07:39 DEBUG  WindowsBackend: bootloader=vista 09-25 07:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268327.402344 mb free ntfs) 09-25 07:39 DEBUG  WindowsBackend: drive=Drive(C: hd 268327.402344 mb free ntfs) 09-25 07:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-25 07:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-25 07:39 DEBUG  WindowsBackend: uninstaller_path=None 09-25 07:39 DEBUG  WindowsBackend: previous_target_dir=None 09-25 07:39 DEBUG  WindowsBackend: previous_distro_name=None 09-25 07:39 DEBUG  WindowsBackend: keyboard_id=67699721 09-25 07:39 DEBUG  WindowsBackend: keyboard_layout=us 09-25 07:39 DEBUG  WindowsBackend: keyboard_variant= 09-25 07:39 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-25 07:39 DEBUG  CommonBackend: Searching ISOs on USB devices 09-25 07:39 DEBUG  CommonBackend: Searching for local CDs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 07:39 INFO   root: Running the installer... 09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en'] 09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en'] 09-25 07:40 INFO   WindowsFrontend: Operation cancelled 09-25 07:40 DEBUG  WindowsFrontend: frontend.quit 09-25 07:40 DEBUG  WindowsFrontend: frontend.on_quit 09-25 07:40 DEBUG  root: application.on_quit 09-25 07:40 INFO   root: sys.exit 09-25 10:02 INFO   root: === wubi 12.04 rev269 === 09-25 10:02 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log 09-25 10:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"'] 09-25 10:02 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\data 09-25 10:02 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\bin\7z.exe 09-25 10:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup 09-25 10:02 DEBUG  CommonBackend: Fetching basic info... 09-25 10:02 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe 09-25 10:02 DEBUG  CommonBackend: platform=win32 09-25 10:02 DEBUG  CommonBackend: osname=nt 09-25 10:02 DEBUG  CommonBackend: language=en_US 09-25 10:02 DEBUG  CommonBackend: encoding=cp1252 09-25 10:02 DEBUG  WindowsBackend: arch=amd64 09-25 10:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\data\isolist.ini 09-25 10:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 09-25 10:02 DEBUG  CommonBackend:   Adding distro Edubuntu-i386 09-25 10:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 09-25 10:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 09-25 10:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 09-25 10:02 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64 09-25 10:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 09-25 10:02 DEBUG  CommonBackend:   Adding distro Lubuntu-i386 09-25 10:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 09-25 10:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 09-25 10:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 09-25 10:02 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64 09-25 10:02 DEBUG  WindowsBackend: Fetching host info... 09-25 10:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 09-25 10:02 DEBUG  WindowsBackend: windows version=vista 09-25 10:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional 09-25 10:02 DEBUG  WindowsBackend: windows_sp=None 09-25 10:02 DEBUG  WindowsBackend: windows_build=7601 09-25 10:02 DEBUG  WindowsBackend: gmt=-6 09-25 10:02 DEBUG  WindowsBackend: country=US 09-25 10:02 DEBUG  WindowsBackend: timezone=America/Chicago 09-25 10:02 DEBUG  WindowsBackend: windows_username=Marc 09-25 10:02 DEBUG  WindowsBackend: user_full_name=Marc 09-25 10:02 DEBUG  WindowsBackend: user_directory=C:\Users\Marc 09-25 10:02 DEBUG  WindowsBackend: windows_language_code=1033 09-25 10:02 DEBUG  WindowsBackend: windows_language=English 09-25 10:02 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor 09-25 10:02 DEBUG  WindowsBackend: bootloader=vista 09-25 10:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268896.460938 mb free ntfs) 09-25 10:02 DEBUG  WindowsBackend: drive=Drive(C: hd 268896.460938 mb free ntfs) 09-25 10:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 09-25 10:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free ) 09-25 10:02 DEBUG  WindowsBackend: uninstaller_path=None 09-25 10:02 DEBUG  WindowsBackend: previous_target_dir=None 09-25 10:02 DEBUG  WindowsBackend: previous_distro_name=None 09-25 10:02 DEBUG  WindowsBackend: keyboard_id=67699721 09-25 10:02 DEBUG  WindowsBackend: keyboard_layout=us 09-25 10:02 DEBUG  WindowsBackend: keyboard_variant= 09-25 10:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252') 09-25 10:02 DEBUG  CommonBackend: locale=en_US.UTF-8 09-25 10:02 DEBUG  WindowsBackend: total_memory_mb=2047.1796875 09-25 10:02 DEBUG  CommonBackend: Searching ISOs on USB devices 09-25 10:02 DEBUG  CommonBackend: Searching for local CDs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Kubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Kubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Xubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Xubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Mythbuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Mythbuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Edubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Edubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Lubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Lubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 INFO   root: Running the installer... 09-25 10:02 DEBUG  WindowsFrontend: __init__... 09-25 10:02 DEBUG  WindowsFrontend: on_init... 09-25 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\translations, languages=['en_US', 'en'] 09-25 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\translations, languages=['en_US', 'en'] 09-25 10:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc 09-25 10:02 INFO   root: Received settings 09-25 10:02 DEBUG  CommonBackend: Searching for local CD 09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs 09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD 09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs 09-25 10:02 DEBUG  CommonBackend: Searching for local ISO 09-25 10:02 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso 09-25 10:02 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso 09-25 10:02 DEBUG  Distro:   parsing info from str=                                                                  09-25 10:02 ERROR  Distro: 'NoneType' object has no attribute 'group' 09-25 10:02 DEBUG  Distro: could not get info None 09-25 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\translations, languages=['en_US', 'en'] 09-25 10:02 DEBUG  TaskList: # Running tasklist... 09-25 10:02 DEBUG  TaskList: ## Running select_target_dir... 09-25 10:02 INFO   WindowsBackend: Installing into C:\ubuntu 09-25 10:02 DEBUG  TaskList: ## Finished select_target_dir 09-25 10:02 DEBUG  TaskList: ## Running create_dir_structure... 09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu 09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks 09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install 09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot 09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot 09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub 09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub 09-25 10:02 DEBUG  TaskList: ## Finished create_dir_structure 09-25 10:02 DEBUG  TaskList: ## Running create_uninstaller... 09-25 10:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com) 09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support) 09-25 10:02 DEBUG  TaskList: ## Finished create_uninstaller 09-25 10:02 DEBUG  TaskList: ## Running create_preseed_diskimage... 09-25 10:02 DEBUG  TaskList: ## Finished create_preseed_diskimage 09-25 10:02 DEBUG  TaskList: ## Running get_diskimage... 09-25 10:02 DEBUG  TaskList: New task download 09-25 10:02 DEBUG  TaskList: ### Running download... 09-25 10:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz 09-25 10:02 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None 09-25 10:08 DEBUG  downloader: download finished (read 506071032 bytes) 09-25 10:08 DEBUG  TaskList: ### Finished download 09-25 10:08 DEBUG  TaskList: ## Finished get_diskimage 09-25 10:08 DEBUG  TaskList: ## Running extract_diskimage... 09-25 10:08 ERROR  TaskList: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2 09-25 10:08 DEBUG  TaskList: # Cancelling tasklist 09-25 10:08 DEBUG  TaskList: # Finished tasklist 09-25 10:08 ERROR  root: Extraction failed with code: 2 Traceback (most recent call last):   File "\lib\wubi\application.py", line 58, in run   File "\lib\wubi\application.py", line 132, in select_task   File "\lib\wubi\application.py", line 158, in run_installer   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__   File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage Exception: Extraction failed with code: 2

---

### Post by bcbc on 2012-09-25
Wowzer, you want to paste that text with some linefeeds.

Anyway this is your problem:
```
DEBUG downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None 09-24 22:49 
DEBUG downloader: download finished (read 506056432 bytes) 09-24 22:49 DEBUG TaskList: ### Finished download 09-24 22:49 
DEBUG TaskList: ## Finished get_diskimage 09-24 22:49 
DEBUG TaskList: ## Running extract_diskimage... 09-24 22:49 
ERROR TaskList: Extraction failed with code: 2 
```
The disk image is 506081252 bytes but it only downloaded 506056432. So the extraction is treating it as corrupt.

Try again, or you can also manually download the diskimage and instruct wubi to use it: [http://askubuntu.com/questions/143463/ubuntu-12-04-wubi-i386-tar-xz-for-the-wubi-installer/143478#143478](http://askubuntu.com/questions/143463/ubuntu-12-04-wubi-i386-tar-xz-for-the-wubi-installer/143478#143478)

Or download the desktop CD ISO into the same folder and run wubi.exe. Either of these methods will work.

---

### Post by DarthTurducken on 2012-09-30
bcbc - 

Thanks for the info but every time I let it try to download the tar file itself it fails with that error code 2. And it always ignores the downloaded ISO in the same folder.

Then I moved the the wubi.ese file and the ubuntu-12.04.1-desktop-i386.iso file to C:\UbuntiImage. Then when I went to command prompt and typed in wubi.exe --dimagepath=C:\UbuntuImage\ubuntu-12.04.1-desktop-i386

Now I get a different error:

```
09-24 22:45 INFO   root: === wubi 12.04 rev269 ===
09-24 22:45 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-24 22:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Downloads\\wubi.exe"']
09-24 22:45 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\data
09-24 22:45 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\bin\7z.exe
09-24 22:45 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-24 22:45 DEBUG  CommonBackend: Fetching basic info...
09-24 22:45 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Downloads\wubi.exe
09-24 22:45 DEBUG  CommonBackend: platform=win32
09-24 22:45 DEBUG  CommonBackend: osname=nt
09-24 22:45 DEBUG  CommonBackend: language=en_US
09-24 22:45 DEBUG  CommonBackend: encoding=cp1252
09-24 22:45 DEBUG  WindowsBackend: arch=amd64
09-24 22:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\data\isolist.ini
09-24 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 22:45 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-24 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 22:45 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-24 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 22:45 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-24 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 22:45 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-24 22:45 DEBUG  WindowsBackend: Fetching host info...
09-24 22:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 22:45 DEBUG  WindowsBackend: windows version=vista
09-24 22:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-24 22:45 DEBUG  WindowsBackend: windows_sp=None
09-24 22:45 DEBUG  WindowsBackend: windows_build=7601
09-24 22:45 DEBUG  WindowsBackend: gmt=-6
09-24 22:45 DEBUG  WindowsBackend: country=US
09-24 22:45 DEBUG  WindowsBackend: timezone=America/Chicago
09-24 22:45 DEBUG  WindowsBackend: windows_username=Marc
09-24 22:45 DEBUG  WindowsBackend: user_full_name=Marc
09-24 22:45 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-24 22:45 DEBUG  WindowsBackend: windows_language_code=1033
09-24 22:45 DEBUG  WindowsBackend: windows_language=English
09-24 22:45 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-24 22:45 DEBUG  WindowsBackend: bootloader=vista
09-24 22:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 269536.660156 mb free ntfs)
09-24 22:45 DEBUG  WindowsBackend: drive=Drive(C: hd 269536.660156 mb free ntfs)
09-24 22:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-24 22:45 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-24 22:45 DEBUG  WindowsBackend: uninstaller_path=None
09-24 22:45 DEBUG  WindowsBackend: previous_target_dir=None
09-24 22:45 DEBUG  WindowsBackend: previous_distro_name=None
09-24 22:45 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 22:45 DEBUG  WindowsBackend: keyboard_layout=us
09-24 22:45 DEBUG  WindowsBackend: keyboard_variant=
09-24 22:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-24 22:45 DEBUG  CommonBackend: locale=en_US.UTF-8
09-24 22:45 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-24 22:45 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 22:45 DEBUG  CommonBackend: Searching for local CDs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Ubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Ubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Kubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Kubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Xubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Xubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Mythbuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Mythbuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Edubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Edubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Lubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Lubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-24 22:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:45 INFO   root: Running the installer...
09-24 22:45 DEBUG  WindowsFrontend: __init__...
09-24 22:45 DEBUG  WindowsFrontend: on_init...
09-24 22:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\translations, languages=['en_US', 'en']
09-24 22:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\translations, languages=['en_US', 'en']
09-24 22:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-24 22:46 INFO   root: Received settings
09-24 22:46 DEBUG  CommonBackend: Searching for local CD
09-24 22:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp is a valid Ubuntu CD
09-24 22:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\casper\filesystem.squashfs
09-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:46 DEBUG  CommonBackend: Searching for local ISO
09-24 22:46 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Downloads\Windows 7 32-bit Repair Disc.iso
09-24 22:46 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-24 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl9FF.tmp\translations, languages=['en_US', 'en']
09-24 22:46 DEBUG  TaskList: # Running tasklist...
09-24 22:46 DEBUG  TaskList: ## Running select_target_dir...
09-24 22:46 INFO   WindowsBackend: Installing into C:\ubuntu
09-24 22:46 DEBUG  TaskList: ## Finished select_target_dir
09-24 22:46 DEBUG  TaskList: ## Running create_dir_structure...
09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-24 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-24 22:46 DEBUG  TaskList: ## Finished create_dir_structure
09-24 22:46 DEBUG  TaskList: ## Running create_uninstaller...
09-24 22:46 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-24 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-24 22:46 DEBUG  TaskList: ## Finished create_uninstaller
09-24 22:46 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-24 22:46 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-24 22:46 DEBUG  TaskList: ## Running get_diskimage...
09-24 22:46 DEBUG  TaskList: New task download
09-24 22:46 DEBUG  TaskList: ### Running download...
09-24 22:46 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-24 22:46 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-24 22:49 DEBUG  downloader: download finished (read 506056432 bytes)
09-24 22:49 DEBUG  TaskList: ### Finished download
09-24 22:49 DEBUG  TaskList: ## Finished get_diskimage
09-24 22:49 DEBUG  TaskList: ## Running extract_diskimage...
09-24 22:49 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-24 22:49 DEBUG  TaskList: # Cancelling tasklist
09-24 22:49 DEBUG  TaskList: # Finished tasklist
09-24 22:49 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-24 22:50 INFO   root: === wubi 12.04 rev269 ===
09-24 22:50 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-24 22:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"']
09-24 22:50 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\data
09-24 22:50 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\bin\7z.exe
09-24 22:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-24 22:50 DEBUG  CommonBackend: Fetching basic info...
09-24 22:50 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-24 22:50 DEBUG  CommonBackend: platform=win32
09-24 22:50 DEBUG  CommonBackend: osname=nt
09-24 22:50 DEBUG  CommonBackend: language=en_US
09-24 22:50 DEBUG  CommonBackend: encoding=cp1252
09-24 22:50 DEBUG  WindowsBackend: arch=amd64
09-24 22:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\data\isolist.ini
09-24 22:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 22:50 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-24 22:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 22:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 22:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 22:50 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-24 22:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 22:50 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-24 22:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 22:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 22:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 22:50 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-24 22:50 DEBUG  WindowsBackend: Fetching host info...
09-24 22:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 22:50 DEBUG  WindowsBackend: windows version=vista
09-24 22:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-24 22:50 DEBUG  WindowsBackend: windows_sp=None
09-24 22:50 DEBUG  WindowsBackend: windows_build=7601
09-24 22:50 DEBUG  WindowsBackend: gmt=-6
09-24 22:50 DEBUG  WindowsBackend: country=US
09-24 22:50 DEBUG  WindowsBackend: timezone=America/Chicago
09-24 22:50 DEBUG  WindowsBackend: windows_username=Marc
09-24 22:50 DEBUG  WindowsBackend: user_full_name=Marc
09-24 22:50 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-24 22:50 DEBUG  WindowsBackend: windows_language_code=1033
09-24 22:50 DEBUG  WindowsBackend: windows_language=English
09-24 22:50 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-24 22:50 DEBUG  WindowsBackend: bootloader=vista
09-24 22:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268553.949219 mb free ntfs)
09-24 22:50 DEBUG  WindowsBackend: drive=Drive(C: hd 268553.949219 mb free ntfs)
09-24 22:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-24 22:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-24 22:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-24 22:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-24 22:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-24 22:50 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 22:50 DEBUG  WindowsBackend: keyboard_layout=us
09-24 22:50 DEBUG  WindowsBackend: keyboard_variant=
09-24 22:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-24 22:50 DEBUG  CommonBackend: locale=en_US.UTF-8
09-24 22:50 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-24 22:50 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 22:50 DEBUG  CommonBackend: Searching for local CDs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-24 22:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:50 INFO   root: Already installed, running the uninstaller...
09-24 22:50 INFO   root: Running the uninstaller...
09-24 22:50 INFO   CommonBackend: This is the uninstaller running
09-24 22:50 DEBUG  WindowsFrontend: __init__...
09-24 22:50 DEBUG  WindowsFrontend: on_init...
09-24 22:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en']
09-24 22:50 INFO   root: Received settings
09-24 22:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en']
09-24 22:50 DEBUG  TaskList: # Running tasklist...
09-24 22:50 DEBUG  TaskList: ## Running Remove bootloader entry...
09-24 22:50 DEBUG  WindowsBackend: Could not find bcd id
09-24 22:50 DEBUG  WindowsBackend: undo_bootini C:
09-24 22:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 268553.949219 mb free ntfs)
09-24 22:51 DEBUG  TaskList: ## Finished Remove bootloader entry
09-24 22:51 DEBUG  TaskList: ## Running Remove target dir...
09-24 22:51 DEBUG  CommonBackend: Deleting C:\ubuntu
09-24 22:51 DEBUG  TaskList: ## Finished Remove target dir
09-24 22:51 DEBUG  TaskList: ## Running Remove registry key...
09-24 22:51 DEBUG  TaskList: ## Finished Remove registry key
09-24 22:51 DEBUG  TaskList: # Finished tasklist
09-24 22:51 INFO   root: Almost finished uninstalling
09-24 22:51 INFO   root: Finished uninstallation
09-24 22:51 DEBUG  CommonBackend: Fetching basic info...
09-24 22:51 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-24 22:51 DEBUG  CommonBackend: platform=win32
09-24 22:51 DEBUG  CommonBackend: osname=nt
09-24 22:51 DEBUG  WindowsBackend: arch=amd64
09-24 22:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\data\isolist.ini
09-24 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-24 22:51 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-24 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-24 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-24 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-24 22:51 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-24 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-24 22:51 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-24 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-24 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-24 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-24 22:51 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-24 22:51 DEBUG  WindowsBackend: Fetching host info...
09-24 22:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-24 22:51 DEBUG  WindowsBackend: windows version=vista
09-24 22:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-24 22:51 DEBUG  WindowsBackend: windows_sp=None
09-24 22:51 DEBUG  WindowsBackend: windows_build=7601
09-24 22:51 DEBUG  WindowsBackend: gmt=-6
09-24 22:51 DEBUG  WindowsBackend: country=US
09-24 22:51 DEBUG  WindowsBackend: timezone=America/Chicago
09-24 22:51 DEBUG  WindowsBackend: windows_username=Marc
09-24 22:51 DEBUG  WindowsBackend: user_full_name=Marc
09-24 22:51 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-24 22:51 DEBUG  WindowsBackend: windows_language_code=1033
09-24 22:51 DEBUG  WindowsBackend: windows_language=English
09-24 22:51 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-24 22:51 DEBUG  WindowsBackend: bootloader=vista
09-24 22:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 269185.140625 mb free ntfs)
09-24 22:51 DEBUG  WindowsBackend: drive=Drive(C: hd 269185.140625 mb free ntfs)
09-24 22:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-24 22:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-24 22:51 DEBUG  WindowsBackend: uninstaller_path=None
09-24 22:51 DEBUG  WindowsBackend: previous_target_dir=None
09-24 22:51 DEBUG  WindowsBackend: previous_distro_name=None
09-24 22:51 DEBUG  WindowsBackend: keyboard_id=67699721
09-24 22:51 DEBUG  WindowsBackend: keyboard_layout=us
09-24 22:51 DEBUG  WindowsBackend: keyboard_variant=
09-24 22:51 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-24 22:51 DEBUG  CommonBackend: Searching ISOs on USB devices
09-24 22:51 DEBUG  CommonBackend: Searching for local CDs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Kubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Xubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Mythbuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Edubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Lubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 INFO   root: Running the installer...
09-24 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en']
09-24 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en']
09-24 22:51 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-24 22:51 INFO   root: Received settings
09-24 22:51 DEBUG  CommonBackend: Searching for local CD
09-24 22:51 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylD124.tmp is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-24 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-24 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-24 22:51 DEBUG  CommonBackend: Searching for local ISO
09-24 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylD124.tmp\translations, languages=['en_US', 'en']
09-24 22:51 DEBUG  TaskList: # Running tasklist...
09-24 22:51 DEBUG  TaskList: ## Running select_target_dir...
09-24 22:51 INFO   WindowsBackend: Installing into C:\ubuntu
09-24 22:51 DEBUG  TaskList: ## Finished select_target_dir
09-24 22:51 DEBUG  TaskList: ## Running create_dir_structure...
09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-24 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-24 22:51 DEBUG  TaskList: ## Finished create_dir_structure
09-24 22:51 DEBUG  TaskList: ## Running create_uninstaller...
09-24 22:51 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-24 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-24 22:51 DEBUG  TaskList: ## Finished create_uninstaller
09-24 22:51 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-24 22:51 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-24 22:51 DEBUG  TaskList: ## Running get_diskimage...
09-24 22:51 DEBUG  TaskList: New task download
09-24 22:51 DEBUG  TaskList: ### Running download...
09-24 22:51 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-24 22:51 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-24 22:54 DEBUG  downloader: download finished (read 506065192 bytes)
09-24 22:54 DEBUG  TaskList: ### Finished download
09-24 22:54 DEBUG  TaskList: ## Finished get_diskimage
09-24 22:54 DEBUG  TaskList: ## Running extract_diskimage...
09-24 22:54 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-24 22:54 DEBUG  TaskList: # Cancelling tasklist
09-24 22:54 DEBUG  TaskList: # Finished tasklist
09-24 22:54 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-25 07:35 INFO   root: === wubi 12.04 rev269 ===
09-25 07:35 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-25 07:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"']
09-25 07:35 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\data
09-25 07:35 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\bin\7z.exe
09-25 07:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-25 07:35 DEBUG  CommonBackend: Fetching basic info...
09-25 07:35 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-25 07:35 DEBUG  CommonBackend: platform=win32
09-25 07:35 DEBUG  CommonBackend: osname=nt
09-25 07:35 DEBUG  CommonBackend: language=en_US
09-25 07:35 DEBUG  CommonBackend: encoding=cp1252
09-25 07:35 DEBUG  WindowsBackend: arch=amd64
09-25 07:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\data\isolist.ini
09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-25 07:35 DEBUG  WindowsBackend: Fetching host info...
09-25 07:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-25 07:35 DEBUG  WindowsBackend: windows version=vista
09-25 07:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-25 07:35 DEBUG  WindowsBackend: windows_sp=None
09-25 07:35 DEBUG  WindowsBackend: windows_build=7601
09-25 07:35 DEBUG  WindowsBackend: gmt=-6
09-25 07:35 DEBUG  WindowsBackend: country=US
09-25 07:35 DEBUG  WindowsBackend: timezone=America/Chicago
09-25 07:35 DEBUG  WindowsBackend: windows_username=Marc
09-25 07:35 DEBUG  WindowsBackend: user_full_name=Marc
09-25 07:35 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-25 07:35 DEBUG  WindowsBackend: windows_language_code=1033
09-25 07:35 DEBUG  WindowsBackend: windows_language=English
09-25 07:35 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-25 07:35 DEBUG  WindowsBackend: bootloader=vista
09-25 07:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 267718.109375 mb free ntfs)
09-25 07:35 DEBUG  WindowsBackend: drive=Drive(C: hd 267718.109375 mb free ntfs)
09-25 07:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-25 07:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-25 07:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-25 07:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-25 07:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-25 07:35 DEBUG  WindowsBackend: keyboard_id=67699721
09-25 07:35 DEBUG  WindowsBackend: keyboard_layout=us
09-25 07:35 DEBUG  WindowsBackend: keyboard_variant=
09-25 07:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-25 07:35 DEBUG  CommonBackend: locale=en_US.UTF-8
09-25 07:35 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-25 07:35 DEBUG  CommonBackend: Searching ISOs on USB devices
09-25 07:35 DEBUG  CommonBackend: Searching for local CDs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 INFO   root: Already installed, running the uninstaller...
09-25 07:35 INFO   root: Running the uninstaller...
09-25 07:35 INFO   CommonBackend: This is the uninstaller running
09-25 07:35 DEBUG  WindowsFrontend: __init__...
09-25 07:35 DEBUG  WindowsFrontend: on_init...
09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en']
09-25 07:35 INFO   root: Received settings
09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en']
09-25 07:35 DEBUG  TaskList: # Running tasklist...
09-25 07:35 DEBUG  TaskList: ## Running Remove bootloader entry...
09-25 07:35 DEBUG  WindowsBackend: Could not find bcd id
09-25 07:35 DEBUG  WindowsBackend: undo_bootini C:
09-25 07:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 267718.109375 mb free ntfs)
09-25 07:35 DEBUG  TaskList: ## Finished Remove bootloader entry
09-25 07:35 DEBUG  TaskList: ## Running Remove target dir...
09-25 07:35 DEBUG  CommonBackend: Deleting C:\ubuntu
09-25 07:35 DEBUG  TaskList: ## Finished Remove target dir
09-25 07:35 DEBUG  TaskList: ## Running Remove registry key...
09-25 07:35 DEBUG  TaskList: ## Finished Remove registry key
09-25 07:35 DEBUG  TaskList: # Finished tasklist
09-25 07:35 INFO   root: Almost finished uninstalling
09-25 07:35 INFO   root: Finished uninstallation
09-25 07:35 DEBUG  CommonBackend: Fetching basic info...
09-25 07:35 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-25 07:35 DEBUG  CommonBackend: platform=win32
09-25 07:35 DEBUG  CommonBackend: osname=nt
09-25 07:35 DEBUG  WindowsBackend: arch=amd64
09-25 07:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\data\isolist.ini
09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-25 07:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-25 07:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-25 07:35 DEBUG  WindowsBackend: Fetching host info...
09-25 07:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-25 07:35 DEBUG  WindowsBackend: windows version=vista
09-25 07:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-25 07:35 DEBUG  WindowsBackend: windows_sp=None
09-25 07:35 DEBUG  WindowsBackend: windows_build=7601
09-25 07:35 DEBUG  WindowsBackend: gmt=-6
09-25 07:35 DEBUG  WindowsBackend: country=US
09-25 07:35 DEBUG  WindowsBackend: timezone=America/Chicago
09-25 07:35 DEBUG  WindowsBackend: windows_username=Marc
09-25 07:35 DEBUG  WindowsBackend: user_full_name=Marc
09-25 07:35 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-25 07:35 DEBUG  WindowsBackend: windows_language_code=1033
09-25 07:35 DEBUG  WindowsBackend: windows_language=English
09-25 07:35 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-25 07:35 DEBUG  WindowsBackend: bootloader=vista
09-25 07:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268327.511719 mb free ntfs)
09-25 07:35 DEBUG  WindowsBackend: drive=Drive(C: hd 268327.511719 mb free ntfs)
09-25 07:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-25 07:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-25 07:35 DEBUG  WindowsBackend: uninstaller_path=None
09-25 07:35 DEBUG  WindowsBackend: previous_target_dir=None
09-25 07:35 DEBUG  WindowsBackend: previous_distro_name=None
09-25 07:35 DEBUG  WindowsBackend: keyboard_id=67699721
09-25 07:35 DEBUG  WindowsBackend: keyboard_layout=us
09-25 07:35 DEBUG  WindowsBackend: keyboard_variant=
09-25 07:35 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-25 07:35 DEBUG  CommonBackend: Searching ISOs on USB devices
09-25 07:35 DEBUG  CommonBackend: Searching for local CDs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:35 INFO   root: Running the installer...
09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en']
09-25 07:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en']
09-25 07:36 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marcnm
09-25 07:36 INFO   root: Received settings
09-25 07:36 DEBUG  CommonBackend: Searching for local CD
09-25 07:36 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp is a valid Ubuntu CD
09-25 07:36 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\casper\filesystem.squashfs
09-25 07:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:36 DEBUG  CommonBackend: Searching for local ISO
09-25 07:36 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-25 07:36 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-25 07:36 DEBUG  Distro:   parsing info from str=                                                                 
09-25 07:36 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-25 07:36 DEBUG  Distro: could not get info None
09-25 07:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4F96.tmp\translations, languages=['en_US', 'en']
09-25 07:36 DEBUG  TaskList: # Running tasklist...
09-25 07:36 DEBUG  TaskList: ## Running select_target_dir...
09-25 07:36 INFO   WindowsBackend: Installing into C:\ubuntu
09-25 07:36 DEBUG  TaskList: ## Finished select_target_dir
09-25 07:36 DEBUG  TaskList: ## Running create_dir_structure...
09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-25 07:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-25 07:36 DEBUG  TaskList: ## Finished create_dir_structure
09-25 07:36 DEBUG  TaskList: ## Running create_uninstaller...
09-25 07:36 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-25 07:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-25 07:36 DEBUG  TaskList: ## Finished create_uninstaller
09-25 07:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-25 07:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-25 07:36 DEBUG  TaskList: ## Running get_diskimage...
09-25 07:36 DEBUG  TaskList: New task download
09-25 07:36 DEBUG  TaskList: ### Running download...
09-25 07:36 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-25 07:36 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-25 07:39 DEBUG  downloader: download finished (read 506060812 bytes)
09-25 07:39 DEBUG  TaskList: ### Finished download
09-25 07:39 DEBUG  TaskList: ## Finished get_diskimage
09-25 07:39 DEBUG  TaskList: ## Running extract_diskimage...
09-25 07:39 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-25 07:39 DEBUG  TaskList: # Cancelling tasklist
09-25 07:39 DEBUG  TaskList: # Finished tasklist
09-25 07:39 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-25 07:39 INFO   root: === wubi 12.04 rev269 ===
09-25 07:39 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-25 07:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"']
09-25 07:39 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\data
09-25 07:39 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\bin\7z.exe
09-25 07:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-25 07:39 DEBUG  CommonBackend: Fetching basic info...
09-25 07:39 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-25 07:39 DEBUG  CommonBackend: platform=win32
09-25 07:39 DEBUG  CommonBackend: osname=nt
09-25 07:39 DEBUG  CommonBackend: language=en_US
09-25 07:39 DEBUG  CommonBackend: encoding=cp1252
09-25 07:39 DEBUG  WindowsBackend: arch=amd64
09-25 07:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\data\isolist.ini
09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-25 07:39 DEBUG  WindowsBackend: Fetching host info...
09-25 07:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-25 07:39 DEBUG  WindowsBackend: windows version=vista
09-25 07:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-25 07:39 DEBUG  WindowsBackend: windows_sp=None
09-25 07:39 DEBUG  WindowsBackend: windows_build=7601
09-25 07:39 DEBUG  WindowsBackend: gmt=-6
09-25 07:39 DEBUG  WindowsBackend: country=US
09-25 07:39 DEBUG  WindowsBackend: timezone=America/Chicago
09-25 07:39 DEBUG  WindowsBackend: windows_username=Marc
09-25 07:39 DEBUG  WindowsBackend: user_full_name=Marc
09-25 07:39 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-25 07:39 DEBUG  WindowsBackend: windows_language_code=1033
09-25 07:39 DEBUG  WindowsBackend: windows_language=English
09-25 07:39 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-25 07:39 DEBUG  WindowsBackend: bootloader=vista
09-25 07:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 267677.550781 mb free ntfs)
09-25 07:39 DEBUG  WindowsBackend: drive=Drive(C: hd 267677.550781 mb free ntfs)
09-25 07:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-25 07:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-25 07:39 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-25 07:39 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-25 07:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-25 07:39 DEBUG  WindowsBackend: keyboard_id=67699721
09-25 07:39 DEBUG  WindowsBackend: keyboard_layout=us
09-25 07:39 DEBUG  WindowsBackend: keyboard_variant=
09-25 07:39 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-25 07:39 DEBUG  CommonBackend: locale=en_US.UTF-8
09-25 07:39 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-25 07:39 DEBUG  CommonBackend: Searching ISOs on USB devices
09-25 07:39 DEBUG  CommonBackend: Searching for local CDs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 INFO   root: Already installed, running the uninstaller...
09-25 07:39 INFO   root: Running the uninstaller...
09-25 07:39 INFO   CommonBackend: This is the uninstaller running
09-25 07:39 DEBUG  WindowsFrontend: __init__...
09-25 07:39 DEBUG  WindowsFrontend: on_init...
09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en']
09-25 07:39 INFO   root: Received settings
09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en']
09-25 07:39 DEBUG  TaskList: # Running tasklist...
09-25 07:39 DEBUG  TaskList: ## Running Remove bootloader entry...
09-25 07:39 DEBUG  WindowsBackend: Could not find bcd id
09-25 07:39 DEBUG  WindowsBackend: undo_bootini C:
09-25 07:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 267677.550781 mb free ntfs)
09-25 07:39 DEBUG  TaskList: ## Finished Remove bootloader entry
09-25 07:39 DEBUG  TaskList: ## Running Remove target dir...
09-25 07:39 DEBUG  CommonBackend: Deleting C:\ubuntu
09-25 07:39 DEBUG  TaskList: ## Finished Remove target dir
09-25 07:39 DEBUG  TaskList: ## Running Remove registry key...
09-25 07:39 DEBUG  TaskList: ## Finished Remove registry key
09-25 07:39 DEBUG  TaskList: # Finished tasklist
09-25 07:39 INFO   root: Almost finished uninstalling
09-25 07:39 INFO   root: Finished uninstallation
09-25 07:39 DEBUG  CommonBackend: Fetching basic info...
09-25 07:39 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-25 07:39 DEBUG  CommonBackend: platform=win32
09-25 07:39 DEBUG  CommonBackend: osname=nt
09-25 07:39 DEBUG  WindowsBackend: arch=amd64
09-25 07:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\data\isolist.ini
09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-25 07:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-25 07:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-25 07:39 DEBUG  WindowsBackend: Fetching host info...
09-25 07:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-25 07:39 DEBUG  WindowsBackend: windows version=vista
09-25 07:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-25 07:39 DEBUG  WindowsBackend: windows_sp=None
09-25 07:39 DEBUG  WindowsBackend: windows_build=7601
09-25 07:39 DEBUG  WindowsBackend: gmt=-6
09-25 07:39 DEBUG  WindowsBackend: country=US
09-25 07:39 DEBUG  WindowsBackend: timezone=America/Chicago
09-25 07:39 DEBUG  WindowsBackend: windows_username=Marc
09-25 07:39 DEBUG  WindowsBackend: user_full_name=Marc
09-25 07:39 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-25 07:39 DEBUG  WindowsBackend: windows_language_code=1033
09-25 07:39 DEBUG  WindowsBackend: windows_language=English
09-25 07:39 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-25 07:39 DEBUG  WindowsBackend: bootloader=vista
09-25 07:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268327.402344 mb free ntfs)
09-25 07:39 DEBUG  WindowsBackend: drive=Drive(C: hd 268327.402344 mb free ntfs)
09-25 07:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-25 07:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-25 07:39 DEBUG  WindowsBackend: uninstaller_path=None
09-25 07:39 DEBUG  WindowsBackend: previous_target_dir=None
09-25 07:39 DEBUG  WindowsBackend: previous_distro_name=None
09-25 07:39 DEBUG  WindowsBackend: keyboard_id=67699721
09-25 07:39 DEBUG  WindowsBackend: keyboard_layout=us
09-25 07:39 DEBUG  WindowsBackend: keyboard_variant=
09-25 07:39 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-25 07:39 DEBUG  CommonBackend: Searching ISOs on USB devices
09-25 07:39 DEBUG  CommonBackend: Searching for local CDs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 07:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 07:39 INFO   root: Running the installer...
09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en']
09-25 07:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE5AD.tmp\translations, languages=['en_US', 'en']
09-25 07:40 INFO   WindowsFrontend: Operation cancelled
09-25 07:40 DEBUG  WindowsFrontend: frontend.quit
09-25 07:40 DEBUG  WindowsFrontend: frontend.on_quit
09-25 07:40 DEBUG  root: application.on_quit
09-25 07:40 INFO   root: sys.exit
09-25 10:02 INFO   root: === wubi 12.04 rev269 ===
09-25 10:02 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-25 10:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"']
09-25 10:02 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\data
09-25 10:02 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\bin\7z.exe
09-25 10:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-25 10:02 DEBUG  CommonBackend: Fetching basic info...
09-25 10:02 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-25 10:02 DEBUG  CommonBackend: platform=win32
09-25 10:02 DEBUG  CommonBackend: osname=nt
09-25 10:02 DEBUG  CommonBackend: language=en_US
09-25 10:02 DEBUG  CommonBackend: encoding=cp1252
09-25 10:02 DEBUG  WindowsBackend: arch=amd64
09-25 10:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\data\isolist.ini
09-25 10:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-25 10:02 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-25 10:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-25 10:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-25 10:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-25 10:02 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-25 10:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-25 10:02 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-25 10:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-25 10:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-25 10:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-25 10:02 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-25 10:02 DEBUG  WindowsBackend: Fetching host info...
09-25 10:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-25 10:02 DEBUG  WindowsBackend: windows version=vista
09-25 10:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-25 10:02 DEBUG  WindowsBackend: windows_sp=None
09-25 10:02 DEBUG  WindowsBackend: windows_build=7601
09-25 10:02 DEBUG  WindowsBackend: gmt=-6
09-25 10:02 DEBUG  WindowsBackend: country=US
09-25 10:02 DEBUG  WindowsBackend: timezone=America/Chicago
09-25 10:02 DEBUG  WindowsBackend: windows_username=Marc
09-25 10:02 DEBUG  WindowsBackend: user_full_name=Marc
09-25 10:02 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-25 10:02 DEBUG  WindowsBackend: windows_language_code=1033
09-25 10:02 DEBUG  WindowsBackend: windows_language=English
09-25 10:02 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-25 10:02 DEBUG  WindowsBackend: bootloader=vista
09-25 10:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 268896.460938 mb free ntfs)
09-25 10:02 DEBUG  WindowsBackend: drive=Drive(C: hd 268896.460938 mb free ntfs)
09-25 10:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-25 10:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-25 10:02 DEBUG  WindowsBackend: uninstaller_path=None
09-25 10:02 DEBUG  WindowsBackend: previous_target_dir=None
09-25 10:02 DEBUG  WindowsBackend: previous_distro_name=None
09-25 10:02 DEBUG  WindowsBackend: keyboard_id=67699721
09-25 10:02 DEBUG  WindowsBackend: keyboard_layout=us
09-25 10:02 DEBUG  WindowsBackend: keyboard_variant=
09-25 10:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-25 10:02 DEBUG  CommonBackend: locale=en_US.UTF-8
09-25 10:02 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-25 10:02 DEBUG  CommonBackend: Searching ISOs on USB devices
09-25 10:02 DEBUG  CommonBackend: Searching for local CDs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Kubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Kubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Xubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Xubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Mythbuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Mythbuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Edubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Edubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Lubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Lubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 INFO   root: Running the installer...
09-25 10:02 DEBUG  WindowsFrontend: __init__...
09-25 10:02 DEBUG  WindowsFrontend: on_init...
09-25 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\translations, languages=['en_US', 'en']
09-25 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\translations, languages=['en_US', 'en']
09-25 10:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-25 10:02 INFO   root: Received settings
09-25 10:02 DEBUG  CommonBackend: Searching for local CD
09-25 10:02 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-25 10:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-25 10:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-25 10:02 DEBUG  CommonBackend: Searching for local ISO
09-25 10:02 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-25 10:02 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-25 10:02 DEBUG  Distro:   parsing info from str=                                                                 
09-25 10:02 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-25 10:02 DEBUG  Distro: could not get info None
09-25 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl7F6E.tmp\translations, languages=['en_US', 'en']
09-25 10:02 DEBUG  TaskList: # Running tasklist...
09-25 10:02 DEBUG  TaskList: ## Running select_target_dir...
09-25 10:02 INFO   WindowsBackend: Installing into C:\ubuntu
09-25 10:02 DEBUG  TaskList: ## Finished select_target_dir
09-25 10:02 DEBUG  TaskList: ## Running create_dir_structure...
09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-25 10:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-25 10:02 DEBUG  TaskList: ## Finished create_dir_structure
09-25 10:02 DEBUG  TaskList: ## Running create_uninstaller...
09-25 10:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-25 10:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-25 10:02 DEBUG  TaskList: ## Finished create_uninstaller
09-25 10:02 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-25 10:02 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-25 10:02 DEBUG  TaskList: ## Running get_diskimage...
09-25 10:02 DEBUG  TaskList: New task download
09-25 10:02 DEBUG  TaskList: ### Running download...
09-25 10:02 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-25 10:02 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-25 10:08 DEBUG  downloader: download finished (read 506071032 bytes)
09-25 10:08 DEBUG  TaskList: ### Finished download
09-25 10:08 DEBUG  TaskList: ## Finished get_diskimage
09-25 10:08 DEBUG  TaskList: ## Running extract_diskimage...
09-25 10:08 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-25 10:08 DEBUG  TaskList: # Cancelling tasklist
09-25 10:08 DEBUG  TaskList: # Finished tasklist
09-25 10:08 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-30 03:46 INFO   root: === wubi 12.04 rev269 ===
09-30 03:46 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\Users\\Marc\\Desktop\\ubuntu-12.04.1-desktop-i386']
09-30 03:46 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\data
09-30 03:46 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\bin\7z.exe
09-30 03:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:46 DEBUG  CommonBackend: Fetching basic info...
09-30 03:46 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:46 DEBUG  CommonBackend: platform=win32
09-30 03:46 DEBUG  CommonBackend: osname=nt
09-30 03:46 DEBUG  CommonBackend: language=en_US
09-30 03:46 DEBUG  CommonBackend: encoding=cp1252
09-30 03:46 DEBUG  WindowsBackend: arch=amd64
09-30 03:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\data\isolist.ini
09-30 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:46 DEBUG  WindowsBackend: Fetching host info...
09-30 03:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:46 DEBUG  WindowsBackend: windows version=vista
09-30 03:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:46 DEBUG  WindowsBackend: windows_sp=None
09-30 03:46 DEBUG  WindowsBackend: windows_build=7601
09-30 03:46 DEBUG  WindowsBackend: gmt=-6
09-30 03:46 DEBUG  WindowsBackend: country=US
09-30 03:46 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:46 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:46 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:46 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:46 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:46 DEBUG  WindowsBackend: windows_language=English
09-30 03:46 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:46 DEBUG  WindowsBackend: bootloader=vista
09-30 03:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250212.546875 mb free ntfs)
09-30 03:46 DEBUG  WindowsBackend: drive=Drive(C: hd 250212.546875 mb free ntfs)
09-30 03:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 03:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 03:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 03:46 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:46 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:46 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:46 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:46 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:46 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:46 DEBUG  CommonBackend: Searching for local CDs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 INFO   root: Already installed, running the uninstaller...
09-30 03:46 INFO   root: Running the uninstaller...
09-30 03:46 INFO   CommonBackend: This is the uninstaller running
09-30 03:46 DEBUG  WindowsFrontend: __init__...
09-30 03:46 DEBUG  WindowsFrontend: on_init...
09-30 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\translations, languages=['en_US', 'en']
09-30 03:46 INFO   root: Received settings
09-30 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\translations, languages=['en_US', 'en']
09-30 03:46 DEBUG  TaskList: # Running tasklist...
09-30 03:46 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 03:46 DEBUG  WindowsBackend: Could not find bcd id
09-30 03:46 DEBUG  WindowsBackend: undo_bootini C:
09-30 03:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 250212.546875 mb free ntfs)
09-30 03:46 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 03:46 DEBUG  TaskList: ## Running Remove target dir...
09-30 03:46 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 03:46 DEBUG  TaskList: ## Finished Remove target dir
09-30 03:46 DEBUG  TaskList: ## Running Remove registry key...
09-30 03:46 DEBUG  TaskList: ## Finished Remove registry key
09-30 03:46 DEBUG  TaskList: # Finished tasklist
09-30 03:46 INFO   root: Almost finished uninstalling
09-30 03:46 INFO   root: Finished uninstallation
09-30 03:46 DEBUG  CommonBackend: Fetching basic info...
09-30 03:46 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:46 DEBUG  CommonBackend: platform=win32
09-30 03:46 DEBUG  CommonBackend: osname=nt
09-30 03:46 DEBUG  WindowsBackend: arch=amd64
09-30 03:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\data\isolist.ini
09-30 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:46 DEBUG  WindowsBackend: Fetching host info...
09-30 03:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:46 DEBUG  WindowsBackend: windows version=vista
09-30 03:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:46 DEBUG  WindowsBackend: windows_sp=None
09-30 03:46 DEBUG  WindowsBackend: windows_build=7601
09-30 03:46 DEBUG  WindowsBackend: gmt=-6
09-30 03:46 DEBUG  WindowsBackend: country=US
09-30 03:46 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:46 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:46 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:46 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:46 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:46 DEBUG  WindowsBackend: windows_language=English
09-30 03:46 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:46 DEBUG  WindowsBackend: bootloader=vista
09-30 03:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 251218.84375 mb free ntfs)
09-30 03:46 DEBUG  WindowsBackend: drive=Drive(C: hd 251218.84375 mb free ntfs)
09-30 03:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:46 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:46 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:46 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:46 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:46 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:46 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:46 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:46 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:46 DEBUG  CommonBackend: Searching for local CDs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:46 INFO   root: Running the installer...
09-30 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\translations, languages=['en_US', 'en']
09-30 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\translations, languages=['en_US', 'en']
09-30 03:47 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 03:47 INFO   root: Received settings
09-30 03:47 DEBUG  CommonBackend: Searching for local CD
09-30 03:47 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp is a valid Ubuntu CD
09-30 03:47 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\casper\filesystem.squashfs
09-30 03:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:47 DEBUG  CommonBackend: Searching for local ISO
09-30 03:47 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 03:47 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 03:47 DEBUG  Distro:   parsing info from str=                                                                 
09-30 03:47 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-30 03:47 DEBUG  Distro: could not get info None
09-30 03:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylE3DE.tmp\translations, languages=['en_US', 'en']
09-30 03:47 DEBUG  TaskList: # Running tasklist...
09-30 03:47 DEBUG  TaskList: ## Running select_target_dir...
09-30 03:47 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 03:47 DEBUG  TaskList: ## Finished select_target_dir
09-30 03:47 DEBUG  TaskList: ## Running create_dir_structure...
09-30 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 03:47 DEBUG  TaskList: ## Finished create_dir_structure
09-30 03:47 DEBUG  TaskList: ## Running create_uninstaller...
09-30 03:47 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 03:47 DEBUG  TaskList: ## Finished create_uninstaller
09-30 03:47 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 03:47 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 03:47 DEBUG  TaskList: ## Running get_diskimage...
09-30 03:47 DEBUG  TaskList: New task download
09-30 03:47 DEBUG  TaskList: ### Running download...
09-30 03:47 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-30 03:47 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-30 03:47 INFO   WindowsFrontend: Operation cancelled
09-30 03:47 DEBUG  WindowsFrontend: frontend.quit
09-30 03:47 DEBUG  WindowsFrontend: frontend.on_quit
09-30 03:47 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-30 03:47 DEBUG  TaskList: # Cancelling tasklist
09-30 03:47 DEBUG  downloader: download finished (read 13221888 bytes)
09-30 03:47 DEBUG  TaskList: ### Finished download
09-30 03:47 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-30 03:47 DEBUG  root: application.on_quit
09-30 03:47 DEBUG  root: Forceful exit
09-30 03:47 INFO   root: sys.exit
09-30 03:49 INFO   root: === wubi 12.04 rev269 ===
09-30 03:49 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\UbuntuImage\\ubuntu-12.04.1-desktop-i386.iso']
09-30 03:49 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\data
09-30 03:49 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\bin\7z.exe
09-30 03:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:49 DEBUG  CommonBackend: Fetching basic info...
09-30 03:49 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:49 DEBUG  CommonBackend: platform=win32
09-30 03:49 DEBUG  CommonBackend: osname=nt
09-30 03:49 DEBUG  CommonBackend: language=en_US
09-30 03:49 DEBUG  CommonBackend: encoding=cp1252
09-30 03:49 DEBUG  WindowsBackend: arch=amd64
09-30 03:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\data\isolist.ini
09-30 03:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:49 DEBUG  WindowsBackend: Fetching host info...
09-30 03:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:49 DEBUG  WindowsBackend: windows version=vista
09-30 03:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:49 DEBUG  WindowsBackend: windows_sp=None
09-30 03:49 DEBUG  WindowsBackend: windows_build=7601
09-30 03:49 DEBUG  WindowsBackend: gmt=-6
09-30 03:49 DEBUG  WindowsBackend: country=US
09-30 03:49 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:49 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:49 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:49 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:49 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:49 DEBUG  WindowsBackend: windows_language=English
09-30 03:49 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:49 DEBUG  WindowsBackend: bootloader=vista
09-30 03:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 251203.242188 mb free ntfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(C: hd 251203.242188 mb free ntfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 03:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 03:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 03:49 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:49 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:49 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:49 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:49 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:49 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:49 DEBUG  CommonBackend: Searching for local CDs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 INFO   root: Already installed, running the uninstaller...
09-30 03:49 INFO   root: Running the uninstaller...
09-30 03:49 INFO   CommonBackend: This is the uninstaller running
09-30 03:49 DEBUG  WindowsFrontend: __init__...
09-30 03:49 DEBUG  WindowsFrontend: on_init...
09-30 03:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\translations, languages=['en_US', 'en']
09-30 03:49 INFO   root: Received settings
09-30 03:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\translations, languages=['en_US', 'en']
09-30 03:49 DEBUG  TaskList: # Running tasklist...
09-30 03:49 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 03:49 DEBUG  WindowsBackend: Could not find bcd id
09-30 03:49 DEBUG  WindowsBackend: undo_bootini C:
09-30 03:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 251203.242188 mb free ntfs)
09-30 03:49 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 03:49 DEBUG  TaskList: ## Running Remove target dir...
09-30 03:49 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 03:49 DEBUG  TaskList: ## Finished Remove target dir
09-30 03:49 DEBUG  TaskList: ## Running Remove registry key...
09-30 03:49 DEBUG  TaskList: ## Finished Remove registry key
09-30 03:49 DEBUG  TaskList: # Finished tasklist
09-30 03:49 INFO   root: Almost finished uninstalling
09-30 03:49 INFO   root: Finished uninstallation
09-30 03:49 DEBUG  CommonBackend: Fetching basic info...
09-30 03:49 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:49 DEBUG  CommonBackend: platform=win32
09-30 03:49 DEBUG  CommonBackend: osname=nt
09-30 03:49 DEBUG  WindowsBackend: arch=amd64
09-30 03:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\data\isolist.ini
09-30 03:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:49 DEBUG  WindowsBackend: Fetching host info...
09-30 03:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:49 DEBUG  WindowsBackend: windows version=vista
09-30 03:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:49 DEBUG  WindowsBackend: windows_sp=None
09-30 03:49 DEBUG  WindowsBackend: windows_build=7601
09-30 03:49 DEBUG  WindowsBackend: gmt=-6
09-30 03:49 DEBUG  WindowsBackend: country=US
09-30 03:49 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:49 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:49 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:49 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:49 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:49 DEBUG  WindowsBackend: windows_language=English
09-30 03:49 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:49 DEBUG  WindowsBackend: bootloader=vista
09-30 03:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 251218.210938 mb free ntfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(C: hd 251218.210938 mb free ntfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:49 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:49 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:49 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:49 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:49 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:49 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:49 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:49 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:49 DEBUG  CommonBackend: Searching for local CDs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 INFO   root: Running the installer...
09-30 03:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\translations, languages=['en_US', 'en']
09-30 03:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl398C.tmp\translations, languages=['en_US', 'en']
09-30 03:49 INFO   WindowsFrontend: Operation cancelled
09-30 03:49 DEBUG  WindowsFrontend: frontend.quit
09-30 03:49 DEBUG  WindowsFrontend: frontend.on_quit
09-30 03:49 DEBUG  root: application.on_quit
09-30 03:49 INFO   root: sys.exit
09-30 03:49 INFO   root: === wubi 12.04 rev269 ===
09-30 03:49 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\UbuntuImage\\ubuntu-12.04.1-desktop-i386.iso']
09-30 03:49 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\data
09-30 03:49 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\bin\7z.exe
09-30 03:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:49 DEBUG  CommonBackend: Fetching basic info...
09-30 03:49 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:49 DEBUG  CommonBackend: platform=win32
09-30 03:49 DEBUG  CommonBackend: osname=nt
09-30 03:49 DEBUG  CommonBackend: language=en_US
09-30 03:49 DEBUG  CommonBackend: encoding=cp1252
09-30 03:49 DEBUG  WindowsBackend: arch=amd64
09-30 03:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\data\isolist.ini
09-30 03:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:49 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:49 DEBUG  WindowsBackend: Fetching host info...
09-30 03:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:49 DEBUG  WindowsBackend: windows version=vista
09-30 03:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:49 DEBUG  WindowsBackend: windows_sp=None
09-30 03:49 DEBUG  WindowsBackend: windows_build=7601
09-30 03:49 DEBUG  WindowsBackend: gmt=-6
09-30 03:49 DEBUG  WindowsBackend: country=US
09-30 03:49 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:49 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:49 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:49 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:49 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:49 DEBUG  WindowsBackend: windows_language=English
09-30 03:49 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:49 DEBUG  WindowsBackend: bootloader=vista
09-30 03:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 251217.5625 mb free ntfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(C: hd 251217.5625 mb free ntfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:49 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:49 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:49 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:49 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:49 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:49 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:49 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:49 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:49 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:49 DEBUG  CommonBackend: Searching for local CDs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 INFO   root: Running the installer...
09-30 03:49 DEBUG  WindowsFrontend: __init__...
09-30 03:49 DEBUG  WindowsFrontend: on_init...
09-30 03:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\translations, languages=['en_US', 'en']
09-30 03:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\translations, languages=['en_US', 'en']
09-30 03:49 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 03:49 INFO   root: Received settings
09-30 03:49 DEBUG  CommonBackend: Searching for local CD
09-30 03:49 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:49 DEBUG  CommonBackend: Searching for local ISO
09-30 03:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\translations, languages=['en_US', 'en']
09-30 03:49 DEBUG  TaskList: # Running tasklist...
09-30 03:49 DEBUG  TaskList: ## Running select_target_dir...
09-30 03:49 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 03:49 DEBUG  TaskList: ## Finished select_target_dir
09-30 03:49 DEBUG  TaskList: ## Running create_dir_structure...
09-30 03:49 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 03:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 03:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 03:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 03:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 03:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 03:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 03:49 DEBUG  TaskList: ## Finished create_dir_structure
09-30 03:49 DEBUG  TaskList: ## Running create_uninstaller...
09-30 03:49 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 03:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 03:49 DEBUG  TaskList: ## Finished create_uninstaller
09-30 03:49 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 03:49 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 03:49 DEBUG  TaskList: ## Running get_diskimage...
09-30 03:49 DEBUG  CommonBackend: Trying to use pre-specified disk image C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:49 DEBUG  TaskList: New task is_valid_dimage
09-30 03:49 DEBUG  TaskList: ### Running is_valid_dimage...
09-30 03:49 DEBUG  Distro:   checking Ubuntu diskimage C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:49 DEBUG  TaskList: ### Finished is_valid_dimage
09-30 03:49 DEBUG  TaskList: ## Finished get_diskimage
09-30 03:49 DEBUG  TaskList: ## Running extract_diskimage...
09-30 03:49 DEBUG  TaskList: ## Finished extract_diskimage
09-30 03:49 DEBUG  TaskList: ## Running choose_disk_sizes...
09-30 03:49 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
09-30 03:49 DEBUG  TaskList: ## Finished choose_disk_sizes
09-30 03:49 DEBUG  TaskList: ## Running expand_diskimage...
09-30 03:49 ERROR  TaskList: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk


09-30 03:49 DEBUG  TaskList: # Cancelling tasklist
09-30 03:49 DEBUG  TaskList: # Finished tasklist
09-30 03:49 ERROR  root: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl8BA1.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk


09-30 03:50 INFO   root: === wubi 12.04 rev269 ===
09-30 03:50 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\Users\\Marc\\Desktop\\ubuntu-12.04.1-desktop-i386']
09-30 03:50 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\data
09-30 03:50 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\bin\7z.exe
09-30 03:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:50 DEBUG  CommonBackend: Fetching basic info...
09-30 03:50 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:50 DEBUG  CommonBackend: platform=win32
09-30 03:50 DEBUG  CommonBackend: osname=nt
09-30 03:50 DEBUG  CommonBackend: language=en_US
09-30 03:50 DEBUG  CommonBackend: encoding=cp1252
09-30 03:50 DEBUG  WindowsBackend: arch=amd64
09-30 03:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\data\isolist.ini
09-30 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:50 DEBUG  WindowsBackend: Fetching host info...
09-30 03:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:50 DEBUG  WindowsBackend: windows version=vista
09-30 03:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:50 DEBUG  WindowsBackend: windows_sp=None
09-30 03:50 DEBUG  WindowsBackend: windows_build=7601
09-30 03:50 DEBUG  WindowsBackend: gmt=-6
09-30 03:50 DEBUG  WindowsBackend: country=US
09-30 03:50 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:50 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:50 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:50 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:50 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:50 DEBUG  WindowsBackend: windows_language=English
09-30 03:50 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:50 DEBUG  WindowsBackend: bootloader=vista
09-30 03:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 251214.972656 mb free ntfs)
09-30 03:50 DEBUG  WindowsBackend: drive=Drive(C: hd 251214.972656 mb free ntfs)
09-30 03:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 03:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 03:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 03:50 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:50 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:50 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:50 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:50 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:50 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:50 DEBUG  CommonBackend: Searching for local CDs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 INFO   root: Already installed, running the uninstaller...
09-30 03:50 INFO   root: Running the uninstaller...
09-30 03:50 INFO   CommonBackend: This is the uninstaller running
09-30 03:50 DEBUG  WindowsFrontend: __init__...
09-30 03:50 DEBUG  WindowsFrontend: on_init...
09-30 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\translations, languages=['en_US', 'en']
09-30 03:50 INFO   root: Received settings
09-30 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\translations, languages=['en_US', 'en']
09-30 03:50 DEBUG  TaskList: # Running tasklist...
09-30 03:50 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 03:50 DEBUG  WindowsBackend: Could not find bcd id
09-30 03:50 DEBUG  WindowsBackend: undo_bootini C:
09-30 03:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 251214.972656 mb free ntfs)
09-30 03:50 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 03:50 DEBUG  TaskList: ## Running Remove target dir...
09-30 03:50 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 03:50 DEBUG  TaskList: ## Finished Remove target dir
09-30 03:50 DEBUG  TaskList: ## Running Remove registry key...
09-30 03:50 DEBUG  TaskList: ## Finished Remove registry key
09-30 03:50 DEBUG  TaskList: # Finished tasklist
09-30 03:50 INFO   root: Almost finished uninstalling
09-30 03:50 INFO   root: Finished uninstallation
09-30 03:50 DEBUG  CommonBackend: Fetching basic info...
09-30 03:50 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:50 DEBUG  CommonBackend: platform=win32
09-30 03:50 DEBUG  CommonBackend: osname=nt
09-30 03:50 DEBUG  WindowsBackend: arch=amd64
09-30 03:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\data\isolist.ini
09-30 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:50 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:50 DEBUG  WindowsBackend: Fetching host info...
09-30 03:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:50 DEBUG  WindowsBackend: windows version=vista
09-30 03:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:50 DEBUG  WindowsBackend: windows_sp=None
09-30 03:50 DEBUG  WindowsBackend: windows_build=7601
09-30 03:50 DEBUG  WindowsBackend: gmt=-6
09-30 03:50 DEBUG  WindowsBackend: country=US
09-30 03:50 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:50 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:50 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:50 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:50 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:50 DEBUG  WindowsBackend: windows_language=English
09-30 03:50 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:50 DEBUG  WindowsBackend: bootloader=vista
09-30 03:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 251217.355469 mb free ntfs)
09-30 03:50 DEBUG  WindowsBackend: drive=Drive(C: hd 251217.355469 mb free ntfs)
09-30 03:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:50 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:50 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:50 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:50 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:50 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:50 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:50 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:50 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:50 DEBUG  CommonBackend: Searching for local CDs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:50 INFO   root: Running the installer...
09-30 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\translations, languages=['en_US', 'en']
09-30 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylAE7C.tmp\translations, languages=['en_US', 'en']
09-30 03:50 INFO   WindowsFrontend: Operation cancelled
09-30 03:50 DEBUG  WindowsFrontend: frontend.quit
09-30 03:50 DEBUG  WindowsFrontend: frontend.on_quit
09-30 03:50 DEBUG  root: application.on_quit
09-30 03:50 INFO   root: sys.exit
09-30 03:52 INFO   root: === wubi 12.04 rev269 ===
09-30 03:52 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\Users\\Marc\\Desktop\\ubuntu-12.04.1-desktop-i386']
09-30 03:52 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\data
09-30 03:52 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\bin\7z.exe
09-30 03:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:52 DEBUG  CommonBackend: Fetching basic info...
09-30 03:52 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:52 DEBUG  CommonBackend: platform=win32
09-30 03:52 DEBUG  CommonBackend: osname=nt
09-30 03:52 DEBUG  CommonBackend: language=en_US
09-30 03:52 DEBUG  CommonBackend: encoding=cp1252
09-30 03:52 DEBUG  WindowsBackend: arch=amd64
09-30 03:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\data\isolist.ini
09-30 03:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:52 DEBUG  WindowsBackend: Fetching host info...
09-30 03:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:52 DEBUG  WindowsBackend: windows version=vista
09-30 03:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:52 DEBUG  WindowsBackend: windows_sp=None
09-30 03:52 DEBUG  WindowsBackend: windows_build=7601
09-30 03:52 DEBUG  WindowsBackend: gmt=-6
09-30 03:52 DEBUG  WindowsBackend: country=US
09-30 03:52 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:52 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:52 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:52 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:52 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:52 DEBUG  WindowsBackend: windows_language=English
09-30 03:52 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:52 DEBUG  WindowsBackend: bootloader=vista
09-30 03:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250521.386719 mb free ntfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(C: hd 250521.386719 mb free ntfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:52 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:52 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:52 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:52 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:52 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:52 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:52 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:52 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:52 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:52 DEBUG  CommonBackend: Searching for local CDs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 INFO   root: Running the installer...
09-30 03:52 DEBUG  WindowsFrontend: __init__...
09-30 03:52 DEBUG  WindowsFrontend: on_init...
09-30 03:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\translations, languages=['en_US', 'en']
09-30 03:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\translations, languages=['en_US', 'en']
09-30 03:52 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 03:52 INFO   root: Received settings
09-30 03:52 DEBUG  CommonBackend: Searching for local CD
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  CommonBackend: Searching for local ISO
09-30 03:52 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 03:52 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 03:52 DEBUG  Distro:   parsing info from str=                                                                 
09-30 03:52 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-30 03:52 DEBUG  Distro: could not get info None
09-30 03:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl3E9B.tmp\translations, languages=['en_US', 'en']
09-30 03:52 DEBUG  TaskList: # Running tasklist...
09-30 03:52 DEBUG  TaskList: ## Running select_target_dir...
09-30 03:52 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 03:52 DEBUG  TaskList: ## Finished select_target_dir
09-30 03:52 DEBUG  TaskList: ## Running create_dir_structure...
09-30 03:52 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 03:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 03:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 03:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 03:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 03:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 03:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 03:52 DEBUG  TaskList: ## Finished create_dir_structure
09-30 03:52 DEBUG  TaskList: ## Running create_uninstaller...
09-30 03:52 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 03:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 03:52 DEBUG  TaskList: ## Finished create_uninstaller
09-30 03:52 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 03:52 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 03:52 DEBUG  TaskList: ## Running get_diskimage...
09-30 03:52 DEBUG  TaskList: New task download
09-30 03:52 DEBUG  TaskList: ### Running download...
09-30 03:52 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-30 03:52 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-30 03:52 INFO   WindowsFrontend: Operation cancelled
09-30 03:52 DEBUG  WindowsFrontend: frontend.quit
09-30 03:52 DEBUG  WindowsFrontend: frontend.on_quit
09-30 03:52 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-30 03:52 DEBUG  TaskList: # Cancelling tasklist
09-30 03:52 DEBUG  downloader: download finished (read 901120 bytes)
09-30 03:52 DEBUG  TaskList: ### Finished download
09-30 03:52 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-30 03:52 DEBUG  root: application.on_quit
09-30 03:52 DEBUG  root: Forceful exit
09-30 03:52 INFO   root: sys.exit
09-30 03:52 INFO   root: === wubi 12.04 rev269 ===
09-30 03:52 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\UbuntuImage\\ubuntu-12.04.1-desktop-i386.iso']
09-30 03:52 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\data
09-30 03:52 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\bin\7z.exe
09-30 03:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:52 DEBUG  CommonBackend: Fetching basic info...
09-30 03:52 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:52 DEBUG  CommonBackend: platform=win32
09-30 03:52 DEBUG  CommonBackend: osname=nt
09-30 03:52 DEBUG  CommonBackend: language=en_US
09-30 03:52 DEBUG  CommonBackend: encoding=cp1252
09-30 03:52 DEBUG  WindowsBackend: arch=amd64
09-30 03:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\data\isolist.ini
09-30 03:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:52 DEBUG  WindowsBackend: Fetching host info...
09-30 03:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:52 DEBUG  WindowsBackend: windows version=vista
09-30 03:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:52 DEBUG  WindowsBackend: windows_sp=None
09-30 03:52 DEBUG  WindowsBackend: windows_build=7601
09-30 03:52 DEBUG  WindowsBackend: gmt=-6
09-30 03:52 DEBUG  WindowsBackend: country=US
09-30 03:52 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:52 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:52 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:52 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:52 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:52 DEBUG  WindowsBackend: windows_language=English
09-30 03:52 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:52 DEBUG  WindowsBackend: bootloader=vista
09-30 03:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250517.960938 mb free ntfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(C: hd 250517.960938 mb free ntfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 03:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 03:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 03:52 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:52 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:52 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:52 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:52 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:52 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:52 DEBUG  CommonBackend: Searching for local CDs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 INFO   root: Already installed, running the uninstaller...
09-30 03:52 INFO   root: Running the uninstaller...
09-30 03:52 INFO   CommonBackend: This is the uninstaller running
09-30 03:52 DEBUG  WindowsFrontend: __init__...
09-30 03:52 DEBUG  WindowsFrontend: on_init...
09-30 03:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\translations, languages=['en_US', 'en']
09-30 03:52 INFO   root: Received settings
09-30 03:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\translations, languages=['en_US', 'en']
09-30 03:52 DEBUG  TaskList: # Running tasklist...
09-30 03:52 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 03:52 DEBUG  WindowsBackend: Could not find bcd id
09-30 03:52 DEBUG  WindowsBackend: undo_bootini C:
09-30 03:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 250517.960938 mb free ntfs)
09-30 03:52 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 03:52 DEBUG  TaskList: ## Running Remove target dir...
09-30 03:52 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 03:52 DEBUG  TaskList: ## Finished Remove target dir
09-30 03:52 DEBUG  TaskList: ## Running Remove registry key...
09-30 03:52 DEBUG  TaskList: ## Finished Remove registry key
09-30 03:52 DEBUG  TaskList: # Finished tasklist
09-30 03:52 INFO   root: Almost finished uninstalling
09-30 03:52 INFO   root: Finished uninstallation
09-30 03:52 DEBUG  CommonBackend: Fetching basic info...
09-30 03:52 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 03:52 DEBUG  CommonBackend: platform=win32
09-30 03:52 DEBUG  CommonBackend: osname=nt
09-30 03:52 DEBUG  WindowsBackend: arch=amd64
09-30 03:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\data\isolist.ini
09-30 03:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:52 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:52 DEBUG  WindowsBackend: Fetching host info...
09-30 03:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:52 DEBUG  WindowsBackend: windows version=vista
09-30 03:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:52 DEBUG  WindowsBackend: windows_sp=None
09-30 03:52 DEBUG  WindowsBackend: windows_build=7601
09-30 03:52 DEBUG  WindowsBackend: gmt=-6
09-30 03:52 DEBUG  WindowsBackend: country=US
09-30 03:52 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:52 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:52 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:52 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:52 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:52 DEBUG  WindowsBackend: windows_language=English
09-30 03:52 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:52 DEBUG  WindowsBackend: bootloader=vista
09-30 03:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250521.191406 mb free ntfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(C: hd 250521.191406 mb free ntfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:52 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:52 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:52 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:52 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:52 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:52 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:52 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:52 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:52 DEBUG  CommonBackend: Searching for local CDs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:52 INFO   root: Running the installer...
09-30 03:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\translations, languages=['en_US', 'en']
09-30 03:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\translations, languages=['en_US', 'en']
09-30 03:53 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 03:53 INFO   root: Received settings
09-30 03:53 DEBUG  CommonBackend: Searching for local CD
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  CommonBackend: Searching for local ISO
09-30 03:53 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 03:53 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 03:53 DEBUG  Distro:   parsing info from str=                                                                 
09-30 03:53 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-30 03:53 DEBUG  Distro: could not get info None
09-30 03:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\translations, languages=['en_US', 'en']
09-30 03:53 DEBUG  TaskList: # Running tasklist...
09-30 03:53 DEBUG  TaskList: ## Running select_target_dir...
09-30 03:53 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 03:53 DEBUG  TaskList: ## Finished select_target_dir
09-30 03:53 DEBUG  TaskList: ## Running create_dir_structure...
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 03:53 DEBUG  TaskList: ## Finished create_dir_structure
09-30 03:53 DEBUG  TaskList: ## Running create_uninstaller...
09-30 03:53 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 03:53 DEBUG  TaskList: ## Finished create_uninstaller
09-30 03:53 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 03:53 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 03:53 DEBUG  TaskList: ## Running get_diskimage...
09-30 03:53 DEBUG  CommonBackend: Trying to use pre-specified disk image C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:53 DEBUG  TaskList: New task is_valid_dimage
09-30 03:53 DEBUG  TaskList: ### Running is_valid_dimage...
09-30 03:53 DEBUG  Distro:   checking Ubuntu diskimage C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:53 DEBUG  TaskList: ### Finished is_valid_dimage
09-30 03:53 DEBUG  TaskList: ## Finished get_diskimage
09-30 03:53 DEBUG  TaskList: ## Running extract_diskimage...
09-30 03:53 DEBUG  TaskList: ## Finished extract_diskimage
09-30 03:53 DEBUG  TaskList: ## Running choose_disk_sizes...
09-30 03:53 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
09-30 03:53 DEBUG  TaskList: ## Finished choose_disk_sizes
09-30 03:53 DEBUG  TaskList: ## Running expand_diskimage...
09-30 03:53 ERROR  TaskList: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk


09-30 03:53 DEBUG  TaskList: # Cancelling tasklist
09-30 03:53 DEBUG  TaskList: # Finished tasklist
09-30 03:53 ERROR  root: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pylBBC5.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk


09-30 03:53 INFO   root: === wubi 12.04 rev269 ===
09-30 03:53 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\UbuntuImage\\wubi.exe"']
09-30 03:53 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\data
09-30 03:53 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\bin\7z.exe
09-30 03:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:53 DEBUG  CommonBackend: Fetching basic info...
09-30 03:53 DEBUG  CommonBackend: original_exe=C:\UbuntuImage\wubi.exe
09-30 03:53 DEBUG  CommonBackend: platform=win32
09-30 03:53 DEBUG  CommonBackend: osname=nt
09-30 03:53 DEBUG  CommonBackend: language=en_US
09-30 03:53 DEBUG  CommonBackend: encoding=cp1252
09-30 03:53 DEBUG  WindowsBackend: arch=amd64
09-30 03:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\data\isolist.ini
09-30 03:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:53 DEBUG  WindowsBackend: Fetching host info...
09-30 03:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:53 DEBUG  WindowsBackend: windows version=vista
09-30 03:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:53 DEBUG  WindowsBackend: windows_sp=None
09-30 03:53 DEBUG  WindowsBackend: windows_build=7601
09-30 03:53 DEBUG  WindowsBackend: gmt=-6
09-30 03:53 DEBUG  WindowsBackend: country=US
09-30 03:53 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:53 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:53 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:53 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:53 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:53 DEBUG  WindowsBackend: windows_language=English
09-30 03:53 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:53 DEBUG  WindowsBackend: bootloader=vista
09-30 03:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250515.242188 mb free ntfs)
09-30 03:53 DEBUG  WindowsBackend: drive=Drive(C: hd 250515.242188 mb free ntfs)
09-30 03:53 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:53 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 03:53 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 03:53 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 03:53 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:53 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:53 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:53 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:53 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:53 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:53 DEBUG  CommonBackend: Searching for local CDs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 INFO   root: Already installed, running the uninstaller...
09-30 03:53 INFO   root: Running the uninstaller...
09-30 03:53 INFO   CommonBackend: This is the uninstaller running
09-30 03:53 DEBUG  WindowsFrontend: __init__...
09-30 03:53 DEBUG  WindowsFrontend: on_init...
09-30 03:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\translations, languages=['en_US', 'en']
09-30 03:53 INFO   root: Received settings
09-30 03:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\translations, languages=['en_US', 'en']
09-30 03:53 DEBUG  TaskList: # Running tasklist...
09-30 03:53 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 03:53 DEBUG  WindowsBackend: Could not find bcd id
09-30 03:53 DEBUG  WindowsBackend: undo_bootini C:
09-30 03:53 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 250515.242188 mb free ntfs)
09-30 03:53 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 03:53 DEBUG  TaskList: ## Running Remove target dir...
09-30 03:53 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 03:53 DEBUG  TaskList: ## Finished Remove target dir
09-30 03:53 DEBUG  TaskList: ## Running Remove registry key...
09-30 03:53 DEBUG  TaskList: ## Finished Remove registry key
09-30 03:53 DEBUG  TaskList: # Finished tasklist
09-30 03:53 INFO   root: Almost finished uninstalling
09-30 03:53 INFO   root: Finished uninstallation
09-30 03:53 DEBUG  CommonBackend: Fetching basic info...
09-30 03:53 DEBUG  CommonBackend: original_exe=C:\UbuntuImage\wubi.exe
09-30 03:53 DEBUG  CommonBackend: platform=win32
09-30 03:53 DEBUG  CommonBackend: osname=nt
09-30 03:53 DEBUG  WindowsBackend: arch=amd64
09-30 03:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\data\isolist.ini
09-30 03:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:53 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:53 DEBUG  WindowsBackend: Fetching host info...
09-30 03:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:53 DEBUG  WindowsBackend: windows version=vista
09-30 03:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:53 DEBUG  WindowsBackend: windows_sp=None
09-30 03:53 DEBUG  WindowsBackend: windows_build=7601
09-30 03:53 DEBUG  WindowsBackend: gmt=-6
09-30 03:53 DEBUG  WindowsBackend: country=US
09-30 03:53 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:53 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:53 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:53 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:53 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:53 DEBUG  WindowsBackend: windows_language=English
09-30 03:53 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:53 DEBUG  WindowsBackend: bootloader=vista
09-30 03:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250517.476563 mb free ntfs)
09-30 03:53 DEBUG  WindowsBackend: drive=Drive(C: hd 250517.476563 mb free ntfs)
09-30 03:53 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:53 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:53 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:53 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:53 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:53 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:53 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:53 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:53 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:53 DEBUG  CommonBackend: Searching for local CDs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 INFO   root: Running the installer...
09-30 03:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\translations, languages=['en_US', 'en']
09-30 03:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\translations, languages=['en_US', 'en']
09-30 03:53 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 03:53 INFO   root: Received settings
09-30 03:53 DEBUG  CommonBackend: Searching for local CD
09-30 03:53 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:53 DEBUG  CommonBackend: Searching for local ISO
09-30 03:53 DEBUG  Distro:   checking Ubuntu ISO C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:53 DEBUG  WindowsBackend:   extracting .disk\info from C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:53 DEBUG  Distro:   parsing info from str=                                                                 
09-30 03:53 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-30 03:53 DEBUG  Distro: could not get info None
09-30 03:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl5871.tmp\translations, languages=['en_US', 'en']
09-30 03:53 DEBUG  TaskList: # Running tasklist...
09-30 03:53 DEBUG  TaskList: ## Running select_target_dir...
09-30 03:53 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 03:53 DEBUG  TaskList: ## Finished select_target_dir
09-30 03:53 DEBUG  TaskList: ## Running create_dir_structure...
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 03:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 03:53 DEBUG  TaskList: ## Finished create_dir_structure
09-30 03:53 DEBUG  TaskList: ## Running create_uninstaller...
09-30 03:53 DEBUG  WindowsBackend: Copying uninstaller C:\UbuntuImage\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 03:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 03:53 DEBUG  TaskList: ## Finished create_uninstaller
09-30 03:53 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 03:53 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 03:53 DEBUG  TaskList: ## Running get_diskimage...
09-30 03:53 DEBUG  TaskList: New task download
09-30 03:53 DEBUG  TaskList: ### Running download...
09-30 03:53 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-30 03:53 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-30 03:53 INFO   WindowsFrontend: Operation cancelled
09-30 03:53 DEBUG  WindowsFrontend: frontend.quit
09-30 03:53 DEBUG  WindowsFrontend: frontend.on_quit
09-30 03:53 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-30 03:53 DEBUG  TaskList: # Cancelling tasklist
09-30 03:53 DEBUG  downloader: download finished (read 2228224 bytes)
09-30 03:53 DEBUG  TaskList: ### Finished download
09-30 03:53 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-30 03:53 DEBUG  root: application.on_quit
09-30 03:53 DEBUG  root: Forceful exit
09-30 03:53 INFO   root: sys.exit
09-30 03:54 INFO   root: === wubi 12.04 rev269 ===
09-30 03:54 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 03:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\UbuntuImage\\wubi.exe"']
09-30 03:54 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\data
09-30 03:54 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\bin\7z.exe
09-30 03:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 03:54 DEBUG  CommonBackend: Fetching basic info...
09-30 03:54 DEBUG  CommonBackend: original_exe=C:\UbuntuImage\wubi.exe
09-30 03:54 DEBUG  CommonBackend: platform=win32
09-30 03:54 DEBUG  CommonBackend: osname=nt
09-30 03:54 DEBUG  CommonBackend: language=en_US
09-30 03:54 DEBUG  CommonBackend: encoding=cp1252
09-30 03:54 DEBUG  WindowsBackend: arch=amd64
09-30 03:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\data\isolist.ini
09-30 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:54 DEBUG  WindowsBackend: Fetching host info...
09-30 03:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:54 DEBUG  WindowsBackend: windows version=vista
09-30 03:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:54 DEBUG  WindowsBackend: windows_sp=None
09-30 03:54 DEBUG  WindowsBackend: windows_build=7601
09-30 03:54 DEBUG  WindowsBackend: gmt=-6
09-30 03:54 DEBUG  WindowsBackend: country=US
09-30 03:54 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:54 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:54 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:54 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:54 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:54 DEBUG  WindowsBackend: windows_language=English
09-30 03:54 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:54 DEBUG  WindowsBackend: bootloader=vista
09-30 03:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250513.347656 mb free ntfs)
09-30 03:54 DEBUG  WindowsBackend: drive=Drive(C: hd 250513.347656 mb free ntfs)
09-30 03:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 03:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 03:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 03:54 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:54 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:54 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 03:54 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 03:54 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:54 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:54 DEBUG  CommonBackend: Searching for local CDs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 INFO   root: Already installed, running the uninstaller...
09-30 03:54 INFO   root: Running the uninstaller...
09-30 03:54 INFO   CommonBackend: This is the uninstaller running
09-30 03:54 DEBUG  WindowsFrontend: __init__...
09-30 03:54 DEBUG  WindowsFrontend: on_init...
09-30 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\translations, languages=['en_US', 'en']
09-30 03:54 INFO   root: Received settings
09-30 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\translations, languages=['en_US', 'en']
09-30 03:54 DEBUG  TaskList: # Running tasklist...
09-30 03:54 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 03:54 DEBUG  WindowsBackend: Could not find bcd id
09-30 03:54 DEBUG  WindowsBackend: undo_bootini C:
09-30 03:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 250513.347656 mb free ntfs)
09-30 03:54 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 03:54 DEBUG  TaskList: ## Running Remove target dir...
09-30 03:54 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 03:54 DEBUG  TaskList: ## Finished Remove target dir
09-30 03:54 DEBUG  TaskList: ## Running Remove registry key...
09-30 03:54 DEBUG  TaskList: ## Finished Remove registry key
09-30 03:54 DEBUG  TaskList: # Finished tasklist
09-30 03:54 INFO   root: Almost finished uninstalling
09-30 03:54 INFO   root: Finished uninstallation
09-30 03:54 DEBUG  CommonBackend: Fetching basic info...
09-30 03:54 DEBUG  CommonBackend: original_exe=C:\UbuntuImage\wubi.exe
09-30 03:54 DEBUG  CommonBackend: platform=win32
09-30 03:54 DEBUG  CommonBackend: osname=nt
09-30 03:54 DEBUG  WindowsBackend: arch=amd64
09-30 03:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\data\isolist.ini
09-30 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 03:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 03:54 DEBUG  WindowsBackend: Fetching host info...
09-30 03:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 03:54 DEBUG  WindowsBackend: windows version=vista
09-30 03:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 03:54 DEBUG  WindowsBackend: windows_sp=None
09-30 03:54 DEBUG  WindowsBackend: windows_build=7601
09-30 03:54 DEBUG  WindowsBackend: gmt=-6
09-30 03:54 DEBUG  WindowsBackend: country=US
09-30 03:54 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 03:54 DEBUG  WindowsBackend: windows_username=Marc
09-30 03:54 DEBUG  WindowsBackend: user_full_name=Marc
09-30 03:54 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 03:54 DEBUG  WindowsBackend: windows_language_code=1033
09-30 03:54 DEBUG  WindowsBackend: windows_language=English
09-30 03:54 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 03:54 DEBUG  WindowsBackend: bootloader=vista
09-30 03:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250517.839844 mb free ntfs)
09-30 03:54 DEBUG  WindowsBackend: drive=Drive(C: hd 250517.839844 mb free ntfs)
09-30 03:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 03:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 03:54 DEBUG  WindowsBackend: uninstaller_path=None
09-30 03:54 DEBUG  WindowsBackend: previous_target_dir=None
09-30 03:54 DEBUG  WindowsBackend: previous_distro_name=None
09-30 03:54 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 03:54 DEBUG  WindowsBackend: keyboard_layout=us
09-30 03:54 DEBUG  WindowsBackend: keyboard_variant=
09-30 03:54 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 03:54 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 03:54 DEBUG  CommonBackend: Searching for local CDs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 INFO   root: Running the installer...
09-30 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\translations, languages=['en_US', 'en']
09-30 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\translations, languages=['en_US', 'en']
09-30 03:54 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 03:54 INFO   root: Received settings
09-30 03:54 DEBUG  CommonBackend: Searching for local CD
09-30 03:54 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 03:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 03:54 DEBUG  CommonBackend: Searching for local ISO
09-30 03:54 DEBUG  Distro:   checking Ubuntu ISO C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:54 DEBUG  WindowsBackend:   extracting .disk\info from C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 03:54 DEBUG  Distro:   parsing info from str=                                                                 
09-30 03:54 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-30 03:54 DEBUG  Distro: could not get info None
09-30 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pylC7B7.tmp\translations, languages=['en_US', 'en']
09-30 03:54 DEBUG  TaskList: # Running tasklist...
09-30 03:54 DEBUG  TaskList: ## Running select_target_dir...
09-30 03:54 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 03:54 DEBUG  TaskList: ## Finished select_target_dir
09-30 03:54 DEBUG  TaskList: ## Running create_dir_structure...
09-30 03:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 03:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 03:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 03:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 03:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 03:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 03:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 03:54 DEBUG  TaskList: ## Finished create_dir_structure
09-30 03:54 DEBUG  TaskList: ## Running create_uninstaller...
09-30 03:54 DEBUG  WindowsBackend: Copying uninstaller C:\UbuntuImage\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 03:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 03:54 DEBUG  TaskList: ## Finished create_uninstaller
09-30 03:54 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 03:54 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 03:54 DEBUG  TaskList: ## Running get_diskimage...
09-30 03:54 DEBUG  TaskList: New task download
09-30 03:54 DEBUG  TaskList: ### Running download...
09-30 03:54 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
09-30 03:54 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
09-30 04:12 DEBUG  downloader: download finished (read 506079792 bytes)
09-30 04:12 DEBUG  TaskList: ### Finished download
09-30 04:12 DEBUG  TaskList: ## Finished get_diskimage
09-30 04:12 DEBUG  TaskList: ## Running extract_diskimage...
09-30 04:13 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-30 04:13 DEBUG  TaskList: # Cancelling tasklist
09-30 04:13 DEBUG  TaskList: # Finished tasklist
09-30 04:13 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
09-30 04:14 INFO   root: === wubi 12.04 rev269 ===
09-30 04:14 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 04:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\UbuntuImage\\ubuntu-12.04.1-desktop-i386.iso']
09-30 04:14 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\data
09-30 04:14 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\bin\7z.exe
09-30 04:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 04:14 DEBUG  CommonBackend: Fetching basic info...
09-30 04:14 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 04:14 DEBUG  CommonBackend: platform=win32
09-30 04:14 DEBUG  CommonBackend: osname=nt
09-30 04:14 DEBUG  CommonBackend: language=en_US
09-30 04:14 DEBUG  CommonBackend: encoding=cp1252
09-30 04:14 DEBUG  WindowsBackend: arch=amd64
09-30 04:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\data\isolist.ini
09-30 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 04:14 DEBUG  WindowsBackend: Fetching host info...
09-30 04:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 04:14 DEBUG  WindowsBackend: windows version=vista
09-30 04:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 04:14 DEBUG  WindowsBackend: windows_sp=None
09-30 04:14 DEBUG  WindowsBackend: windows_build=7601
09-30 04:14 DEBUG  WindowsBackend: gmt=-6
09-30 04:14 DEBUG  WindowsBackend: country=US
09-30 04:14 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 04:14 DEBUG  WindowsBackend: windows_username=Marc
09-30 04:14 DEBUG  WindowsBackend: user_full_name=Marc
09-30 04:14 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 04:14 DEBUG  WindowsBackend: windows_language_code=1033
09-30 04:14 DEBUG  WindowsBackend: windows_language=English
09-30 04:14 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 04:14 DEBUG  WindowsBackend: bootloader=vista
09-30 04:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 248862.964844 mb free ntfs)
09-30 04:14 DEBUG  WindowsBackend: drive=Drive(C: hd 248862.964844 mb free ntfs)
09-30 04:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 04:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 04:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 04:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 04:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 04:14 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 04:14 DEBUG  WindowsBackend: keyboard_layout=us
09-30 04:14 DEBUG  WindowsBackend: keyboard_variant=
09-30 04:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 04:14 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 04:14 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 04:14 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 04:14 DEBUG  CommonBackend: Searching for local CDs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 INFO   root: Already installed, running the uninstaller...
09-30 04:14 INFO   root: Running the uninstaller...
09-30 04:14 INFO   CommonBackend: This is the uninstaller running
09-30 04:14 DEBUG  WindowsFrontend: __init__...
09-30 04:14 DEBUG  WindowsFrontend: on_init...
09-30 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\translations, languages=['en_US', 'en']
09-30 04:14 INFO   root: Received settings
09-30 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\translations, languages=['en_US', 'en']
09-30 04:14 DEBUG  TaskList: # Running tasklist...
09-30 04:14 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 04:14 DEBUG  WindowsBackend: Could not find bcd id
09-30 04:14 DEBUG  WindowsBackend: undo_bootini C:
09-30 04:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 248862.964844 mb free ntfs)
09-30 04:14 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 04:14 DEBUG  TaskList: ## Running Remove target dir...
09-30 04:14 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 04:14 DEBUG  TaskList: ## Finished Remove target dir
09-30 04:14 DEBUG  TaskList: ## Running Remove registry key...
09-30 04:14 DEBUG  TaskList: ## Finished Remove registry key
09-30 04:14 DEBUG  TaskList: # Finished tasklist
09-30 04:14 INFO   root: Almost finished uninstalling
09-30 04:14 INFO   root: Finished uninstallation
09-30 04:14 DEBUG  CommonBackend: Fetching basic info...
09-30 04:14 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 04:14 DEBUG  CommonBackend: platform=win32
09-30 04:14 DEBUG  CommonBackend: osname=nt
09-30 04:14 DEBUG  WindowsBackend: arch=amd64
09-30 04:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\data\isolist.ini
09-30 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 04:14 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 04:14 DEBUG  WindowsBackend: Fetching host info...
09-30 04:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 04:14 DEBUG  WindowsBackend: windows version=vista
09-30 04:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 04:14 DEBUG  WindowsBackend: windows_sp=None
09-30 04:14 DEBUG  WindowsBackend: windows_build=7601
09-30 04:14 DEBUG  WindowsBackend: gmt=-6
09-30 04:14 DEBUG  WindowsBackend: country=US
09-30 04:14 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 04:14 DEBUG  WindowsBackend: windows_username=Marc
09-30 04:14 DEBUG  WindowsBackend: user_full_name=Marc
09-30 04:14 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 04:14 DEBUG  WindowsBackend: windows_language_code=1033
09-30 04:14 DEBUG  WindowsBackend: windows_language=English
09-30 04:14 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 04:14 DEBUG  WindowsBackend: bootloader=vista
09-30 04:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250075.535156 mb free ntfs)
09-30 04:14 DEBUG  WindowsBackend: drive=Drive(C: hd 250075.535156 mb free ntfs)
09-30 04:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 04:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 04:14 DEBUG  WindowsBackend: uninstaller_path=None
09-30 04:14 DEBUG  WindowsBackend: previous_target_dir=None
09-30 04:14 DEBUG  WindowsBackend: previous_distro_name=None
09-30 04:14 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 04:14 DEBUG  WindowsBackend: keyboard_layout=us
09-30 04:14 DEBUG  WindowsBackend: keyboard_variant=
09-30 04:14 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 04:14 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 04:14 DEBUG  CommonBackend: Searching for local CDs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 INFO   root: Running the installer...
09-30 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\translations, languages=['en_US', 'en']
09-30 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\translations, languages=['en_US', 'en']
09-30 04:14 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 04:14 INFO   root: Received settings
09-30 04:14 DEBUG  CommonBackend: Searching for local CD
09-30 04:14 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:14 DEBUG  CommonBackend: Searching for local ISO
09-30 04:14 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 04:14 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 04:14 DEBUG  Distro:   parsing info from str=                                                                 
09-30 04:14 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-30 04:14 DEBUG  Distro: could not get info None
09-30 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\translations, languages=['en_US', 'en']
09-30 04:14 DEBUG  TaskList: # Running tasklist...
09-30 04:14 DEBUG  TaskList: ## Running select_target_dir...
09-30 04:14 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 04:14 DEBUG  TaskList: ## Finished select_target_dir
09-30 04:14 DEBUG  TaskList: ## Running create_dir_structure...
09-30 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 04:14 DEBUG  TaskList: ## Finished create_dir_structure
09-30 04:14 DEBUG  TaskList: ## Running create_uninstaller...
09-30 04:14 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 04:14 DEBUG  TaskList: ## Finished create_uninstaller
09-30 04:14 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 04:14 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 04:14 DEBUG  TaskList: ## Running get_diskimage...
09-30 04:14 DEBUG  CommonBackend: Trying to use pre-specified disk image C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 04:14 DEBUG  TaskList: New task is_valid_dimage
09-30 04:14 DEBUG  TaskList: ### Running is_valid_dimage...
09-30 04:14 DEBUG  Distro:   checking Ubuntu diskimage C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 04:14 DEBUG  TaskList: ### Finished is_valid_dimage
09-30 04:14 DEBUG  TaskList: ## Finished get_diskimage
09-30 04:14 DEBUG  TaskList: ## Running extract_diskimage...
09-30 04:14 DEBUG  TaskList: ## Finished extract_diskimage
09-30 04:14 DEBUG  TaskList: ## Running choose_disk_sizes...
09-30 04:14 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
09-30 04:14 DEBUG  TaskList: ## Finished choose_disk_sizes
09-30 04:14 DEBUG  TaskList: ## Running expand_diskimage...
09-30 04:14 ERROR  TaskList: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk


09-30 04:14 DEBUG  TaskList: # Cancelling tasklist
09-30 04:14 DEBUG  TaskList: # Finished tasklist
09-30 04:14 ERROR  root: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl4993.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk


09-30 04:16 INFO   root: === wubi 12.04 rev269 ===
09-30 04:16 DEBUG  root: Logfile is c:\users\marc\appdata\local\temp\wubi-12.04-rev269.log
09-30 04:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Marc\\Desktop\\wubi.exe"', '--dimagepath=C:\\UbuntuImage\\ubuntu-12.04.1-desktop-i386.iso']
09-30 04:16 DEBUG  CommonBackend: data_dir=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\data
09-30 04:16 DEBUG  WindowsBackend: 7z=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\bin\7z.exe
09-30 04:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 04:16 DEBUG  CommonBackend: Fetching basic info...
09-30 04:16 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 04:16 DEBUG  CommonBackend: platform=win32
09-30 04:16 DEBUG  CommonBackend: osname=nt
09-30 04:16 DEBUG  CommonBackend: language=en_US
09-30 04:16 DEBUG  CommonBackend: encoding=cp1252
09-30 04:16 DEBUG  WindowsBackend: arch=amd64
09-30 04:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\data\isolist.ini
09-30 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 04:16 DEBUG  WindowsBackend: Fetching host info...
09-30 04:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 04:16 DEBUG  WindowsBackend: windows version=vista
09-30 04:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 04:16 DEBUG  WindowsBackend: windows_sp=None
09-30 04:16 DEBUG  WindowsBackend: windows_build=7601
09-30 04:16 DEBUG  WindowsBackend: gmt=-6
09-30 04:16 DEBUG  WindowsBackend: country=US
09-30 04:16 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 04:16 DEBUG  WindowsBackend: windows_username=Marc
09-30 04:16 DEBUG  WindowsBackend: user_full_name=Marc
09-30 04:16 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 04:16 DEBUG  WindowsBackend: windows_language_code=1033
09-30 04:16 DEBUG  WindowsBackend: windows_language=English
09-30 04:16 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 04:16 DEBUG  WindowsBackend: bootloader=vista
09-30 04:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250072.976563 mb free ntfs)
09-30 04:16 DEBUG  WindowsBackend: drive=Drive(C: hd 250072.976563 mb free ntfs)
09-30 04:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 04:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 04:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 04:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 04:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-30 04:16 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 04:16 DEBUG  WindowsBackend: keyboard_layout=us
09-30 04:16 DEBUG  WindowsBackend: keyboard_variant=
09-30 04:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 04:16 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 04:16 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 04:16 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 04:16 DEBUG  CommonBackend: Searching for local CDs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 INFO   root: Already installed, running the uninstaller...
09-30 04:16 INFO   root: Running the uninstaller...
09-30 04:16 INFO   CommonBackend: This is the uninstaller running
09-30 04:16 DEBUG  WindowsFrontend: __init__...
09-30 04:16 DEBUG  WindowsFrontend: on_init...
09-30 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\translations, languages=['en_US', 'en']
09-30 04:16 INFO   root: Received settings
09-30 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\translations, languages=['en_US', 'en']
09-30 04:16 DEBUG  TaskList: # Running tasklist...
09-30 04:16 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 04:16 DEBUG  WindowsBackend: Could not find bcd id
09-30 04:16 DEBUG  WindowsBackend: undo_bootini C:
09-30 04:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 250072.976563 mb free ntfs)
09-30 04:16 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 04:16 DEBUG  TaskList: ## Running Remove target dir...
09-30 04:16 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 04:16 DEBUG  TaskList: ## Finished Remove target dir
09-30 04:16 DEBUG  TaskList: ## Running Remove registry key...
09-30 04:16 DEBUG  TaskList: ## Finished Remove registry key
09-30 04:16 DEBUG  TaskList: # Finished tasklist
09-30 04:16 INFO   root: Almost finished uninstalling
09-30 04:16 INFO   root: Finished uninstallation
09-30 04:16 DEBUG  CommonBackend: Fetching basic info...
09-30 04:16 DEBUG  CommonBackend: original_exe=C:\Users\Marc\Desktop\wubi.exe
09-30 04:16 DEBUG  CommonBackend: platform=win32
09-30 04:16 DEBUG  CommonBackend: osname=nt
09-30 04:16 DEBUG  WindowsBackend: arch=amd64
09-30 04:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\data\isolist.ini
09-30 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 04:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-30 04:16 DEBUG  WindowsBackend: Fetching host info...
09-30 04:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 04:16 DEBUG  WindowsBackend: windows version=vista
09-30 04:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
09-30 04:16 DEBUG  WindowsBackend: windows_sp=None
09-30 04:16 DEBUG  WindowsBackend: windows_build=7601
09-30 04:16 DEBUG  WindowsBackend: gmt=-6
09-30 04:16 DEBUG  WindowsBackend: country=US
09-30 04:16 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 04:16 DEBUG  WindowsBackend: windows_username=Marc
09-30 04:16 DEBUG  WindowsBackend: user_full_name=Marc
09-30 04:16 DEBUG  WindowsBackend: user_directory=C:\Users\Marc
09-30 04:16 DEBUG  WindowsBackend: windows_language_code=1033
09-30 04:16 DEBUG  WindowsBackend: windows_language=English
09-30 04:16 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 8750 Triple-Core Processor
09-30 04:16 DEBUG  WindowsBackend: bootloader=vista
09-30 04:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 250075.339844 mb free ntfs)
09-30 04:16 DEBUG  WindowsBackend: drive=Drive(C: hd 250075.339844 mb free ntfs)
09-30 04:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-30 04:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-30 04:16 DEBUG  WindowsBackend: uninstaller_path=None
09-30 04:16 DEBUG  WindowsBackend: previous_target_dir=None
09-30 04:16 DEBUG  WindowsBackend: previous_distro_name=None
09-30 04:16 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 04:16 DEBUG  WindowsBackend: keyboard_layout=us
09-30 04:16 DEBUG  WindowsBackend: keyboard_variant=
09-30 04:16 DEBUG  WindowsBackend: total_memory_mb=2047.1796875
09-30 04:16 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 04:16 DEBUG  CommonBackend: Searching for local CDs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 INFO   root: Running the installer...
09-30 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\translations, languages=['en_US', 'en']
09-30 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\translations, languages=['en_US', 'en']
09-30 04:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marc
09-30 04:16 INFO   root: Received settings
09-30 04:16 DEBUG  CommonBackend: Searching for local CD
09-30 04:16 DEBUG  Distro:   checking whether C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-30 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-30 04:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-30 04:16 DEBUG  CommonBackend: Searching for local ISO
09-30 04:16 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 04:16 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-30 04:16 DEBUG  Distro:   parsing info from str=                                                                 
09-30 04:16 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-30 04:16 DEBUG  Distro: could not get info None
09-30 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\translations, languages=['en_US', 'en']
09-30 04:16 DEBUG  TaskList: # Running tasklist...
09-30 04:16 DEBUG  TaskList: ## Running select_target_dir...
09-30 04:16 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 04:16 DEBUG  TaskList: ## Finished select_target_dir
09-30 04:16 DEBUG  TaskList: ## Running create_dir_structure...
09-30 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 04:16 DEBUG  TaskList: ## Finished create_dir_structure
09-30 04:16 DEBUG  TaskList: ## Running create_uninstaller...
09-30 04:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Marc\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 04:16 DEBUG  TaskList: ## Finished create_uninstaller
09-30 04:16 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-30 04:16 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-30 04:16 DEBUG  TaskList: ## Running get_diskimage...
09-30 04:16 DEBUG  CommonBackend: Trying to use pre-specified disk image C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 04:16 DEBUG  TaskList: New task is_valid_dimage
09-30 04:16 DEBUG  TaskList: ### Running is_valid_dimage...
09-30 04:16 DEBUG  Distro:   checking Ubuntu diskimage C:\UbuntuImage\ubuntu-12.04.1-desktop-i386.iso
09-30 04:16 DEBUG  TaskList: ### Finished is_valid_dimage
09-30 04:16 DEBUG  TaskList: ## Finished get_diskimage
09-30 04:16 DEBUG  TaskList: ## Running extract_diskimage...
09-30 04:16 DEBUG  TaskList: ## Finished extract_diskimage
09-30 04:16 DEBUG  TaskList: ## Running choose_disk_sizes...
09-30 04:16 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
09-30 04:16 DEBUG  TaskList: ## Finished choose_disk_sizes
09-30 04:16 DEBUG  TaskList: ## Running expand_diskimage...
09-30 04:16 ERROR  TaskList: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk


09-30 04:16 DEBUG  TaskList: # Cancelling tasklist
09-30 04:16 DEBUG  TaskList: # Finished tasklist
09-30 04:16 ERROR  root: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Marc\AppData\Local\Temp\pyl6666.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
open: No such file or directory while opening C:\ubuntu\disks\root.disk

```

---

### Post by bcbc on 2012-09-30
The diskimage refers to a compressed disk image already preinstalled with Ubuntu. As opposed to the ISO which is in your case the desktop CD image which can be burned to CD or used to create a bootable ISO as well as used to install Ubuntu.

Why is it rejecting the ISO? There's something wrong with it.
```
09-25 07:36 DEBUG  CommonBackend: Searching for local ISO
09-25 07:36 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-25 07:36 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Marc\Desktop\ubuntu-12.04.1-desktop-i386.iso
09-25 07:36 DEBUG  Distro:   parsing info from str=                                                                 
09-25 07:36 ERROR  Distro: 'NoneType' object has no attribute 'group'
09-25 07:36 DEBUG  Distro: could not get info None
```
Unfortunately the wubi code is buggy so instead of getting a proper error you're getting a null reference error. The wubi code has many of these.

So your choices are to:
1. re-download the ISO (ubuntu-12.04.1-desktop-amd64.iso) and try again (same folder)
2. download the diskimage (ubuntu-12.04.1-wubi-amd64.tar.xz) and run it with that --dimagepath option.

If you're having internet problems, which might explain why these downloads are not completing properly, then use a bittorrent client to download the ISO. The diskimage doesn't have a torrent, but you can download directly from:
[http://releases.ubuntu.com/12.04.1/](http://releases.ubuntu.com/12.04.1/)

You can use the 64 bit (amd64) if you want as your computer supports it, or the 32 bit as well if you prefer. But there's no downside to running 64 bit.

---

### Post by DarthTurducken on 2012-09-30
Thanks again [bcbc]("http://ubuntuforums.org/member.php?u=946783"). I have high speed internet through Comcast so I can't imagine I'm having a download problem, but I'll try bittorrent or the diskimage link you provided. Thank you very much for all your assitance

---

### Post by bcbc on 2012-10-01
FYI someone else ran into the same problem here: [http://ubuntuforums.org/showthread.php?t=2065209](http://ubuntuforums.org/showthread.php?t=2065209)

Perhaps there is a problem on the server side that's terminating the download prematurely. Anyway, they fixed it by manually downloading the disk image.

---

