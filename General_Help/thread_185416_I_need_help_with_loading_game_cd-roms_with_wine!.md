---
title: "I need help with loading game cd-roms with wine!"
date: 2006-05-31
forum: General Help
---

### Post by novik420 on 2006-05-31
I am still continuing to accmplish diablo 2 LOD on ubuntu i have seen many guides but i now think its my drive that is the problem. Is it supposed to make a "hdd" file in media ex:  ls /media
cdrom  cdrom0  hdd
 That is what comes up, I use wine, if that is not supposed to be there (hdd) or if someone can jsut help with diablo 2 and d2 LOD installation it would be much appreciated

---

### Post by Kilz on 2006-05-31
[QUOTE=novik420]I am still continuing to accmplish diablo 2 LOD on ubuntu i have seen many guides but i now think its my drive that is the problem. Is it supposed to make a "hdd" file in media ex:  ls /media
cdrom  cdrom0  hdd
 That is what comes up, I use wine, if that is not supposed to be there (hdd) or if someone can jsut help with diablo 2 and d2 LOD installation it would be much appreciated[/QUOTE]

No I think cdroms are loaded to /media/cdrom or /media/cdrom0 the hdd is in /dev/hdd , it is the raw drive link that is mounted to /media/cdrom. As in the previous post on this subject there are a few ways of getting the game to run under Linux. 
1. wine There is an excelent howto here [http://appdb.winehq.org/appview.php?versionId=315](http://appdb.winehq.org/appview.php?versionId=315) 
2. Cedega - Easy to setup, game runs flawlessly but it costs money. 
3. Duel boot with windows - 100% free if you own a copy of windows and easy to setup. 
Wine is not perfect and is under constant change, sometimes it makes it hard to install games. But remember , you are trying to run a Windows program on Linux with an emulator. It may be harder than you think. If you find you cant get it to run, duel boot with windows.

---

