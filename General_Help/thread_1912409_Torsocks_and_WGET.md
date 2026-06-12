---
title: "Torsocks and WGET"
date: 2012-01-20
forum: General Help
---

### Post by alphaamanitin on 2012-01-20
Anyone know how to do this?

[http://code.google.com/p/torsocks/](http://code.google.com/p/torsocks/)

Using Ubuntu 9.10 and 10.04.  Downloaded, untarred, and tried to install following the instructions.  Not sure I understand their install instructions:
To Compile from CVS/SVN```



  make -f Makefile.cvs
  ./configure
  make
  make install

```I know it doesn't work.  I assume it is something to do with the CVS/SVN.  

Also, anyone know about using tor and privoxy at the same time?

AlphaA

---

### Post by alphaamanitin on 2012-01-21
Think I may have been doing it wrong.  Found these instructions on what to do after getting torsocks via git:```
./autogen.sh
./configure
make
sudo make install
```

Didn't get torsocks via get [downloaded directly via website], but will try it when I get home from the lab tonight.  Will mark thread as solved if it works.

AlphaA

---

### Post by alphaamanitin on 2012-01-22
There was no ./autogen, but if you follow the rest of it works.  

Tested this, used these to codes:```
usewithtor wget https://check.torproject.org
``` 
This results in the html page that says Congratulations, blah blah blah, you are using tor. 
```
wget http://check.torproject.org
```
This results in the html page that says "You SUCK!!!"  Nah, it just says you are not using tor.

AlphaA

---

