---
title: "Dual boot Edubuntu 5.1 and Win98"
date: 2006-06-02
forum: General Help
---

### Post by Shronin on 2006-06-02
Ok im trying to dual boot Edubuntu 5.1 and windows 98 i have each one installed on seperate hard drives already but i have no i dea what to do now. . . i cant delete my Win98 since i need the stuff on it so how do i do this? 

Im a noob :D

---

### Post by SHodges on 2006-06-02
[QUOTE=Shronin]Ok im trying to dual boot Edubuntu 5.1 and windows 98 i have each one installed on seperate hard drives already but i have no i dea what to do now. . . i cant delete my Win98 since i need the stuff on it so how do i do this? 

Im a noob :D[/QUOTE]
I don't know how it works for windows 98, but when I did edubuntu 5.1 and windows xp, all I had to do was install windows xp first on one harddrive, then edubuntu on the other and the grub thing automatically detected windows and installed it in the list.  If you have two harddrives, just install windows on one, then edubuntu on the other, and that should be all you need to do.

---

### Post by ubuntu27 on 2006-06-05
[QUOTE=SHodges]I don't know how it works for windows 98, but when I did edubuntu 5.1 and windows xp, all I had to do was install windows xp first on one harddrive, then edubuntu on the other and the grub thing automatically detected windows and installed it in the list.  If you have two harddrives, just install windows on one, then edubuntu on the other, and that should be all you need to do.[/QUOTE]

And that's the exact answer!
Except that current Edubunt's version is 6.06: [http://www.edubuntu.org/](http://www.edubuntu.org/)

Dual booting Edubuntu & WIndows is the same as dualbooting Ubuntuand WINdows :)

---

### Post by cetheriel on 2006-09-15
well, point is i had ubuntu 6.06 installed, then installed win98, which seems to have written mbr over ubuntu's boot. what should i do now, reinstall?

---

### Post by ubuntu27 on 2006-09-16
> **cetheriel said:**
> well, point is i had ubuntu 6.06 installed, then installed win98, which seems to have written mbr over ubuntu's boot. what should i do now, reinstall?


Don't worry. Windows didn't delete UBuntu, it just replaced the MBR/Grub.

ALl you have to do it recover it. Follow this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

