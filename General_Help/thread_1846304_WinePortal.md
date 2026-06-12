---
title: "Wine/Portal"
date: 2011-09-18
forum: General Help
---

### Post by rvgsd on 2011-09-18
Hi, 
I was wondering what would be the best way to play Portal on ubuntu. I have the PC version of it. So far I have managed to stay wine-free on my Ubuntu. 
Will installing Wine make windows viruses effective in the wine-installed programs? do I need anti virus if I install wine?
Can I simply install it on a guest win-XP in virtualbox? I read somewhere that it doesn't run because of haveing no DirectX/OpenGl graphics acceleration support.
I tried google-ing for the above topics but the information is scattered all over, and I couldn't come to a solid conclusion.
Any suggestions would be appreciated.

---

### Post by rvgsd on 2011-09-23
b.u.m.p.!

---

### Post by patryk77 on 2011-09-23
> **rvgsd said:**
> Will installing Wine make windows viruses effective in the wine-installed programs? do I need anti virus if I install wine?
Can I simply install it on a guest win-XP in virtualbox? I read somewhere that it doesn't run because of haveing no DirectX/OpenGl graphics acceleration support.

Generally, you would have to execute a virus with wine specifically to get infected (or run vulnerable software like IE in wine on a malware page). I wouldn't worry about it too much, unless you mean you have a copy downloaded from a shady site that distributes infected games.

Either way, you can scan it with Clam AV.

As for viruses being effective... They might have *some* effect, but really it's unlikely and they can't infect your entire system.

As for installing on a VBox guest, you can install DX/OpenGL support if you install the Guest Additions (in the non-GPL versions of VBox). I use it to run Google Earth + its plugin with 3D acceleration, never really cared much to play games on it so I wouldn't know.

You can try to search Wine's AppDB or perhaps PlayOnLinux for more info.

[http://appdb.winehq.org/objectManager.php?sClass=category&iId=&sAction=view&sTitle=Browse+Applications](http://appdb.winehq.org/objectManager.php?sClass=category&iId=&sAction=view&sTitle=Browse+Applications)

---

