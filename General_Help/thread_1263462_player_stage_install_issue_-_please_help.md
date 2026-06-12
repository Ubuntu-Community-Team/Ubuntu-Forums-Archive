---
title: "player stage install issue - please help"
date: 2009-09-11
forum: General Help
---

### Post by liquidmonkey on 2009-09-11
not sure if u can help but i'm trying to install player v2.1.2 and stage v2.1.1 on UBUNTU 9.04

the player part installs just fine.
i can MAKE the stage but when i run the test on the website src/stest worlds/simple.world robot1
i get the following... bash: src/stest: No such file or directory

just for the fun of it i tried to MAKE INSTALL but no luck, the error

' /usr/bin/ld: cannot find -lstage
collect2: ld returned 1 exit status
libtool: install: error: relink `libstageplugin.la' with the above command before installing it
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/urmamma/Desktop/stage-
2.1.1/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/urmamma/Desktop/stage-2.1.1/src'
make: *** [install-recursive] Error 1
 '

comes up. any ideas? do the version numbers go ok together? we were told from our uni to install v2.1.1 so i matched it up best i could from the DL page.

thanks!

---

