---
title: "installation question"
date: 2006-03-07
forum: General Help
---

### Post by issueperson on 2006-03-07
I know to type this stuff (or something like it) in when i'm trying to install from source:

tar -xvzf obscure-1.0.tar.gz
cd obscure-1.0
[B]./configure
make
sudo make install[/B]

could someone explain to me what the last 3 lines are doing exactly?
i just want to know how this all works.

---

### Post by o_fortuna on 2006-03-07
[QUOTE=issueperson]I know to type this stuff (or something like it) in when i'm trying to install from source:

tar -xvzf obscure-1.0.tar.gz
cd obscure-1.0
[B]./configure
make
sudo make install[/B]

could someone explain to me what the last 3 lines are doing exactly?
i just want to know how this all works.[/QUOTE]
./configure runs a script within the source's directory, which configures the compile according to the libraries on your system. Depending on the program, this could take awhile as it must check tons of different libraries.

make does just what it sounds like it does. It makes the source into a binary by finding a "makefile" within the source directory which tells the compiler what to compile, link, etc.

make install takes the binary files created by make and installs them to the system based, once again, on a file within the source directory. This will, for example, copy binary files to /usr/bin so that they can be run from the command line without ./ .

Hope that helps. There is probably a tutorial somewhere that explains it better. That's what google is for ;)

---

### Post by taurus on 2006-03-07
./configure will look for all the dependencies on your system and it will create an appropriate Makefiles for it.  

Make is actually compiling the program.

And "sudo make install" installs the binaries, libraries, and docs into default directories unless you specify otherwise.  The reason you have to include "sudo" in front because you need a write access to system's directories like /usr/local.

---

### Post by issueperson on 2006-03-07
thanks.

every time i google installation i get directions on how to install.  no one explained it though...

---

