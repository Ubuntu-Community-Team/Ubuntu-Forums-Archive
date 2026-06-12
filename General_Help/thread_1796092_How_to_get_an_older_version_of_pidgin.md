---
title: "How to get an older version of pidgin ?"
date: 2011-07-03
forum: General Help
---

### Post by RaiGal on 2011-07-03
Hello everyone,
My favorite IM application, Pidgin,have been causing me some problems with it's new release (2.9.0).More specifically I can't see friends which are visible in normal versions of MSN or hotmail web interface, even though I have searched any options available thoroughly. Also some of my contacts can see me online but cannot message me.

Therefore, I would like to install an older version to find out whether these problems are version or application related. However the only available version is 2.9.0 and I would like to downgrade to an older version,let's say 2.6.0 but I have no idea on how to do that. 

Help much appreciated,thanks guys! :KS

---

### Post by Enigmapond on 2011-07-03
In Synaptic, select the search for the package then hit the "package" tab on top/Force Version, which should bring up a pick-list....

---

### Post by in-dust-rial on 2011-07-03
hey there,
so I wrote several kinds of solutions according to different kinds of skill and or lazyness.



RECOMMENDED SOLUTION:
did you have a look at this page
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)
and look at the packages available there? via aptitude update and search
(maybe there is no old package ... but you have to see for yourself)

QUICK AND DIRTY:
search an DEB-package 
for example here:
[http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=all&section=all)
or here:
[http://packages.debian.org/search?keywords=pidgin](http://packages.debian.org/search?keywords=pidgin)
and install it via DPKG -i
(remember to chose "distribution == any" for your search)


MORE RELIABLE BUT MORE COMPLICATED:
[http://sourceforge.net/projects/pidgin/files/Pidgin/](http://sourceforge.net/projects/pidgin/files/Pidgin/)
download the RPM 
and indirectlz install it
[http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/](http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/)

MORE HARD but even MORE RELIABLE SOLUTION:
otherwise you can also build the version of your desire by make install:
source code
[http://developer.pidgin.im/wiki/UsingPidginMonotone](http://developer.pidgin.im/wiki/UsingPidginMonotone)
how to make install
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)
(just the first hit on my google request)


hope this helps!


p.s.:
i would go from here :D
[http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=all&section=all)

---

### Post by in-dust-rial on 2011-07-03
okay, the synaptic solutions sounds very fine too 

even though I cannot test it it seems to be most elegant 
:D

---

### Post by dcstar on 2011-07-04
> **in-dust-rial said:**
> 
.........
QUICK AND DIRTY:
search an DEB-package 
for example here:
[http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=all&section=all)
or here:
[http://packages.debian.org/search?keywords=pidgin](http://packages.debian.org/search?keywords=pidgin)
and install it via DPKG -i
(remember to chose "distribution == any" for your search)
.........

There is **no** reason to use command line when installing a downloaded .deb package from the Ubuntu packages site, simply select it in Nautilus and the Package Installer will run.

---

### Post by RaiGal on 2011-07-13
Worked out okay, thank you guys! :)

---

