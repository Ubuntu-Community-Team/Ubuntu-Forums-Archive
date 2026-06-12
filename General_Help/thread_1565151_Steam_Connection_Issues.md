---
title: "Steam Connection Issues"
date: 2010-08-31
forum: General Help
---

### Post by MHardeman25 on 2010-08-31
Hey guys, having a problem here. I have been running steam through wine and it has worked fine, at least up until now. For the past two days, i haven't been able to connect to the steam network. I have tried everything, clean installing wine, updating wine to the 1.3 developmental version, reinstalling steam, deleting the ClientRegistry.blob, installing with winetricks... etc. I just cant make wine connect to the steam servers. My internet is working fine, I have had no problems with it. Now, after a clean "install" of steam, it won't even get to the main program. You know how it goes, It installs itself and says, "Steam will now finish installing" and try to connect to the steam servers, at this point, It exits with a message

"Steam.exe (main exception): To run Steam, you must first connect to the Internet"

 If anyone else has had these problems, could you point me to the solution? Specs below

Computer:
OS: Ubuntu 10.04 (Lucid Linux) x64 bit
Processor: Intel i7 2.80GHz
Ram: 8GB ddr3 ram
Graphics Card: Nvidia 240gt

Wine: 1.31 clean install
winetricks: clean install

```

kronos@kronos-desktop:~$ sh
$ winetricks corefonts vcrun6
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/arial32.exe
/home/kronos/.winetrickscache/arial32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/Arial.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Arialbd.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Arialbi.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Ariali.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/arialb32.exe
/home/kronos/.winetrickscache/arialb32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/AriBlk.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/comic32.exe
/home/kronos/.winetrickscache/comic32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/Comic.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Comicbd.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/courie32.exe
/home/kronos/.winetrickscache/courie32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/cour.ttf /home/kronos/.wine/dosdevices/c:/winetrickstmp/courbd.ttf /home/kronos/.wine/dosdevices/c:/winetrickstmp/courbi.ttf /home/kronos/.wine/dosdevices/c:/winetrickstmp/couri.ttf /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/georgi32.exe
/home/kronos/.winetrickscache/georgi32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/Georgia.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Georgiab.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Georgiai.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Georgiaz.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/impact32.exe
/home/kronos/.winetrickscache/impact32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/Impact.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/times32.exe
/home/kronos/.winetrickscache/times32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/Times.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Timesbd.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Timesbi.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Timesi.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/trebuc32.exe
/home/kronos/.winetrickscache/trebuc32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/trebuc.ttf /home/kronos/.wine/dosdevices/c:/winetrickstmp/trebucbi.ttf /home/kronos/.wine/dosdevices/c:/winetrickstmp/trebucit.ttf /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/verdan32.exe
/home/kronos/.winetrickscache/verdan32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/Verdana.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Verdanab.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Verdanai.TTF /home/kronos/.wine/dosdevices/c:/winetrickstmp/Verdanaz.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
egister-font.regwine regedit c:\winetrickstmp
Executing /usr/bin/cabextract -q --directory=/home/kronos/.wine/dosdevices/c:/winetrickstmp /home/kronos/.winetrickscache/webdin32.exe
/home/kronos/.winetrickscache/webdin32.exe: library not compiled to support large files.
Executing cp -f /home/kronos/.wine/dosdevices/c:/winetrickstmp/Webdings.TTF /home/kronos/.wine/dosdevices/c:/windows/Fonts
egister-font.regwine regedit c:\winetrickstmp
Install of corefonts done
Executing /usr/bin/cabextract /home/kronos/.winetrickscache/vcredist.exe -d /home/kronos/.wine/dosdevices/c:/windows/system32/ -F mfc42u.dll
/home/kronos/.winetrickscache/vcredist.exe: library not compiled to support large files.
Extracting cabinet: /home/kronos/.winetrickscache/vcredist.exe
  extracting /home/kronos/.wine/dosdevices/c:/windows/system32//mfc42u.dll

All done, no errors.
Using native,builtin override for following DLLs: msvcrt
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*msvcrt"="native,builtin"
Install of vcrun6 done
winetricks done.
$ winetricks steam
Executing wget -O SteamInstall.msi -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://storefront.steampowered.com/download/SteamInstall.msi
--2010-08-31 13:43:38--  http://storefront.steampowered.com/download/SteamInstall.msi
Resolving storefront.steampowered.com... 208.111.185.140, 68.142.118.249
Connecting to storefront.steampowered.com|208.111.185.140|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1588224 (1.5M) [application/x-msi]
Saving to: `SteamInstall.msi'

100%[======================================>] 1,588,224   1.29M/s   in 1.2s    

2010-08-31 13:43:39 (1.29 MB/s) - `SteamInstall.msi' saved [1588224/1588224]

Executing wine msiexec /i /home/kronos/.winetrickscache/SteamInstall.msi
fixme:advapi:LookupAccountNameW (null) L"kronos" (nil) 0x32f150 (nil) 0x32f154 0x32f148 - stub
fixme:advapi:LookupAccountNameW (null) L"kronos" 0x1373c0 0x32f150 0x137908 0x32f154 0x32f148 - stub
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:advapi:SetEntriesInAclA 1 0x33fcc8 (nil) 0x33fcec
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Steam\\" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 1 0x33fcc8 (nil) 0x33fcec
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Valve\\Steam" 4 4 (nil) (nil) (nil) (nil)
fixme:hnetcfg:fw_app_put_ProcessImageFileName 0x12e830, L"C:\\Program Files\\Steam\\\\Steam.exe"
fixme:hnetcfg:fw_app_put_Name 0x12e830, L"Steam"
fixme:hnetcfg:fw_apps_Add 0x12e7e8, 0x12e830
Steam Client Service install completed.------------------------------------------------------
Once Steam is running, disable player notifications and in-game chat in Settings, or games will crash on launch; see wine bug 22053
------------------------------------------------------
Install of steam done
winetricks done.
$exit
kronos@kronos-desktop:~$ wine "C:\\Program Files\\Steam\\Steam.exe"
kronos@kronos-desktop:~$ 

```at this point, i get the above specified error message.

---

### Post by 1chess2u Christian on 2011-02-15
Thank you! I have never gotten Steam to work, and I am glad that I am not the only one with Ubuntu that runs Steam. I am getting the same error message, and I am connected to the internet when I am trying to run it.

---

