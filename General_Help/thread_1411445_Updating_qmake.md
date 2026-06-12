---
title: "Updating qmake"
date: 2010-02-19
forum: General Help
---

### Post by skytreader on 2010-02-19
Hello. I'm trying to install Stellarium on ubuntu 9.10. This being a freshmost installation, I first had to _sudo apt-get install cmake_ then _sudo apt-get install dev-essential_.

After I thought that everything is now fine, I proceeded with my installation. However, it seems that I still don't have qmake. So I did _sudo apt-get install qt4-qmake_.

I tried installing Stellarium again and I bumped into this error:
```
CMake Error at /usr/share/cmake-2.6/Modules/FindQt4.cmake:1426 (MESSAGE):
  The installed Qt version 4.5.2 is too old, at least version 4.6.0 is
  required
```So, my question: How do I get version 4.6.0?

Thanks!

---

### Post by darolu on 2010-02-20
Why don't you install it from the Software Centre, Synaptic or via apt-get?
```
sudo apt-get install stellarium
```

If you want to compile it anyways, I would recommend installing the build-essential and automake (if you don't already have them):
```
sudo apt-get install build-essential automake
```

I think you will have to manually compile qt 4.6 too, there is no qt 4.6 karmic package (that I know) available. You may get valuable info from this links:
[http://lists.trolltech.com/pipermail/qt4-preview-feedback/2009-December/001161.html](http://lists.trolltech.com/pipermail/qt4-preview-feedback/2009-December/001161.html)
[http://qt.nokia.com/downloads](http://qt.nokia.com/downloads)

---

### Post by skytreader on 2010-02-20
I wasn't aware of _sudo apt-get install stellarium_. That was neat darolu, thanks!

---

### Post by roil13 on 2010-03-28
> **darolu said:**
> Why don't you install it from the Software Centre, Synaptic or via apt-get?
```
sudo apt-get install stellarium
```

If you want to compile it anyways, I would recommend installing the build-essential and automake (if you don't already have them):
```
sudo apt-get install build-essential automake
```

I think you will have to manually compile qt 4.6 too, there is no qt 4.6 karmic package (that I know) available. You may get valuable info from this links:
[http://lists.trolltech.com/pipermail/qt4-preview-feedback/2009-December/001161.html](http://lists.trolltech.com/pipermail/qt4-preview-feedback/2009-December/001161.html)
[http://qt.nokia.com/downloads](http://qt.nokia.com/downloads)

I want to compile it because the version in the repositories is 0.10.2 which have some bugs regarding rtl languages.
I've installed QT4 by using the 2nd link and I'm still receiving the same error message.

---

### Post by stanz on 2011-01-15
> **roil13 said:**
> I want to compile it because the version in the repositories is 0.10.2 which have some bugs regarding rtl languages.
I've installed QT4 by using the 2nd link and I'm still receiving the same error message.

I've just run into needing qmake myself, for a [jacknsee]("http://sourceforge.net/projects/jacknsee/") program.
Unsure of using things outside the repo's, I'd be interested to know how
this worked out for you all.
Thanks.......

---

