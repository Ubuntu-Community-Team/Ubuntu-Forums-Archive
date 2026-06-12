---
title: "Problems installing from tar.gz"
date: 2006-06-04
forum: General Help
---

### Post by sweeper on 2006-06-04
*I am trying to install from a tar.gz, I thought I was getting the hang of it but I am getting this*

stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ pwd
/home/stonerat/Desktop/turboprint-1.94-3
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ ls
bin doc locale rpm testmargins-letter.ps
BUGREPORT dump printers setup testpage-a4.ps
CHANGES INSTALLATION profiles system.cfg testpage-letter.ps
colors lib README testmargins-a4.ps uninstall
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ ./configure
bash: ./configure: No such file or directory
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ make
make: *** No targets specified and no makefile found. Stop.
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ sudo make install
make: *** No rule to make target `install'. Stop.
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ /configure
bash: /configure: No such file or directory
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ ./configure
bash: ./configure: No such file or directory
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ sudo checkinstall
sudo: checkinstall: command not found
stonerat@ubuntu:~/Desktop/turboprint-1.94-3$ make
make: *** No targets specified and no makefile found. Stop.

[I]It could be that I have no compiler tools but I downloaded 'build-essential' which I think covers it. You can see I am in the right folder for installing turboprint but it just isn't having it. Any ideas?

I tried using checkinstall[/I]

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs? [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
true_fopen == 0 for fopen64("/proc/mounts", "r")
make: *** No rule to make target `install'. Stop.

**** Installation failed. Aborting package creation.

Cleaning up...OK

Bye.




*I cannot see what I am doing wrong.*

*I would download the rpm version but, when I try to it opens Mplayer which I am using to stream radio as Realplayer causes Firefox to hang.*

---

### Post by tonyr on 2006-06-04
I don't see any **configure** file in your **ls** result.  My first instinct is
to read the **README** and **INSTALLATION** file and see what they say.

---

### Post by DoktorSeven on 2006-06-04
Read the README file; it seems like that isn't a typical source package, and you may have to do something different.

If [this](http://www.turboprint.de/) is the package you're installing, a quick look at the installation instructions on their site says you need to run the **setup** program:
```

./setup
```

---

### Post by sweeper on 2006-06-04
> **DoktorSeven]Read the README file said:**
> this[/url] is the package you're installing, a quick look at the installation instructions on their site says you need to run the **setup** program:
```

./setup
```

Thanks, sorry for the noobness :)

---

### Post by professor_chaos on 2006-06-04
from the output of your "ls" command, I can see no configuaration file or make files, so your definitely goind to have these problems. Maybe your in the wrong directory when executing these commands. 
I assume you already un-tarred/un-zipped this file and now are trying to install turboprint-1.94-3?

Take a look at the file INSTALLATION, as it is your best bet at documentation for install, or perhaps it is a script that you can run to install. Check to see if its executable.

---

