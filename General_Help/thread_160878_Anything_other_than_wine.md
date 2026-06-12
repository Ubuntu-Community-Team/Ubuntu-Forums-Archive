---
title: "Anything other than wine"
date: 2006-04-15
forum: General Help
---

### Post by morbid_bean on 2006-04-15
Im wondering if there are any other programs just like wine out there because wine isnt workin on my ubuntu for some reason and dose to other people. If there is let me know PLEASE!! I use it for games (starcraft, diablo ii, half-life, etc.)

---

### Post by trent dillman on 2006-04-15
For games, try Cedega. It's pay software, but I believe you can install the cvs branch for free....

---

### Post by John.Michael.Kane on 2006-04-15
[http://www.win4lin.com/](http://www.win4lin.com/)
[http://www.linuxlinks.com/Software/Emulators/Videogames/index.shtml](http://www.linuxlinks.com/Software/Emulators/Videogames/index.shtml)
[http://www.emulator-zone.com/](http://www.emulator-zone.com/)
[http://en.wikipedia.org/wiki/Category:Linux_games](http://en.wikipedia.org/wiki/Category:Linux_games)

---

### Post by trent dillman on 2006-04-15
In case you're interested in Cedega:

```
sudo apt-get install cvs build-essential bison flex xlibs-dev
cd /opt
cvs -d:pserver:cvs@cvs.transgaming.org:/cvsroot login
Password: cvs
cvs -z3 -d:pserver:cvs@cvs.transgaming.org:/cvsroot co winex
cd winex
sudo ./configure
sudo make
sudo make install
```

---

