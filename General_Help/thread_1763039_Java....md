---
title: "Java...?"
date: 2011-05-19
forum: General Help
---

### Post by searinglead15 on 2011-05-19
I'm running Ubuntu 11.04, and everytime I install anything with apt-get this message pops up:

The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.24-1build0.10.10.1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.24-1build0.10.10.1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I had tried getting Java so I could run Minecraft through the browser, which didnt really work, and I kinda forgot about it.. but I don't want to leave this error. What should I do, both to fix this and possibly get minecraft running on Ubuntu? Thanks

---

### Post by hulkman on 2011-05-20
This happens many times if a package was installed but it could not install all the dependencies.  Most the time you can fix it by entering the following command into the terminal:

sudo apt-get -f install

If that doesn't work then I would try uninstalling sun-java6-jre by entering the following command into the terminal: (Note: this may disable some features on your computer which need java.)

sudo apt-get remove sun-java6-jre

and then again entering the first command I gave into the terminal.

sudo apt-get -f install

-------------------------
Check out the deb packages available at [http://www.dotdeb.com](http://www.dotdeb.com)

---

### Post by linuxinstalledfromhdd on 2011-05-20
Sounds like you don't have all the repositories open..

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by wildmanne39 on 2011-05-20
> **searinglead15 said:**
> I'm running Ubuntu 11.04, and everytime I install anything with apt-get this message pops up:

The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.24-1build0.10.10.1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.24-1build0.10.10.1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I had tried getting Java so I could run Minecraft through the browser, which didnt really work, and I kinda forgot about it.. but I don't want to leave this error. What should I do, both to fix this and possibly get minecraft running on Ubuntu? ThanksHi, and you do have to accept the liceince agreement.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Always need to watch for the EULA agreement.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Minecraft can be installed with a script file over here..  A cake walk of an installation.

[http://cinderbox.net/2011/04/19/games-minecraft-for-ubuntu-installation-script/](http://cinderbox.net/2011/04/19/games-minecraft-for-ubuntu-installation-script/)

---

