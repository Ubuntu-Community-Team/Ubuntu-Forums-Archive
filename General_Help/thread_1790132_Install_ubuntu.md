---
title: "Install ubuntu"
date: 2011-06-24
forum: General Help
---

### Post by pcsinner on 2011-06-24
I am what is called a silver surfer although less silver these days. Can you help with an installation problem? I have tried to install ubuntu 11.04 following burning an iso disc and following a look by using the disc I really liked it. Since then I have been trying to install inside windows but all I seem to be getting is this:
Error executing comand
>>command=C:\Windows\sysnative\bcdedit.exe/create/ d Ubuntu/application/boot sector
>>retval=1
>>stderr=The boot configuration data store could not be opened.
The system cannot find the file specified.

>>stdout=

For more information, please see the log file:
c:\users\user\appdata\data\local\temp\wubi-11.04-rev211.log

I am running W7 and have no idea what all this means but I really would like to run ubuntu. Even using a a purchased disc the same error occurs and similarly with Mint.

If anybody can assist plus I have never used a forum before I hope I can get back for any answers.

Thank you piskie and please find log:06-25 13:28 INFO   root: === wubi 11.04 rev211 ===
06-25 13:28 DEBUG  root: Logfile is c:\users\user\appdata\local\temp\wubi-11.04-rev211.log
06-25 13:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-25 13:28 DEBUG  CommonBackend: data_dir=C:\Users\User\AppData\Local\Temp\pyl510.tmp\data
06-25 13:28 DEBUG  WindowsBackend: 7z=C:\Users\User\AppData\Local\Temp\pyl510.tmp\bin\7z.exe
06-25 13:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-25 13:28 DEBUG  CommonBackend: Fetching basic info...
06-25 13:28 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-25 13:28 DEBUG  CommonBackend: platform=win32
06-25 13:28 DEBUG  CommonBackend: osname=nt
06-25 13:28 DEBUG  CommonBackend: language=en_GB
06-25 13:28 DEBUG  CommonBackend: encoding=cp1252
06-25 13:28 DEBUG  WindowsBackend: arch=amd64
06-25 13:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\User\AppData\Local\Temp\pyl510.tmp\data\isolist.ini
06-25 13:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-25 13:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-25 13:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-25 13:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-25 13:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-25 13:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-25 13:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-25 13:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-25 13:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-25 13:28 DEBUG  WindowsBackend: Fetching host info...
06-25 13:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-25 13:28 DEBUG  WindowsBackend: windows version=vista
06-25 13:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-25 13:28 DEBUG  WindowsBackend: windows_sp=None
06-25 13:28 DEBUG  WindowsBackend: windows_build=7601
06-25 13:28 DEBUG  WindowsBackend: gmt=0
06-25 13:28 DEBUG  WindowsBackend: country=GB
06-25 13:28 DEBUG  WindowsBackend: timezone=Europe/London
06-25 13:28 DEBUG  WindowsBackend: windows_username=User
06-25 13:28 DEBUG  WindowsBackend: user_full_name=User
06-25 13:28 DEBUG  WindowsBackend: user_directory=C:\Users\User
06-25 13:28 DEBUG  WindowsBackend: windows_language_code=1033
06-25 13:28 DEBUG  WindowsBackend: windows_language=English
06-25 13:28 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz
06-25 13:28 DEBUG  WindowsBackend: bootloader=vista
06-25 13:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 416623.183594 mb free ntfs)
06-25 13:28 DEBUG  WindowsBackend: drive=Drive(C: hd 416623.183594 mb free ntfs)
06-25 13:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-25 13:28 DEBUG  WindowsBackend: uninstaller_path=C:\linuxmint\uninstall-wubi.exe
06-25 13:28 DEBUG  WindowsBackend: previous_target_dir=C:\linuxmint
06-25 13:28 DEBUG  WindowsBackend: previous_distro_name=Linux Mint
06-25 13:28 DEBUG  WindowsBackend: keyboard_id=134809609
06-25 13:28 DEBUG  WindowsBackend: keyboard_layout=gb
06-25 13:28 DEBUG  WindowsBackend: keyboard_variant=
06-25 13:28 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
06-25 13:28 DEBUG  CommonBackend: locale=en_GB.UTF-8
06-25 13:28 DEBUG  WindowsBackend: total_memory_mb=4095.2421875
06-25 13:28 DEBUG  CommonBackend: Searching ISOs on USB devices
06-25 13:28 DEBUG  CommonBackend: Searching for local CDs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Ubuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Ubuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Ubuntu Netbook CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Kubuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Kubuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Xubuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Xubuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Mythbuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether C:\Users\User\AppData\Local\Temp\pyl510.tmp is a valid Mythbuntu CD
06-25 13:28 DEBUG  Distro:     does not contain C:\Users\User\AppData\Local\Temp\pyl510.tmp\casper\filesystem.squashfs
06-25 13:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-25 13:28 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
06-25 13:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
06-25 13:28 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-25 13:28 INFO   root: Running the CD menu...
06-25 13:28 DEBUG  WindowsFrontend: __init__...
06-25 13:28 DEBUG  WindowsFrontend: on_init...
06-25 13:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\User\AppData\Local\Temp\pyl510.tmp\translations, languages=['en_GB', 'en']
06-25 13:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\User\AppData\Local\Temp\pyl510.tmp\translations, languages=['en_GB', 'en']
06-25 13:28 INFO   root: CD menu finished
06-25 13:28 INFO   root: Running the installer...
06-25 13:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\User\AppData\Local\Temp\pyl510.tmp\translations, languages=['en_GB', 'en']
06-25 13:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\User\AppData\Local\Temp\pyl510.tmp\translations, languages=['en_GB', 'en']
06-25 13:28 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=tom
06-25 13:28 INFO   root: Received settings
06-25 13:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\User\AppData\Local\Temp\pyl510.tmp\translations, languages=['en_GB', 'en']
06-25 13:28 DEBUG  TaskList: # Running tasklist...
06-25 13:28 DEBUG  TaskList: ## Running select_target_dir...
06-25 13:28 INFO   WindowsBackend: Installing into C:\ubuntu
06-25 13:28 DEBUG  TaskList: ## Finished select_target_dir
06-25 13:28 DEBUG  TaskList: ## Running create_dir_structure...
06-25 13:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-25 13:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-25 13:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-25 13:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-25 13:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-25 13:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-25 13:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-25 13:28 DEBUG  TaskList: ## Finished create_dir_structure
06-25 13:28 DEBUG  TaskList: ## Running uncompress_target_dir...
06-25 13:28 DEBUG  TaskList: ## Finished uncompress_target_dir
06-25 13:28 DEBUG  TaskList: ## Running create_uninstaller...
06-25 13:28 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-25 13:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-25 13:28 DEBUG  TaskList: ## Finished create_uninstaller
06-25 13:28 DEBUG  TaskList: ## Running copy_installation_files...
06-25 13:28 DEBUG  WindowsBackend: Copying C:\Users\User\AppData\Local\Temp\pyl510.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-25 13:28 DEBUG  WindowsBackend: Copying C:\Users\User\AppData\Local\Temp\pyl510.tmp\winboot -> C:\ubuntu\winboot
06-25 13:28 DEBUG  WindowsBackend: Copying C:\Users\User\AppData\Local\Temp\pyl510.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-25 13:28 DEBUG  TaskList: ## Finished copy_installation_files
06-25 13:28 DEBUG  TaskList: ## Running get_iso...
06-25 13:28 DEBUG  TaskList: New task copy_file
06-25 13:28 DEBUG  TaskList: ### Running copy_file...
06-25 13:31 DEBUG  TaskList: ### Finished copy_file
06-25 13:31 DEBUG  TaskList: New task check_iso
06-25 13:31 DEBUG  TaskList: ### Running check_iso...
06-25 13:31 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
06-25 13:31 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
06-25 13:31 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
06-25 13:31 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
06-25 13:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
06-25 13:31 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
06-25 13:31 DEBUG  TaskList: New task get_metalink
06-25 13:31 DEBUG  TaskList: #### Running get_metalink...
06-25 13:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
06-25 13:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
06-25 13:31 DEBUG  downloader: download finished (read 28363 bytes)
06-25 13:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
06-25 13:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
06-25 13:31 DEBUG  downloader: download finished (read 874 bytes)
06-25 13:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
06-25 13:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
06-25 13:31 DEBUG  downloader: download finished (read 198 bytes)
06-25 13:31 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-25 13:31 INFO   saplog: Checking block bindings..
06-25 13:31 INFO   saplog: Key verified successfully.
06-25 13:31 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

06-25 13:31 DEBUG  TaskList: #### Finished get_metalink
06-25 13:31 DEBUG  TaskList: New task get_file_md5
06-25 13:31 DEBUG  TaskList: #### Running get_file_md5...
06-25 13:31 DEBUG  TaskList: #### Finished get_file_md5
06-25 13:31 DEBUG  TaskList: ### Finished check_iso
06-25 13:31 DEBUG  TaskList: ## Finished get_iso
06-25 13:31 DEBUG  TaskList: ## Running extract_kernel...
06-25 13:31 DEBUG  CommonBackend: Copying files from CD D:\
06-25 13:31 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
06-25 13:31 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
06-25 13:31 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
06-25 13:31 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
06-25 13:31 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
06-25 13:31 DEBUG  TaskList: ## Finished extract_kernel
06-25 13:31 DEBUG  TaskList: ## Running choose_disk_sizes...
06-25 13:31 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
06-25 13:31 DEBUG  TaskList: ## Finished choose_disk_sizes
06-25 13:31 DEBUG  TaskList: ## Running create_preseed...
06-25 13:31 DEBUG  TaskList: ## Finished create_preseed
06-25 13:31 DEBUG  TaskList: ## Running modify_bootloader...
06-25 13:31 DEBUG  TaskList: New task modify_bcd
06-25 13:31 DEBUG  TaskList: ### Running modify_bcd...
06-25 13:31 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 416623.183594 mb free ntfs)
06-25 13:31 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 645, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
06-25 13:31 DEBUG  TaskList: # Cancelling tasklist
06-25 13:31 DEBUG  TaskList: ## Finished modify_bootloader
06-25 13:31 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 645, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
06-25 13:31 DEBUG  TaskList: # Finished tasklist

Now installed by booting from the disc - you are probably saying I should have done that anyway. My thanks to Piskie and Ruby1200. Ubuntu is now preferred and love it.:P

---

### Post by Rubi1200 on 2011-06-24
Hi and welcome to the forums :-)

Try placing the wubi.exe and downloaded ISO image in the same folder and then run the executable.

If this doesn't help resolve the problem, then please post the contents of the error log.

Once posted, highlight all the text and click on the # icon on the menu to wrap the text with code tags before submitting the post.

Thanks.

---

### Post by pcsinner on 2011-06-25
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Try placing the wubi.exe and downloaded ISO image in the same folder and then run the executable.

If this doesn't help resolve the problem, then please post the contents of the error log.

Once posted, highlight all the text and click on the # icon on the menu to wrap the text with code tags before submitting the post.

Thanks.
Hi Rubi1200 and thank you.
Sorry but I hope I have done this correctly. I posted the log prior to your message but will try your suggestion.
Thanks

---

### Post by Rubi1200 on 2011-06-25
Did you try the suggestion to place the executable and ISO in the same folder?

What was the outcome?

If it did not work, please boot the computer with a LiveCD and do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
 sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by pcsinner on 2011-06-30
> **Rubi1200 said:**
> Did you try the suggestion to place the executable and ISO in the same folder?

What was the outcome?

If it did not work, please boot the computer with a LiveCD and do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
 sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.
Carried out CD boot and installed with partition and now have duel boot facility. Ubuntu is now my preferred OS and have only gone back to W7 once. Thanks for you assistance and appreciate your advice and glad to know there is always assistance when I need it.

---

### Post by Rubi1200 on 2011-07-01
Excellent! I am really pleased you got things working the way you want :-)

Enjoy!

Please also mark this Solved using the Thread Tools near the top of the page.

---

### Post by dee119 on 2011-07-01
:D:D:D

Welcome to the Ubuntu club,  glad you have got your
installation sorted now.  Hope you will continue to enjoy
Ubuntu as much as I do.

Like you,  I am a silver surfer.  Started using Ubuntu in
April this year and have not looked back since.  It's been
a joy to use,  no more messing about with other distro's or
even the dreaded "Windoze."  Have had no down time since 
I installed 10.10.

Everything worked straight out of the box.  Had one issue with
the download package manager, (my finger trouble)  - but thanks 
to the guys+girls on  this forum it was soon sorted.  
So you are in good hands here.

Good Luck with Ubuntu - I am sure you will get to love it as much
as we all do.  It's a FAB distro so tell all your friends how good it is.

Cheers + Beers - happy surfing with Ubuntu,  I changed to it and 
am as happy as Larry now with my O/S.  :D:D:D

---

### Post by pcsinner on 2011-07-05
> **Rubi1200 said:**
> Excellent! I am really pleased you got things working the way you want :-)

Enjoy!

Please also mark this Solved using the Thread Tools near the top of the page.
Thanks Rubi1200 - absolutely brilliant. I went into W7 for something over the weekend - didn't stay long. Once again thanks.

---

### Post by pcsinner on 2011-07-05
> **dee119 said:**
> :D:D:D

Welcome to the Ubuntu club,  glad you have got your
installation sorted now.  Hope you will continue to enjoy
Ubuntu as much as I do.

Like you,  I am a silver surfer.  Started using Ubuntu in
April this year and have not looked back since.  It's been
a joy to use,  no more messing about with other distro's or
even the dreaded "Windoze."  Have had no down time since 
I installed 10.10.

Everything worked straight out of the box.  Had one issue with
the download package manager, (my finger trouble)  - but thanks 
to the guys+girls on  this forum it was soon sorted.  
So you are in good hands here.

Good Luck with Ubuntu - I am sure you will get to love it as much
as we all do.  It's a FAB distro so tell all your friends how good it is.

Cheers + Beers - happy surfing with Ubuntu,  I changed to it and 
am as happy as Larry now with my O/S.  :D:D:D

Cannot argue with that. I knew from the 'try it' it looked good and now I have it it is brilliant. Definitely cheers and beers. Thanks for your info - I actually got straight in today - couldn't figure out how I got to the forum before to reply to everybody. All the best

---

