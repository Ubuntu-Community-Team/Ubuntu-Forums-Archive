---
title: "programs will not run in wine"
date: 2009-12-26
forum: General Help
---

### Post by mkeyes001 on 2009-12-26
so I've installed ubuntu 9.10 and ran the apt-get install wine & winecfg which completed good (I think).   I installed ACDSee using wine but cannot get the program to run.  So I thought maybe it was just this program.  I then tried to install photoshop cs4 using the wine setup.exe command from the directory and I get nothing, it will not begin the installation.  What am I doing wrong? I also tried installing an older version of itunes, it 8.2.3 I think and it also isn't working, I get an error message and it backs out.  Any ideas?

---

### Post by blackened on 2009-12-26
> **mkeyes001 said:**
> so I've installed ubuntu 9.10 and ran the apt-get install wine & winecfg which completed good (I think).   I installed ACDSee using wine but cannot get the program to run...

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=299]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=299")

> ...So I thought maybe it was just this program.  I then tried to install photoshop cs4 using the wine setup.exe command from the directory and I get nothing, it will not begin the installation...

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318")

> ...What am I doing wrong? I also tried installing an older version of itunes, it 8.2.3 I think and it also isn't working, I get an error message and it backs out.  Any ideas?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

[http://appdb.winehq.org](http://appdb.winehq.org) is always the place to start if you have wine compatibility questions.

---

### Post by Mark Phelps on 2009-12-26
> **mkeyes001 said:**
> .. What am I doing wrong? ...

You're making the mistake of presuming that any MS Windows programs will run in Wine, when in fact, only a few do.

The links that blackened provided you should provide some clues as to how you're wasting your time with Wine.

As already said, you should check WineHQ before you install anything in Wine -- can save you a lot of time and frustration.

---

### Post by blackened on 2009-12-27
> **Mark Phelps said:**
> ...how you're wasting your time with Wine.

I wouldn't exactly take as hardline a stance on Wine as you have, mainly because I've had very good luck with the programs that I've tried to run with it. That said, if you're attempting to run bleeding-edge stuff in Wine, then you will be sorely disappointed.

Wine is a compatibility layer and nothing more. It is not Windows, and will probably never be a true replacement for Windows. Sometimes it works, sometimes it doesn't. Save yourself some potential heartache and use the appDB.

---

