---
title: "Newbie"
date: 2011-04-07
forum: General Help
---

### Post by DiNozzo89 on 2011-04-07
Hey, i am newbie in Ubuntu, so I am trying to install it. But I have some problems. I recently downloaded the ISO file from the official Ubuntu site, I burned the image using UnetBootin, but if I reboot the PC it gives me an error: 

SYSLINUX 3.85 2010-02-20 CBIOS Copyright (c) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:


If I try to install it from wubi.exe it gives me another error (and says something about a log file) :

Could not retrieve the required installation files.

I would like to get rid of Windows and go to Ubuntu, but how to do that? My pc is:

Windows XP SP2
AMD Athlon(tm) XP 2200+
1.80 GHz
640 Mb RAM
250 Gb HDD
Video card: NVidia GeForce FX 5200: 128 Mb

---

### Post by nothingspecial on 2011-04-07
Hi, I'd try reformatting your usb stick and using unetbootin again.

---

### Post by roger_1960 on 2011-04-07
Hi

Have you tried burning a CD from the download (and checking the md5 sum)?  Its simplest to install from CD (IMHO), try the "live" CD to check hardware and then, after backing up all data, install using whole drive (which will wipe everything). There are options for all these in the install menus on the CD.

If you dont have a CD drive ignore the above!

---

### Post by ~Plue on 2011-04-07
if reformatting the stick doesn't fix it, try checking the md5sum of the downloaded iso

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")
> 

[LIST=1]
[*]Download and install [winMD5Sum]("http://www.nullriver.com/index/products/winmd5sum"), a free and open source hash verification program.
[*]Right-click the ISO file.
[*]Click Send To, then winMD5Sum.
[*]Wait for winMD5Sum to load and finish the checksum (this may take a significant amount of time depending on your computer's performance).
[*]Copy the corresponding hash from [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") into the bottom text box.
[*]Click "Compare"
[*]A message box will say "MD5 Check Sums are the same" if the hashes are equal.
[/LIST]
if they arent equal, then you'll need to download it again

---

### Post by DiNozzo89 on 2011-04-07
> **~Plue said:**
> if reformatting the stick doesn't fix it, try checking the md5sum of the downloaded iso

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)
[/LIST]
if they arent equal, then you'll need to download it again

they are equal ... i compared wubi.exe and ubuntu 10.10 ISO file ... with that MD5SUM

---

### Post by dirty_harry on 2011-04-07
Downthemall also handles checksum! 

And fs-type of the** usb-stick should be fat32**! :!:

I found this -> *howto use unetbootin form Win32*:[URL="http://ubuntuforums.org/showthread.php?t=811397"]
http://ubuntuforums.org/showthread.php?t=811397[/URL]

---

### Post by DiNozzo89 on 2011-04-07
> **roger_1960 said:**
> Hi

Have you tried burning a CD from the download (and checking the md5 sum)?  Its simplest to install from CD (IMHO), try the "live" CD to check hardware and then, after backing up all data, install using whole drive (which will wipe everything). There are options for all these in the install menus on the CD.

If you dont have a CD drive ignore the above!

my CD-ROM is not working.. it doesn`t read any CD ... i don`t know what is wrong with that... so.. I have the only alternative of USB but..i got those 2 errors..

---

### Post by DiNozzo89 on 2011-04-07
> **dirty_harry said:**
> Downthemall also handles checksum! 

And fs-type of the** usb-stick should be fat32**! :!:

I found this -> *howto use unetbootin form Win32*:[URL="http://ubuntuforums.org/showthread.php?t=811397"]
http://ubuntuforums.org/showthread.php?t=811397[/URL]

it is FAT32, i checked it with WinMD5SUM .. and they are all equal :(

---

### Post by Dark Dreamer UK on 2011-04-07
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) <---run from windows desktop

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) <---download and burn to a CD

if you decide to go with the CD option at the download screen select Ubuntu 10.10 - Latest Version & you'll want to get the 32-bit version as well  

Now as for burning it you want to download a program called infra recorder
Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog box pops up.
Open Infra Recorder and click the 'Write Image' button in the main screen.
Alternatively you can select the 'Actions' menu, then 'Burn image'.
Select the Ubuntu CD image file you want to use, then click 'Open'.
In the dialog box, click 'OK'.
Once it's burnt to CD
Then reboot PC
Select boot from CD

If you are trying from a USB stick it's recommended that you use the _Universal USB __[U]Installer_[/U]

Hope this helps:)

---

### Post by DiNozzo89 on 2011-04-07
> **Dark Dreamer UK said:**
> [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) <---run from windows desktop

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) <---download and burn to a CD

if you decide to go with the CD option at the download screen select Ubuntu 10.10 - Latest Version & you'll want to get the 32-bit version as well  

Now as for burning it you want to download a program called infra recorder
Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog box pops up.
Open Infra Recorder and click the 'Write Image' button in the main screen.
Alternatively you can select the 'Actions' menu, then 'Burn image'.
Select the Ubuntu CD image file you want to use, then click 'Open'.
In the dialog box, click 'OK'.
Once it's burnt to CD
Then reboot PC
Select boot from CD

If you are trying from a USB stick it's recommended that you use the _Universal USB __[U]Installer_[/U]

Hope this helps:)

so...I want to install Ubuntu 10.10 instead of Windows.. i dont want to hear anymore about Windows.. the problem is that I can`t install it..if i try to boot it from the stick it says "**no default or UI configuration directive found"   and if i try to install it using wubi.exe it says "****Wubi 10.10 could not retrieve the required installation files"** and it says something about a log file. I cant make CD`s... My CD-ROM is not working.. so.. the only option I have is the USB ..what now ?

---

### Post by dirty_harry on 2011-04-07
Sometimes I find computers really hard to get going.

Not long ago I had an usb-stick that was faulty. I copied iso-files back and forth, then compared checksum. Was very annoying, because I'd tried to ignore that possibility. Currently I'm using usb-hdds for such occasions (installation via usb)...

I remeber that I once tried to install Xubuntu via usb and I had to choose a 10.10 instead of 10.04 and it worked. 

And I tried to search your error once more, and others are dealing with the same:
[http://ubuntuforums.org/showthread.php?t=1487937](http://ubuntuforums.org/showthread.php?t=1487937)

in short: some suggested to copy the iso to the usb-drive, others had to rename "isolinux" to "syslinux" or format with FAT(what appears to be fat16, limit 2GB partition) instead of FAT32 from Windows Vista/Seven.

---

### Post by DiNozzo89 on 2011-04-07
> **dirty_harry said:**
> Sometimes I find computers really hard to get going.

Not long ago I had an usb-stick that was faulty. I copied iso-files back and forth, then compared checksum. Was very annoying, because I'd tried to ignore that possibility. Currently I'm using usb-hdds for such occasions (installation via usb)...

I remeber that I once tried to install Xubuntu via usb and I had to choose a 10.10 instead of 10.04 and it worked. 

And I tried to search your error once more, and others are dealing with the same:
[http://ubuntuforums.org/showthread.php?t=1487937](http://ubuntuforums.org/showthread.php?t=1487937)

in short: some suggested to copy the iso to the usb-drive, others had to rename "isolinux" to "syslinux" or format with FAT(what appears to be fat16, limit 2GB partition) instead of FAT32 from Windows Vista/Seven.


well I just have FAT or FAT32 (using windows xp sp2)..dunno what to do else :(

---

### Post by Elfy on 2011-04-07
To start with not post like the one that I've just jailed.

---

### Post by DiNozzo89 on 2011-04-07
> **forestpiskie said:**
> To start with not post like the one that I've just jailed.

huh?

---

### Post by DiNozzo89 on 2011-04-07
```
03-17 09:53 INFO   root: === wubi 10.10 rev197 ===
03-17 09:53 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
03-17 09:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Ubuntu\\wubi.exe"']
03-17 09:53 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\data
03-17 09:53 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\bin\7z.exe
03-17 09:53 DEBUG  CommonBackend: Fetching basic info...
03-17 09:53 DEBUG  CommonBackend: original_exe=C:\Ubuntu\wubi.exe
03-17 09:53 DEBUG  CommonBackend: platform=win32
03-17 09:53 DEBUG  CommonBackend: osname=nt
03-17 09:53 DEBUG  CommonBackend: language=en_US
03-17 09:53 DEBUG  CommonBackend: encoding=cp1252
03-17 09:53 DEBUG  WindowsBackend: arch=i386
03-17 09:53 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\data\isolist.ini
03-17 09:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 09:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 09:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 09:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 09:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 09:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 09:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 09:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 09:53 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-17 09:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-17 09:53 DEBUG  WindowsBackend: Fetching host info...
03-17 09:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 09:53 DEBUG  WindowsBackend: windows version=xp
03-17 09:53 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-17 09:53 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-17 09:53 DEBUG  WindowsBackend: windows_build=2600
03-17 09:53 DEBUG  WindowsBackend: gmt=2
03-17 09:53 DEBUG  WindowsBackend: country=US
03-17 09:53 DEBUG  WindowsBackend: timezone=America/New_York
03-17 09:53 DEBUG  WindowsBackend: windows_username=Sylar
03-17 09:53 DEBUG  WindowsBackend: user_full_name=Sylar
03-17 09:53 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
03-17 09:53 DEBUG  WindowsBackend: windows_language_code=1033
03-17 09:53 DEBUG  WindowsBackend: windows_language=English
03-17 09:53 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
03-17 09:53 DEBUG  WindowsBackend: bootloader=xp
03-17 09:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38622.0 mb free ntfs)
03-17 09:53 DEBUG  WindowsBackend: drive=Drive(C: hd 38622.0 mb free ntfs)
03-17 09:53 DEBUG  WindowsBackend: drive=Drive(D: hd 117675.347656 mb free ntfs)
03-17 09:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-17 09:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-17 09:53 DEBUG  WindowsBackend: uninstaller_path=None
03-17 09:53 DEBUG  WindowsBackend: previous_target_dir=None
03-17 09:53 DEBUG  WindowsBackend: previous_distro_name=None
03-17 09:53 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 09:53 DEBUG  WindowsBackend: keyboard_layout=us
03-17 09:53 DEBUG  WindowsBackend: keyboard_variant=
03-17 09:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 09:53 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 09:53 DEBUG  WindowsBackend: total_memory_mb=639.484375
03-17 09:53 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 09:53 DEBUG  CommonBackend: Searching for local CDs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Ubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Kubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-17 09:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:53 INFO   root: Running the installer...
03-17 09:53 DEBUG  WindowsFrontend: __init__...
03-17 09:53 DEBUG  WindowsFrontend: on_init...
03-17 09:53 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\translations, languages=['en_US', 'en']
03-17 09:53 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\translations, languages=['en_US', 'en']
03-17 09:53 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=alex
03-17 09:53 INFO   root: Received settings
03-17 09:53 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\translations, languages=['en_US', 'en']
03-17 09:53 DEBUG  TaskList: # Running tasklist...
03-17 09:53 DEBUG  TaskList: ## Running select_target_dir...
03-17 09:53 INFO   WindowsBackend: Installing into D:\ubuntu
03-17 09:53 DEBUG  TaskList: ## Finished select_target_dir
03-17 09:53 DEBUG  TaskList: ## Running create_dir_structure...
03-17 09:53 DEBUG  CommonBackend: Creating dir D:\ubuntu
03-17 09:53 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
03-17 09:53 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
03-17 09:53 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
03-17 09:53 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
03-17 09:53 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
03-17 09:53 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
03-17 09:53 DEBUG  TaskList: ## Finished create_dir_structure
03-17 09:53 DEBUG  TaskList: ## Running uncompress_target_dir...
03-17 09:54 DEBUG  TaskList: ## Finished uncompress_target_dir
03-17 09:54 DEBUG  TaskList: ## Running create_uninstaller...
03-17 09:54 DEBUG  WindowsBackend: Copying uninstaller C:\Ubuntu\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-17 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-17 09:54 DEBUG  TaskList: ## Finished create_uninstaller
03-17 09:54 DEBUG  TaskList: ## Running copy_installation_files...
03-17 09:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
03-17 09:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\winboot -> D:\ubuntu\winboot
03-17 09:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
03-17 09:54 DEBUG  TaskList: ## Finished copy_installation_files
03-17 09:54 DEBUG  TaskList: ## Running get_iso...
03-17 09:54 DEBUG  CommonBackend: Searching for local CD
03-17 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp is a valid Ubuntu CD
03-17 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\casper\filesystem.squashfs
03-17 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-17 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 09:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 09:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 09:54 DEBUG  CommonBackend: Searching for local ISO
03-17 09:54 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-17 09:54 DEBUG  TaskList: New task get_metalink
03-17 09:54 DEBUG  TaskList: ### Running get_metalink...
03-17 09:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink) > D:\ubuntu\install
03-17 09:54 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
03-17 09:54 DEBUG  downloader: download finished (read 9071 bytes)
03-17 09:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > D:\ubuntu\install
03-17 09:54 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-17 09:54 DEBUG  downloader: download finished (read 488 bytes)
03-17 09:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > D:\ubuntu\install
03-17 09:54 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-17 09:54 DEBUG  downloader: download finished (read 198 bytes)
03-17 09:54 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-17 09:54 INFO   saplog: Checking block bindings..
03-17 09:54 INFO   saplog: Key verified successfully.
03-17 09:54 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-17 09:54 DEBUG  TaskList: ### Finished get_metalink
03-17 09:54 DEBUG  TaskList: New task download
03-17 09:54 DEBUG  TaskList: ### Running download...
03-17 09:54 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:10 DEBUG  TaskList: ### Finished download
03-17 10:10 DEBUG  TaskList: New task check_iso
03-17 10:10 DEBUG  TaskList: ### Running check_iso...
03-17 10:10 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:10 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:10 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:10 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-17 10:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-17 10:10 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:10 DEBUG  TaskList: New task get_file_md5
03-17 10:10 DEBUG  TaskList: #### Running get_file_md5...
03-17 10:11 DEBUG  TaskList: #### Finished get_file_md5
03-17 10:11 DEBUG  TaskList: ### Finished check_iso
03-17 10:11 DEBUG  TaskList: ## Finished get_iso
03-17 10:11 DEBUG  TaskList: ## Running extract_kernel...
03-17 10:11 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:11 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:11 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:11 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-17 10:11 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-17 10:11 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
03-17 10:11 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-17 10:11 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
03-17 10:11 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-17 10:11 DEBUG  TaskList: ## Finished extract_kernel
03-17 10:11 DEBUG  TaskList: ## Running choose_disk_sizes...
03-17 10:11 DEBUG  WindowsBackend: total size=3000
  root=2744
  swap=256
  home=0
  usr=0
03-17 10:11 DEBUG  TaskList: ## Finished choose_disk_sizes
03-17 10:11 DEBUG  TaskList: ## Running create_preseed...
03-17 10:11 DEBUG  TaskList: ## Finished create_preseed
03-17 10:11 DEBUG  TaskList: ## Running modify_bootloader...
03-17 10:11 DEBUG  TaskList: New task modify_bootini
03-17 10:11 DEBUG  TaskList: ### Running modify_bootini...
03-17 10:11 DEBUG  WindowsBackend: modify_bootini C:
03-17 10:11 DEBUG  TaskList: ### Finished modify_bootini
03-17 10:11 DEBUG  TaskList: New task modify_bootini
03-17 10:11 DEBUG  TaskList: ### Running modify_bootini...
03-17 10:11 DEBUG  WindowsBackend: modify_bootini D:
03-17 10:11 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
03-17 10:11 DEBUG  TaskList: ### Finished modify_bootini
03-17 10:11 DEBUG  TaskList: ## Finished modify_bootloader
03-17 10:11 DEBUG  TaskList: ## Running modify_grub_configuration...
03-17 10:11 DEBUG  TaskList: ## Finished modify_grub_configuration
03-17 10:11 DEBUG  TaskList: ## Running create_virtual_disks...
03-17 10:11 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 2744MB
03-17 10:11 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
03-17 10:11 DEBUG  TaskList: ## Finished create_virtual_disks
03-17 10:11 DEBUG  TaskList: ## Running uncompress_files...
03-17 10:11 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
03-17 10:11 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
03-17 10:11 DEBUG  TaskList: ## Finished uncompress_files
03-17 10:11 DEBUG  TaskList: ## Running eject_cd...
03-17 10:11 DEBUG  TaskList: ## Finished eject_cd
03-17 10:11 DEBUG  TaskList: # Finished tasklist
03-17 10:11 INFO   root: Almost finished installing
03-17 10:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pylE5.tmp\translations, languages=['en_US', 'en']
03-17 10:11 INFO   root: Finished installation
03-17 10:11 INFO   root: Rebooting
03-17 10:11 DEBUG  TaskList: # Running tasklist...
03-17 10:11 DEBUG  TaskList: ## Running reboot...
03-17 10:11 DEBUG  TaskList: ## Finished reboot
03-17 10:11 DEBUG  TaskList: # Finished tasklist
03-17 10:11 DEBUG  root: application.quit
03-17 10:11 DEBUG  WindowsFrontend: frontend.quit
03-17 10:11 DEBUG  WindowsFrontend: frontend.on_quit
03-17 10:11 DEBUG  root: application.on_quit
03-17 10:11 INFO   root: sys.exit
03-17 05:05 INFO   root: === wubi 10.10 rev197 ===
03-17 05:05 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
03-17 05:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
03-17 05:05 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\data
03-17 05:05 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\bin\7z.exe
03-17 05:05 DEBUG  CommonBackend: Fetching basic info...
03-17 05:05 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
03-17 05:05 DEBUG  CommonBackend: platform=win32
03-17 05:05 DEBUG  CommonBackend: osname=nt
03-17 05:05 DEBUG  CommonBackend: language=en_US
03-17 05:05 DEBUG  CommonBackend: encoding=cp1252
03-17 05:05 DEBUG  WindowsBackend: arch=i386
03-17 05:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\data\isolist.ini
03-17 05:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 05:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 05:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 05:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 05:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 05:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 05:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 05:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 05:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-17 05:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-17 05:05 DEBUG  WindowsBackend: Fetching host info...
03-17 05:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 05:05 DEBUG  WindowsBackend: windows version=xp
03-17 05:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-17 05:05 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-17 05:05 DEBUG  WindowsBackend: windows_build=2600
03-17 05:05 DEBUG  WindowsBackend: gmt=2
03-17 05:05 DEBUG  WindowsBackend: country=US
03-17 05:05 DEBUG  WindowsBackend: timezone=America/New_York
03-17 05:05 DEBUG  WindowsBackend: windows_username=Sylar
03-17 05:05 DEBUG  WindowsBackend: user_full_name=Sylar
03-17 05:05 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
03-17 05:05 DEBUG  WindowsBackend: windows_language_code=1033
03-17 05:05 DEBUG  WindowsBackend: windows_language=English
03-17 05:05 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
03-17 05:05 DEBUG  WindowsBackend: bootloader=xp
03-17 05:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38638.5507813 mb free ntfs)
03-17 05:05 DEBUG  WindowsBackend: drive=Drive(C: hd 38638.5507813 mb free ntfs)
03-17 05:05 DEBUG  WindowsBackend: drive=Drive(D: hd 113980.609375 mb free ntfs)
03-17 05:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-17 05:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-17 05:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
03-17 05:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
03-17 05:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-17 05:05 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 05:05 DEBUG  WindowsBackend: keyboard_layout=us
03-17 05:05 DEBUG  WindowsBackend: keyboard_variant=
03-17 05:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 05:05 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 05:05 DEBUG  WindowsBackend: total_memory_mb=639.484375
03-17 05:05 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 05:05 DEBUG  CommonBackend: Searching for local CDs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-17 05:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-17 05:05 INFO   root: Running the uninstaller...
03-17 05:05 INFO   CommonBackend: This is the uninstaller running
03-17 05:05 DEBUG  WindowsFrontend: __init__...
03-17 05:05 DEBUG  WindowsFrontend: on_init...
03-17 05:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-17 05:05 INFO   root: Received settings
03-17 05:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-17 05:05 DEBUG  TaskList: # Running tasklist...
03-17 05:05 DEBUG  TaskList: ## Running Backup ISO...
03-17 05:05 DEBUG  TaskList: ## Finished Backup ISO
03-17 05:05 DEBUG  TaskList: ## Running Remove bootloader entry...
03-17 05:05 ERROR  WindowsBackend: Cannot find bcdedit
03-17 05:05 DEBUG  WindowsBackend: undo_bootini C:
03-17 05:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 38638.5507813 mb free ntfs)
03-17 05:05 DEBUG  WindowsBackend: undo_bootini D:
03-17 05:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 113980.609375 mb free ntfs)
03-17 05:05 DEBUG  TaskList: ## Finished Remove bootloader entry
03-17 05:05 DEBUG  TaskList: ## Running Remove target dir...
03-17 05:05 DEBUG  CommonBackend: Deleting D:\ubuntu
03-17 05:05 DEBUG  TaskList: ## Finished Remove target dir
03-17 05:05 DEBUG  TaskList: ## Running Remove registry key...
03-17 05:05 DEBUG  TaskList: ## Finished Remove registry key
03-17 05:05 DEBUG  TaskList: # Finished tasklist
03-17 05:05 INFO   root: Almost finished uninstalling
03-17 05:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-17 05:05 INFO   root: Finished uninstallation
03-17 05:05 DEBUG  root: application.quit
03-17 05:05 DEBUG  WindowsFrontend: frontend.quit
03-17 05:05 DEBUG  WindowsFrontend: frontend.on_quit
03-17 05:05 DEBUG  root: application.on_quit
03-17 05:05 INFO   root: sys.exit
03-20 19:32 INFO   root: === wubi 10.10 rev197 ===
03-20 19:32 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
03-20 19:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-20 19:32 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\data
03-20 19:32 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\bin\7z.exe
03-20 19:32 DEBUG  CommonBackend: Fetching basic info...
03-20 19:32 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-20 19:32 DEBUG  CommonBackend: platform=win32
03-20 19:32 DEBUG  CommonBackend: osname=nt
03-20 19:32 DEBUG  CommonBackend: language=en_US
03-20 19:32 DEBUG  CommonBackend: encoding=cp1252
03-20 19:32 DEBUG  WindowsBackend: arch=i386
03-20 19:32 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\data\isolist.ini
03-20 19:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-20 19:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-20 19:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-20 19:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-20 19:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-20 19:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-20 19:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-20 19:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-20 19:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-20 19:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-20 19:32 DEBUG  WindowsBackend: Fetching host info...
03-20 19:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-20 19:32 DEBUG  WindowsBackend: windows version=xp
03-20 19:32 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-20 19:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-20 19:32 DEBUG  WindowsBackend: windows_build=2600
03-20 19:32 DEBUG  WindowsBackend: gmt=2
03-20 19:32 DEBUG  WindowsBackend: country=US
03-20 19:32 DEBUG  WindowsBackend: timezone=America/New_York
03-20 19:32 DEBUG  WindowsBackend: windows_username=Sylar
03-20 19:32 DEBUG  WindowsBackend: user_full_name=Sylar
03-20 19:32 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
03-20 19:32 DEBUG  WindowsBackend: windows_language_code=1033
03-20 19:32 DEBUG  WindowsBackend: windows_language=English
03-20 19:32 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
03-20 19:32 DEBUG  WindowsBackend: bootloader=xp
03-20 19:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85957.9414063 mb free ntfs)
03-20 19:32 DEBUG  WindowsBackend: drive=Drive(C: hd 85957.9414063 mb free ntfs)
03-20 19:32 DEBUG  WindowsBackend: drive=Drive(D: hd 81127.0273438 mb free ntfs)
03-20 19:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-20 19:32 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-20 19:32 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.26953125 mb free fat32)
03-20 19:32 DEBUG  WindowsBackend: uninstaller_path=None
03-20 19:32 DEBUG  WindowsBackend: previous_target_dir=None
03-20 19:32 DEBUG  WindowsBackend: previous_distro_name=None
03-20 19:32 DEBUG  WindowsBackend: keyboard_id=67699721
03-20 19:32 DEBUG  WindowsBackend: keyboard_layout=us
03-20 19:32 DEBUG  WindowsBackend: keyboard_variant=
03-20 19:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-20 19:32 DEBUG  CommonBackend: locale=en_US.UTF-8
03-20 19:32 DEBUG  WindowsBackend: total_memory_mb=639.484375
03-20 19:32 DEBUG  CommonBackend: Searching ISOs on USB devices
03-20 19:32 DEBUG  CommonBackend: Searching for local CDs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Ubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Kubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-20 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 19:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-20 19:32 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-20 19:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-20 19:32 DEBUG  Distro: wrong arch: i386 != amd64
03-20 19:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-20 19:32 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-20 19:32 INFO   root: Running the CD menu...
03-20 19:32 DEBUG  WindowsFrontend: __init__...
03-20 19:32 DEBUG  WindowsFrontend: on_init...
03-20 19:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\translations, languages=['en_US', 'en']
03-20 19:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\translations, languages=['en_US', 'en']
03-20 19:32 INFO   root: CD menu finished
03-20 19:32 INFO   root: Running the installer...
03-20 19:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\translations, languages=['en_US', 'en']
03-20 19:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\translations, languages=['en_US', 'en']
03-20 19:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=alex
03-20 19:33 INFO   root: Received settings
03-20 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\translations, languages=['en_US', 'en']
03-20 19:33 DEBUG  TaskList: # Running tasklist...
03-20 19:33 DEBUG  TaskList: ## Running select_target_dir...
03-20 19:33 INFO   WindowsBackend: Installing into C:\ubuntu
03-20 19:33 DEBUG  TaskList: ## Finished select_target_dir
03-20 19:33 DEBUG  TaskList: ## Running create_dir_structure...
03-20 19:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-20 19:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-20 19:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-20 19:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-20 19:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-20 19:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-20 19:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-20 19:33 DEBUG  TaskList: ## Finished create_dir_structure
03-20 19:33 DEBUG  TaskList: ## Running uncompress_target_dir...
03-20 19:33 DEBUG  TaskList: ## Finished uncompress_target_dir
03-20 19:33 DEBUG  TaskList: ## Running create_uninstaller...
03-20 19:33 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-20 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-20 19:33 DEBUG  TaskList: ## Finished create_uninstaller
03-20 19:33 DEBUG  TaskList: ## Running copy_installation_files...
03-20 19:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-20 19:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\winboot -> C:\ubuntu\winboot
03-20 19:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-20 19:33 DEBUG  TaskList: ## Finished copy_installation_files
03-20 19:33 DEBUG  TaskList: ## Running get_iso...
03-20 19:33 DEBUG  TaskList: New task copy_file
03-20 19:33 DEBUG  TaskList: ### Running copy_file...
03-20 19:38 DEBUG  TaskList: ### Finished copy_file
03-20 19:38 DEBUG  TaskList: New task check_iso
03-20 19:38 DEBUG  TaskList: ### Running check_iso...
03-20 19:38 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-20 19:38 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-20 19:38 DEBUG  Distro:     wrong size: 1967058432 > 900000000
03-20 19:38 DEBUG  TaskList: ### Finished check_iso
03-20 19:38 DEBUG  CommonBackend: Searching for local ISO
03-20 19:38 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-20 19:38 DEBUG  TaskList: New task get_metalink
03-20 19:38 DEBUG  TaskList: ### Running get_metalink...
03-20 19:38 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink) > C:\ubuntu\install
03-20 19:38 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
03-20 19:38 DEBUG  downloader: download finished (read 9071 bytes)
03-20 19:38 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
03-20 19:38 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-20 19:38 DEBUG  downloader: download finished (read 488 bytes)
03-20 19:38 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-20 19:38 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-20 19:38 DEBUG  downloader: download finished (read 198 bytes)
03-20 19:38 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-20 19:38 INFO   saplog: Checking block bindings..
03-20 19:38 INFO   saplog: Key verified successfully.
03-20 19:38 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-20 19:38 DEBUG  TaskList: ### Finished get_metalink
03-20 19:38 DEBUG  TaskList: New task download
03-20 19:38 DEBUG  TaskList: ### Running download...
03-20 19:38 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  TaskList: ### Finished download
03-20 19:58 DEBUG  TaskList: New task check_iso
03-20 19:58 DEBUG  TaskList: ### Running check_iso...
03-20 19:58 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-20 19:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-20 19:58 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  TaskList: New task get_file_md5
03-20 19:58 DEBUG  TaskList: #### Running get_file_md5...
03-20 19:58 DEBUG  TaskList: #### Finished get_file_md5
03-20 19:58 DEBUG  TaskList: ### Finished check_iso
03-20 19:58 DEBUG  TaskList: ## Finished get_iso
03-20 19:58 DEBUG  TaskList: ## Running extract_kernel...
03-20 19:58 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 19:58 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-20 19:58 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
03-20 19:58 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-20 19:58 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
03-20 19:58 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-20 19:58 DEBUG  TaskList: ## Finished extract_kernel
03-20 19:58 DEBUG  TaskList: ## Running choose_disk_sizes...
03-20 19:58 DEBUG  WindowsBackend: total size=3000
  root=2744
  swap=256
  home=0
  usr=0
03-20 19:58 DEBUG  TaskList: ## Finished choose_disk_sizes
03-20 19:58 DEBUG  TaskList: ## Running create_preseed...
03-20 19:58 DEBUG  TaskList: ## Finished create_preseed
03-20 19:58 DEBUG  TaskList: ## Running modify_bootloader...
03-20 19:58 DEBUG  TaskList: New task modify_bootini
03-20 19:58 DEBUG  TaskList: ### Running modify_bootini...
03-20 19:58 DEBUG  WindowsBackend: modify_bootini C:
03-20 19:58 DEBUG  TaskList: ### Finished modify_bootini
03-20 19:58 DEBUG  TaskList: New task modify_bootini
03-20 19:58 DEBUG  TaskList: ### Running modify_bootini...
03-20 19:58 DEBUG  WindowsBackend: modify_bootini D:
03-20 19:58 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
03-20 19:58 DEBUG  TaskList: ### Finished modify_bootini
03-20 19:58 DEBUG  TaskList: New task modify_bootini
03-20 19:58 DEBUG  TaskList: ### Running modify_bootini...
03-20 19:58 DEBUG  WindowsBackend: modify_bootini I:
03-20 19:58 DEBUG  WindowsBackend: Could not find boot.ini I:\boot.ini
03-20 19:58 DEBUG  TaskList: ### Finished modify_bootini
03-20 19:58 DEBUG  TaskList: ## Finished modify_bootloader
03-20 19:58 DEBUG  TaskList: ## Running modify_grub_configuration...
03-20 19:58 DEBUG  TaskList: ## Finished modify_grub_configuration
03-20 19:58 DEBUG  TaskList: ## Running create_virtual_disks...
03-20 19:58 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 2744MB
03-20 19:58 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
03-20 19:58 DEBUG  TaskList: ## Finished create_virtual_disks
03-20 19:58 DEBUG  TaskList: ## Running uncompress_files...
03-20 19:58 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
03-20 19:58 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
03-20 19:58 DEBUG  TaskList: ## Finished uncompress_files
03-20 19:58 DEBUG  TaskList: ## Running eject_cd...
03-20 19:58 DEBUG  TaskList: ## Finished eject_cd
03-20 19:58 DEBUG  TaskList: # Finished tasklist
03-20 19:58 INFO   root: Almost finished installing
03-20 19:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl651.tmp\translations, languages=['en_US', 'en']
03-20 20:25 INFO   root: Finished installation
03-20 20:25 INFO   root: Rebooting
03-20 20:25 DEBUG  TaskList: # Running tasklist...
03-20 20:25 DEBUG  TaskList: ## Running reboot...
03-20 20:25 DEBUG  TaskList: ## Finished reboot
03-20 20:25 DEBUG  TaskList: # Finished tasklist
03-20 20:25 DEBUG  root: application.quit
03-20 20:25 DEBUG  WindowsFrontend: frontend.quit
03-20 20:25 DEBUG  WindowsFrontend: frontend.on_quit
03-20 20:25 DEBUG  root: application.on_quit
03-20 20:25 INFO   root: sys.exit
03-20 15:26 INFO   root: === wubi 10.10 rev197 ===
03-20 15:26 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
03-20 15:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
03-20 15:26 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\data
03-20 15:26 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\bin\7z.exe
03-20 15:26 DEBUG  CommonBackend: Fetching basic info...
03-20 15:26 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
03-20 15:26 DEBUG  CommonBackend: platform=win32
03-20 15:26 DEBUG  CommonBackend: osname=nt
03-20 15:26 DEBUG  CommonBackend: language=en_US
03-20 15:26 DEBUG  CommonBackend: encoding=cp1252
03-20 15:26 DEBUG  WindowsBackend: arch=i386
03-20 15:26 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\data\isolist.ini
03-20 15:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-20 15:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-20 15:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-20 15:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-20 15:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-20 15:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-20 15:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-20 15:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-20 15:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-20 15:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-20 15:26 DEBUG  WindowsBackend: Fetching host info...
03-20 15:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-20 15:26 DEBUG  WindowsBackend: windows version=xp
03-20 15:26 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-20 15:26 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-20 15:26 DEBUG  WindowsBackend: windows_build=2600
03-20 15:26 DEBUG  WindowsBackend: gmt=2
03-20 15:26 DEBUG  WindowsBackend: country=US
03-20 15:26 DEBUG  WindowsBackend: timezone=America/New_York
03-20 15:26 DEBUG  WindowsBackend: windows_username=Sylar
03-20 15:26 DEBUG  WindowsBackend: user_full_name=Sylar
03-20 15:26 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
03-20 15:26 DEBUG  WindowsBackend: windows_language_code=1033
03-20 15:26 DEBUG  WindowsBackend: windows_language=English
03-20 15:26 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
03-20 15:26 DEBUG  WindowsBackend: bootloader=xp
03-20 15:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 82323.4453125 mb free ntfs)
03-20 15:26 DEBUG  WindowsBackend: drive=Drive(C: hd 82323.4453125 mb free ntfs)
03-20 15:26 DEBUG  WindowsBackend: drive=Drive(D: hd 81134.5351563 mb free ntfs)
03-20 15:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-20 15:26 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-20 15:26 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.26953125 mb free fat32)
03-20 15:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-20 15:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-20 15:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-20 15:26 DEBUG  WindowsBackend: keyboard_id=67699721
03-20 15:26 DEBUG  WindowsBackend: keyboard_layout=us
03-20 15:26 DEBUG  WindowsBackend: keyboard_variant=
03-20 15:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-20 15:26 DEBUG  CommonBackend: locale=en_US.UTF-8
03-20 15:26 DEBUG  WindowsBackend: total_memory_mb=639.484375
03-20 15:26 DEBUG  CommonBackend: Searching ISOs on USB devices
03-20 15:26 DEBUG  CommonBackend: Searching for local CDs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-20 15:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-20 15:26 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-20 15:26 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-20 15:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-20 15:26 DEBUG  Distro: wrong arch: i386 != amd64
03-20 15:26 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-20 15:26 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-20 15:26 INFO   root: Running the uninstaller...
03-20 15:26 INFO   CommonBackend: This is the uninstaller running
03-20 15:26 DEBUG  WindowsFrontend: __init__...
03-20 15:26 DEBUG  WindowsFrontend: on_init...
03-20 15:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
03-20 15:26 INFO   root: Received settings
03-20 15:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
03-20 15:26 DEBUG  TaskList: # Running tasklist...
03-20 15:26 DEBUG  TaskList: ## Running Backup ISO...
03-20 15:26 DEBUG  TaskList: ## Finished Backup ISO
03-20 15:26 DEBUG  TaskList: ## Running Remove bootloader entry...
03-20 15:26 ERROR  WindowsBackend: Cannot find bcdedit
03-20 15:26 DEBUG  WindowsBackend: undo_bootini C:
03-20 15:26 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 82323.4453125 mb free ntfs)
03-20 15:26 DEBUG  WindowsBackend: undo_bootini D:
03-20 15:26 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 81134.5351563 mb free ntfs)
03-20 15:26 DEBUG  WindowsBackend: undo_bootini I:
03-20 15:26 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 1179.26953125 mb free fat32)
03-20 15:26 DEBUG  TaskList: ## Finished Remove bootloader entry
03-20 15:26 DEBUG  TaskList: ## Running Remove target dir...
03-20 15:26 DEBUG  CommonBackend: Deleting C:\ubuntu
03-20 15:26 DEBUG  TaskList: ## Finished Remove target dir
03-20 15:26 DEBUG  TaskList: ## Running Remove registry key...
03-20 15:26 DEBUG  TaskList: ## Finished Remove registry key
03-20 15:26 DEBUG  TaskList: # Finished tasklist
03-20 15:26 INFO   root: Almost finished uninstalling
03-20 15:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
03-20 15:26 INFO   root: Finished uninstallation
03-20 15:26 DEBUG  root: application.quit
03-20 15:26 DEBUG  WindowsFrontend: frontend.quit
03-20 15:26 DEBUG  WindowsFrontend: frontend.on_quit
03-20 15:26 DEBUG  root: application.on_quit
03-20 15:26 INFO   root: sys.exit
03-21 03:04 INFO   root: === wubi 10.10 rev197 ===
03-21 03:04 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
03-21 03:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-21 03:04 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\data
03-21 03:04 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\bin\7z.exe
03-21 03:04 DEBUG  CommonBackend: Fetching basic info...
03-21 03:04 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-21 03:04 DEBUG  CommonBackend: platform=win32
03-21 03:04 DEBUG  CommonBackend: osname=nt
03-21 03:04 DEBUG  CommonBackend: language=en_US
03-21 03:04 DEBUG  CommonBackend: encoding=cp1252
03-21 03:04 DEBUG  WindowsBackend: arch=i386
03-21 03:04 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\data\isolist.ini
03-21 03:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-21 03:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-21 03:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-21 03:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-21 03:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-21 03:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-21 03:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-21 03:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-21 03:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-21 03:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-21 03:04 DEBUG  WindowsBackend: Fetching host info...
03-21 03:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-21 03:04 DEBUG  WindowsBackend: windows version=xp
03-21 03:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-21 03:04 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-21 03:04 DEBUG  WindowsBackend: windows_build=2600
03-21 03:04 DEBUG  WindowsBackend: gmt=2
03-21 03:04 DEBUG  WindowsBackend: country=US
03-21 03:04 DEBUG  WindowsBackend: timezone=America/New_York
03-21 03:04 DEBUG  WindowsBackend: windows_username=Sylar
03-21 03:04 DEBUG  WindowsBackend: user_full_name=Sylar
03-21 03:04 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
03-21 03:04 DEBUG  WindowsBackend: windows_language_code=1033
03-21 03:04 DEBUG  WindowsBackend: windows_language=English
03-21 03:04 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
03-21 03:04 DEBUG  WindowsBackend: bootloader=xp
03-21 03:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85818.8984375 mb free ntfs)
03-21 03:04 DEBUG  WindowsBackend: drive=Drive(C: hd 85818.8984375 mb free ntfs)
03-21 03:04 DEBUG  WindowsBackend: drive=Drive(D: hd 81134.5351563 mb free ntfs)
03-21 03:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-21 03:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-21 03:04 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.2109375 mb free fat32)
03-21 03:04 DEBUG  WindowsBackend: uninstaller_path=None
03-21 03:04 DEBUG  WindowsBackend: previous_target_dir=None
03-21 03:04 DEBUG  WindowsBackend: previous_distro_name=None
03-21 03:04 DEBUG  WindowsBackend: keyboard_id=67699721
03-21 03:04 DEBUG  WindowsBackend: keyboard_layout=us
03-21 03:04 DEBUG  WindowsBackend: keyboard_variant=
03-21 03:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-21 03:04 DEBUG  CommonBackend: locale=en_US.UTF-8
03-21 03:04 DEBUG  WindowsBackend: total_memory_mb=639.484375
03-21 03:04 DEBUG  CommonBackend: Searching ISOs on USB devices
03-21 03:04 DEBUG  CommonBackend: Searching for local CDs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Kubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-21 03:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 03:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 03:04 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-21 03:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-21 03:04 DEBUG  Distro: wrong arch: i386 != amd64
03-21 03:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 03:04 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-21 03:04 INFO   root: Running the CD menu...
03-21 03:04 DEBUG  WindowsFrontend: __init__...
03-21 03:04 DEBUG  WindowsFrontend: on_init...
03-21 03:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
03-21 03:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
03-21 03:04 INFO   root: CD menu finished
03-21 03:04 INFO   root: Running the installer...
03-21 03:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
03-21 03:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
03-21 03:04 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=alex
03-21 03:04 INFO   root: Received settings
03-21 03:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
03-21 03:04 DEBUG  TaskList: # Running tasklist...
03-21 03:04 DEBUG  TaskList: ## Running select_target_dir...
03-21 03:04 INFO   WindowsBackend: Installing into C:\ubuntu
03-21 03:04 DEBUG  TaskList: ## Finished select_target_dir
03-21 03:04 DEBUG  TaskList: ## Running create_dir_structure...
03-21 03:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-21 03:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-21 03:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-21 03:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-21 03:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-21 03:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-21 03:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-21 03:04 DEBUG  TaskList: ## Finished create_dir_structure
03-21 03:04 DEBUG  TaskList: ## Running uncompress_target_dir...
03-21 03:04 DEBUG  TaskList: ## Finished uncompress_target_dir
03-21 03:04 DEBUG  TaskList: ## Running create_uninstaller...
03-21 03:04 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-21 03:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-21 03:04 DEBUG  TaskList: ## Finished create_uninstaller
03-21 03:04 DEBUG  TaskList: ## Running copy_installation_files...
03-21 03:04 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-21 03:04 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\winboot -> C:\ubuntu\winboot
03-21 03:04 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-21 03:04 DEBUG  TaskList: ## Finished copy_installation_files
03-21 03:04 DEBUG  TaskList: ## Running get_iso...
03-21 03:04 DEBUG  TaskList: New task copy_file
03-21 03:04 DEBUG  TaskList: ### Running copy_file...
03-21 03:10 DEBUG  TaskList: ### Finished copy_file
03-21 03:10 DEBUG  TaskList: New task check_iso
03-21 03:10 DEBUG  TaskList: ### Running check_iso...
03-21 03:10 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-21 03:10 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-21 03:10 DEBUG  Distro:     wrong size: 1967058432 > 900000000
03-21 03:10 DEBUG  TaskList: ### Finished check_iso
03-21 03:10 DEBUG  CommonBackend: Searching for local ISO
03-21 03:10 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-21 03:10 DEBUG  TaskList: New task get_metalink
03-21 03:10 DEBUG  TaskList: ### Running get_metalink...
03-21 03:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink) > C:\ubuntu\install
03-21 03:10 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
03-21 03:10 DEBUG  downloader: download finished (read 9071 bytes)
03-21 03:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
03-21 03:10 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-21 03:10 DEBUG  downloader: download finished (read 488 bytes)
03-21 03:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-21 03:10 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-21 03:10 DEBUG  downloader: download finished (read 198 bytes)
03-21 03:10 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-21 03:10 INFO   saplog: Checking block bindings..
03-21 03:10 INFO   saplog: Key verified successfully.
03-21 03:10 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-21 03:10 DEBUG  TaskList: ### Finished get_metalink
03-21 03:10 DEBUG  TaskList: New task download
03-21 03:10 DEBUG  TaskList: ### Running download...
03-21 03:10 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  TaskList: ### Finished download
03-21 03:28 DEBUG  TaskList: New task check_iso
03-21 03:28 DEBUG  TaskList: ### Running check_iso...
03-21 03:28 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-21 03:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-21 03:28 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  TaskList: New task get_file_md5
03-21 03:28 DEBUG  TaskList: #### Running get_file_md5...
03-21 03:28 DEBUG  TaskList: #### Finished get_file_md5
03-21 03:28 DEBUG  TaskList: ### Finished check_iso
03-21 03:28 DEBUG  TaskList: ## Finished get_iso
03-21 03:28 DEBUG  TaskList: ## Running extract_kernel...
03-21 03:28 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-21 03:28 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-21 03:28 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
03-21 03:28 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-21 03:28 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
03-21 03:28 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-21 03:28 DEBUG  TaskList: ## Finished extract_kernel
03-21 03:28 DEBUG  TaskList: ## Running choose_disk_sizes...
03-21 03:28 DEBUG  WindowsBackend: total size=3000
  root=2744
  swap=256
  home=0
  usr=0
03-21 03:28 DEBUG  TaskList: ## Finished choose_disk_sizes
03-21 03:28 DEBUG  TaskList: ## Running create_preseed...
03-21 03:28 DEBUG  TaskList: ## Finished create_preseed
03-21 03:28 DEBUG  TaskList: ## Running modify_bootloader...
03-21 03:28 DEBUG  TaskList: New task modify_bootini
03-21 03:28 DEBUG  TaskList: ### Running modify_bootini...
03-21 03:28 DEBUG  WindowsBackend: modify_bootini C:
03-21 03:28 DEBUG  TaskList: ### Finished modify_bootini
03-21 03:28 DEBUG  TaskList: New task modify_bootini
03-21 03:28 DEBUG  TaskList: ### Running modify_bootini...
03-21 03:28 DEBUG  WindowsBackend: modify_bootini D:
03-21 03:28 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
03-21 03:28 DEBUG  TaskList: ### Finished modify_bootini
03-21 03:28 DEBUG  TaskList: New task modify_bootini
03-21 03:28 DEBUG  TaskList: ### Running modify_bootini...
03-21 03:28 DEBUG  WindowsBackend: modify_bootini I:
03-21 03:28 DEBUG  WindowsBackend: Could not find boot.ini I:\boot.ini
03-21 03:28 DEBUG  TaskList: ### Finished modify_bootini
03-21 03:28 DEBUG  TaskList: ## Finished modify_bootloader
03-21 03:28 DEBUG  TaskList: ## Running modify_grub_configuration...
03-21 03:28 DEBUG  TaskList: ## Finished modify_grub_configuration
03-21 03:28 DEBUG  TaskList: ## Running create_virtual_disks...
03-21 03:28 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 2744MB
03-21 03:28 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
03-21 03:28 DEBUG  TaskList: ## Finished create_virtual_disks
03-21 03:28 DEBUG  TaskList: ## Running uncompress_files...
03-21 03:28 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
03-21 03:28 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
03-21 03:28 DEBUG  TaskList: ## Finished uncompress_files
03-21 03:28 DEBUG  TaskList: ## Running eject_cd...
03-21 03:28 DEBUG  TaskList: ## Finished eject_cd
03-21 03:28 DEBUG  TaskList: # Finished tasklist
03-21 03:28 INFO   root: Almost finished installing
03-21 03:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
03-21 04:00 INFO   root: Finished installation
03-21 04:00 INFO   root: Rebooting
03-21 04:00 DEBUG  TaskList: # Running tasklist...
03-21 04:00 DEBUG  TaskList: ## Running reboot...
03-21 04:00 DEBUG  TaskList: ## Finished reboot
03-21 04:00 DEBUG  TaskList: # Finished tasklist
03-21 04:00 DEBUG  root: application.quit
03-21 04:00 DEBUG  WindowsFrontend: frontend.quit
03-21 04:00 DEBUG  WindowsFrontend: frontend.on_quit
03-21 04:00 DEBUG  root: application.on_quit
03-21 04:00 INFO   root: sys.exit
03-21 04:28 INFO   root: === wubi 10.10 rev197 ===
03-21 04:28 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
03-21 04:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
03-21 04:28 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data
03-21 04:28 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\bin\7z.exe
03-21 04:28 DEBUG  CommonBackend: Fetching basic info...
03-21 04:28 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
03-21 04:28 DEBUG  CommonBackend: platform=win32
03-21 04:28 DEBUG  CommonBackend: osname=nt
03-21 04:28 DEBUG  CommonBackend: language=en_US
03-21 04:28 DEBUG  CommonBackend: encoding=cp1252
03-21 04:28 DEBUG  WindowsBackend: arch=i386
03-21 04:28 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\isolist.ini
03-21 04:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-21 04:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-21 04:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-21 04:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-21 04:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-21 04:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-21 04:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-21 04:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-21 04:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-21 04:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-21 04:28 DEBUG  WindowsBackend: Fetching host info...
03-21 04:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-21 04:28 DEBUG  WindowsBackend: windows version=xp
03-21 04:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-21 04:28 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-21 04:28 DEBUG  WindowsBackend: windows_build=2600
03-21 04:28 DEBUG  WindowsBackend: gmt=2
03-21 04:28 DEBUG  WindowsBackend: country=US
03-21 04:28 DEBUG  WindowsBackend: timezone=America/New_York
03-21 04:28 DEBUG  WindowsBackend: windows_username=Sylar
03-21 04:28 DEBUG  WindowsBackend: user_full_name=Sylar
03-21 04:28 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
03-21 04:28 DEBUG  WindowsBackend: windows_language_code=1033
03-21 04:28 DEBUG  WindowsBackend: windows_language=English
03-21 04:28 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
03-21 04:28 DEBUG  WindowsBackend: bootloader=xp
03-21 04:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 80184.7773438 mb free ntfs)
03-21 04:28 DEBUG  WindowsBackend: drive=Drive(C: hd 80184.7773438 mb free ntfs)
03-21 04:28 DEBUG  WindowsBackend: drive=Drive(D: hd 81134.2460938 mb free ntfs)
03-21 04:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-21 04:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-21 04:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-21 04:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-21 04:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-21 04:28 DEBUG  WindowsBackend: keyboard_id=67699721
03-21 04:28 DEBUG  WindowsBackend: keyboard_layout=us
03-21 04:28 DEBUG  WindowsBackend: keyboard_variant=
03-21 04:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-21 04:28 DEBUG  CommonBackend: locale=en_US.UTF-8
03-21 04:28 DEBUG  WindowsBackend: total_memory_mb=639.484375
03-21 04:28 DEBUG  CommonBackend: Searching ISOs on USB devices
03-21 04:28 DEBUG  CommonBackend: Searching for local CDs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-21 04:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 04:28 INFO   root: Running the uninstaller...
03-21 04:28 INFO   CommonBackend: This is the uninstaller running
03-21 04:28 DEBUG  WindowsFrontend: __init__...
03-21 04:28 DEBUG  WindowsFrontend: on_init...
03-21 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-21 04:28 INFO   root: Received settings
03-21 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-21 04:28 DEBUG  TaskList: # Running tasklist...
03-21 04:28 DEBUG  TaskList: ## Running Backup ISO...
03-21 04:28 DEBUG  TaskList: ## Finished Backup ISO
03-21 04:28 DEBUG  TaskList: ## Running Remove bootloader entry...
03-21 04:28 ERROR  WindowsBackend: Cannot find bcdedit
03-21 04:28 DEBUG  WindowsBackend: undo_bootini C:
03-21 04:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 80184.7773438 mb free ntfs)
03-21 04:28 DEBUG  WindowsBackend: undo_bootini D:
03-21 04:28 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 81134.2460938 mb free ntfs)
03-21 04:28 DEBUG  TaskList: ## Finished Remove bootloader entry
03-21 04:28 DEBUG  TaskList: ## Running Remove target dir...
03-21 04:28 DEBUG  CommonBackend: Deleting C:\ubuntu
03-21 04:28 DEBUG  TaskList: ## Finished Remove target dir
03-21 04:28 DEBUG  TaskList: ## Running Remove registry key...
03-21 04:28 DEBUG  TaskList: ## Finished Remove registry key
03-21 04:28 DEBUG  TaskList: # Finished tasklist
03-21 04:28 INFO   root: Almost finished uninstalling
03-21 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-21 04:28 INFO   root: Finished uninstallation
03-21 04:28 DEBUG  root: application.quit
03-21 04:28 DEBUG  WindowsFrontend: frontend.quit
03-21 04:28 DEBUG  WindowsFrontend: frontend.on_quit
03-21 04:28 DEBUG  root: application.on_quit
03-21 04:28 INFO   root: sys.exit
04-07 09:43 INFO   root: === wubi 10.10 rev197 ===
04-07 09:43 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 09:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 09:43 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\data
04-07 09:43 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\bin\7z.exe
04-07 09:43 DEBUG  CommonBackend: Fetching basic info...
04-07 09:43 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 09:43 DEBUG  CommonBackend: platform=win32
04-07 09:43 DEBUG  CommonBackend: osname=nt
04-07 09:43 DEBUG  CommonBackend: language=en_US
04-07 09:43 DEBUG  CommonBackend: encoding=cp1252
04-07 09:43 DEBUG  WindowsBackend: arch=i386
04-07 09:43 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\data\isolist.ini
04-07 09:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 09:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 09:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 09:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 09:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 09:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 09:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 09:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 09:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 09:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 09:43 DEBUG  WindowsBackend: Fetching host info...
04-07 09:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 09:43 DEBUG  WindowsBackend: windows version=xp
04-07 09:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 09:43 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 09:43 DEBUG  WindowsBackend: windows_build=2600
04-07 09:43 DEBUG  WindowsBackend: gmt=2
04-07 09:43 DEBUG  WindowsBackend: country=US
04-07 09:43 DEBUG  WindowsBackend: timezone=America/New_York
04-07 09:43 DEBUG  WindowsBackend: windows_username=Sylar
04-07 09:43 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 09:43 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 09:43 DEBUG  WindowsBackend: windows_language_code=1033
04-07 09:43 DEBUG  WindowsBackend: windows_language=English
04-07 09:43 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 09:43 DEBUG  WindowsBackend: bootloader=xp
04-07 09:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87323.6992188 mb free ntfs)
04-07 09:43 DEBUG  WindowsBackend: drive=Drive(C: hd 87323.6992188 mb free ntfs)
04-07 09:43 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 09:43 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 09:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 09:43 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 09:43 DEBUG  WindowsBackend: uninstaller_path=None
04-07 09:43 DEBUG  WindowsBackend: previous_target_dir=None
04-07 09:43 DEBUG  WindowsBackend: previous_distro_name=None
04-07 09:43 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 09:43 DEBUG  WindowsBackend: keyboard_layout=us
04-07 09:43 DEBUG  WindowsBackend: keyboard_variant=
04-07 09:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 09:43 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 09:43 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 09:43 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 09:43 DEBUG  CommonBackend: Searching for local CDs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:43 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 09:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 09:43 DEBUG  Distro: wrong arch: i386 != amd64
04-07 09:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:43 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 09:43 INFO   root: Running the CD menu...
04-07 09:43 DEBUG  WindowsFrontend: __init__...
04-07 09:43 DEBUG  WindowsFrontend: on_init...
04-07 09:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
04-07 09:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
04-07 09:43 INFO   root: CD menu finished
04-07 09:43 INFO   root: Rebooting
04-07 09:43 DEBUG  TaskList: # Running tasklist...
04-07 09:43 DEBUG  TaskList: ## Running reboot...
04-07 09:43 DEBUG  TaskList: ## Finished reboot
04-07 09:43 DEBUG  TaskList: # Finished tasklist
04-07 09:43 DEBUG  root: application.quit
04-07 09:43 DEBUG  WindowsFrontend: frontend.quit
04-07 09:43 DEBUG  WindowsFrontend: frontend.on_quit
04-07 09:43 DEBUG  root: application.on_quit
04-07 09:43 INFO   root: sys.exit
04-07 09:45 INFO   root: === wubi 10.10 rev197 ===
04-07 09:45 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 09:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 09:45 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\data
04-07 09:45 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\bin\7z.exe
04-07 09:45 DEBUG  CommonBackend: Fetching basic info...
04-07 09:45 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 09:45 DEBUG  CommonBackend: platform=win32
04-07 09:45 DEBUG  CommonBackend: osname=nt
04-07 09:45 DEBUG  CommonBackend: language=en_US
04-07 09:45 DEBUG  CommonBackend: encoding=cp1252
04-07 09:45 DEBUG  WindowsBackend: arch=i386
04-07 09:45 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\data\isolist.ini
04-07 09:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 09:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 09:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 09:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 09:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 09:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 09:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 09:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 09:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 09:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 09:45 DEBUG  WindowsBackend: Fetching host info...
04-07 09:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 09:45 DEBUG  WindowsBackend: windows version=xp
04-07 09:45 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 09:45 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 09:45 DEBUG  WindowsBackend: windows_build=2600
04-07 09:45 DEBUG  WindowsBackend: gmt=2
04-07 09:45 DEBUG  WindowsBackend: country=US
04-07 09:45 DEBUG  WindowsBackend: timezone=America/New_York
04-07 09:45 DEBUG  WindowsBackend: windows_username=Sylar
04-07 09:45 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 09:45 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 09:45 DEBUG  WindowsBackend: windows_language_code=1033
04-07 09:45 DEBUG  WindowsBackend: windows_language=English
04-07 09:45 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 09:45 DEBUG  WindowsBackend: bootloader=xp
04-07 09:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87309.515625 mb free ntfs)
04-07 09:45 DEBUG  WindowsBackend: drive=Drive(C: hd 87309.515625 mb free ntfs)
04-07 09:45 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 09:45 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 09:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 09:45 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 09:45 DEBUG  WindowsBackend: uninstaller_path=None
04-07 09:45 DEBUG  WindowsBackend: previous_target_dir=None
04-07 09:45 DEBUG  WindowsBackend: previous_distro_name=None
04-07 09:45 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 09:45 DEBUG  WindowsBackend: keyboard_layout=us
04-07 09:45 DEBUG  WindowsBackend: keyboard_variant=
04-07 09:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 09:45 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 09:45 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 09:45 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 09:45 DEBUG  CommonBackend: Searching for local CDs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:45 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:45 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 09:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 09:45 DEBUG  Distro: wrong arch: i386 != amd64
04-07 09:45 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:45 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 09:45 INFO   root: Running the CD menu...
04-07 09:45 DEBUG  WindowsFrontend: __init__...
04-07 09:45 DEBUG  WindowsFrontend: on_init...
04-07 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
04-07 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
04-07 09:45 INFO   root: CD menu finished
04-07 09:45 INFO   root: Running the CD boot helper...
04-07 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
04-07 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
04-07 09:45 INFO   root: CD boot helper confirmed
04-07 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
04-07 09:45 DEBUG  TaskList: # Running tasklist...
04-07 09:45 DEBUG  TaskList: ## Running select_target_dir...
04-07 09:45 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 09:45 DEBUG  TaskList: ## Finished select_target_dir
04-07 09:45 DEBUG  TaskList: ## Running create_dir_structure...
04-07 09:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 09:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 09:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 09:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 09:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 09:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 09:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 09:45 DEBUG  TaskList: ## Finished create_dir_structure
04-07 09:45 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 09:45 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 09:45 DEBUG  TaskList: ## Running create_uninstaller...
04-07 09:45 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 09:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 09:45 DEBUG  TaskList: ## Finished create_uninstaller
04-07 09:45 DEBUG  TaskList: ## Running copy_installation_files...
04-07 09:45 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 09:45 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\winboot -> C:\ubuntu\winboot
04-07 09:45 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 09:45 DEBUG  TaskList: ## Finished copy_installation_files
04-07 09:45 DEBUG  TaskList: ## Running use_cd...
04-07 09:45 DEBUG  TaskList: New task copy_file
04-07 09:45 DEBUG  TaskList: ### Running copy_file...
04-07 09:52 DEBUG  TaskList: ### Finished copy_file
04-07 09:52 DEBUG  TaskList: New task check_iso
04-07 09:52 DEBUG  TaskList: ### Running check_iso...
04-07 09:52 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 09:52 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 09:52 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 09:52 DEBUG  TaskList: ### Finished check_iso
04-07 09:52 DEBUG  TaskList: ## Finished use_cd
04-07 09:52 DEBUG  TaskList: ## Running extract_kernel...
04-07 09:52 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 09:52 DEBUG  TaskList: # Cancelling tasklist
04-07 09:52 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 09:52 DEBUG  TaskList: # Finished tasklist
04-07 09:54 INFO   root: === wubi 10.10 rev197 ===
04-07 09:54 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 09:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-07 09:54 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data
04-07 09:54 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\bin\7z.exe
04-07 09:54 DEBUG  CommonBackend: Fetching basic info...
04-07 09:54 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-07 09:54 DEBUG  CommonBackend: platform=win32
04-07 09:54 DEBUG  CommonBackend: osname=nt
04-07 09:54 DEBUG  CommonBackend: language=en_US
04-07 09:54 DEBUG  CommonBackend: encoding=cp1252
04-07 09:54 DEBUG  WindowsBackend: arch=i386
04-07 09:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\isolist.ini
04-07 09:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 09:54 DEBUG  WindowsBackend: Fetching host info...
04-07 09:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 09:54 DEBUG  WindowsBackend: windows version=xp
04-07 09:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 09:54 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 09:54 DEBUG  WindowsBackend: windows_build=2600
04-07 09:54 DEBUG  WindowsBackend: gmt=2
04-07 09:54 DEBUG  WindowsBackend: country=US
04-07 09:54 DEBUG  WindowsBackend: timezone=America/New_York
04-07 09:54 DEBUG  WindowsBackend: windows_username=Sylar
04-07 09:54 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 09:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 09:54 DEBUG  WindowsBackend: windows_language_code=1033
04-07 09:54 DEBUG  WindowsBackend: windows_language=English
04-07 09:54 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 09:54 DEBUG  WindowsBackend: bootloader=xp
04-07 09:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85420.0976563 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(C: hd 85420.0976563 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 09:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 09:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 09:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 09:54 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 09:54 DEBUG  WindowsBackend: keyboard_layout=us
04-07 09:54 DEBUG  WindowsBackend: keyboard_variant=
04-07 09:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 09:54 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 09:54 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 09:54 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 09:54 DEBUG  CommonBackend: Searching for local CDs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 09:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 09:54 DEBUG  Distro: wrong arch: i386 != amd64
04-07 09:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:54 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 09:54 INFO   root: Running the uninstaller...
04-07 09:54 INFO   CommonBackend: This is the uninstaller running
04-07 09:54 DEBUG  WindowsFrontend: __init__...
04-07 09:54 DEBUG  WindowsFrontend: on_init...
04-07 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 09:54 INFO   root: Received settings
04-07 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 09:54 DEBUG  TaskList: # Running tasklist...
04-07 09:54 DEBUG  TaskList: ## Running Backup ISO...
04-07 09:54 DEBUG  TaskList: ## Finished Backup ISO
04-07 09:54 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 09:54 ERROR  WindowsBackend: Cannot find bcdedit
04-07 09:54 DEBUG  WindowsBackend: undo_bootini C:
04-07 09:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 85420.0976563 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: undo_bootini D:
04-07 09:54 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112502.550781 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: undo_bootini I:
04-07 09:54 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 1164.0546875 mb free fat32)
04-07 09:54 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 09:54 DEBUG  TaskList: ## Running Remove target dir...
04-07 09:54 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 09:54 DEBUG  TaskList: ## Finished Remove target dir
04-07 09:54 DEBUG  TaskList: ## Running Remove registry key...
04-07 09:54 DEBUG  TaskList: ## Finished Remove registry key
04-07 09:54 DEBUG  TaskList: # Finished tasklist
04-07 09:54 INFO   root: Almost finished uninstalling
04-07 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 09:54 INFO   root: Finished uninstallation
04-07 09:54 DEBUG  root: application.quit
04-07 09:54 DEBUG  WindowsFrontend: frontend.quit
04-07 09:54 DEBUG  WindowsFrontend: frontend.on_quit
04-07 09:54 DEBUG  root: application.on_quit
04-07 09:54 INFO   root: sys.exit
04-07 09:54 INFO   root: === wubi 10.10 rev197 ===
04-07 09:54 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 09:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 09:54 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\data
04-07 09:54 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\bin\7z.exe
04-07 09:54 DEBUG  CommonBackend: Fetching basic info...
04-07 09:54 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 09:54 DEBUG  CommonBackend: platform=win32
04-07 09:54 DEBUG  CommonBackend: osname=nt
04-07 09:54 DEBUG  CommonBackend: language=en_US
04-07 09:54 DEBUG  CommonBackend: encoding=cp1252
04-07 09:54 DEBUG  WindowsBackend: arch=i386
04-07 09:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
04-07 09:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 09:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 09:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 09:54 DEBUG  WindowsBackend: Fetching host info...
04-07 09:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 09:54 DEBUG  WindowsBackend: windows version=xp
04-07 09:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 09:54 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 09:54 DEBUG  WindowsBackend: windows_build=2600
04-07 09:54 DEBUG  WindowsBackend: gmt=2
04-07 09:54 DEBUG  WindowsBackend: country=US
04-07 09:54 DEBUG  WindowsBackend: timezone=America/New_York
04-07 09:54 DEBUG  WindowsBackend: windows_username=Sylar
04-07 09:54 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 09:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 09:54 DEBUG  WindowsBackend: windows_language_code=1033
04-07 09:54 DEBUG  WindowsBackend: windows_language=English
04-07 09:54 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 09:54 DEBUG  WindowsBackend: bootloader=xp
04-07 09:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87297.4335938 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(C: hd 87297.4335938 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 09:54 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 09:54 DEBUG  WindowsBackend: uninstaller_path=None
04-07 09:54 DEBUG  WindowsBackend: previous_target_dir=None
04-07 09:54 DEBUG  WindowsBackend: previous_distro_name=None
04-07 09:54 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 09:54 DEBUG  WindowsBackend: keyboard_layout=us
04-07 09:54 DEBUG  WindowsBackend: keyboard_variant=
04-07 09:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 09:54 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 09:54 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 09:54 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 09:54 DEBUG  CommonBackend: Searching for local CDs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:54 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 09:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 09:54 DEBUG  Distro: wrong arch: i386 != amd64
04-07 09:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:54 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 09:54 INFO   root: Running the CD menu...
04-07 09:54 DEBUG  WindowsFrontend: __init__...
04-07 09:54 DEBUG  WindowsFrontend: on_init...
04-07 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 09:54 INFO   root: CD menu finished
04-07 09:54 INFO   root: Running the CD boot helper...
04-07 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 09:54 INFO   WindowsFrontend: Operation cancelled
04-07 09:54 DEBUG  WindowsFrontend: frontend.quit
04-07 09:54 DEBUG  WindowsFrontend: frontend.on_quit
04-07 09:54 DEBUG  root: application.on_quit
04-07 09:54 INFO   root: sys.exit
04-07 09:55 INFO   root: === wubi 10.10 rev197 ===
04-07 09:55 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 09:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 09:55 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data
04-07 09:55 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\bin\7z.exe
04-07 09:55 DEBUG  CommonBackend: Fetching basic info...
04-07 09:55 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 09:55 DEBUG  CommonBackend: platform=win32
04-07 09:55 DEBUG  CommonBackend: osname=nt
04-07 09:55 DEBUG  CommonBackend: language=en_US
04-07 09:55 DEBUG  CommonBackend: encoding=cp1252
04-07 09:55 DEBUG  WindowsBackend: arch=i386
04-07 09:55 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data\isolist.ini
04-07 09:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 09:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 09:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 09:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 09:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 09:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 09:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 09:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 09:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 09:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 09:55 DEBUG  WindowsBackend: Fetching host info...
04-07 09:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 09:55 DEBUG  WindowsBackend: windows version=xp
04-07 09:55 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 09:55 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 09:55 DEBUG  WindowsBackend: windows_build=2600
04-07 09:55 DEBUG  WindowsBackend: gmt=2
04-07 09:55 DEBUG  WindowsBackend: country=US
04-07 09:55 DEBUG  WindowsBackend: timezone=America/New_York
04-07 09:55 DEBUG  WindowsBackend: windows_username=Sylar
04-07 09:55 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 09:55 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 09:55 DEBUG  WindowsBackend: windows_language_code=1033
04-07 09:55 DEBUG  WindowsBackend: windows_language=English
04-07 09:55 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 09:55 DEBUG  WindowsBackend: bootloader=xp
04-07 09:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87297.3984375 mb free ntfs)
04-07 09:55 DEBUG  WindowsBackend: drive=Drive(C: hd 87297.3984375 mb free ntfs)
04-07 09:55 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 09:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 09:55 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 09:55 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 09:55 DEBUG  WindowsBackend: uninstaller_path=None
04-07 09:55 DEBUG  WindowsBackend: previous_target_dir=None
04-07 09:55 DEBUG  WindowsBackend: previous_distro_name=None
04-07 09:55 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 09:55 DEBUG  WindowsBackend: keyboard_layout=us
04-07 09:55 DEBUG  WindowsBackend: keyboard_variant=
04-07 09:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 09:55 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 09:55 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 09:55 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 09:55 DEBUG  CommonBackend: Searching for local CDs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 09:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 09:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 09:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 09:55 DEBUG  Distro: wrong arch: i386 != amd64
04-07 09:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 09:55 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 09:55 INFO   root: Running the CD menu...
04-07 09:55 DEBUG  WindowsFrontend: __init__...
04-07 09:55 DEBUG  WindowsFrontend: on_init...
04-07 09:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 09:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 09:55 INFO   root: CD menu finished
04-07 09:55 INFO   root: Running the CD boot helper...
04-07 09:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 09:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 09:55 INFO   root: CD boot helper confirmed
04-07 09:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 09:55 DEBUG  TaskList: # Running tasklist...
04-07 09:55 DEBUG  TaskList: ## Running select_target_dir...
04-07 09:55 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 09:55 DEBUG  TaskList: ## Finished select_target_dir
04-07 09:55 DEBUG  TaskList: ## Running create_dir_structure...
04-07 09:55 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 09:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 09:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 09:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 09:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 09:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 09:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 09:55 DEBUG  TaskList: ## Finished create_dir_structure
04-07 09:55 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 09:55 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 09:55 DEBUG  TaskList: ## Running create_uninstaller...
04-07 09:55 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 09:55 DEBUG  TaskList: ## Finished create_uninstaller
04-07 09:55 DEBUG  TaskList: ## Running copy_installation_files...
04-07 09:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 09:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\winboot -> C:\ubuntu\winboot
04-07 09:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 09:55 DEBUG  TaskList: ## Finished copy_installation_files
04-07 09:55 DEBUG  TaskList: ## Running use_cd...
04-07 09:55 DEBUG  TaskList: New task copy_file
04-07 09:55 DEBUG  TaskList: ### Running copy_file...
04-07 09:56 INFO   WindowsFrontend: Operation cancelled
04-07 09:56 DEBUG  WindowsFrontend: frontend.quit
04-07 09:56 DEBUG  WindowsFrontend: frontend.on_quit
04-07 09:56 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-07 09:56 DEBUG  TaskList: # Cancelling tasklist
04-07 09:56 DEBUG  TaskList: ### Finished copy_file
04-07 09:56 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-07 09:56 DEBUG  root: application.on_quit
04-07 09:56 DEBUG  root: Forceful exit
04-07 09:56 INFO   root: sys.exit
04-07 10:49 INFO   root: === wubi 10.10 rev197 ===
04-07 10:49 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 10:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 10:49 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\data
04-07 10:49 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\bin\7z.exe
04-07 10:49 DEBUG  CommonBackend: Fetching basic info...
04-07 10:49 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 10:49 DEBUG  CommonBackend: platform=win32
04-07 10:49 DEBUG  CommonBackend: osname=nt
04-07 10:49 DEBUG  CommonBackend: language=en_US
04-07 10:49 DEBUG  CommonBackend: encoding=cp1252
04-07 10:49 DEBUG  WindowsBackend: arch=i386
04-07 10:49 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\data\isolist.ini
04-07 10:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 10:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 10:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 10:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 10:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 10:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 10:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 10:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 10:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 10:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 10:49 DEBUG  WindowsBackend: Fetching host info...
04-07 10:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 10:49 DEBUG  WindowsBackend: windows version=xp
04-07 10:49 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 10:49 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 10:49 DEBUG  WindowsBackend: windows_build=2600
04-07 10:49 DEBUG  WindowsBackend: gmt=2
04-07 10:49 DEBUG  WindowsBackend: country=US
04-07 10:49 DEBUG  WindowsBackend: timezone=America/New_York
04-07 10:49 DEBUG  WindowsBackend: windows_username=Sylar
04-07 10:49 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 10:49 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 10:49 DEBUG  WindowsBackend: windows_language_code=1033
04-07 10:49 DEBUG  WindowsBackend: windows_language=English
04-07 10:49 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 10:49 DEBUG  WindowsBackend: bootloader=xp
04-07 10:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 86575.5703125 mb free ntfs)
04-07 10:49 DEBUG  WindowsBackend: drive=Drive(C: hd 86575.5703125 mb free ntfs)
04-07 10:49 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 10:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 10:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 10:49 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 10:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 10:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 10:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 10:49 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 10:49 DEBUG  WindowsBackend: keyboard_layout=us
04-07 10:49 DEBUG  WindowsBackend: keyboard_variant=
04-07 10:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 10:49 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 10:49 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 10:49 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 10:49 DEBUG  CommonBackend: Searching for local CDs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 10:49 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 10:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 10:49 DEBUG  Distro: wrong arch: i386 != amd64
04-07 10:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 10:49 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 10:49 INFO   root: Running the CD menu...
04-07 10:49 DEBUG  WindowsFrontend: __init__...
04-07 10:49 DEBUG  WindowsFrontend: on_init...
04-07 10:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\translations, languages=['en_US', 'en']
04-07 10:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\translations, languages=['en_US', 'en']
04-07 10:49 INFO   root: CD menu finished
04-07 10:49 INFO   root: Already installed, running the uninstaller...
04-07 10:49 INFO   root: Running the uninstaller...
04-07 10:49 INFO   CommonBackend: This is the uninstaller running
04-07 10:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\translations, languages=['en_US', 'en']
04-07 10:50 INFO   root: Received settings
04-07 10:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\translations, languages=['en_US', 'en']
04-07 10:50 DEBUG  TaskList: # Running tasklist...
04-07 10:50 DEBUG  TaskList: ## Running Backup ISO...
04-07 10:50 DEBUG  TaskList: ## Finished Backup ISO
04-07 10:50 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 10:50 ERROR  WindowsBackend: Cannot find bcdedit
04-07 10:50 DEBUG  WindowsBackend: undo_bootini C:
04-07 10:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 86575.5703125 mb free ntfs)
04-07 10:50 DEBUG  WindowsBackend: undo_bootini D:
04-07 10:50 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112502.550781 mb free ntfs)
04-07 10:50 DEBUG  WindowsBackend: undo_bootini I:
04-07 10:50 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 1164.0546875 mb free fat32)
04-07 10:50 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 10:50 DEBUG  TaskList: ## Running Remove target dir...
04-07 10:50 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 10:50 DEBUG  TaskList: ## Finished Remove target dir
04-07 10:50 DEBUG  TaskList: ## Running Remove registry key...
04-07 10:50 DEBUG  TaskList: ## Finished Remove registry key
04-07 10:50 DEBUG  TaskList: # Finished tasklist
04-07 10:50 INFO   root: Almost finished uninstalling
04-07 10:50 INFO   root: Finished uninstallation
04-07 10:50 DEBUG  CommonBackend: Fetching basic info...
04-07 10:50 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 10:50 DEBUG  CommonBackend: platform=win32
04-07 10:50 DEBUG  CommonBackend: osname=nt
04-07 10:50 DEBUG  WindowsBackend: arch=i386
04-07 10:50 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\data\isolist.ini
04-07 10:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 10:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 10:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 10:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 10:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 10:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 10:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 10:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 10:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 10:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 10:50 DEBUG  WindowsBackend: Fetching host info...
04-07 10:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 10:50 DEBUG  WindowsBackend: windows version=xp
04-07 10:50 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 10:50 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 10:50 DEBUG  WindowsBackend: windows_build=2600
04-07 10:50 DEBUG  WindowsBackend: gmt=2
04-07 10:50 DEBUG  WindowsBackend: country=US
04-07 10:50 DEBUG  WindowsBackend: timezone=America/New_York
04-07 10:50 DEBUG  WindowsBackend: windows_username=Sylar
04-07 10:50 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 10:50 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 10:50 DEBUG  WindowsBackend: windows_language_code=1033
04-07 10:50 DEBUG  WindowsBackend: windows_language=English
04-07 10:50 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 10:50 DEBUG  WindowsBackend: bootloader=xp
04-07 10:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87246.3359375 mb free ntfs)
04-07 10:50 DEBUG  WindowsBackend: drive=Drive(C: hd 87246.3359375 mb free ntfs)
04-07 10:50 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 10:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 10:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 10:50 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 10:50 DEBUG  WindowsBackend: uninstaller_path=None
04-07 10:50 DEBUG  WindowsBackend: previous_target_dir=None
04-07 10:50 DEBUG  WindowsBackend: previous_distro_name=None
04-07 10:50 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 10:50 DEBUG  WindowsBackend: keyboard_layout=us
04-07 10:50 DEBUG  WindowsBackend: keyboard_variant=
04-07 10:50 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 10:50 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 10:50 DEBUG  CommonBackend: Searching for local CDs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 10:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 10:50 DEBUG  Distro: wrong arch: i386 != amd64
04-07 10:50 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 10:50 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 10:50 INFO   root: Running the CD boot helper...
04-07 10:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\translations, languages=['en_US', 'en']
04-07 10:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\translations, languages=['en_US', 'en']
04-07 10:50 INFO   root: CD boot helper confirmed
04-07 10:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\translations, languages=['en_US', 'en']
04-07 10:50 DEBUG  TaskList: # Running tasklist...
04-07 10:50 DEBUG  TaskList: ## Running select_target_dir...
04-07 10:50 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 10:50 DEBUG  TaskList: ## Finished select_target_dir
04-07 10:50 DEBUG  TaskList: ## Running create_dir_structure...
04-07 10:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 10:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 10:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 10:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 10:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 10:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 10:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 10:50 DEBUG  TaskList: ## Finished create_dir_structure
04-07 10:50 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 10:50 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 10:50 DEBUG  TaskList: ## Running create_uninstaller...
04-07 10:50 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 10:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 10:50 DEBUG  TaskList: ## Finished create_uninstaller
04-07 10:50 DEBUG  TaskList: ## Running copy_installation_files...
04-07 10:50 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 10:50 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\winboot -> C:\ubuntu\winboot
04-07 10:50 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl30.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 10:50 DEBUG  TaskList: ## Finished copy_installation_files
04-07 10:50 DEBUG  TaskList: ## Running use_cd...
04-07 10:50 DEBUG  TaskList: New task copy_file
04-07 10:50 DEBUG  TaskList: ### Running copy_file...
04-07 10:56 DEBUG  TaskList: ### Finished copy_file
04-07 10:56 DEBUG  TaskList: New task check_iso
04-07 10:56 DEBUG  TaskList: ### Running check_iso...
04-07 10:56 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 10:56 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 10:56 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 10:56 DEBUG  TaskList: ### Finished check_iso
04-07 10:56 DEBUG  TaskList: ## Finished use_cd
04-07 10:56 DEBUG  TaskList: ## Running extract_kernel...
04-07 10:56 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 10:56 DEBUG  TaskList: # Cancelling tasklist
04-07 10:56 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 10:56 DEBUG  TaskList: # Finished tasklist
04-07 10:57 INFO   root: === wubi 10.10 rev197 ===
04-07 10:57 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 10:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-07 10:57 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\data
04-07 10:57 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\bin\7z.exe
04-07 10:57 DEBUG  CommonBackend: Fetching basic info...
04-07 10:57 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-07 10:57 DEBUG  CommonBackend: platform=win32
04-07 10:57 DEBUG  CommonBackend: osname=nt
04-07 10:57 DEBUG  CommonBackend: language=en_US
04-07 10:57 DEBUG  CommonBackend: encoding=cp1252
04-07 10:57 DEBUG  WindowsBackend: arch=i386
04-07 10:57 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\data\isolist.ini
04-07 10:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 10:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 10:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 10:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 10:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 10:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 10:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 10:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 10:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 10:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 10:57 DEBUG  WindowsBackend: Fetching host info...
04-07 10:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 10:57 DEBUG  WindowsBackend: windows version=xp
04-07 10:57 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 10:57 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 10:57 DEBUG  WindowsBackend: windows_build=2600
04-07 10:57 DEBUG  WindowsBackend: gmt=2
04-07 10:57 DEBUG  WindowsBackend: country=US
04-07 10:57 DEBUG  WindowsBackend: timezone=America/New_York
04-07 10:57 DEBUG  WindowsBackend: windows_username=Sylar
04-07 10:57 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 10:57 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 10:57 DEBUG  WindowsBackend: windows_language_code=1033
04-07 10:57 DEBUG  WindowsBackend: windows_language=English
04-07 10:57 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 10:57 DEBUG  WindowsBackend: bootloader=xp
04-07 10:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85394.3632813 mb free ntfs)
04-07 10:57 DEBUG  WindowsBackend: drive=Drive(C: hd 85394.3632813 mb free ntfs)
04-07 10:57 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 10:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 10:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 10:57 DEBUG  WindowsBackend: drive=Drive(I: removable 1164.0546875 mb free fat32)
04-07 10:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 10:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 10:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 10:57 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 10:57 DEBUG  WindowsBackend: keyboard_layout=us
04-07 10:57 DEBUG  WindowsBackend: keyboard_variant=
04-07 10:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 10:57 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 10:57 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 10:57 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 10:57 DEBUG  CommonBackend: Searching for local CDs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Ubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Kubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 10:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 10:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 10:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 10:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 10:57 DEBUG  Distro: wrong arch: i386 != amd64
04-07 10:57 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 10:57 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 10:57 INFO   root: Running the uninstaller...
04-07 10:57 INFO   CommonBackend: This is the uninstaller running
04-07 10:57 DEBUG  WindowsFrontend: __init__...
04-07 10:57 DEBUG  WindowsFrontend: on_init...
04-07 10:57 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\translations, languages=['en_US', 'en']
04-07 10:57 INFO   root: Received settings
04-07 10:57 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\translations, languages=['en_US', 'en']
04-07 10:57 DEBUG  TaskList: # Running tasklist...
04-07 10:57 DEBUG  TaskList: ## Running Backup ISO...
04-07 10:57 DEBUG  TaskList: ## Finished Backup ISO
04-07 10:57 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 10:57 ERROR  WindowsBackend: Cannot find bcdedit
04-07 10:57 DEBUG  WindowsBackend: undo_bootini C:
04-07 10:57 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 85394.3632813 mb free ntfs)
04-07 10:57 DEBUG  WindowsBackend: undo_bootini D:
04-07 10:57 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112502.550781 mb free ntfs)
04-07 10:57 DEBUG  WindowsBackend: undo_bootini I:
04-07 10:57 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 1164.0546875 mb free fat32)
04-07 10:57 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 10:57 DEBUG  TaskList: ## Running Remove target dir...
04-07 10:57 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 10:57 DEBUG  TaskList: ## Finished Remove target dir
04-07 10:57 DEBUG  TaskList: ## Running Remove registry key...
04-07 10:57 DEBUG  TaskList: ## Finished Remove registry key
04-07 10:57 DEBUG  TaskList: # Finished tasklist
04-07 10:57 INFO   root: Almost finished uninstalling
04-07 10:57 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl45.tmp\translations, languages=['en_US', 'en']
04-07 10:57 INFO   root: Finished uninstallation
04-07 10:57 DEBUG  root: application.quit
04-07 10:57 DEBUG  WindowsFrontend: frontend.quit
04-07 10:57 DEBUG  WindowsFrontend: frontend.on_quit
04-07 10:57 DEBUG  root: application.on_quit
04-07 10:57 INFO   root: sys.exit
04-07 11:18 INFO   root: === wubi 10.10 rev197 ===
04-07 11:18 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 11:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 11:18 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\data
04-07 11:18 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\bin\7z.exe
04-07 11:18 DEBUG  CommonBackend: Fetching basic info...
04-07 11:18 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 11:18 DEBUG  CommonBackend: platform=win32
04-07 11:18 DEBUG  CommonBackend: osname=nt
04-07 11:18 DEBUG  CommonBackend: language=en_US
04-07 11:18 DEBUG  CommonBackend: encoding=cp1252
04-07 11:18 DEBUG  WindowsBackend: arch=i386
04-07 11:18 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\data\isolist.ini
04-07 11:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 11:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 11:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 11:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 11:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 11:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 11:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 11:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 11:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 11:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 11:18 DEBUG  WindowsBackend: Fetching host info...
04-07 11:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 11:18 DEBUG  WindowsBackend: windows version=xp
04-07 11:18 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 11:18 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 11:18 DEBUG  WindowsBackend: windows_build=2600
04-07 11:18 DEBUG  WindowsBackend: gmt=2
04-07 11:18 DEBUG  WindowsBackend: country=US
04-07 11:18 DEBUG  WindowsBackend: timezone=America/New_York
04-07 11:18 DEBUG  WindowsBackend: windows_username=Sylar
04-07 11:18 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 11:18 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 11:18 DEBUG  WindowsBackend: windows_language_code=1033
04-07 11:18 DEBUG  WindowsBackend: windows_language=English
04-07 11:18 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 11:18 DEBUG  WindowsBackend: bootloader=xp
04-07 11:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87347.1289063 mb free ntfs)
04-07 11:18 DEBUG  WindowsBackend: drive=Drive(C: hd 87347.1289063 mb free ntfs)
04-07 11:18 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 11:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 11:18 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 11:18 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 11:18 DEBUG  WindowsBackend: uninstaller_path=None
04-07 11:18 DEBUG  WindowsBackend: previous_target_dir=None
04-07 11:18 DEBUG  WindowsBackend: previous_distro_name=None
04-07 11:18 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 11:18 DEBUG  WindowsBackend: keyboard_layout=us
04-07 11:18 DEBUG  WindowsBackend: keyboard_variant=
04-07 11:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 11:18 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 11:18 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 11:18 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 11:18 DEBUG  CommonBackend: Searching for local CDs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 11:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 11:18 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 11:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 11:18 DEBUG  Distro: wrong arch: i386 != amd64
04-07 11:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 11:18 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 11:18 INFO   root: Running the CD menu...
04-07 11:18 DEBUG  WindowsFrontend: __init__...
04-07 11:18 DEBUG  WindowsFrontend: on_init...
04-07 11:18 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
04-07 11:18 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
04-07 11:18 INFO   root: CD menu finished
04-07 11:18 INFO   root: Rebooting
04-07 11:18 DEBUG  TaskList: # Running tasklist...
04-07 11:18 DEBUG  TaskList: ## Running reboot...
04-07 11:18 DEBUG  TaskList: ## Finished reboot
04-07 11:18 DEBUG  TaskList: # Finished tasklist
04-07 11:18 DEBUG  root: application.quit
04-07 11:18 DEBUG  WindowsFrontend: frontend.quit
04-07 11:18 DEBUG  WindowsFrontend: frontend.on_quit
04-07 11:18 DEBUG  root: application.on_quit
04-07 11:18 INFO   root: sys.exit
04-07 11:23 INFO   root: === wubi 10.10 rev197 ===
04-07 11:23 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 11:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 11:23 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data
04-07 11:23 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\bin\7z.exe
04-07 11:23 DEBUG  CommonBackend: Fetching basic info...
04-07 11:23 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 11:23 DEBUG  CommonBackend: platform=win32
04-07 11:23 DEBUG  CommonBackend: osname=nt
04-07 11:23 DEBUG  CommonBackend: language=en_US
04-07 11:23 DEBUG  CommonBackend: encoding=cp1252
04-07 11:23 DEBUG  WindowsBackend: arch=i386
04-07 11:23 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\isolist.ini
04-07 11:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 11:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 11:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 11:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 11:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 11:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 11:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 11:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 11:23 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 11:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 11:23 DEBUG  WindowsBackend: Fetching host info...
04-07 11:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 11:23 DEBUG  WindowsBackend: windows version=xp
04-07 11:23 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 11:23 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 11:23 DEBUG  WindowsBackend: windows_build=2600
04-07 11:23 DEBUG  WindowsBackend: gmt=2
04-07 11:23 DEBUG  WindowsBackend: country=US
04-07 11:23 DEBUG  WindowsBackend: timezone=America/New_York
04-07 11:23 DEBUG  WindowsBackend: windows_username=Sylar
04-07 11:23 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 11:23 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 11:23 DEBUG  WindowsBackend: windows_language_code=1033
04-07 11:23 DEBUG  WindowsBackend: windows_language=English
04-07 11:23 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 1500+
04-07 11:23 DEBUG  WindowsBackend: bootloader=xp
04-07 11:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87322.8359375 mb free ntfs)
04-07 11:23 DEBUG  WindowsBackend: drive=Drive(C: hd 87322.8359375 mb free ntfs)
04-07 11:23 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 11:23 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 11:23 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 11:23 DEBUG  WindowsBackend: drive=Drive(I: removable 1178.01953125 mb free fat32)
04-07 11:23 DEBUG  WindowsBackend: uninstaller_path=None
04-07 11:23 DEBUG  WindowsBackend: previous_target_dir=None
04-07 11:23 DEBUG  WindowsBackend: previous_distro_name=None
04-07 11:23 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 11:23 DEBUG  WindowsBackend: keyboard_layout=us
04-07 11:23 DEBUG  WindowsBackend: keyboard_variant=
04-07 11:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 11:23 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 11:23 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 11:23 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 11:23 DEBUG  CommonBackend: Searching for local CDs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 11:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 11:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 11:23 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 11:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 11:23 DEBUG  Distro: wrong arch: i386 != amd64
04-07 11:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 11:23 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 11:23 INFO   root: Running the CD menu...
04-07 11:23 DEBUG  WindowsFrontend: __init__...
04-07 11:23 DEBUG  WindowsFrontend: on_init...
04-07 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 11:23 INFO   root: CD menu finished
04-07 11:23 INFO   root: Running the CD boot helper...
04-07 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 11:23 INFO   root: CD boot helper confirmed
04-07 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 11:23 DEBUG  TaskList: # Running tasklist...
04-07 11:23 DEBUG  TaskList: ## Running select_target_dir...
04-07 11:23 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 11:23 DEBUG  TaskList: ## Finished select_target_dir
04-07 11:23 DEBUG  TaskList: ## Running create_dir_structure...
04-07 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 11:23 DEBUG  TaskList: ## Finished create_dir_structure
04-07 11:23 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 11:23 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 11:23 DEBUG  TaskList: ## Running create_uninstaller...
04-07 11:23 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 11:23 DEBUG  TaskList: ## Finished create_uninstaller
04-07 11:23 DEBUG  TaskList: ## Running copy_installation_files...
04-07 11:23 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 11:23 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\winboot -> C:\ubuntu\winboot
04-07 11:23 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 11:23 DEBUG  TaskList: ## Finished copy_installation_files
04-07 11:23 DEBUG  TaskList: ## Running use_cd...
04-07 11:23 DEBUG  TaskList: New task copy_file
04-07 11:23 DEBUG  TaskList: ### Running copy_file...
04-07 11:30 DEBUG  TaskList: ### Finished copy_file
04-07 11:30 DEBUG  TaskList: New task check_iso
04-07 11:30 DEBUG  TaskList: ### Running check_iso...
04-07 11:30 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 11:30 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 11:30 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 11:30 DEBUG  TaskList: ### Finished check_iso
04-07 11:30 DEBUG  TaskList: ## Finished use_cd
04-07 11:30 DEBUG  TaskList: ## Running extract_kernel...
04-07 11:30 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 11:30 DEBUG  TaskList: # Cancelling tasklist
04-07 11:30 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 11:30 DEBUG  TaskList: # Finished tasklist
04-07 12:33 INFO   root: === wubi 10.10 rev197 ===
04-07 12:33 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 12:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 12:33 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\data
04-07 12:33 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\bin\7z.exe
04-07 12:33 DEBUG  CommonBackend: Fetching basic info...
04-07 12:33 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 12:33 DEBUG  CommonBackend: platform=win32
04-07 12:33 DEBUG  CommonBackend: osname=nt
04-07 12:33 DEBUG  CommonBackend: language=en_US
04-07 12:33 DEBUG  CommonBackend: encoding=cp1252
04-07 12:33 DEBUG  WindowsBackend: arch=i386
04-07 12:33 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\data\isolist.ini
04-07 12:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 12:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 12:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 12:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 12:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 12:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 12:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 12:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 12:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 12:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 12:33 DEBUG  WindowsBackend: Fetching host info...
04-07 12:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 12:33 DEBUG  WindowsBackend: windows version=xp
04-07 12:33 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 12:33 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 12:33 DEBUG  WindowsBackend: windows_build=2600
04-07 12:33 DEBUG  WindowsBackend: gmt=2
04-07 12:33 DEBUG  WindowsBackend: country=US
04-07 12:33 DEBUG  WindowsBackend: timezone=America/New_York
04-07 12:33 DEBUG  WindowsBackend: windows_username=Sylar
04-07 12:33 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 12:33 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 12:33 DEBUG  WindowsBackend: windows_language_code=1033
04-07 12:33 DEBUG  WindowsBackend: windows_language=English
04-07 12:33 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 12:33 DEBUG  WindowsBackend: bootloader=xp
04-07 12:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85421.7617188 mb free ntfs)
04-07 12:33 DEBUG  WindowsBackend: drive=Drive(C: hd 85421.7617188 mb free ntfs)
04-07 12:33 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 12:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 12:33 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 12:33 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 12:33 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 12:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 12:33 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 12:33 DEBUG  WindowsBackend: keyboard_layout=us
04-07 12:33 DEBUG  WindowsBackend: keyboard_variant=
04-07 12:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 12:33 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 12:33 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 12:33 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 12:33 DEBUG  CommonBackend: Searching for local CDs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Ubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Kubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 12:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 12:33 DEBUG  Distro: wrong arch: i386 != amd64
04-07 12:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:33 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 12:33 INFO   root: Running the CD menu...
04-07 12:33 DEBUG  WindowsFrontend: __init__...
04-07 12:33 DEBUG  WindowsFrontend: on_init...
04-07 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\translations, languages=['en_US', 'en']
04-07 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl2E.tmp\translations, languages=['en_US', 'en']
04-07 12:33 INFO   root: CD menu finished
04-07 12:33 INFO   root: Rebooting
04-07 12:33 DEBUG  TaskList: # Running tasklist...
04-07 12:33 DEBUG  TaskList: ## Running reboot...
04-07 12:33 DEBUG  TaskList: ## Finished reboot
04-07 12:33 DEBUG  TaskList: # Finished tasklist
04-07 12:33 DEBUG  root: application.quit
04-07 12:33 DEBUG  WindowsFrontend: frontend.quit
04-07 12:33 DEBUG  WindowsFrontend: frontend.on_quit
04-07 12:33 DEBUG  root: application.on_quit
04-07 12:33 INFO   root: sys.exit
04-07 12:36 INFO   root: === wubi 10.10 rev197 ===
04-07 12:36 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 12:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 12:36 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\data
04-07 12:36 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\bin\7z.exe
04-07 12:36 DEBUG  CommonBackend: Fetching basic info...
04-07 12:36 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 12:36 DEBUG  CommonBackend: platform=win32
04-07 12:36 DEBUG  CommonBackend: osname=nt
04-07 12:36 DEBUG  CommonBackend: language=en_US
04-07 12:36 DEBUG  CommonBackend: encoding=cp1252
04-07 12:36 DEBUG  WindowsBackend: arch=i386
04-07 12:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
04-07 12:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 12:36 DEBUG  WindowsBackend: Fetching host info...
04-07 12:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 12:36 DEBUG  WindowsBackend: windows version=xp
04-07 12:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 12:36 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 12:36 DEBUG  WindowsBackend: windows_build=2600
04-07 12:36 DEBUG  WindowsBackend: gmt=2
04-07 12:36 DEBUG  WindowsBackend: country=US
04-07 12:36 DEBUG  WindowsBackend: timezone=America/New_York
04-07 12:36 DEBUG  WindowsBackend: windows_username=Sylar
04-07 12:36 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 12:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 12:36 DEBUG  WindowsBackend: windows_language_code=1033
04-07 12:36 DEBUG  WindowsBackend: windows_language=English
04-07 12:36 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 12:36 DEBUG  WindowsBackend: bootloader=xp
04-07 12:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85412.6601563 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(C: hd 85412.6601563 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 12:36 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 12:36 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 12:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 12:36 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 12:36 DEBUG  WindowsBackend: keyboard_layout=us
04-07 12:36 DEBUG  WindowsBackend: keyboard_variant=
04-07 12:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 12:36 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 12:36 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 12:36 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 12:36 DEBUG  CommonBackend: Searching for local CDs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 12:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 12:36 DEBUG  Distro: wrong arch: i386 != amd64
04-07 12:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:36 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 12:36 INFO   root: Running the CD menu...
04-07 12:36 DEBUG  WindowsFrontend: __init__...
04-07 12:36 DEBUG  WindowsFrontend: on_init...
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   root: CD menu finished
04-07 12:36 INFO   root: Already installed, running the uninstaller...
04-07 12:36 INFO   root: Running the uninstaller...
04-07 12:36 INFO   CommonBackend: This is the uninstaller running
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   root: Received settings
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 12:36 DEBUG  TaskList: # Running tasklist...
04-07 12:36 DEBUG  TaskList: ## Running Backup ISO...
04-07 12:36 DEBUG  TaskList: ## Finished Backup ISO
04-07 12:36 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 12:36 ERROR  WindowsBackend: Cannot find bcdedit
04-07 12:36 DEBUG  WindowsBackend: undo_bootini C:
04-07 12:36 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 85412.6601563 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: undo_bootini D:
04-07 12:36 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: undo_bootini I:
04-07 12:36 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 1179.046875 mb free fat32)
04-07 12:36 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 12:36 DEBUG  TaskList: ## Running Remove target dir...
04-07 12:36 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 12:36 DEBUG  TaskList: ## Finished Remove target dir
04-07 12:36 DEBUG  TaskList: ## Running Remove registry key...
04-07 12:36 DEBUG  TaskList: ## Finished Remove registry key
04-07 12:36 DEBUG  TaskList: # Finished tasklist
04-07 12:36 INFO   root: Almost finished uninstalling
04-07 12:36 INFO   root: Finished uninstallation
04-07 12:36 DEBUG  CommonBackend: Fetching basic info...
04-07 12:36 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 12:36 DEBUG  CommonBackend: platform=win32
04-07 12:36 DEBUG  CommonBackend: osname=nt
04-07 12:36 DEBUG  WindowsBackend: arch=i386
04-07 12:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
04-07 12:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 12:36 DEBUG  WindowsBackend: Fetching host info...
04-07 12:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 12:36 DEBUG  WindowsBackend: windows version=xp
04-07 12:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 12:36 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 12:36 DEBUG  WindowsBackend: windows_build=2600
04-07 12:36 DEBUG  WindowsBackend: gmt=2
04-07 12:36 DEBUG  WindowsBackend: country=US
04-07 12:36 DEBUG  WindowsBackend: timezone=America/New_York
04-07 12:36 DEBUG  WindowsBackend: windows_username=Sylar
04-07 12:36 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 12:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 12:36 DEBUG  WindowsBackend: windows_language_code=1033
04-07 12:36 DEBUG  WindowsBackend: windows_language=English
04-07 12:36 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 12:36 DEBUG  WindowsBackend: bootloader=xp
04-07 12:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87288.59375 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(C: hd 87288.59375 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 12:36 DEBUG  WindowsBackend: uninstaller_path=None
04-07 12:36 DEBUG  WindowsBackend: previous_target_dir=None
04-07 12:36 DEBUG  WindowsBackend: previous_distro_name=None
04-07 12:36 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 12:36 DEBUG  WindowsBackend: keyboard_layout=us
04-07 12:36 DEBUG  WindowsBackend: keyboard_variant=
04-07 12:36 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 12:36 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 12:36 DEBUG  CommonBackend: Searching for local CDs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro: wrong arch: i386 != amd64
04-07 12:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:36 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 12:36 INFO   root: Running the installer...
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   WindowsFrontend: Operation cancelled
04-07 12:36 DEBUG  WindowsFrontend: frontend.quit
04-07 12:36 DEBUG  WindowsFrontend: frontend.on_quit
04-07 12:36 DEBUG  root: application.on_quit
04-07 12:36 INFO   root: sys.exit
04-07 12:36 INFO   root: === wubi 10.10 rev197 ===
04-07 12:36 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 12:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 12:36 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data
04-07 12:36 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\bin\7z.exe
04-07 12:36 DEBUG  CommonBackend: Fetching basic info...
04-07 12:36 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 12:36 DEBUG  CommonBackend: platform=win32
04-07 12:36 DEBUG  CommonBackend: osname=nt
04-07 12:36 DEBUG  CommonBackend: language=en_US
04-07 12:36 DEBUG  CommonBackend: encoding=cp1252
04-07 12:36 DEBUG  WindowsBackend: arch=i386
04-07 12:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data\isolist.ini
04-07 12:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 12:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 12:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 12:36 DEBUG  WindowsBackend: Fetching host info...
04-07 12:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 12:36 DEBUG  WindowsBackend: windows version=xp
04-07 12:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 12:36 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 12:36 DEBUG  WindowsBackend: windows_build=2600
04-07 12:36 DEBUG  WindowsBackend: gmt=2
04-07 12:36 DEBUG  WindowsBackend: country=US
04-07 12:36 DEBUG  WindowsBackend: timezone=America/New_York
04-07 12:36 DEBUG  WindowsBackend: windows_username=Sylar
04-07 12:36 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 12:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 12:36 DEBUG  WindowsBackend: windows_language_code=1033
04-07 12:36 DEBUG  WindowsBackend: windows_language=English
04-07 12:36 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 12:36 DEBUG  WindowsBackend: bootloader=xp
04-07 12:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87288.5820313 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(C: hd 87288.5820313 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 12:36 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 12:36 DEBUG  WindowsBackend: uninstaller_path=None
04-07 12:36 DEBUG  WindowsBackend: previous_target_dir=None
04-07 12:36 DEBUG  WindowsBackend: previous_distro_name=None
04-07 12:36 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 12:36 DEBUG  WindowsBackend: keyboard_layout=us
04-07 12:36 DEBUG  WindowsBackend: keyboard_variant=
04-07 12:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 12:36 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 12:36 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 12:36 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 12:36 DEBUG  CommonBackend: Searching for local CDs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:36 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 12:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 12:36 DEBUG  Distro: wrong arch: i386 != amd64
04-07 12:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:36 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 12:36 INFO   root: Running the CD menu...
04-07 12:36 DEBUG  WindowsFrontend: __init__...
04-07 12:36 DEBUG  WindowsFrontend: on_init...
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   root: CD menu finished
04-07 12:36 INFO   root: Running the CD boot helper...
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 12:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 12:37 INFO   WindowsFrontend: Operation cancelled
04-07 12:37 DEBUG  WindowsFrontend: frontend.quit
04-07 12:37 DEBUG  WindowsFrontend: frontend.on_quit
04-07 12:37 DEBUG  root: application.on_quit
04-07 12:37 INFO   root: sys.exit
04-07 12:37 INFO   root: === wubi 10.10 rev197 ===
04-07 12:37 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 12:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 12:37 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\data
04-07 12:37 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\bin\7z.exe
04-07 12:37 DEBUG  CommonBackend: Fetching basic info...
04-07 12:37 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 12:37 DEBUG  CommonBackend: platform=win32
04-07 12:37 DEBUG  CommonBackend: osname=nt
04-07 12:37 DEBUG  CommonBackend: language=en_US
04-07 12:37 DEBUG  CommonBackend: encoding=cp1252
04-07 12:37 DEBUG  WindowsBackend: arch=i386
04-07 12:37 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\data\isolist.ini
04-07 12:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 12:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 12:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 12:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 12:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 12:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 12:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 12:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 12:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 12:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 12:37 DEBUG  WindowsBackend: Fetching host info...
04-07 12:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 12:37 DEBUG  WindowsBackend: windows version=xp
04-07 12:37 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 12:37 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 12:37 DEBUG  WindowsBackend: windows_build=2600
04-07 12:37 DEBUG  WindowsBackend: gmt=2
04-07 12:37 DEBUG  WindowsBackend: country=US
04-07 12:37 DEBUG  WindowsBackend: timezone=America/New_York
04-07 12:37 DEBUG  WindowsBackend: windows_username=Sylar
04-07 12:37 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 12:37 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 12:37 DEBUG  WindowsBackend: windows_language_code=1033
04-07 12:37 DEBUG  WindowsBackend: windows_language=English
04-07 12:37 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 12:37 DEBUG  WindowsBackend: bootloader=xp
04-07 12:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87288.546875 mb free ntfs)
04-07 12:37 DEBUG  WindowsBackend: drive=Drive(C: hd 87288.546875 mb free ntfs)
04-07 12:37 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 12:37 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 12:37 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 12:37 DEBUG  WindowsBackend: uninstaller_path=None
04-07 12:37 DEBUG  WindowsBackend: previous_target_dir=None
04-07 12:37 DEBUG  WindowsBackend: previous_distro_name=None
04-07 12:37 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 12:37 DEBUG  WindowsBackend: keyboard_layout=us
04-07 12:37 DEBUG  WindowsBackend: keyboard_variant=
04-07 12:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 12:37 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 12:37 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 12:37 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 12:37 DEBUG  CommonBackend: Searching for local CDs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:37 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 12:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 12:37 DEBUG  Distro: wrong arch: i386 != amd64
04-07 12:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:37 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 12:37 INFO   root: Running the CD menu...
04-07 12:37 DEBUG  WindowsFrontend: __init__...
04-07 12:37 DEBUG  WindowsFrontend: on_init...
04-07 12:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
04-07 12:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
04-07 12:37 INFO   root: CD menu finished
04-07 12:37 INFO   root: Running the CD boot helper...
04-07 12:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
04-07 12:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
04-07 12:37 INFO   root: CD boot helper confirmed
04-07 12:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
04-07 12:37 DEBUG  TaskList: # Running tasklist...
04-07 12:37 DEBUG  TaskList: ## Running select_target_dir...
04-07 12:37 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 12:37 DEBUG  TaskList: ## Finished select_target_dir
04-07 12:37 DEBUG  TaskList: ## Running create_dir_structure...
04-07 12:37 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 12:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 12:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 12:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 12:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 12:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 12:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 12:37 DEBUG  TaskList: ## Finished create_dir_structure
04-07 12:37 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 12:37 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 12:37 DEBUG  TaskList: ## Running create_uninstaller...
04-07 12:37 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 12:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 12:37 DEBUG  TaskList: ## Finished create_uninstaller
04-07 12:37 DEBUG  TaskList: ## Running copy_installation_files...
04-07 12:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 12:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\winboot -> C:\ubuntu\winboot
04-07 12:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 12:37 DEBUG  TaskList: ## Finished copy_installation_files
04-07 12:37 DEBUG  TaskList: ## Running use_cd...
04-07 12:37 DEBUG  TaskList: New task copy_file
04-07 12:37 DEBUG  TaskList: ### Running copy_file...
04-07 12:43 DEBUG  TaskList: ### Finished copy_file
04-07 12:43 DEBUG  TaskList: New task check_iso
04-07 12:43 DEBUG  TaskList: ### Running check_iso...
04-07 12:43 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 12:43 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 12:43 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 12:43 DEBUG  TaskList: ### Finished check_iso
04-07 12:43 DEBUG  TaskList: ## Finished use_cd
04-07 12:43 DEBUG  TaskList: ## Running extract_kernel...
04-07 12:43 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 12:43 DEBUG  TaskList: # Cancelling tasklist
04-07 12:43 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 12:43 DEBUG  TaskList: # Finished tasklist
04-07 12:49 INFO   root: === wubi 10.10 rev197 ===
04-07 12:49 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 12:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 12:49 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\data
04-07 12:49 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\bin\7z.exe
04-07 12:49 DEBUG  CommonBackend: Fetching basic info...
04-07 12:49 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 12:49 DEBUG  CommonBackend: platform=win32
04-07 12:49 DEBUG  CommonBackend: osname=nt
04-07 12:49 DEBUG  CommonBackend: language=en_US
04-07 12:49 DEBUG  CommonBackend: encoding=cp1252
04-07 12:49 DEBUG  WindowsBackend: arch=i386
04-07 12:49 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\data\isolist.ini
04-07 12:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 12:49 DEBUG  WindowsBackend: Fetching host info...
04-07 12:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 12:49 DEBUG  WindowsBackend: windows version=xp
04-07 12:49 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 12:49 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 12:49 DEBUG  WindowsBackend: windows_build=2600
04-07 12:49 DEBUG  WindowsBackend: gmt=2
04-07 12:49 DEBUG  WindowsBackend: country=US
04-07 12:49 DEBUG  WindowsBackend: timezone=America/New_York
04-07 12:49 DEBUG  WindowsBackend: windows_username=Sylar
04-07 12:49 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 12:49 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 12:49 DEBUG  WindowsBackend: windows_language_code=1033
04-07 12:49 DEBUG  WindowsBackend: windows_language=English
04-07 12:49 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 12:49 DEBUG  WindowsBackend: bootloader=xp
04-07 12:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 86054.859375 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(C: hd 86054.859375 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 12:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 12:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 12:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 12:49 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 12:49 DEBUG  WindowsBackend: keyboard_layout=us
04-07 12:49 DEBUG  WindowsBackend: keyboard_variant=
04-07 12:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 12:49 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 12:49 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 12:49 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 12:49 DEBUG  CommonBackend: Searching for local CDs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 12:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 12:49 DEBUG  Distro: wrong arch: i386 != amd64
04-07 12:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:49 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 12:49 INFO   root: Running the CD menu...
04-07 12:49 DEBUG  WindowsFrontend: __init__...
04-07 12:49 DEBUG  WindowsFrontend: on_init...
04-07 12:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
04-07 12:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
04-07 12:49 INFO   root: CD menu finished
04-07 12:49 INFO   root: Already installed, running the uninstaller...
04-07 12:49 INFO   root: Running the uninstaller...
04-07 12:49 INFO   CommonBackend: This is the uninstaller running
04-07 12:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
04-07 12:49 INFO   root: Received settings
04-07 12:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
04-07 12:49 DEBUG  TaskList: # Running tasklist...
04-07 12:49 DEBUG  TaskList: ## Running Backup ISO...
04-07 12:49 DEBUG  TaskList: ## Finished Backup ISO
04-07 12:49 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 12:49 ERROR  WindowsBackend: Cannot find bcdedit
04-07 12:49 DEBUG  WindowsBackend: undo_bootini C:
04-07 12:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 86054.859375 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: undo_bootini D:
04-07 12:49 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: undo_bootini I:
04-07 12:49 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 1179.046875 mb free fat32)
04-07 12:49 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 12:49 DEBUG  TaskList: ## Running Remove target dir...
04-07 12:49 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 12:49 DEBUG  TaskList: ## Finished Remove target dir
04-07 12:49 DEBUG  TaskList: ## Running Remove registry key...
04-07 12:49 DEBUG  TaskList: ## Finished Remove registry key
04-07 12:49 DEBUG  TaskList: # Finished tasklist
04-07 12:49 INFO   root: Almost finished uninstalling
04-07 12:49 INFO   root: Finished uninstallation
04-07 12:49 DEBUG  CommonBackend: Fetching basic info...
04-07 12:49 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 12:49 DEBUG  CommonBackend: platform=win32
04-07 12:49 DEBUG  CommonBackend: osname=nt
04-07 12:49 DEBUG  WindowsBackend: arch=i386
04-07 12:49 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\data\isolist.ini
04-07 12:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 12:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 12:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 12:49 DEBUG  WindowsBackend: Fetching host info...
04-07 12:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 12:49 DEBUG  WindowsBackend: windows version=xp
04-07 12:49 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 12:49 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 12:49 DEBUG  WindowsBackend: windows_build=2600
04-07 12:49 DEBUG  WindowsBackend: gmt=2
04-07 12:49 DEBUG  WindowsBackend: country=US
04-07 12:49 DEBUG  WindowsBackend: timezone=America/New_York
04-07 12:49 DEBUG  WindowsBackend: windows_username=Sylar
04-07 12:49 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 12:49 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 12:49 DEBUG  WindowsBackend: windows_language_code=1033
04-07 12:49 DEBUG  WindowsBackend: windows_language=English
04-07 12:49 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 12:49 DEBUG  WindowsBackend: bootloader=xp
04-07 12:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87928.6015625 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(C: hd 87928.6015625 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(D: hd 112502.550781 mb free ntfs)
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 12:49 DEBUG  WindowsBackend: drive=Drive(I: removable 1179.046875 mb free fat32)
04-07 12:49 DEBUG  WindowsBackend: uninstaller_path=None
04-07 12:49 DEBUG  WindowsBackend: previous_target_dir=None
04-07 12:49 DEBUG  WindowsBackend: previous_distro_name=None
04-07 12:49 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 12:49 DEBUG  WindowsBackend: keyboard_layout=us
04-07 12:49 DEBUG  WindowsBackend: keyboard_variant=
04-07 12:49 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 12:49 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 12:49 DEBUG  CommonBackend: Searching for local CDs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 12:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 12:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:49 DEBUG  Distro: wrong arch: i386 != amd64
04-07 12:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 12:49 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 12:49 INFO   root: Running the CD boot helper...
04-07 12:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
04-07 12:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
04-07 12:49 INFO   root: CD boot helper confirmed
04-07 12:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
04-07 12:49 DEBUG  TaskList: # Running tasklist...
04-07 12:49 DEBUG  TaskList: ## Running select_target_dir...
04-07 12:49 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 12:49 DEBUG  TaskList: ## Finished select_target_dir
04-07 12:49 DEBUG  TaskList: ## Running create_dir_structure...
04-07 12:49 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 12:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 12:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 12:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 12:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 12:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 12:49 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 12:49 DEBUG  TaskList: ## Finished create_dir_structure
04-07 12:49 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 12:49 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 12:49 DEBUG  TaskList: ## Running create_uninstaller...
04-07 12:49 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 12:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 12:49 DEBUG  TaskList: ## Finished create_uninstaller
04-07 12:49 DEBUG  TaskList: ## Running copy_installation_files...
04-07 12:49 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 12:49 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\winboot -> C:\ubuntu\winboot
04-07 12:49 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl21.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 12:49 DEBUG  TaskList: ## Finished copy_installation_files
04-07 12:49 DEBUG  TaskList: ## Running use_cd...
04-07 12:49 DEBUG  TaskList: New task copy_file
04-07 12:49 DEBUG  TaskList: ### Running copy_file...
04-07 12:54 DEBUG  TaskList: ### Finished copy_file
04-07 12:54 DEBUG  TaskList: New task check_iso
04-07 12:54 DEBUG  TaskList: ### Running check_iso...
04-07 12:54 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 12:54 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 12:54 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 12:54 DEBUG  TaskList: ### Finished check_iso
04-07 12:54 DEBUG  TaskList: ## Finished use_cd
04-07 12:54 DEBUG  TaskList: ## Running extract_kernel...
04-07 12:54 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 12:54 DEBUG  TaskList: # Cancelling tasklist
04-07 12:54 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 12:54 DEBUG  TaskList: # Finished tasklist
04-07 15:49 INFO   root: === wubi 10.10 rev197 ===
04-07 15:49 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 15:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 15:49 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\data
04-07 15:49 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\bin\7z.exe
04-07 15:49 DEBUG  CommonBackend: Fetching basic info...
04-07 15:49 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 15:49 DEBUG  CommonBackend: platform=win32
04-07 15:49 DEBUG  CommonBackend: osname=nt
04-07 15:49 DEBUG  CommonBackend: language=en_US
04-07 15:49 DEBUG  CommonBackend: encoding=cp1252
04-07 15:49 DEBUG  WindowsBackend: arch=i386
04-07 15:49 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\data\isolist.ini
04-07 15:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 15:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 15:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 15:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 15:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 15:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 15:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 15:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 15:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 15:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 15:49 DEBUG  WindowsBackend: Fetching host info...
04-07 15:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 15:49 DEBUG  WindowsBackend: windows version=xp
04-07 15:49 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 15:49 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 15:49 DEBUG  WindowsBackend: windows_build=2600
04-07 15:49 DEBUG  WindowsBackend: gmt=2
04-07 15:49 DEBUG  WindowsBackend: country=US
04-07 15:49 DEBUG  WindowsBackend: timezone=America/New_York
04-07 15:49 DEBUG  WindowsBackend: windows_username=Sylar
04-07 15:49 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 15:49 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 15:49 DEBUG  WindowsBackend: windows_language_code=1033
04-07 15:49 DEBUG  WindowsBackend: windows_language=English
04-07 15:49 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 15:49 DEBUG  WindowsBackend: bootloader=xp
04-07 15:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81377.8085938 mb free ntfs)
04-07 15:49 DEBUG  WindowsBackend: drive=Drive(C: hd 81377.8085938 mb free ntfs)
04-07 15:49 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.453125 mb free ntfs)
04-07 15:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 15:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 15:49 DEBUG  WindowsBackend: drive=Drive(I: removable 482.55859375 mb free fat32)
04-07 15:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 15:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 15:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 15:49 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 15:49 DEBUG  WindowsBackend: keyboard_layout=us
04-07 15:49 DEBUG  WindowsBackend: keyboard_variant=
04-07 15:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 15:49 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 15:49 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 15:49 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 15:49 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:49 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu-10.10-desktop-i386.iso
04-07 15:49 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:49 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:49 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:49 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu-10.10-desktop-i386.iso
04-07 15:49 DEBUG  CommonBackend: Searching for local CDs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Ubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Kubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:49 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:49 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:49 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 15:49 INFO   root: Running the CD menu...
04-07 15:49 DEBUG  WindowsFrontend: __init__...
04-07 15:49 DEBUG  WindowsFrontend: on_init...
04-07 15:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\translations, languages=['en_US', 'en']
04-07 15:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl5A.tmp\translations, languages=['en_US', 'en']
04-07 15:49 INFO   root: CD menu finished
04-07 15:49 INFO   root: Rebooting
04-07 15:49 DEBUG  TaskList: # Running tasklist...
04-07 15:49 DEBUG  TaskList: ## Running reboot...
04-07 15:49 DEBUG  TaskList: ## Finished reboot
04-07 15:49 DEBUG  TaskList: # Finished tasklist
04-07 15:49 DEBUG  root: application.quit
04-07 15:49 DEBUG  WindowsFrontend: frontend.quit
04-07 15:49 DEBUG  WindowsFrontend: frontend.on_quit
04-07 15:49 DEBUG  root: application.on_quit
04-07 15:49 INFO   root: sys.exit
04-07 15:52 INFO   root: === wubi 10.10 rev197 ===
04-07 15:52 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 15:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 15:52 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data
04-07 15:52 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\bin\7z.exe
04-07 15:52 DEBUG  CommonBackend: Fetching basic info...
04-07 15:52 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 15:52 DEBUG  CommonBackend: platform=win32
04-07 15:52 DEBUG  CommonBackend: osname=nt
04-07 15:52 DEBUG  CommonBackend: language=en_US
04-07 15:52 DEBUG  CommonBackend: encoding=cp1252
04-07 15:52 DEBUG  WindowsBackend: arch=i386
04-07 15:52 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\isolist.ini
04-07 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 15:52 DEBUG  WindowsBackend: Fetching host info...
04-07 15:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 15:52 DEBUG  WindowsBackend: windows version=xp
04-07 15:52 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 15:52 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 15:52 DEBUG  WindowsBackend: windows_build=2600
04-07 15:52 DEBUG  WindowsBackend: gmt=2
04-07 15:52 DEBUG  WindowsBackend: country=US
04-07 15:52 DEBUG  WindowsBackend: timezone=America/New_York
04-07 15:52 DEBUG  WindowsBackend: windows_username=Sylar
04-07 15:52 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 15:52 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 15:52 DEBUG  WindowsBackend: windows_language_code=1033
04-07 15:52 DEBUG  WindowsBackend: windows_language=English
04-07 15:52 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 15:52 DEBUG  WindowsBackend: bootloader=xp
04-07 15:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81370.9101563 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(C: hd 81370.9101563 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.464844 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(I: removable 482.55859375 mb free fat32)
04-07 15:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 15:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 15:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 15:52 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 15:52 DEBUG  WindowsBackend: keyboard_layout=us
04-07 15:52 DEBUG  WindowsBackend: keyboard_variant=
04-07 15:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 15:52 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 15:52 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 15:52 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 15:52 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:52 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:52 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 DEBUG  CommonBackend: Searching for local CDs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:52 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:52 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 15:52 INFO   root: Running the CD menu...
04-07 15:52 DEBUG  WindowsFrontend: __init__...
04-07 15:52 DEBUG  WindowsFrontend: on_init...
04-07 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 15:52 INFO   root: CD menu finished
04-07 15:52 INFO   root: Already installed, running the uninstaller...
04-07 15:52 INFO   root: Running the uninstaller...
04-07 15:52 INFO   CommonBackend: This is the uninstaller running
04-07 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 15:52 INFO   root: Received settings
04-07 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 15:52 DEBUG  TaskList: # Running tasklist...
04-07 15:52 DEBUG  TaskList: ## Running Backup ISO...
04-07 15:52 DEBUG  TaskList: ## Finished Backup ISO
04-07 15:52 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 15:52 ERROR  WindowsBackend: Cannot find bcdedit
04-07 15:52 DEBUG  WindowsBackend: undo_bootini C:
04-07 15:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 81370.9101563 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: undo_bootini D:
04-07 15:52 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112851.464844 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: undo_bootini I:
04-07 15:52 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 482.55859375 mb free fat32)
04-07 15:52 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 15:52 DEBUG  TaskList: ## Running Remove target dir...
04-07 15:52 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 15:52 DEBUG  TaskList: ## Finished Remove target dir
04-07 15:52 DEBUG  TaskList: ## Running Remove registry key...
04-07 15:52 DEBUG  TaskList: ## Finished Remove registry key
04-07 15:52 DEBUG  TaskList: # Finished tasklist
04-07 15:52 INFO   root: Almost finished uninstalling
04-07 15:52 INFO   root: Finished uninstallation
04-07 15:52 DEBUG  CommonBackend: Fetching basic info...
04-07 15:52 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 15:52 DEBUG  CommonBackend: platform=win32
04-07 15:52 DEBUG  CommonBackend: osname=nt
04-07 15:52 DEBUG  WindowsBackend: arch=i386
04-07 15:52 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\isolist.ini
04-07 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 15:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 15:52 DEBUG  WindowsBackend: Fetching host info...
04-07 15:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 15:52 DEBUG  WindowsBackend: windows version=xp
04-07 15:52 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 15:52 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 15:52 DEBUG  WindowsBackend: windows_build=2600
04-07 15:52 DEBUG  WindowsBackend: gmt=2
04-07 15:52 DEBUG  WindowsBackend: country=US
04-07 15:52 DEBUG  WindowsBackend: timezone=America/New_York
04-07 15:52 DEBUG  WindowsBackend: windows_username=Sylar
04-07 15:52 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 15:52 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 15:52 DEBUG  WindowsBackend: windows_language_code=1033
04-07 15:52 DEBUG  WindowsBackend: windows_language=English
04-07 15:52 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 15:52 DEBUG  WindowsBackend: bootloader=xp
04-07 15:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 83246.4960938 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(C: hd 83246.4960938 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.464844 mb free ntfs)
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 15:52 DEBUG  WindowsBackend: drive=Drive(I: removable 482.55859375 mb free fat32)
04-07 15:52 DEBUG  WindowsBackend: uninstaller_path=None
04-07 15:52 DEBUG  WindowsBackend: previous_target_dir=None
04-07 15:52 DEBUG  WindowsBackend: previous_distro_name=None
04-07 15:52 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 15:52 DEBUG  WindowsBackend: keyboard_layout=us
04-07 15:52 DEBUG  WindowsBackend: keyboard_variant=
04-07 15:52 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 15:52 DEBUG  CommonBackend: Checking pre-specified ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:52 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu-10.10-desktop-i386.iso
04-07 15:52 DEBUG  CommonBackend: Searching for local CDs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:52 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:52 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 15:52 INFO   root: Running the CD boot helper...
04-07 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 15:52 INFO   root: CD boot helper confirmed
04-07 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
04-07 15:52 DEBUG  TaskList: # Running tasklist...
04-07 15:52 DEBUG  TaskList: ## Running select_target_dir...
04-07 15:52 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 15:52 DEBUG  TaskList: ## Finished select_target_dir
04-07 15:52 DEBUG  TaskList: ## Running create_dir_structure...
04-07 15:52 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 15:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 15:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 15:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 15:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 15:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 15:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 15:52 DEBUG  TaskList: ## Finished create_dir_structure
04-07 15:52 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 15:52 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 15:52 DEBUG  TaskList: ## Running create_uninstaller...
04-07 15:52 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 15:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 15:52 DEBUG  TaskList: ## Finished create_uninstaller
04-07 15:52 DEBUG  TaskList: ## Running copy_installation_files...
04-07 15:52 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 15:52 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\winboot -> C:\ubuntu\winboot
04-07 15:52 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl14.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 15:52 DEBUG  TaskList: ## Finished copy_installation_files
04-07 15:52 DEBUG  TaskList: ## Running use_cd...
04-07 15:52 DEBUG  TaskList: New task copy_file
04-07 15:52 DEBUG  TaskList: ### Running copy_file...
04-07 15:58 DEBUG  TaskList: ### Finished copy_file
04-07 15:58 DEBUG  TaskList: New task check_iso
04-07 15:58 DEBUG  TaskList: ### Running check_iso...
04-07 15:58 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 15:58 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 15:58 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 15:58 DEBUG  TaskList: ### Finished check_iso
04-07 15:58 DEBUG  TaskList: ## Finished use_cd
04-07 15:58 DEBUG  TaskList: ## Running extract_kernel...
04-07 15:58 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 15:58 DEBUG  TaskList: # Cancelling tasklist
04-07 15:58 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 15:58 DEBUG  TaskList: # Finished tasklist
04-07 15:58 INFO   root: === wubi 10.10 rev197 ===
04-07 15:58 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 15:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-07 15:58 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data
04-07 15:58 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\bin\7z.exe
04-07 15:58 DEBUG  CommonBackend: Fetching basic info...
04-07 15:58 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-07 15:58 DEBUG  CommonBackend: platform=win32
04-07 15:58 DEBUG  CommonBackend: osname=nt
04-07 15:58 DEBUG  CommonBackend: language=en_US
04-07 15:58 DEBUG  CommonBackend: encoding=cp1252
04-07 15:58 DEBUG  WindowsBackend: arch=i386
04-07 15:58 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\data\isolist.ini
04-07 15:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 15:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 15:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 15:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 15:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 15:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 15:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 15:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 15:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 15:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 15:58 DEBUG  WindowsBackend: Fetching host info...
04-07 15:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 15:58 DEBUG  WindowsBackend: windows version=xp
04-07 15:58 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 15:58 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 15:58 DEBUG  WindowsBackend: windows_build=2600
04-07 15:58 DEBUG  WindowsBackend: gmt=2
04-07 15:58 DEBUG  WindowsBackend: country=US
04-07 15:58 DEBUG  WindowsBackend: timezone=America/New_York
04-07 15:58 DEBUG  WindowsBackend: windows_username=Sylar
04-07 15:58 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 15:58 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 15:58 DEBUG  WindowsBackend: windows_language_code=1033
04-07 15:58 DEBUG  WindowsBackend: windows_language=English
04-07 15:58 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 15:58 DEBUG  WindowsBackend: bootloader=xp
04-07 15:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81360.3515625 mb free ntfs)
04-07 15:58 DEBUG  WindowsBackend: drive=Drive(C: hd 81360.3515625 mb free ntfs)
04-07 15:58 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.464844 mb free ntfs)
04-07 15:58 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 15:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 15:58 DEBUG  WindowsBackend: drive=Drive(I: removable 482.55859375 mb free fat32)
04-07 15:58 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 15:58 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 15:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 15:58 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 15:58 DEBUG  WindowsBackend: keyboard_layout=us
04-07 15:58 DEBUG  WindowsBackend: keyboard_variant=
04-07 15:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 15:58 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 15:58 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 15:58 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 15:58 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:58 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu-10.10-desktop-i386.iso
04-07 15:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:58 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:58 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:58 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu-10.10-desktop-i386.iso
04-07 15:58 DEBUG  CommonBackend: Searching for local CDs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Ubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Kubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:58 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:58 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 15:58 INFO   root: Running the uninstaller...
04-07 15:58 INFO   CommonBackend: This is the uninstaller running
04-07 15:58 DEBUG  WindowsFrontend: __init__...
04-07 15:58 DEBUG  WindowsFrontend: on_init...
04-07 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 15:58 INFO   root: Received settings
04-07 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 15:58 DEBUG  TaskList: # Running tasklist...
04-07 15:58 DEBUG  TaskList: ## Running Backup ISO...
04-07 15:58 DEBUG  TaskList: ## Finished Backup ISO
04-07 15:58 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 15:58 ERROR  WindowsBackend: Cannot find bcdedit
04-07 15:58 DEBUG  WindowsBackend: undo_bootini C:
04-07 15:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 81360.3515625 mb free ntfs)
04-07 15:58 DEBUG  WindowsBackend: undo_bootini D:
04-07 15:58 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112851.464844 mb free ntfs)
04-07 15:58 DEBUG  WindowsBackend: undo_bootini I:
04-07 15:58 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 482.55859375 mb free fat32)
04-07 15:58 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 15:58 DEBUG  TaskList: ## Running Remove target dir...
04-07 15:58 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 15:58 DEBUG  TaskList: ## Finished Remove target dir
04-07 15:58 DEBUG  TaskList: ## Running Remove registry key...
04-07 15:58 DEBUG  TaskList: ## Finished Remove registry key
04-07 15:58 DEBUG  TaskList: # Finished tasklist
04-07 15:58 INFO   root: Almost finished uninstalling
04-07 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl16.tmp\translations, languages=['en_US', 'en']
04-07 15:58 INFO   root: Finished uninstallation
04-07 15:58 DEBUG  root: application.quit
04-07 15:58 DEBUG  WindowsFrontend: frontend.quit
04-07 15:58 DEBUG  WindowsFrontend: frontend.on_quit
04-07 15:58 DEBUG  root: application.on_quit
04-07 15:58 INFO   root: sys.exit
04-07 15:59 INFO   root: === wubi 10.10 rev197 ===
04-07 15:59 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 15:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 15:59 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\data
04-07 15:59 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\bin\7z.exe
04-07 15:59 DEBUG  CommonBackend: Fetching basic info...
04-07 15:59 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 15:59 DEBUG  CommonBackend: platform=win32
04-07 15:59 DEBUG  CommonBackend: osname=nt
04-07 15:59 DEBUG  CommonBackend: language=en_US
04-07 15:59 DEBUG  CommonBackend: encoding=cp1252
04-07 15:59 DEBUG  WindowsBackend: arch=i386
04-07 15:59 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\data\isolist.ini
04-07 15:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 15:59 DEBUG  WindowsBackend: Fetching host info...
04-07 15:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 15:59 DEBUG  WindowsBackend: windows version=xp
04-07 15:59 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 15:59 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 15:59 DEBUG  WindowsBackend: windows_build=2600
04-07 15:59 DEBUG  WindowsBackend: gmt=2
04-07 15:59 DEBUG  WindowsBackend: country=US
04-07 15:59 DEBUG  WindowsBackend: timezone=America/New_York
04-07 15:59 DEBUG  WindowsBackend: windows_username=Sylar
04-07 15:59 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 15:59 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 15:59 DEBUG  WindowsBackend: windows_language_code=1033
04-07 15:59 DEBUG  WindowsBackend: windows_language=English
04-07 15:59 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 15:59 DEBUG  WindowsBackend: bootloader=xp
04-07 15:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 83237.6289063 mb free ntfs)
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(C: hd 83237.6289063 mb free ntfs)
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.464844 mb free ntfs)
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(I: removable 482.55859375 mb free fat32)
04-07 15:59 DEBUG  WindowsBackend: uninstaller_path=None
04-07 15:59 DEBUG  WindowsBackend: previous_target_dir=None
04-07 15:59 DEBUG  WindowsBackend: previous_distro_name=None
04-07 15:59 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 15:59 DEBUG  WindowsBackend: keyboard_layout=us
04-07 15:59 DEBUG  WindowsBackend: keyboard_variant=
04-07 15:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 15:59 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 15:59 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 15:59 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 15:59 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:59 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu-10.10-desktop-i386.iso
04-07 15:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:59 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:59 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu-10.10-desktop-i386.iso
04-07 15:59 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu-10.10-desktop-i386.iso
04-07 15:59 DEBUG  CommonBackend: Searching for local CDs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:59 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:59 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 15:59 INFO   root: Running the CD menu...
04-07 15:59 DEBUG  WindowsFrontend: __init__...
04-07 15:59 DEBUG  WindowsFrontend: on_init...
04-07 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
04-07 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
04-07 15:59 INFO   WindowsFrontend: Operation cancelled
04-07 15:59 DEBUG  WindowsFrontend: frontend.quit
04-07 15:59 DEBUG  WindowsFrontend: frontend.on_quit
04-07 15:59 DEBUG  root: application.on_quit
04-07 15:59 INFO   root: sys.exit
04-07 15:59 INFO   root: === wubi 10.10 rev197 ===
04-07 15:59 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 15:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 15:59 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\data
04-07 15:59 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\bin\7z.exe
04-07 15:59 DEBUG  CommonBackend: Fetching basic info...
04-07 15:59 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 15:59 DEBUG  CommonBackend: platform=win32
04-07 15:59 DEBUG  CommonBackend: osname=nt
04-07 15:59 DEBUG  CommonBackend: language=en_US
04-07 15:59 DEBUG  CommonBackend: encoding=cp1252
04-07 15:59 DEBUG  WindowsBackend: arch=i386
04-07 15:59 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
04-07 15:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 15:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 15:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 15:59 DEBUG  WindowsBackend: Fetching host info...
04-07 15:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 15:59 DEBUG  WindowsBackend: windows version=xp
04-07 15:59 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 15:59 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 15:59 DEBUG  WindowsBackend: windows_build=2600
04-07 15:59 DEBUG  WindowsBackend: gmt=2
04-07 15:59 DEBUG  WindowsBackend: country=US
04-07 15:59 DEBUG  WindowsBackend: timezone=America/New_York
04-07 15:59 DEBUG  WindowsBackend: windows_username=Sylar
04-07 15:59 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 15:59 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 15:59 DEBUG  WindowsBackend: windows_language_code=1033
04-07 15:59 DEBUG  WindowsBackend: windows_language=English
04-07 15:59 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 15:59 DEBUG  WindowsBackend: bootloader=xp
04-07 15:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 83237.46875 mb free ntfs)
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(C: hd 83237.46875 mb free ntfs)
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.464844 mb free ntfs)
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 15:59 DEBUG  WindowsBackend: drive=Drive(I: removable 1175.71484375 mb free fat32)
04-07 15:59 DEBUG  WindowsBackend: uninstaller_path=None
04-07 15:59 DEBUG  WindowsBackend: previous_target_dir=None
04-07 15:59 DEBUG  WindowsBackend: previous_distro_name=None
04-07 15:59 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 15:59 DEBUG  WindowsBackend: keyboard_layout=us
04-07 15:59 DEBUG  WindowsBackend: keyboard_variant=
04-07 15:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 15:59 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 15:59 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 15:59 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 15:59 DEBUG  CommonBackend: Searching for local CDs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 15:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 15:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 15:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 15:59 DEBUG  Distro: wrong arch: i386 != amd64
04-07 15:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 15:59 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 15:59 INFO   root: Running the CD menu...
04-07 15:59 DEBUG  WindowsFrontend: __init__...
04-07 15:59 DEBUG  WindowsFrontend: on_init...
04-07 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
04-07 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
04-07 15:59 INFO   root: CD menu finished
04-07 15:59 INFO   root: Running the CD boot helper...
04-07 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
04-07 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
04-07 16:00 INFO   root: CD boot helper confirmed
04-07 16:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
04-07 16:00 DEBUG  TaskList: # Running tasklist...
04-07 16:00 DEBUG  TaskList: ## Running select_target_dir...
04-07 16:00 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 16:00 DEBUG  TaskList: ## Finished select_target_dir
04-07 16:00 DEBUG  TaskList: ## Running create_dir_structure...
04-07 16:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 16:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 16:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 16:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 16:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 16:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 16:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 16:00 DEBUG  TaskList: ## Finished create_dir_structure
04-07 16:00 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 16:00 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 16:00 DEBUG  TaskList: ## Running create_uninstaller...
04-07 16:00 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 16:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 16:00 DEBUG  TaskList: ## Finished create_uninstaller
04-07 16:00 DEBUG  TaskList: ## Running copy_installation_files...
04-07 16:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 16:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\winboot -> C:\ubuntu\winboot
04-07 16:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl18.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 16:00 DEBUG  TaskList: ## Finished copy_installation_files
04-07 16:00 DEBUG  TaskList: ## Running use_cd...
04-07 16:00 DEBUG  TaskList: New task copy_file
04-07 16:00 DEBUG  TaskList: ### Running copy_file...
04-07 16:05 DEBUG  TaskList: ### Finished copy_file
04-07 16:05 DEBUG  TaskList: New task check_iso
04-07 16:05 DEBUG  TaskList: ### Running check_iso...
04-07 16:05 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 16:05 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 16:05 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 16:05 DEBUG  TaskList: ### Finished check_iso
04-07 16:05 DEBUG  TaskList: ## Finished use_cd
04-07 16:05 DEBUG  TaskList: ## Running extract_kernel...
04-07 16:05 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 16:05 DEBUG  TaskList: # Cancelling tasklist
04-07 16:05 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 16:05 DEBUG  TaskList: # Finished tasklist
04-07 16:06 INFO   root: === wubi 10.10 rev197 ===
04-07 16:06 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 16:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-07 16:06 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\data
04-07 16:06 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\bin\7z.exe
04-07 16:06 DEBUG  CommonBackend: Fetching basic info...
04-07 16:06 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-07 16:06 DEBUG  CommonBackend: platform=win32
04-07 16:06 DEBUG  CommonBackend: osname=nt
04-07 16:06 DEBUG  CommonBackend: language=en_US
04-07 16:06 DEBUG  CommonBackend: encoding=cp1252
04-07 16:06 DEBUG  WindowsBackend: arch=i386
04-07 16:06 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\data\isolist.ini
04-07 16:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 16:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 16:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 16:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 16:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 16:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 16:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 16:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 16:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 16:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 16:06 DEBUG  WindowsBackend: Fetching host info...
04-07 16:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 16:06 DEBUG  WindowsBackend: windows version=xp
04-07 16:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 16:06 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 16:06 DEBUG  WindowsBackend: windows_build=2600
04-07 16:06 DEBUG  WindowsBackend: gmt=2
04-07 16:06 DEBUG  WindowsBackend: country=US
04-07 16:06 DEBUG  WindowsBackend: timezone=America/New_York
04-07 16:06 DEBUG  WindowsBackend: windows_username=Sylar
04-07 16:06 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 16:06 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 16:06 DEBUG  WindowsBackend: windows_language_code=1033
04-07 16:06 DEBUG  WindowsBackend: windows_language=English
04-07 16:06 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 16:06 DEBUG  WindowsBackend: bootloader=xp
04-07 16:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81359.40625 mb free ntfs)
04-07 16:06 DEBUG  WindowsBackend: drive=Drive(C: hd 81359.40625 mb free ntfs)
04-07 16:06 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.464844 mb free ntfs)
04-07 16:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 16:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 16:06 DEBUG  WindowsBackend: drive=Drive(I: removable 1175.71484375 mb free fat32)
04-07 16:06 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-07 16:06 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-07 16:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-07 16:06 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 16:06 DEBUG  WindowsBackend: keyboard_layout=us
04-07 16:06 DEBUG  WindowsBackend: keyboard_variant=
04-07 16:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 16:06 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 16:06 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 16:06 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 16:06 DEBUG  CommonBackend: Searching for local CDs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:06 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 16:06 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 16:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 16:06 DEBUG  Distro: wrong arch: i386 != amd64
04-07 16:06 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 16:06 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 16:06 INFO   root: Running the uninstaller...
04-07 16:06 INFO   CommonBackend: This is the uninstaller running
04-07 16:06 DEBUG  WindowsFrontend: __init__...
04-07 16:06 DEBUG  WindowsFrontend: on_init...
04-07 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en']
04-07 16:06 INFO   root: Received settings
04-07 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en']
04-07 16:06 DEBUG  TaskList: # Running tasklist...
04-07 16:06 DEBUG  TaskList: ## Running Backup ISO...
04-07 16:06 DEBUG  TaskList: ## Finished Backup ISO
04-07 16:06 DEBUG  TaskList: ## Running Remove bootloader entry...
04-07 16:06 ERROR  WindowsBackend: Cannot find bcdedit
04-07 16:06 DEBUG  WindowsBackend: undo_bootini C:
04-07 16:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 81359.40625 mb free ntfs)
04-07 16:06 DEBUG  WindowsBackend: undo_bootini D:
04-07 16:06 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 112851.464844 mb free ntfs)
04-07 16:06 DEBUG  WindowsBackend: undo_bootini I:
04-07 16:06 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 1175.71484375 mb free fat32)
04-07 16:06 DEBUG  TaskList: ## Finished Remove bootloader entry
04-07 16:06 DEBUG  TaskList: ## Running Remove target dir...
04-07 16:06 DEBUG  CommonBackend: Deleting C:\ubuntu
04-07 16:06 DEBUG  TaskList: ## Finished Remove target dir
04-07 16:06 DEBUG  TaskList: ## Running Remove registry key...
04-07 16:06 DEBUG  TaskList: ## Finished Remove registry key
04-07 16:06 DEBUG  TaskList: # Finished tasklist
04-07 16:06 INFO   root: Almost finished uninstalling
04-07 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en']
04-07 16:06 INFO   root: Finished uninstallation
04-07 16:06 DEBUG  root: application.quit
04-07 16:06 DEBUG  WindowsFrontend: frontend.quit
04-07 16:06 DEBUG  WindowsFrontend: frontend.on_quit
04-07 16:06 DEBUG  root: application.on_quit
04-07 16:06 INFO   root: sys.exit
04-07 16:12 INFO   root: === wubi 10.10 rev197 ===
04-07 16:12 DEBUG  root: Logfile is c:\docume~1\sylar\locals~1\temp\wubi-10.10-rev197.log
04-07 16:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
04-07 16:12 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\data
04-07 16:12 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\bin\7z.exe
04-07 16:12 DEBUG  CommonBackend: Fetching basic info...
04-07 16:12 DEBUG  CommonBackend: original_exe=I:\wubi.exe
04-07 16:12 DEBUG  CommonBackend: platform=win32
04-07 16:12 DEBUG  CommonBackend: osname=nt
04-07 16:12 DEBUG  CommonBackend: language=en_US
04-07 16:12 DEBUG  CommonBackend: encoding=cp1252
04-07 16:12 DEBUG  WindowsBackend: arch=i386
04-07 16:12 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\data\isolist.ini
04-07 16:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-07 16:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-07 16:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-07 16:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-07 16:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-07 16:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-07 16:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-07 16:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-07 16:12 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-07 16:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-07 16:12 DEBUG  WindowsBackend: Fetching host info...
04-07 16:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-07 16:12 DEBUG  WindowsBackend: windows version=xp
04-07 16:12 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-07 16:12 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-07 16:12 DEBUG  WindowsBackend: windows_build=2600
04-07 16:12 DEBUG  WindowsBackend: gmt=2
04-07 16:12 DEBUG  WindowsBackend: country=US
04-07 16:12 DEBUG  WindowsBackend: timezone=America/New_York
04-07 16:12 DEBUG  WindowsBackend: windows_username=Sylar
04-07 16:12 DEBUG  WindowsBackend: user_full_name=Sylar
04-07 16:12 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sylar
04-07 16:12 DEBUG  WindowsBackend: windows_language_code=1033
04-07 16:12 DEBUG  WindowsBackend: windows_language=English
04-07 16:12 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2200+
04-07 16:12 DEBUG  WindowsBackend: bootloader=xp
04-07 16:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 83236.6171875 mb free ntfs)
04-07 16:12 DEBUG  WindowsBackend: drive=Drive(C: hd 83236.6171875 mb free ntfs)
04-07 16:12 DEBUG  WindowsBackend: drive=Drive(D: hd 112851.464844 mb free ntfs)
04-07 16:12 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-07 16:12 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-07 16:12 DEBUG  WindowsBackend: drive=Drive(I: removable 1174.80273438 mb free fat32)
04-07 16:12 DEBUG  WindowsBackend: uninstaller_path=None
04-07 16:12 DEBUG  WindowsBackend: previous_target_dir=None
04-07 16:12 DEBUG  WindowsBackend: previous_distro_name=None
04-07 16:12 DEBUG  WindowsBackend: keyboard_id=67699721
04-07 16:12 DEBUG  WindowsBackend: keyboard_layout=us
04-07 16:12 DEBUG  WindowsBackend: keyboard_variant=
04-07 16:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-07 16:12 DEBUG  CommonBackend: locale=en_US.UTF-8
04-07 16:12 DEBUG  WindowsBackend: total_memory_mb=639.484375
04-07 16:12 DEBUG  CommonBackend: Searching ISOs on USB devices
04-07 16:12 DEBUG  CommonBackend: Searching for local CDs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-07 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-07 16:12 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 16:12 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-07 16:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-07 16:12 DEBUG  Distro: wrong arch: i386 != amd64
04-07 16:12 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-07 16:12 INFO   Distro: Found a valid CD for Ubuntu: I:\
04-07 16:12 INFO   root: Running the CD menu...
04-07 16:12 DEBUG  WindowsFrontend: __init__...
04-07 16:12 DEBUG  WindowsFrontend: on_init...
04-07 16:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
04-07 16:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
04-07 16:12 INFO   root: CD menu finished
04-07 16:12 INFO   root: Running the CD boot helper...
04-07 16:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
04-07 16:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
04-07 16:12 INFO   root: CD boot helper confirmed
04-07 16:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
04-07 16:12 DEBUG  TaskList: # Running tasklist...
04-07 16:12 DEBUG  TaskList: ## Running select_target_dir...
04-07 16:12 INFO   WindowsBackend: Installing into C:\ubuntu
04-07 16:12 DEBUG  TaskList: ## Finished select_target_dir
04-07 16:12 DEBUG  TaskList: ## Running create_dir_structure...
04-07 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-07 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-07 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-07 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-07 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-07 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-07 16:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-07 16:12 DEBUG  TaskList: ## Finished create_dir_structure
04-07 16:12 DEBUG  TaskList: ## Running uncompress_target_dir...
04-07 16:12 DEBUG  TaskList: ## Finished uncompress_target_dir
04-07 16:12 DEBUG  TaskList: ## Running create_uninstaller...
04-07 16:12 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-07 16:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-07 16:12 DEBUG  TaskList: ## Finished create_uninstaller
04-07 16:12 DEBUG  TaskList: ## Running copy_installation_files...
04-07 16:12 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-07 16:12 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\winboot -> C:\ubuntu\winboot
04-07 16:12 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sylar\LOCALS~1\Temp\pyl1A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-07 16:12 DEBUG  TaskList: ## Finished copy_installation_files
04-07 16:12 DEBUG  TaskList: ## Running use_cd...
04-07 16:12 DEBUG  TaskList: New task copy_file
04-07 16:12 DEBUG  TaskList: ### Running copy_file...
04-07 16:17 DEBUG  TaskList: ### Finished copy_file
04-07 16:17 DEBUG  TaskList: New task check_iso
04-07 16:17 DEBUG  TaskList: ### Running check_iso...
04-07 16:17 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-07 16:17 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-07 16:17 DEBUG  Distro:     wrong size: 1966918144 > 900000000
04-07 16:17 DEBUG  TaskList: ### Finished check_iso
04-07 16:17 DEBUG  TaskList: ## Finished use_cd
04-07 16:17 DEBUG  TaskList: ## Running extract_kernel...
04-07 16:17 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 16:17 DEBUG  TaskList: # Cancelling tasklist
04-07 16:17 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
04-07 16:17 DEBUG  TaskList: # Finished tasklist
```

---

### Post by DiNozzo89 on 2011-04-07
now i have another problem.. the same log, but this time if i try to boot it says: Could not find the kernel image: linux

---

### Post by DiNozzo89 on 2011-04-09
way too hard.. so.. i want to install Ubuntu 10.10 from USB (my cell phone, microSD card of 2GB)... i can install it just from wubi.exe, and install it inside windows..but i can`t install it instead of windows. why? why do it gives me that errors?

---

