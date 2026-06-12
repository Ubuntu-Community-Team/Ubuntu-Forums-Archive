---
title: "Make Deb file"
date: 2011-06-21
forum: General Help
---

### Post by bakegoodz on 2011-06-21
I downloaded a out of date deb file (not in repository) that has a dependency problem with Ubuntu 11.04 I was able to compile a new binary, it is just a simple command line program. I want to update my deb file with the new binary. I can extract the files from the deb with file roller, but how can I pack up the files into a new deb file. I already tried Checkinstall to create a deb from the source, but it doesn't work because the Make file doesn't support "make install" Any Ideas?

---

### Post by westie457 on 2011-06-21
> **bakegoodz said:**
> I downloaded a out of date deb file (not in repository) that has a dependency problem with Ubuntu 11.04 I was able to compile a new binary, it is just a simple command line program. I want to update my deb file with the new binary. I can extract the files from the deb with file roller, but how can I pack up the files into a new deb file. I already tried Checkinstall to create a deb from the source, but it doesn't work because the Make file doesn't support "make install" Any Ideas?

Hi, this is probably a good place to start

[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/]("http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/")

Never have tried to make my own package though. I might try one day.

---

### Post by bakegoodz on 2011-06-26
Found the answer! Use command: dpkg -b

---

