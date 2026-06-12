---
title: "trouble with WoW in 9.10 help plz :)"
date: 2010-03-05
forum: General Help
---

### Post by lotsamuffins on 2010-03-05
i installed wrath of the lich king (world of warcraft) i get the following message when trying to launch from terminal and get nothing when launching from the button on my desktop. i have found i can load it the wow.exe in the files. but i dont want to do this i want to do it through the launcher. any help appreciated.

running newest wine and 91.0 ubuntu 64bit
8800gtc card
q6600 quadcore 4gb or ram.







matthew@matthew-desktop:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw: PersistStreamInit_Load (0x13c470)->(0x32e0f4)
fixme:shdocvw:OleControl_FreezeEvents (0x13c470)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x13c470)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x13ca18 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13c9f8 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13c9f8 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d370 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d370 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d370 ) : WIN32_FIND_DATA is not yet filled.
fixme:urlmon:URLMoniker_BindToObject use running object table
matthew@matthew-desktop:~$ wine "/media/windowsdrive/WorldofWarcraft/Wow.exe" -opengl
wine: cannot find '/media/windowsdrive/WorldofWarcraft/Wow.exe'
matthew@matthew-desktop:~$

---

