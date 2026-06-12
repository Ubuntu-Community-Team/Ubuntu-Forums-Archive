---
title: "/usr/bin/ld: cannot find -lXi"
date: 2011-05-15
forum: General Help
---

### Post by Jonnyishman on 2011-05-15
Good day.

I'm currently trying to install geant4 onto Ubuntu 10.10. 

I'm following these instructions here [http://conquer-ur-computer.blogspot.com/2011/02/how-to-install-geant4-in-ubuntu-linux.html](http://conquer-ur-computer.blogspot.com/2011/02/how-to-install-geant4-in-ubuntu-linux.html) to do so. 

It was well up until I had to ./Configure -build when the following kept coming up

/usr/bin/ld: cannot find -lXi
collect2: ld returned 1 exit status

The same comes up when I try to make any of the examples.

Anyone know what I'm doing wrong?

Cheers

---

### Post by gmargo on 2011-05-15
Install the **libxi-dev** package and give it another try.

---

