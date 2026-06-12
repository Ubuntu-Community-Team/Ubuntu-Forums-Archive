---
title: "amarok crash on startup"
date: 2006-01-21
forum: General Help
---

### Post by tonyo46 on 2006-01-21
Hello !

I installed amarok on my Ubuntu Breezy, but I can't use it because of this error when I start the program :

> 
amarok could'nt find any sound extension engine. amarok is updating the configuration database of KDE. Please, wait a minute, and then start again amaroK.

If it doesn't help you, it's posible that amaroK is installed under a erroneous prefix, please correct your installation using :
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$amaroK


That is what I can see in the terminal :
> 
$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokap p.
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-antoine/ksycoca'!
kbuildsycoca: Wrong permissions on directory? Disk full?
kio (KMimeType): WARNING: KServiceType::offers : servicetype amaroK/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype amaroK/Plugin not found
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-antoine/ksycoca'!
kbuildsycoca: Wrong permissions on directory? Disk full?
amaroK: [Loader] amaroK is taking a long time to load! Perhaps something has gone wrong?


I tried to solve the problem installing those packages : amarok-engines, amarok-arts, amarok-xine, but it didn't change anything !! (the packages amarok and amarok-gstreamer were already installed)

Finally, I don't know how can I solve this problem ? :???:
thank you for your help,
tonyo

---

### Post by Ulrik on 2006-01-28
As indicated, it appeared to be a permission problem with /var/tmp/kdecache-ulrik/ksycoca

Somebody else on this forum suggested a very elaborate procedure involving an upgrade to KDE 3.5, but the following seemed to do the trick for me:

> sudo chmod 777 /var/tmp/kdecache-ulrik/ksycoca

If this is somehow wrong, let med know.

---

