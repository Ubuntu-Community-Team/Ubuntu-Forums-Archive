---
title: "trying to enable MP4 support with Fuppes"
date: 2010-08-07
forum: General Help
---

### Post by Slow_MO on 2010-08-07
Hi,

i'm trying to install Fuppes with MP4 support but it wouldn't do it, instead i get the errors in the screenshots that would indicate that the mp4v2.h/mp4v2.h file is missing.

[http://yfrog.com/12screenshot2wtp](http://yfrog.com/12screenshot2wtp)

[http://yfrog.com/mnscreenshot3kp](http://yfrog.com/mnscreenshot3kp)

i already have the following packages installed:

1. libmpeg4ip-dev
2. libmp4v2-dev

i'm not sure what other packages i'm missing so any help would be appreciated.

thanks.

---

### Post by gnivler on 2010-12-11
Had and fixed the same issue, as follows.  Not sure why the packages do not install the .h files as expected (I'm not a developer).

First off, remove those two packages:
```
sudo apt-get remove libmp4v2-0 libmp4v2-dev
```

Then download the source, most recent link:
[http://mp4v2.googlecode.com/files/mp4v2-1.9.1.tar.bz2](http://mp4v2.googlecode.com/files/mp4v2-1.9.1.tar.bz2)

Unpack it and configure it and compile it:
```
tar xvjf mp4v2-1.9.1.tar.bz2
cd mp4v2-1.9.1
./configure --prefix=/usr
make
sudo make install
sudo ldconfig
```

Not sure if you NEED to run ldconfig at the end but it doesn't hurt.
Reconfigure fuppes as before: 
```
checking mp4v2/mp4v2.h usability... yes
checking mp4v2/mp4v2.h presence... yes
checking for mp4v2/mp4v2.h... yes
```

---

