---
title: "problems installing with ./configure"
date: 2006-06-15
forum: General Help
---

### Post by mrmustardman on 2006-06-15
I am trying to install lmms, which comes with the configure file and the makefile file. when i give the command ./configure, it returns
"checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details."

any ideas?
or any other way i can install this,,,?:confused:

---

### Post by xXx 0wn3d xXx on 2006-06-15
[QUOTE=mrmustardman]I am trying to install lmms, which comes with the configure file and the makefile file. when i give the command ./configure, it returns
"checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details."

any ideas?
or any other way i can install this,,,?:confused:[/QUOTE]
Do you have build-essential installed ?
> sudo apt-get install build-essential

---

### Post by mrmustardman on 2006-06-15
thanks i didnt have that now i get a new error:
"checking QTDIR... configure: error: *** QTDIR must be defined, or --with-qtdir o ption given"

---

### Post by vigleik on 2006-06-15
[QUOTE=mrmustardman] or any other way i can install this,,,?:confused:[/QUOTE]

Did you try "sudo apt-get install lmms"? It's in the repositories, though I'm not sure which one. Maybe you have to enable some more sources.

There's a discussion going on about whether or not to include build-essential in the default install. One of the reasons it's not there is that they want to encourage people not to compile programs themselves, when there's a much easier way to install things.

Sooner or later you'll run into a program which is not in the repositories, but in this case you should be able to install it with apt-get.

Vigleik

---

