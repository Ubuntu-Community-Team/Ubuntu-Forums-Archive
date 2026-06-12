---
title: "Trying to install some things but errors"
date: 2006-06-25
forum: General Help
---

### Post by CameronCalver on 2006-06-25
Hello whenever i install something from a .tar.gz i do ./configure and at then end it says checking for libz and it says not found and then when i do make and make install it says make:

 *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

so i download the .rpm and alien it to a deb and it installs then i run it and it says
kguitar: error while loading shared libraries: libkparts.so.1: cannot open shared object file: No such file or directory

---

### Post by aysiu on 2006-06-25
How about [enabling extra repositories](http://www.psychocats.net/ubuntu/sources) and then doing this? ```
sudo aptitude update
sudo aptitude install kguitar
```

---

### Post by CameronCalver on 2006-06-25
ok 1stly what if i want to install another program and i get that error can idownload that file and that kguitar crashes when you open a song thats is .gp3

---

### Post by CameronCalver on 2006-06-25
when i try to run something from it it crashes

---

