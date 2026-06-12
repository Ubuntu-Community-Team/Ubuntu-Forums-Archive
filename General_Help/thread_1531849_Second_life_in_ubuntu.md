---
title: "Second life in ubuntu"
date: 2010-07-15
forum: General Help
---

### Post by Fred Doolie on 2010-07-15
First of all the Linux version of SL works like a champ and is WAY faster than the windows version. Secondly I have a little gift for you and a request for help.

Both versions of SL run fine from a flash drive but I have only created the script for the Winblows version of "Portable Second Life". If somebody would translate this into Linuxspeak I'd depreciate it. It assumes that the script is in the same folder as all the SL files and the SL folder is on the flashdrive.

THIS IS A WINBLOWS SCRIPT! SOMEBODY PLEASE TRANSLATE INTO LINUX-SPEAK!

----------------------------
REM Copy the backup cache files to the proper place and delete the backup
XCOPY CACHE-BACKUP "%APPDATA%\SecondLife" /H /R /E /Y /I 
RMDIR  /q /s "CACHE-BACKUP"

REM Run SL and wait until it exits
START /wait secondlife.exe

REM Copy the cache files to a backup and delete the cache 
XCOPY "%APPDATA%\SecondLife" CACHE-BACKUP /H /R /E /Y /I 
RMDIR  /q /s "%APPDATA%\SecondLife"

EXIT
----------------------------------------



Alternate script if you don't care about saving the cache. Works but *everything* has to be reloaded and you lose the auto fill-in for the log-in . 

-----------------------
START /wait secondlife.exe
RMDIR  /q /s "%APPDATA%\SecondLife"
Exit
-------------------------------------








With this you can carry your second life with you. 
Please translate into Linuxspeak (me no speak-um Linux Script), repost here and have fun with it. OK, the script isn't totally needed but restoring the cache saves a LOT of download time!

This script can be modified to play any game that doesn't depend on winblows registry entries.



Thanks

---

