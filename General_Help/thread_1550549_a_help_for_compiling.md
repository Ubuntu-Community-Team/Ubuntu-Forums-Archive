---
title: "a help for compiling"
date: 2010-08-11
forum: General Help
---

### Post by thelastblack on 2010-08-11
hi
i have downloaded a game(Warzone 2010) which is a source package
the prob is that i dont know how to compile it. i a bit newbie in linux. i have ubuntu lucid. so any help?
if u need any info plz tell here so that i give u.
thx

---

### Post by realzippy on 2010-08-11
Why don't you install directly from playdeb?

[http://www.unixmen.com/gaming-on-linux/448-warzone2100-for-ubuntu-and-debian](http://www.unixmen.com/gaming-on-linux/448-warzone2100-for-ubuntu-and-debian)


If you don`t want this,give a link to the package you want to compile....

---

### Post by anglican on 2010-08-11
> **thelastblack said:**
> hi
i have downloaded a game(Warzone 2010) which is a source package
the prob is that i dont know how to compile it. i a bit newbie in linux. i have ubuntu lucid. so any help?
if u need any info plz tell here so that i give u.
thxThere are instructions for compiling here:

[http://developer.wz2100.net/wiki/LinuxCompileGuide](http://developer.wz2100.net/wiki/LinuxCompileGuide)

Basically you need to install necessary package for the compilation (some may be already installed):
```
apt-get install build-essential automake flex bison libpng12-dev  libsdl1.2-dev libopenal-dev libphysfs-dev libvorbis-dev libtheora-dev  libglc-dev zip unzip libpopt-dev bisonc++
```unzip the archive:
```
tar xfz warzone2100-<version>.tar.gz
```(substitute <version> according to the file you downloaded)
change to the source directory:
```
cd warzone2100-<version>
```and run:
```
./configure --prefix=/opt/warzone2010-trunk
make
make install
```You can install different versions into different prefixes, if you want to run e.g. both trunk and 2.3.

H

---

### Post by thelastblack on 2010-08-11
thx u all
i dont have time to test it now but i will test ASAP....
thx again

---

