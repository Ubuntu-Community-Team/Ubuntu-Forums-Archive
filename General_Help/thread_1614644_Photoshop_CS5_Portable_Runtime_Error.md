---
title: "Photoshop CS5 Portable Runtime Error"
date: 2010-11-05
forum: General Help
---

### Post by lostprophetpunk on 2010-11-05
Heya there,

I did originally have Ubuntu 10.04, in which gave me the same problem. I have upgraded to Ubuntu 10.10.

I have been using the portable Adobe Photoshop CS5 application for a while now...however...it has kind of broken on me now.

Everytime I tun the application now, it gives me a runtime error.

"Runtime Error!

Program C:\Pro...

R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more info"

I have tried re-installing several times now. Even downloading a different version.

I am also running it through wine through the following command...
"wine "C:\Program Files\PhotoshopPortable\PhotoshopCS5Portable.exe"

If anyone could help, I would be ever so thankful.

---

### Post by kaldor on 2010-11-05
Remember, this is Linux and not Windows... Windows applications are likely to not work properly. I have heard CS4 works pretty well, though.

[WINE AppDB Entry for CS5]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158")

[WINE AppDB Entry for CS4]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318")

---

### Post by adamtstop on 2010-12-20
Cs4 Portable and Lightroom portable 2.x work perfectly.

---

### Post by guile82 on 2011-02-08
try to run 

#wine /path/to/photoshop.exe

it works for me. 

I m using a script "run as root" on the exe of photoshop

i will try to find a fix to this. I its looks that is a permission problem, but I tried to change de owner, but still no go.

cump

---

### Post by guile82 on 2011-02-08
[http://ubuntuone.com/p/FdZ/](http://ubuntuone.com/p/FdZ/)

put this in .wine/c:/windows/winSxS

It works for me. No need to be root again.

I hope it helps


peace

---

### Post by guile82 on 2011-02-08
[B]Sorry the double post
[/B]

---

