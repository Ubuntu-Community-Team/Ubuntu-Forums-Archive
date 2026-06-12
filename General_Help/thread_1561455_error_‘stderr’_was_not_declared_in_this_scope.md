---
title: "error: ‘stderr’ was not declared in this scope"
date: 2010-08-26
forum: General Help
---

### Post by firens on 2010-08-26
Hello,

i have this error when i tried to compil a program :

jacktrip_globals.cpp: In function ‘int set_fifo_priority(bool)’:
jacktrip_globals.cpp:146: error: ‘stderr’ was not declared in this scope
jacktrip_globals.cpp:148: error: ‘fprintf’ was not declared in this scope
jacktrip_globals.cpp:158: error: ‘stderr’ was not declared in this scope
jacktrip_globals.cpp:159: error: ‘fprintf’ was not declared in this scope
jacktrip_globals.cpp: In function ‘int set_realtime_priority()’:
jacktrip_globals.cpp:177: error: ‘perror’ was not declared in this scope
make[1]: *** [release/jacktrip_globals.o] Erreur 1
make[1]: quittant le répertoire « /media/DATA/jacktrip/src »
make: *** [release] Erreur 2
someone would have already encountered the same problem or would have an idea?

Thk ;)

---

### Post by spjackson on 2010-08-26
```
#include <stdio.h>
```

---

### Post by firens on 2010-08-26
Thk spjackson...but i have already tried to put this line in the file jacktrip_globals.cpp but i didn't see any change :/

---

### Post by Vaphell on 2010-08-26
shouldn't you use <iostream> in C++? stdio.h is more like C
do you have build-essential package installed?

---

### Post by firens on 2010-08-26
In fact i'm trying to compile a programm which call jacktrip....i've allready had problem with another ".h" like QThread and jack.h etc...so i've installed qt4-dev-tools and jack audio...but the problem was still here ??!!...i had to put the .h in the program file and for this part everything has been settled...

it just remains this problem with stderr etc...
[COLOR=#000000]I also tried to put in the file [/COLOR]jacktrip_globals.cpp[COLOR=#000000]  an #include iostream.h  but nothing changed

[/COLOR]

---

### Post by Vaphell on 2010-08-26
#include <iostream> is enough (no .h)

when you do **locate c++**, do you get a bunch of /usr/include/c++ in the output?

---

### Post by firens on 2010-08-26
> **Vaphell said:**
> #include <iostream> is enough (no .h)

when you do **locate c++**, do you get a bunch of /usr/include/c++ in the output?

yes  :

```

/usr/include/c++
/usr/include/c++/4.4
/usr/include/c++/4.4.3
/usr/include/c++/4.4/algorithm

etc.....

```

---

### Post by Vaphell on 2010-08-26
i forgot you compile some ready code, so you need that stdio.h
i assume you have it (**locate stdio.h**), for whatever reason compilator doesn't find it

[http://ubuntuforums.org/showthread.php?t=462153](http://ubuntuforums.org/showthread.php?t=462153)
maybe some suggestion here will help

---

### Post by firens on 2010-08-26
> **Vaphell said:**
> i forgot you compile some ready code, so you need that stdio.h
i assume you have it (**locate stdio.h**), for whatever reason compilator doesn't find it

[http://ubuntuforums.org/showthread.php?t=462153](http://ubuntuforums.org/showthread.php?t=462153)
maybe some suggestion here will help

Thank you that's better....but now :/

```

JackTripWorker.h:89: error: ‘uint32_t’ has not been declared
JackTripWorker.h:90: error: ‘uint16_t’ has not been declared
JackTripWorker.h:90: error: ‘uint16_t’ has not been declared
JackTripWorker.h:105: error: ‘uint16_t’ does not name a type
JackTripWorker.h:108: error: ‘uint16_t’ does not name a type
JackTripWorker.cpp:82: error: prototype for ‘void JackTripWorker::setJackTrip(int, quint32, quint16, quint16, int)’ does not match any in class ‘JackTripWorker’
JackTripWorker.h:89: error: candidate is: void JackTripWorker::setJackTrip(int, int, int, int, int)
JackTripWorker.cpp: In member function ‘virtual void JackTripWorker::run()’:
JackTripWorker.cpp:118: error: ‘mServerPort’ was not declared in this scope
JackTripWorker.cpp:119: error: ‘mClientPort’ was not declared in this scope


```

I'm desperate :(

---

### Post by firens on 2010-08-26
I find the problem....stdint.h has not been declared in the file...well...it runs now :)

Thank you very much for the help

---

