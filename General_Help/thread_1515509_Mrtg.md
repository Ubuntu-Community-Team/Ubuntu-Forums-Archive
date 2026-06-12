---
title: "Mrtg"
date: 2010-06-22
forum: General Help
---

### Post by wsoxfan10 on 2010-06-22
I am trying to install MRTG to use with Nagios. I am running Ubuntu 9.10. I am trying to go through the preparation process listed in the MRTG documentation here:

[http://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html](http://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html). 

Going down the list I am stuck installing the gd library. I downloaded the latest source code and when I go through the motions to install it (sudo tar xzf, ./configure, make all, make install) I get errors.

When doing ./configure it checks for a lot of things and I get "no" for a bunch (if you need the entire output I will post it). Then at the end it says

Support for PNG library: no
Support for JPEG library: no
Support for Freetype 2.x library: no
Support for Fontconfig library: no
Support for Xpm library: no
Support for pthreads: yes

Am I supposed to install all of these packages first?

 Here are the "make all" errors at the end:

make [2]: *** [gdparttopng] Error 1
make [2]: Leaving directory '/home/tech/Downloads/gd-2.0.35'
make [1]: *** [all-recursive] Error 1
make [1]: Leaving directory '/home/tech/Downloads/gd-2.0.35'
make: *** [all] Error 2

Here are the "make install" errors:

collect2: ld returned 1 exit status
make [1]: *** [gdparttopng] Error 1
make [1]: Leaving directory '/home/tech/Downloads/gd-2.0.35'
make [1]: *** [install-recursive] Error 1

 I'm pretty confused on what to do. I've tried searching for answers, but nothing has worked.

---

### Post by LoloftheRings on 2010-06-22
Yup, you have to install those. I think they are called something like libpng-dev, not sure though. I'm currently on Arch Linux.
Just open up synaptics and look for the libraries.

---

