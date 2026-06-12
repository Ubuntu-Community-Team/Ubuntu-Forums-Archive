---
title: "winetricks - how to reinstall previously downloaded runtime libraries offline?"
date: 2010-03-02
forum: General Help
---

### Post by thed2010 on 2010-03-02
hello all.

i am running ubuntu 8.10 (intrepid) with wine (1.0.1).

when using the latest winetricks file (VERSION=20100201) to download various runtime libraries to enable my system for Microsoft Word 2007 use, for example by running:

~$ sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1

the downloads and subsequent file installs are successful and Word 2007 runs fine.

the runtime libraries are downloaded to ~/.winetrickscache


what i would like to do is archive the downloaded files located in ~/.winetrickscache, and reinstall these files (sometime in the future) offline, without any reliance on an internet connection.

i don't always have an internet connection, and so i would like a way to reinstall these files on subsequent new installs of intrepid without relying on an internet connection.

is there a way of running winetricks so that winetricks installs archived runtime files, which can be placed in a user-made ~/.winetrickscache folder?

this option would allow me to clean my drive, and then reinstall intrepid, wine and the MS runtime files without the need for an internet connection.  

any specific help would be greatly appreciated.

regards,

thed

.

---

### Post by thed2010 on 2010-03-02
following an initial download and install of any runtime libraries through winetricks, archive the contents of the ~/.winetrickscache directory.

if you need to reinstall the same runtime file(s), say, after a clean install of ubuntu/wine, create a .winetrickscache directory in your home directory (~/.winetrickscache), place your archived runtime files/directories within this directory, and execute winetricks in a terminal window as before to install the runtime libraries located within ~/.winetrickscache. no internet connection is needed when reinstalling from archived/cached files.

i hope this can help. thanks.

thed

.



.

---

