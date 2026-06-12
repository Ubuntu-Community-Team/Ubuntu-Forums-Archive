---
title: "wine won't work on Ubuntu 10.10 64-bit?"
date: 2011-05-01
forum: General Help
---

### Post by emmiesix on 2011-05-01
I'm running Maverick on a 64-bit Dell laptop.  I have uninstalled and re-installed wine 1.3 from the repository, but I still get this error any time I use it:

wine BYKIDownloaderPC.exe 
wine: error while loading shared libraries: /usr/bin/../lib32/libpthread.so.0: invalid ELF header

What am I doing wrong?  This library issue seems to have persisted for a while now (basically the whole time I've used 10.10.  It gives similar errors when using Acrobat, for instance.  Normally when I have a problem I'm not alone. This time google/ubuntuforums searches got me nothing useful.

Please help!

---

### Post by wolfen69 on 2011-05-01
> **emmiesix said:**
> Normally when I have a problem I'm not alone. This time google/ubuntuforums searches got me nothing useful.


Well, wine in 10.10 64 worked flawlessly for me and a friend of mine. I know this doesn't help, but at least your thread is getting a bump.

---

### Post by 3Miro on 2011-05-01
1. Check winehq forum for information about the specific program that you are trying to run with wine. They are the wine experts and the right place to do this.

2. Check if you have libpthread installed. You can do that form Synaptic Package Manager (System -> Admin -> Synaptic).

---

### Post by Bas232 on 2011-12-07
Same problem here under 10.04 64bit, it won't run and complains about the libraries, no matter what I do, it keeps giving this error:

error while loading shared libraries: /usr/bin/../lib32/libpthread.so.0: invalid ELF header

Tried all versions of Wine, reinstalled several libraries, nothing works.

---

### Post by oldtimer7777 on 2011-12-07
I would recommend installing Wine from the PPA.  It is about 1/3rd the way down this walk-through..  Make sure you aren't missing anything else on the checklist either:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **emmiesix said:**
> I'm running Maverick on a 64-bit Dell laptop.  I have uninstalled and re-installed wine 1.3 from the repository, but I still get this error any time I use it:

wine BYKIDownloaderPC.exe 
wine: error while loading shared libraries: /usr/bin/../lib32/libpthread.so.0: invalid ELF header

What am I doing wrong?  This library issue seems to have persisted for a while now (basically the whole time I've used 10.10.  It gives similar errors when using Acrobat, for instance.  Normally when I have a problem I'm not alone. This time google/ubuntuforums searches got me nothing useful.

Please help!

---

