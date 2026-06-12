---
title: "how to compile programs?"
date: 2011-08-25
forum: General Help
---

### Post by princeofnam on 2011-08-25
I'd like to compile Cockatrice to play Magic but I don't know how to. 

--> [http://cockatrice.de/index.php?a=download](http://cockatrice.de/index.php?a=download)

The first step I tried failed

> x@y:~/Downloads/cockatrice-20110309/cockatrice$ ./configure
bash: ./configure: No such file or directory




---

### Post by WikedX on 2011-08-25
Open terminal
cd into the folder with the program(unzipped of course)

Type
./configure
make
make install

If ./configure doesnt work try ./config

---

### Post by seawolf167 on 2011-08-25
Take a look at [these]("https://help.ubuntu.com/community/CompilingEasyHowTo") links for [more]("https://help.ubuntu.com/community/CompilingSoftware") information.

---

### Post by sisco311 on 2011-08-25
[http://cockatrice.de/dokuwiki/doku.php?id=downloading_the_cockatrice_program](http://cockatrice.de/dokuwiki/doku.php?id=downloading_the_cockatrice_program)

scroll down the page for installation instructions.

---

### Post by princeofnam on 2011-08-25
Both "/.config" and "/.configure" didn't work

---

### Post by seawolf167 on 2011-08-25
its "./" since you are attempting to run something not in your $PATH variable, but in the current folder

---

### Post by bruno9779 on 2011-08-25
It uses qmake. Follow sisco311 advice

---

