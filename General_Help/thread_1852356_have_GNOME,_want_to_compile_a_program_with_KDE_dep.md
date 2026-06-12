---
title: "have GNOME, want to compile a program with KDE dependencies"
date: 2011-09-30
forum: General Help
---

### Post by wannabegeek on 2011-09-30
Hi all,

I am running Gnome and would like to compile a cool program I downloaded which has  KDE dependencies.

I went ahead and tried to run a ./configure to see what errors I would get and the got:

```
checking for X... configure: error: Can't find X includes. 
Please check your installation and add the correct paths!
```

I am not very experienced with compiling software, can someone please advise me ?

TIA !

wbg

PS here's the program I'm trying to install:
[http://www.orcero.org/irbis/kradview/](http://www.orcero.org/irbis/kradview/)

---

### Post by sumski on 2011-09-30
You need libx11-dev package

EDIT:
You will also need qt3 and kdelibs4  -dev packages

---

### Post by oldos2er on 2011-09-30
Look for the files README and/or INSTALL, which should contain info on the dependencies you'll need to install.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware)

---

