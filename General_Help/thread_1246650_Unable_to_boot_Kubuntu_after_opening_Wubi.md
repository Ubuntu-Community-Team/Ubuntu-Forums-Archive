---
title: "Unable to boot Kubuntu after opening Wubi"
date: 2009-08-22
forum: General Help
---

### Post by xubun2 on 2009-08-22
I installed kubuntu in my PC using wubi and it worked fine until I opened wubi again to show to friend how it works. When opened wubi I did not selected the Ok option but aparently opening it was enough change the boot config of my PC. Now, when select to boot kubuntu, i get an error saying the hal.dll is missing or corrupt. 
I found a similar thread from someone with the same problem but there is not an spcific explnation to fix it ([http://ubuntuforums.org/showthread.php?t=1157596&goto=nextoldest](http://ubuntuforums.org/showthread.php?t=1157596&goto=nextoldest))
 
The following lines are a log created aparently after I ran wubi:
 
08-19 17:34 INFO root: === wubi 9.04 rev129 ===
08-19 17:34 DEBUG root: Logfile is c:\docume~1\user\locals~1\temp\wubi-9.04-rev129.log
08-19 17:34 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Program Files\\wubi\\wubi.exe"']
08-19 17:34 DEBUG CommonBackend: data_dir=C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\data
08-19 17:34 DEBUG WindowsBackend: 7z=C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
08-19 17:34 DEBUG CommonBackend: Fetching basic info...
08-19 17:34 DEBUG CommonBackend: original_exe=C:\Program Files\wubi\wubi.exe
08-19 17:34 DEBUG CommonBackend: platform=win32
08-19 17:34 DEBUG CommonBackend: osname=nt
08-19 17:34 DEBUG CommonBackend: language=en_US
08-19 17:34 DEBUG CommonBackend: encoding=cp1252
08-19 17:34 DEBUG WindowsBackend: arch=i386
08-19 17:34 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
08-19 17:34 DEBUG CommonBackend: Adding distro Xubuntu-i386
08-19 17:34 DEBUG CommonBackend: Adding distro Xubuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Kubuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Mythbuntu-i386
08-19 17:34 DEBUG CommonBackend: Adding distro Ubuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Ubuntu-i386
08-19 17:34 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Kubuntu-i386
08-19 17:34 DEBUG WindowsBackend: Fetching host info...
08-19 17:34 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 17:34 DEBUG WindowsBackend: windows version=xp
08-19 17:34 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
08-19 17:34 DEBUG WindowsBackend: windows_sp=Service Pack 3
08-19 17:34 DEBUG WindowsBackend: windows_build=2600
08-19 17:34 DEBUG WindowsBackend: gmt=-7
08-19 17:34 DEBUG WindowsBackend: country=US
08-19 17:34 DEBUG WindowsBackend: timezone=America/hometown
08-19 17:34 DEBUG WindowsBackend: windows_username=user
08-19 17:34 DEBUG WindowsBackend: user_full_name=user
08-19 17:34 DEBUG WindowsBackend: user_directory=user
08-19 17:34 DEBUG WindowsBackend: windows_language_code=1033
08-19 17:34 DEBUG WindowsBackend: windows_language=English
08-19 17:34 DEBUG WindowsBackend: processor_name= Intel(R) Atom(TM) CPU N270 @ 1.60GHz
08-19 17:34 DEBUG WindowsBackend: bootloader=xp
08-19 17:34 DEBUG WindowsBackend: system_drive=Drive(C: hd 122660.023438 mb free )
08-19 17:34 DEBUG WindowsBackend: drive=Drive(C: hd 122660.023438 mb free )
08-19 17:34 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-19 17:34 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
08-19 17:34 DEBUG WindowsBackend: previous_distro_name=Kubuntu
08-19 17:34 DEBUG WindowsBackend: keyboard_id=67699721
08-19 17:34 DEBUG WindowsBackend: keyboard_layout=us
08-19 17:34 DEBUG WindowsBackend: keyboard_variant=
08-19 17:34 DEBUG CommonBackend: locale=en_US.UTF-8
08-19 17:34 DEBUG WindowsBackend: total_memory_mb=1015.16796875
08-19 17:34 DEBUG CommonBackend: Searching ISOs on USB devices
08-19 17:34 DEBUG CommonBackend: Searching for local CDs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 INFO root: Already installed, running the uninstaller...
08-19 17:34 INFO root: Running the uninstaller...
08-19 17:34 INFO CommonBackend: This is the uninstaller running
08-19 17:34 DEBUG WindowsFrontend: __init__...
08-19 17:34 DEBUG WindowsFrontend: on_init...
08-19 17:34 INFO root: Received settings
08-19 17:34 DEBUG TaskList: # Running tasklist...
08-19 17:34 DEBUG TaskList: ## Running Backup ISO...
08-19 17:34 DEBUG TaskList: ## Finished Backup ISO
08-19 17:34 DEBUG TaskList: ## Running Remove bootloader entry...
08-19 17:34 ERROR WindowsBackend: Cannot find bcdedit
08-19 17:34 DEBUG WindowsBackend: undo_bootini C:
08-19 17:34 DEBUG WindowsBackend: undo_configsys Drive(C: hd 122660.023438 mb free )
08-19 17:34 DEBUG TaskList: ## Finished Remove bootloader entry
08-19 17:34 DEBUG TaskList: ## Running Remove target dir...
08-19 17:34 DEBUG CommonBackend: Deleting C:\ubuntu
08-19 17:34 DEBUG TaskList: ## Finished Remove target dir
08-19 17:34 DEBUG TaskList: ## Running Remove registry key...
08-19 17:34 DEBUG TaskList: ## Finished Remove registry key
08-19 17:34 DEBUG TaskList: # Finished tasklist
08-19 17:34 INFO root: Almost finished uninstalling
08-19 17:34 INFO root: Finished uninstallation
08-19 17:34 DEBUG CommonBackend: Fetching basic info...
08-19 17:34 DEBUG CommonBackend: original_exe=C:\Program Files\wubi\wubi.exe
08-19 17:34 DEBUG CommonBackend: platform=win32
08-19 17:34 DEBUG CommonBackend: osname=nt
08-19 17:34 DEBUG CommonBackend: language=en_US
08-19 17:34 DEBUG CommonBackend: encoding=cp1252
08-19 17:34 DEBUG WindowsBackend: arch=i386
08-19 17:34 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
08-19 17:34 DEBUG CommonBackend: Adding distro Xubuntu-i386
08-19 17:34 DEBUG CommonBackend: Adding distro Xubuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Kubuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Mythbuntu-i386
08-19 17:34 DEBUG CommonBackend: Adding distro Ubuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Ubuntu-i386
08-19 17:34 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
08-19 17:34 DEBUG CommonBackend: Adding distro Kubuntu-i386
08-19 17:34 DEBUG WindowsBackend: Fetching host info...
08-19 17:34 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 17:34 DEBUG WindowsBackend: windows version=xp
08-19 17:34 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
08-19 17:34 DEBUG WindowsBackend: windows_sp=Service Pack 3
08-19 17:34 DEBUG WindowsBackend: windows_build=2600
08-19 17:34 DEBUG WindowsBackend: gmt=-7
08-19 17:34 DEBUG WindowsBackend: country=US
08-19 17:34 DEBUG WindowsBackend: timezone=America/hometown
08-19 17:34 DEBUG WindowsBackend: windows_username=user
08-19 17:34 DEBUG WindowsBackend: user_full_name=user
08-19 17:34 DEBUG WindowsBackend: user_directory=user
08-19 17:34 DEBUG WindowsBackend: windows_language_code=1033
08-19 17:34 DEBUG WindowsBackend: windows_language=English
08-19 17:34 DEBUG WindowsBackend: processor_name= Intel(R) Atom(TM) CPU N270 @ 1.60GHz
08-19 17:34 DEBUG WindowsBackend: bootloader=xp
08-19 17:34 DEBUG WindowsBackend: system_drive=Drive(C: hd 140378.191406 mb free )
08-19 17:34 DEBUG WindowsBackend: drive=Drive(C: hd 140378.191406 mb free )
08-19 17:34 DEBUG WindowsBackend: uninstaller_path=None
08-19 17:34 DEBUG WindowsBackend: previous_target_dir=None
08-19 17:34 DEBUG WindowsBackend: previous_distro_name=None
08-19 17:34 DEBUG WindowsBackend: keyboard_id=67699721
08-19 17:34 DEBUG WindowsBackend: keyboard_layout=us
08-19 17:34 DEBUG WindowsBackend: keyboard_variant=
08-19 17:34 DEBUG CommonBackend: locale=en_US.UTF-8
08-19 17:34 DEBUG WindowsBackend: total_memory_mb=1015.16796875
08-19 17:34 DEBUG CommonBackend: Searching ISOs on USB devices
08-19 17:34 DEBUG CommonBackend: Searching for local CDs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 DEBUG Distro: checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
08-19 17:34 DEBUG Distro: does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
08-19 17:34 INFO root: Running the installer...
08-19 17:35 DEBUG WindowsFrontend: frontend.on_quit
08-19 17:35 DEBUG root: application.on_quit
08-19 17:35 INFO root: sys.exit
 
Please help.

---

### Post by bchurchill on 2009-08-22
I'm quite sure this is more of a Windows issue than an Ubuntu issue.  It seems like it's not an uncommon problem.  See [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm).  It's made for Windows XP, but its suggestions are probably applicable to any windows system.

---

### Post by xubun2 on 2009-08-22
Already re-installed the hal.dll and still faling. I do not think is related to the hal.dll because my windows partiton is working fine.

---

### Post by bchurchill on 2009-08-22
> **xubun2 said:**
> Already re-installed the hal.dll and still faling. I do not think is related to the hal.dll because my windows partiton is working fine.

Well it's definitely not an Ubuntu problem because linux doesn't use DLL files.  It could be a dependency issue where your version of hal.dll is too new, or maybe some weird versioning issue.  Did you do an update recently?  

Unfortunately the Wubi logs don't show any kind of error, so without more information there's nothing we can do.

Your best bet is to search google for others who have had this exact problem, or look at the general case of bad hal.dll files.  You could try doing other things that the about.com article recommends too.

You might benefit from leaving Wubi and do a standard dual-boot install.

---

### Post by xubun2 on 2009-08-22
The hal.dll was replaced with the same exact version.

---

