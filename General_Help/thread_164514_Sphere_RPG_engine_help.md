---
title: "Sphere RPG engine help"
date: 2006-04-22
forum: General Help
---

### Post by dracule on 2006-04-22
I was recently trying to compile the sphere rpg engine from source forge to no avail. can you help please? i found no documentation on how to compile it and was wondering if there was debian package with it. If any of you use or used sohere rpg engine please help me!!

---

### Post by Chickenmonger on 2006-04-22
Looks like Linux compilation instructions are in the following file:

[http://sphere.sourceforge.net/flik/files/linux.txt](http://sphere.sourceforge.net/flik/files/linux.txt)

The instructions are for an RPM-based distribution, so you'll most likely have to search with Synaptic for the required libraries. Sorry I can't be more help, as I rarely, if ever, compile Linux software from source.

---

### Post by tunginobi on 2007-01-19
[http://www.spheredev.org/wiki/Sphere:Latest]("http://www.spheredev.org/wiki/Sphere:Latest")

Read the recently-added Linux notes and Ubuntu section.

* SpiderMonkey (libsmjs, for JavaScript)
* Audiere (for sound)
* Corona (for images) 

Recommended:
* wxWidgets (for the Linux Sphere editor)
* libmng (for MNG support; think PNG images, but animated like GIFs)
* scintilla (for the script editor)
* zlib (just for the SPK file format, but still required) 

You can install most dependencies from the excellent Ubuntu repositories. [Corona]("http://corona.sourceforge.net/") you'll need to grab and install from source.

Some people have run into problems with Audiere and Corona not being found. The library symlinks aren't set up right or something, you need to copy the library-name.so files manually from the make dir's src/.lib/ directory (e.g. for Corona: cp corona-1.0.2/.libs/libcorona-1.0.2.so /usr/lib).


There's no deb package yet, but if a package for Corona is made, a Sphere package should be easy.

---

