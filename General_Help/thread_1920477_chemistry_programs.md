---
title: "chemistry programs"
date: 2012-02-04
forum: General Help
---

### Post by conradin on 2012-02-04
Hi all,
ive been working for the last few days trying to get atomtv, and moviemol some really ancient molecular modeling programs to work on modern Linux systems, to no avail. These programs where intended for SGI IRIX computers, and Im having general torment to get them working anywhere else. If anyone is familiar with these programs, can you tell me if there is something else similar that works in modern linux environments?

---

### Post by Rodney9 on 2012-02-04
I'm not familiar with those programs but have you had a look through the Science and Engineering section of the Software Center.

Rodney

---

### Post by llamabr on 2012-02-04
> **conradin said:**
> Hi all,
ive been working for the last few days trying to get atomtv, and moviemol some really ancient molecular modeling programs to work on modern Linux systems, to no avail. These programs where intended for SGI IRIX computers, and Im having general torment to get them working anywhere else. If anyone is familiar with these programs, can you tell me if there is something else similar that works in modern linux environments?

I don't know.  See below.  But if you're trying to run something intended for IRIX, why don't you just install IRIX?  Anyway:

```
brock@vader:~$ apt-cache search chemistry | grep hemistry
libcdk-java - Chemistry Development Kit (CDK) Java libraries
education-chemistry - Debian Edu chemistry related applications
science-chemistry - Debian Science Chemistry packages
garlic-doc - [Chemistry] a molecular visualization program - documents
gcu-bin - GNOME chemistry utils (helper applications)
gcu-plugin - GNOME chemistry utils (browser plugin)
libgcu-dbg - GNOME chemistry utils (debugging symbols)
libgcu0 - GNOME chemistry utils (library)
kalzium - periodic table and chemistry tools for KDE
libchemistry-elements-perl - Perl extension for working with Chemical Elements
libchemistry-formula-perl - enumerate elements in a chemical formula
libmopac7-1gf - Semi-empirical Quantum Chemistry Library (library)
libmopac7-dev - Semi-empirical Quantum Chemistry Library (development files)
mopac7-bin - Semi-empirical Quantum Chemistry Library (binaries)
mpqc-openmpi - The Massively Parallel Quantum Chemistry Program (OpenMPI Version)
mpqc - The Massively Parallel Quantum Chemistry Program
viewmol - A graphical front end for computational chemistry programs.
brock@vader:~$ 

```

---

### Post by imachavel on 2012-02-05
download this:

[http://spdbv.vital-it.ch/download.html](http://spdbv.vital-it.ch/download.html)

it will appear in downloads folder. try to unzip it in the directory of your choosing. Now open up the folder and find the .exe, right click on the file, go to permissions, then where it says

execute:     (check box) Allow executing file as a program

put a check mark in the execute box

now right click on spdbv.exe, and chose to open with wine, it should open up as swiss-pdbviewer 4.0.4. Enjoy now! Also, I don't have a clue as to how this thing works, you'll have to meet me back at xchat and give me some pointers :popcorn:

---

### Post by conradin on 2012-02-07
IRIX hasnt had a release since 1998, and using IRIX sux. Using IRIX any further into the future is exactly what I want to avoid. Additionally, SGI was sold to open rack in 2010, and these computers running the programs are from 1991-98 14yrs old! thats like 140 in computer years! (I met a Fedora dev who did that constantly...)

There are also dos ports for moviemol but I dont want to go back to DOS either.

[QUOTE=llamabr;11664983]I don't know.  See below.  But if you're trying to run something intended for IRIX, why don't you just install IRIX?  Anyway:

---

