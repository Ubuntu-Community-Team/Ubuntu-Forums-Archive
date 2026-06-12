---
title: "Photoshop CS5 portable is no longer opening with Wine?"
date: 2010-11-23
forum: General Help
---

### Post by kako13 on 2010-11-23
I had PS CS5 portable running with Wine and everything was fine.  However, from a couple of days ago I click on the icon to open the application and it keep loading.

I had attached a screen-shoot with more details.  I am running Ubuntu 10.10 and Wine (wine-1.3.7).

---

### Post by WorMzy on 2010-11-23
Have you changed any settings in winecfg, or upgraded to a newer version of wine than you used to install it? CS5 has only got a Bronze ranking in the Wine AppsDB, so I wouldn't expect it to work well.

[This guy]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158&iTestingId=56851") gave it a silver ranking, so maybe there's a few hints on that page you can use to get your installation working again.

---

### Post by kako13 on 2010-11-23
> **WorMzy said:**
> Have you changed any settings in winecfg, or upgraded to a newer version of wine than you used to install it? CS5 has only got a Bronze ranking in the Wine AppsDB, so I wouldn't expect it to work well.

[This guy]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158&iTestingId=56851") gave it a silver ranking, so maybe there's a few hints on that page you can use to get your installation working again.

I had not changed anything on winecfg nor upgraded. 

I do not think that the Bronze ranking on WineHQ necessarily apply to me because I am running a portable version.

---

### Post by kako13 on 2010-11-24
Any other suggestion? :(

---

### Post by kako13 on 2010-11-24
Any other suggestion?

---

### Post by guile82 on 2011-02-08
try to run 

#wine /path/to/photoshop.exe

it works for me. 

I m using a script "run as root" on the exe of photoshop

i will try to find a fix to this. I its looks that is a permission problem, but I tried to change de owner, but still no go.


Peace

---

### Post by guile82 on 2011-02-08
[http://ubuntuone.com/p/FdZ/](http://ubuntuone.com/p/FdZ/)

Put it all in C:/windows/WinSxS

It worked for me

cump

---

