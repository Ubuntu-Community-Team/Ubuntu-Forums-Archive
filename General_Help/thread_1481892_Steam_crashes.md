---
title: "Steam crashes"
date: 2010-05-13
forum: General Help
---

### Post by timinator94 on 2010-05-13
Hey i could use some help here... steam wont run when i install it... here is wines output inc. the installation.




rodney@rodney-laptop ~ $ wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
--2010-05-12 23:07:19--  [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
Resolving kegel.com... 216.92.86.126
Connecting to kegel.com|216.92.86.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 156711 (153K) [text/plain]
Saving to: `winetricks'

100%[======================================>] 156,711      154K/s   in 1.0s    

2010-05-12 23:07:21 (154 KB/s) - `winetricks' saved [156711/156711]

rodney@rodney-laptop ~ $ sh winetricks steam

Executing wget -O install_flash_player_ax.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_ax.exe](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_ax.exe)
--2010-05-12 23:08:22--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_ax.exe](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_ax.exe)
Resolving fpdownload.macromedia.com... 96.7.146.70
Connecting to fpdownload.macromedia.com|96.7.146.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1956656 (1.9M) [application/octet-stream]
Saving to: `install_flash_player_ax.exe'

100%[======================================>] 1,956,656    163K/s   in 12s     

2010-05-12 23:08:34 (163 KB/s) - `install_flash_player_ax.exe' saved [1956656/1956656]

Executing wine /home/rodney/.winetrickscache/install_flash_player_ax.exe
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\CLSID\\{D27CDB6E-AE6D-11CF-96B8-444553540000}" 4 4 (nil) (nil) 0x1599ac (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\CLSID\\{D27CDB70-AE6D-11CF-96B8-444553540000}" 4 4 (nil) (nil) 0x1599ac (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\TypeLib\\{D27CDB6B-AE6D-11CF-96B8-444553540000}" 4 4 (nil) (nil) 0x1599ac (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\CLSID\\{19114156-8E9A-4D4E-9EE9-17A0E48D3BBB}" 4 4 (nil) (nil) 0x1599ac (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\Interface\\{1D4C8A81-B7AC-460A-8C23-98713C41D6B3}" 4 4 (nil) (nil) 0x1599ac (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\TypeLib\\{FAB3E735-69C7-453B-A446-B6823C6DF1C9}" 4 4 (nil) (nil) 0x1599ac (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b640 0x159abc 0x7ed4b68c
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\Macromed\\Flash\\Flash10e.ocx" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b640 0x159abc 0x7ed4b68c
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\Macromed\\Flash\\FlashUtil10e.exe" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b1f8 0x1599ac 0x7ed4b244
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\CLSID\\{D27CDB6E-AE6D-11CF-96B8-444553540000}" 4 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b1ec 0x1599ac 0x7ed4b238
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\CLSID\\{D27CDB70-AE6D-11CF-96B8-444553540000}" 4 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b1e0 0x1599ac 0x7ed4b22c
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\TypeLib\\{D27CDB6B-AE6D-11CF-96B8-444553540000}" 4 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b1d4 0x1599ac 0x7ed4b220
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\CLSID\\{19114156-8E9A-4D4E-9EE9-17A0E48D3BBB}" 4 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b1c8 0x1599ac 0x7ed4b214
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\Interface\\{1D4C8A81-B7AC-460A-8C23-98713C41D6B3}" 4 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 2 0x7ed4b1bc 0x1599ac 0x7ed4b208
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\TypeLib\\{FAB3E735-69C7-453B-A446-B6823C6DF1C9}" 4 4 (nil) (nil) (nil) (nil)
Executing wget -O install_flash_player.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player.exe](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player.exe)
--2010-05-12 23:08:50--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player.exe](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player.exe)
Resolving fpdownload.macromedia.com... 96.7.146.70
Connecting to fpdownload.macromedia.com|96.7.146.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1924976 (1.8M) [application/octet-stream]
Saving to: `install_flash_player.exe'

100%[======================================>] 1,924,976    185K/s   in 10s     

2010-05-12 23:09:01 (183 KB/s) - `install_flash_player.exe' saved [1924976/1924976]

Executing wine /home/rodney/.winetrickscache/install_flash_player.exe
prerequisite gecko already installed, skipping
Executing wget -O InstMsiA.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe)
--2010-05-12 23:09:05--  [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe)
Resolving download.microsoft.com... 63.80.242.9, 63.80.242.32
Connecting to download.microsoft.com|63.80.242.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1709160 (1.6M) [application/octet-stream]
Saving to: `InstMsiA.exe'

100%[======================================>] 1,709,160    158K/s   in 9.5s    

2010-05-12 23:09:15 (175 KB/s) - `InstMsiA.exe' saved [1709160/1709160]

Executing /usr/bin/cabextract --directory=/home/rodney/.wine/dosdevices/c:/winetrickstmp /home/rodney/.winetrickscache/InstMsiA.exe
Extracting cabinet: /home/rodney/.winetrickscache/InstMsiA.exe
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msi.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msiexec.exe
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msihnd.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msisip.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msimsg.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msimain.sdb
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msiinst.exe
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/riched20.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/usp10.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/msls31.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/shfolder.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/instmsi.msi
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/imagehlp.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/cabinet.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/mspatcha.dll
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/sdbapi.dll

All done, no errors.
Executing cp -f /home/rodney/.wine/dosdevices/c:/winetrickstmp/msls31.dll /home/rodney/.wine/dosdevices/c:/windows/system32
Executing wine iexplore -unregserver
Using native,builtin override for following DLLs: iexplore.exe itircl itss jscript mlang mshtml msimtf shdoclc shdocvw shlwapi urlmon
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing wget -O ie6sites.dat -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://www.microsoft.com/windows/ie/ie6sp1/download/rtw/x86/ie6sites.dat](http://www.microsoft.com/windows/ie/ie6sp1/download/rtw/x86/ie6sites.dat)
--2010-05-12 23:09:16--  [http://www.microsoft.com/windows/ie/ie6sp1/download/rtw/x86/ie6sites.dat](http://www.microsoft.com/windows/ie/ie6sp1/download/rtw/x86/ie6sites.dat)
Resolving [www.microsoft.com]("http://www.microsoft.com")... 207.46.19.190, 207.46.19.254, 64.4.31.252
Connecting to [www.microsoft.com|207.46.19.190|:80]("http://www.microsoft.com%7C207.46.19.190%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2788 (2.7K) [application/octet-stream]
Saving to: `ie6sites.dat'

100%[======================================>] 2,788       --.-K/s   in 0s      

2010-05-12 23:09:16 (81.7 MB/s) - `ie6sites.dat' saved [2788/2788]

Executing wget -O ie6setup.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe)
--2010-05-12 23:09:16--  [http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe)
Resolving download.microsoft.com... 63.80.242.32, 63.80.242.9
Connecting to download.microsoft.com|63.80.242.32|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 491768 (480K) [application/octet-stream]
Saving to: `ie6setup.exe'

100%[======================================>] 491,768      186K/s   in 2.6s    

2010-05-12 23:09:19 (186 KB/s) - `ie6setup.exe' saved [491768/491768]

fixme:advapi:CheckTokenMembership ((nil) 0x122848 0x32fd78) stub!
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:NeedReboot (0): stub
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7ed7b6c3, 0x7ed7b6bc): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15cfd0, 0x7ed7b6bc): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14b5b0, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14acb0, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14abc0, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x17f490, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14ad10, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x17f450, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14b378, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14ad20, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1625d0, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14b378, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14b4a0, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14b498, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14b438, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1806e8, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x17f590, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x7eb7843f, 0x7eb78438): stub
fixme:urlmon:ObtainUserAgentString (0, 0x17f630, 0x7eb78438): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:crypt:CertEnumCTLsInStore (0x125288, (nil)): stub
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
err:setupapi:SetupDefaultQueueCallbackW copy error 2 L"C:\\windows\\msdownld.tmp\\AS0373A2.tmp\\IEEX\\expinst.exe" -> L"C:\\Program Files\\Internet Explorer\\W2K\\expinst.exe"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:shell:MLLoadLibraryA ("inetres.dll",0x5ec00000,0) semi-stub!
fixme:shell:MLLoadLibraryA ("acctres.dll",0x64300000,0) semi-stub!
fixme:shell:MLLoadLibraryA ("inetres.dll",0x5ec00000,0) semi-stub!
fixme:shell:MLLoadLibraryA ("msoeres.dll",0xcf0000,0) semi-stub!
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:shell:MLLoadLibraryA ("msoeres.dll",0xcf0000,0) semi-stub!
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:shell:MLLoadLibraryA ("acctres.dll",0x64300000,0) semi-stub!
fixme:shell:MLLoadLibraryW (L"wab32res.dll",0x35c40000,1) semi-stub!
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:shell:MLLoadLibraryA ("wab32res.dll",0x6b500000,0) semi-stub!
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:shell:MLLoadLibraryA ("wab32res.dll",0x403f0000,0) semi-stub!
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:propsheet:PROPSHEET_UnImplementedFlags PSH_RTLREADING 
fixme:wintrust:CryptCATAdminAcquireContext 0x7ed49fdc {f750e6c3-38ee-11d1-85e5-00c04fc295ee} 0
fixme:wintrust:CryptCATAdminAddCatalog 0xdeadbeef L"C:\\windows\\msdownld.tmp\\AS03772B.tmp\\mplay2u.CAT" L"mplay2u.CAT" 0
fixme:wintrust:CryptCATAdminReleaseCatalogContext 0xdeadbeef 0x1 0
fixme:wintrust:CryptCATAdminReleaseContext 0xdeadbeef 0
err:module:import_dll Library DRMClien.DLL (which is needed by L"C:\\windows\\system32\\dxmasf.dll") not found
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
err:wineboot:ProcessRunKeys Error running cmd #0 (2)
Clearing Windows version back to default
Executing early_wine regedit c:\winetrickstmp\unset-winver.reg
Executing wget -O liberation-fonts-1.04.tar.gz -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [https://fedorahosted.org/releases/l/i/liberation-fonts/liberation-fonts-1.04.tar.gz](https://fedorahosted.org/releases/l/i/liberation-fonts/liberation-fonts-1.04.tar.gz)
--2010-05-12 23:11:47--  [https://fedorahosted.org/releases/l/i/liberation-fonts/liberation-fonts-1.04.tar.gz](https://fedorahosted.org/releases/l/i/liberation-fonts/liberation-fonts-1.04.tar.gz)
Resolving fedorahosted.org... 66.135.52.17
Connecting to fedorahosted.org|66.135.52.17|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1011820 (988K) [application/x-gzip]
Saving to: `liberation-fonts-1.04.tar.gz'

100%[======================================>] 1,011,820    177K/s   in 5.7s    

2010-05-12 23:11:54 (174 KB/s) - `liberation-fonts-1.04.tar.gz' saved [1011820/1011820]

Executing wget -O tahoma32.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe](http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe)
--2010-05-12 23:11:54--  [http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe](http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe)
Resolving download.microsoft.com... 63.80.242.32, 63.80.242.9
Connecting to download.microsoft.com|63.80.242.32|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 312440 (305K) [application/octet-stream]
Saving to: `tahoma32.exe'

100%[======================================>] 312,440      188K/s   in 1.6s    

2010-05-12 23:11:56 (188 KB/s) - `tahoma32.exe' saved [312440/312440]

Executing /usr/bin/cabextract --directory=/home/rodney/.wine/dosdevices/c:/winetrickstmp /home/rodney/.winetrickscache/tahoma32.exe
Extracting cabinet: /home/rodney/.winetrickscache/tahoma32.exe
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/Tahoma.TTF
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/Tahomabd.TTF
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/fontinst.inf
  extracting /home/rodney/.wine/dosdevices/c:/winetrickstmp/fontinst.exe

All done, no errors.
Executing cp -f /home/rodney/.wine/dosdevices/c:/winetrickstmp/Tahoma.TTF /home/rodney/.wine/dosdevices/c:/windows/Fonts/tahoma.ttf
Executing cp -f /home/rodney/.wine/dosdevices/c:/winetrickstmp/Tahomabd.TTF /home/rodney/.wine/dosdevices/c:/windows/Fonts/tahomabd.ttf
Executing wget -O SteamInstall.msi -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://storefront.steampowered.com/download/SteamInstall.msi](http://storefront.steampowered.com/download/SteamInstall.msi)
--2010-05-12 23:11:56--  [http://storefront.steampowered.com/download/SteamInstall.msi](http://storefront.steampowered.com/download/SteamInstall.msi)
Resolving storefront.steampowered.com... 208.111.148.251, 208.111.148.152
Connecting to storefront.steampowered.com|208.111.148.251|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1588224 (1.5M) [application/x-msi]
Saving to: `SteamInstall.msi'

100%[======================================>] 1,588,224    148K/s   in 9.1s    

2010-05-12 23:12:05 (171 KB/s) - `SteamInstall.msi' saved [1588224/1588224]

Executing wine msiexec /i /home/rodney/.winetrickscache/SteamInstall.msi
fixme:advapi:LookupAccountNameW (null) L"rodney" (nil) 0x32f864 (nil) 0x32f868 0x32f85c - stub
fixme:advapi:LookupAccountNameW (null) L"rodney" 0x130728 0x32f864 0x1307b8 0x32f868 0x32f85c - stub
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 2 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:shell:DllCanUnloadNow stub
fixme:advapi:SetEntriesInAclA 1 0x33fd40 (nil) 0x33fd64
fixme:advapi:SetNamedSecurityInfoW L"C:\\Steam\\" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 1 0x33fd40 (nil) 0x33fd64
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Valve\\Steam" 4 4 (nil) (nil) (nil) (nil)
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
Steam Client Service install completed.fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
------------------------------------------------------
Once Steam is running, disable player notifications and in-game chat in Settings, or games will crash on launch; see wine bug 22053
------------------------------------------------------
Install of steam done
winetricks done.
rodney@rodney-laptop ~ $ 
rodney@rodney-laptop ~ $ CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 162 servers.
CellID: Connecting to 87.248.209.139:27031. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: Connect to 87.248.209.139:27031 took 170 MS
CellID: Nothing beat our old best time of 15 MS
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:shell:IsUserAdmin stub
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error



Thanks

---

### Post by quinnten83 on 2010-05-13
Dude,
code tags...

---

### Post by timinator94 on 2010-05-13
> **quinnten83 said:**
> Dude,
code tags...
Im sorry? Im still a bit of a noob so i need you to clarify....

---

### Post by timinator94 on 2010-05-13
Oh figured it out... needed to run it in win 7 mode. works fine now:guitar:
p.s. anybody hear a rumor that steam is making a linux native version?

---

### Post by Pant Burner on 2010-05-14
So, you ran *winecfg* and changed the Windows Version to Windows 7? 
And then? How did you fix the memory allocation problem? Running *sh winetricks steam* again doesn't do anything new for me.

---

### Post by timinator94 on 2010-06-08
> **Pant Burner said:**
> So, you ran *winecfg* and changed the Windows Version to Windows 7? 
And then? How did you fix the memory allocation problem? Running *sh winetricks steam* again doesn't do anything new for me.

hmmm try installing play on linux and installing it from there

---

